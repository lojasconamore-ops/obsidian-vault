---
title: Relatório Executivo — Atribuição de Vendas B2B ao Google Ads (diagnóstico consolidado)
tags: [atribuicao, google-ads, compra_erp, firestore, gclid, debx, gap, relatorio]
gerado: 2026-09-03
autor: Flávia (Marketing)
aprovacao: Sérgio / DigitalCEO
---

# Atribuição de Vendas B2B ao Google Ads — Diagnóstico Consolidado

> **Tese central:** o Google Ads está otimizando (Smart Bidding) com **~15–20% do sinal real de receita**. A venda B2B não fecha no clique, e a ponte "clique → pedido faturado no DEBX" está quebrada em **4 camadas independentes** que se somam.

---

## 1. Gap de cobertura — Increazy captura só ~46% do PED (e 0% do físico)

Janela: últimos 30 dias (04/08 → 03/09).

| Lado | Pedidos | Valor |
|---|---:|---:|
| **Real DEBX** (6 schemas PED) | 4.154 | R$ 2.668.415,74 |
| + Venda física (F_MOVTO) | — | R$ 319.477,78 |
| **Total real** | — | **R$ 2.987.893,52** |
| **compra_erp (Increazy)** | 392 links / 336 pagos | R$ 1.034.176,04 (confirmado) |
| **Capturado** | 376 | R$ 1.225.118,41 |
| **GAP** | 3.778 | R$ 1.443.297,33 + físico R$ 319.477,78 |

- **E-mail como chave:** compra_erp tem e-mail 100% (392/392); o PED real tem `PDV_EMAILU` **vazio** (0 historicamente) e só 27% recuperável via cadastro mestre `F_ENDERE` (MATRIZ). E-mail casa por **cliente**, não por pedido (supercasa 395 vs 376 exatos).
- **Chave exata = nº do pedido** (`IPV_NUMPED` = `PDV_NUMPED`, 100%).
- compra_erp cobre só MATRIZ+ACL+BRG+GCL; **nada de CHC/FILIAL nem venda física**.

## 2. Fragmentação no Google Ads — a venda se espalha em 4+ ações

O "126,23 conversões / R$ 454K" que o Sérgio vê = ação **`WEB Conamore Offline ERP (compra_erp)`** (DDA, `primary_for_goal=true`). A mesma venda ERP cai em várias ações:

- `WEB Conamore Offline ERP (compra_erp)` — 127,29 conv / R$ 455.928,74 (primária)
- `01092024 Compra Otimizada (Web)` — 295,57 / R$ 229.349,26 (legado, primária)
- `[SERVERSIDE] Conv. Otimiz - Purchase` — 268,84 / R$ 233.009,80 (não-primária)
- `CONAMORE Hotelaria - GA4 purchase` — 99,19 / R$ 88.324,12 (Magento)
- `SERVER SIDE Compra ERP` — 0 (não dispara)

- **Tags legadas 140/175** (`purchase_webhook_*`) **ativas em paralelo**.
- **Checkout órfão `i1764011093`** (462 pagamentos aprovados, ainda ativo) **fora da lookup table** → não dispara conversão nenhuma.
- **Frete = 1,6%** → subtotal × total NÃO explica o gap (descartado).

## 3. Firestore (base de atribuição) — pagamentos congelados desde fev/2025

Projeto `agile-kite-392211`. 4 collections:

| Collection | Docs | Última escrita |
|---|---:|---|
| `increazy-erp` | 242 | **12/02/2025** ❄️ |
| `increazy-site` | 514 | **12/02/2025** ❄️ |
| `increazy_site` | 2 | **11/02/2025** ❄️ |
| `init_checkout_web` | 20.088 | **hoje** ✅ |

- As collections de **pagamento** (`increazy-erp`/`increazy-site`, que guardavam pagamento↔client_id↔e-mail) **morreram há ~18 meses**. O Firestore Writer atual (template 135 + tag 151) só grava `init_checkout_web`.
- O Firestore TEM first-party rico (e-mail, CPF, telefone, nome) — mas preso nos registros de 2025.

## 4. gclid órfão — ninguém captura/salva/usa o clique do Ads

- Varredura no server-side: **0** variáveis / **0** tags / **0** transformações referenciando `gclid`/`gdid`.
- `x-ga-gdid` chega **placeholder fixo** (`dY2E1Nz.dNzQzZD`), igual em 2025 e 2026.
- Reatribuição funciona por `id_cart` (busca utm/session/user_data no Firestore), mas **não carrega gclid**.
- Client-side (`GTM-MMGX8ZL`, outra conta) captura gclid via cookie `__k` mas **não persiste**.

---

## Plano de correção (priorizado)

| # | Ação | Camada | Dono | Esforço | Impacto |
|---|---|---|---|---|---|
| 1 | Adicionar checkout órfão `i1764011093` à lookup table | GTM | Matias | Baixo | Alto (desbloqueia vendas que nem disparam) |
| 2 | Consolidar ações duplicadas + desativar tags 140/175 | Ads/GTM | Flávia+Matias | Baixo | Alto (1 métrica limpa) |
| 3 | Reativar Firestore de pagamentos (2 tags espelho) | GTM | Matias | Médio | Médio (histórico de atribuição volta) |
| 4 | Capturar gclid end-to-end (client→server→Firestore→conversão) | GTM | Matias | Médio-alto | Alto (fecha atribuição ao clique) |
| 5 | Migrar p/ Data Manager + ECL (subir faturamento DEBX direto) | Ads/GCP | Flávia+Matias | Alto | Estrutural (fonte de verdade) |

**Dependências/riscos:** Consent Mode quebrado (29/08, Matias+Adrian) afeta o gclid; LGPD para voltar a gravar PII no Firestore (Adrian); ações destrutivas no Ads exigem aprovação do Sérgio.

## Detalhes
- `Diagnóstico compra_erp vs DEBX` · `Cruzamento venda a venda` · `Diagnóstico 2º gap Increazy→Ads` · `Mapeamento Firestore` · `Passo a passo Firestore` · `Desenho captura gclid` (todos em Agentes/Flávia/).
