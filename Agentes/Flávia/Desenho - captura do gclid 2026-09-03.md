---
title: Desenho — captura e fluxo do gclid (atribuição Google Ads)
tags: [gclid, gtm, sgtm, firestore, atribuicao, google-ads, desenho-tecnico]
gerado: 2026-09-03
status: proposta-para-aprovacao
---

# Desenho técnico — captura do gclid de ponta a ponta

> Objetivo: fazer o clique do Google Ads (`gclid`) atravessar todo o funil e chegar na conversão `compra_erp`, fechando a atribuição. Hoje ele está **órfão** (ver diagnóstico abaixo).

## Diagnóstico — onde o gclid se perde hoje

```
Clique Google Ads → URL ?gclid=XXXX (cookie first-party _gcl_aw)
   ↓
Site (Magento PWA) → GTM client-side GTM-MMGX8ZL
   ↓  captura gclid via cookie __k, mas NÃO persiste (usa só no disparo imediato)
begin_checkout → request → gtmserver.conamore.com.br (sGTM)
   ↓  client GA4 server-side injeta x-ga-gdid = PLACEHOLDER (dY2E1Nz.dNzQzZD)
Firestore init_checkout_web ← grava evento (com gdid placeholder, SEM gclid real)
   ↓
Pagamento confirmado → webhook Increazy /purchase_erp
   ↓  sGTM pesquisa Firestore por id_cart → recupera utm/session/user_data (NÃO gclid)
Conversão compra_erp → GA4/Ads SEM gclid → atribuição órfã
```

**Raiz (3 pontos de quebra):**
1. Client-side não persiste o gclid.
2. Server-side não tem variável `gclid`/`gdid` (0 em 113 vars / 44 tags / 2 transforms).
3. Firestore grava o evento, mas o campo de clique do Ads chega placeholder.

## Fluxo alvo (corrigido)

```
Clique Google Ads → ?gclid=XXXX / cookie _gcl_aw
   ↓
[1] CLIENT-SIDE (GTM-MMGX8ZL)
    capturar gclid (URL param ou cookie _gcl_aw) → persistir em cookie first-party
    → incluir gclid no request do begin_checkout (event data)
   ↓
[2] SERVER-SIDE (GTM-N7Z62R96) — entrada
    client GA4 injeta x-ga-gclid REAL (não placeholder)
    → nova variável "ED - x-ga-gclid" (ed) lendo do event data
   ↓
[3] FIRESTORE — gravação
    tag Firestore Writer init_checkout_web grava o gclid (addEventData=true já grava
    se o campo estiver no event data) junto com utm/session/client_id
   ↓
[4] SERVER-SIDE — pagamento
    webhook Increazy /purchase_erp → sGTM pesquisa Firestore por id_cart
    → nova variável "Consulta Firestore - x-ga-gclid" (fs)
   ↓
[5] CONVERSÃO — injeção
    transformação "Incluir Parâmetros x-ga" (id 229) passa a incluir x-ga-gclid
    → tag GA4 compra_erp + Google Ads enviam gclid → atribuição fecha
```

## Peças a criar/alterar (por camada)

### A. Client-side (GTM-MMGX8ZL — Matias, outra conta)
- [ ] Variável de URL/cookie para ler `gclid` (ou cookie `_gcl_aw`).
- [ ] Persistir o gclid em cookie first-party (ou incluir no `dataLayer`/request do begin_checkout).
- [ ] Garantir que o request pro server-side leve o `gclid` (o client GA4 server-side lê dele automaticamente).
- ⚠️ Consent Mode quebrado (29/08) pode bloquear a leitura — resolver junto (Matias + Adrian).

### B. Server-side (GTM-N7Z62R96 — Matias)
- [ ] Variável **"ED - x-ga-gclid"** (type `ed`) lendo o gclid do event data.
- [ ] Variável **"Consulta Firestore - x-ga-gclid"** (type `fs`) lendo o gclid gravado no Firestore (espelho das demais "Consulta Firestore - x-ga-*").
- [ ] Atualizar a transformação **"Incluir Parâmetros x-ga"** (id 229, `tf_augment_event`) para também injetar `x-ga-gclid` na tag `compra_erp` (e não só dma/ecid/session).

### C. Firestore (projeto agile-kite-392211 — sem mudança)
- Nada: `addEventData=true` já grava o gclid se ele estiver no event data.
- (Complementar) Reativar `increazy-erp`/`increazy-site` com as 2 tags espelho (passo a passo separado).

## Ordem de execução
1. **Client-side persistir gclid** (pré-requisito — sem isso o resto não tem dado real).
2. **Server-side variável `ED - x-ga-gclid`** (ler na entrada).
3. **Confirmar gravação no Firestore** (`init_checkout_web` passa a ter gclid real).
4. **Server-side variável `fs` + transformação** (ler de volta e injetar na conversão).
5. **Validar end-to-end**: clique de teste → begin_checkout → pagamento → conversão com gclid no GA4/Ads.

## Validação
- DebugView do GA4 / Preview do sGTM: conferir `x-ga-gclid` preenchido (não placeholder).
- Firestore: `init_checkout_web` com doc recente contendo `gclid` real.
- Google Ads: conversão `compra_erp` com atribuição ao clique (não mais "não atribuída").

## Donos / aprovações
- Client-side + server-side = **Matias (TI)**.
- Consent Mode / LGPD = **Matias + Adrian**.
- Aprovação de escopo = **Sérgio / DigitalCEO**.

## Observações
- `gdid` ≠ `gclid`: o que aparece hoje (`x-ga-gdid`, placeholder) é um artefato do protocolo GA4; o que importa para a atribuição do Ads é o **`gclid`**.
- A service account atual só acessa a conta do server-side (`6100042948`); o client-side (`GTM-MMGX8ZL`) está em outra conta → Matias precisa liberar acesso (ou executar ele mesmo).
