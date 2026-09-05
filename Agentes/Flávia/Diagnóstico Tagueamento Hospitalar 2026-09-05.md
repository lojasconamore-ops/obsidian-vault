---
tags: [hospitalar, gtm, ga4, google-ads, consent-mode, atribuicao, diagnostico]
data: 2026-09-05
status: diagnostico-concluido
---

# Diagnóstico de tagueamento — hospitalar.conamore.com.br — 2026-09-05

## Resumo executivo

O Hospitalar mede navegação e compras no GA4 próprio, mas o desenho atual tem quatro falhas relevantes para atribuição:

1. **GTM só carrega no primeiro scroll** — visitante que sai sem rolar a página não gera page_view/sessão no GA4 nem sinal para Ads.
2. **Consent Mode ausente** — depois do scroll, GA4, Google Ads, Meta, Bing e Clarity disparam com consentimento implícito; o banner é apenas informativo e não atualiza consentimento.
3. **Contaminação entre propriedades** — a página Hospitalar também envia page_view ao GA4 da Hotelaria (`G-V0KMM7L6M6`). Em 30 dias, 524 sessões Hospitalar entraram na property Hotelaria, 92,6% das 566 sessões registradas no GA4 próprio.
4. **Compra Hospitalar não alimenta o Smart Bidding** — o GA4 Hospitalar registrou 5 compras/R$ 5.800,33, mas não existe ação de conversão de compra Hospitalar no Google Ads. Só `contato_whatsapp` Hospitalar foi importado e está como secundário (`primary_for_goal=false`).

## Executado

- URL: `https://hospitalar.conamore.com.br/`
- Horário: 05/09/2026 06:37 BRT
- Teste em contexto limpo, antes/depois do primeiro scroll e depois de fechar o banner.
- Inspeção do container público `GTM-WCG6FZW`.
- GA4 Hospitalar: property `372899047`, stream `5136821046`, measurement `G-BNBJFTE5VT`.
- Janela GA4 consolidada: 03/08/2026 a 02/09/2026; comparação 03/07/2026 a 02/08/2026.
- Inventário atual das ações de conversão Google Ads `2335779078` via GAQL.
- Teste dos endpoints server-side antigo e atual.

## Evidências técnicas

### 1. Carregamento tardio

O HTML contém o GTM dentro de `onFirstScroll()`:

- Antes do scroll: nenhum `gtm.js`, nenhum beacon GA4/Ads e apenas `cart_id`/`conversion_id`.
- Depois do scroll: carrega `GTM-WCG6FZW`, GA4, Google Ads, Meta Pixel, Bing UET, Clarity e RD.

Impacto: sessões de rejeição sem scroll ficam invisíveis e a origem paga fica subcontada. O tamanho da perda não é mensurável pelo próprio GA4 porque os usuários perdidos não enviam evento.

### 2. Consentimento/LGPD

Depois do scroll:

- `usedDefault=false`
- `usedImplicit=true`
- `ad_storage`, `analytics_storage`, `ad_user_data` e `ad_personalization` em modo implícito
- Beacons: `gcd=13l3l3l3l1l1`, `npa=0`, `pscdl=noapi`
- Cookies criados antes do clique: `_ga`, `_gcl_au`, `_fbp`, `_clck`, `_uetsid`, `_uetvid`, `rdtrk`
- Fechar o banner cria apenas `CookieInfoScript`; não aparece `consent default` nem `consent update`.

Conclusão: o banner atual não é CMP/Consent Mode v2; é apenas aviso de cookies.

### 3. Destinos disparados no Hospitalar

Observados após o primeiro scroll:

- GTM: `GTM-WCG6FZW`
- GA4 Hospitalar: `G-BNBJFTE5VT`
- GA4 Hotelaria: `G-V0KMM7L6M6` — destino indevido para page_view Hospitalar
- GA4 adicional: `G-4HC4FT0C7X` — destino ainda não identificado
- Google Ads: `AW-1041572367`
- Meta Pixel: `583931423939058`
- Bing UET: `343046885`

O GA4 Hotelaria recebeu 524 sessões e 3.977 eventos com hostname `hospitalar.conamore.com.br` no período, sem compras. O GA4 próprio registrou 566 sessões: sobreposição equivalente a 92,6%.

### 4. Server-side desatualizado

O container Hospitalar referencia o endpoint antigo:

`https://gtm-w9gnwqw-nzbjy.uc.r.appspot.com`

- Endpoint antigo `/healthz`: HTTP 404.
- Endpoint atual `https://gtmserver.conamore.com.br/healthz`: HTTP 200.
- O container não contém `gtmserver.conamore.com.br`, `purchase_erp` nem `compra_erp`.
- Somente a tag de `add_to_cart` contém `transport_url`; purchase/begin_checkout/outros usam apenas parâmetro `server_container_url` apontando para o endpoint antigo.

Conclusão: o navegador Hospitalar não está integrado corretamente ao sGTM atual da Stape. O webhook backend de uma compra pode existir separadamente, mas não foi comprovado pelo front-end; a aplicação Hospitalar observada é `app=211` / ecommerce `i1723987853` e precisa ser validada na Increazy quanto ao envio para `/purchase`.

### 5. Ecommerce e atribuição GA4

GA4 Hospitalar, 03/08–02/09:

- 566 sessões
- 28 `contato_whatsapp` (key events)
- 5 `purchase`
- Receita: R$ 5.800,33
- Taxa compra/sessão: 0,88%
- Taxa WhatsApp/sessão: 4,95%

Período anterior, 03/07–02/08:

- 699 sessões
- 45 WhatsApp
- 3 compras
- Receita: R$ 3.511,33
- Taxa compra/sessão: 0,43%

Variações:

- Sessões: -19,0%
- Compras: +66,7%
- Receita: +65,2%
- WhatsApp: -37,8%
- Sessões Google CPC/Cross-network: 255 → 89 (-65,1%)

Atribuição das 5 compras recentes:

- Direct: 2 compras, R$ 4.466,83 (77,0%)
- ChatGPT / ai-assistant: 2 compras, R$ 924,74 (15,9%)
- (not set): 1 compra, R$ 408,76 (7,0%)
- Google CPC: 0 compras atribuídas apesar de 89 sessões

### 6. Compra Hospitalar no Google Ads

Situação atual verificada:

- Property Hospitalar está vinculada ao Ads `2335779078`.
- No GA4, `purchase` e `contato_whatsapp` são eventos de conversão.
- No Ads existe apenas `CONAMORE Hospitalar - GA4 G-BNBJFTE5VT (web) contato_whatsapp`, secundária (`primary_for_goal=false`).
- Não existe ação `CONAMORE Hospitalar ... purchase` no inventário Ads.

Conclusão: as 5 compras/R$ 5.800,33 medidas no GA4 Hospitalar não entram em `metrics.conversions` e não orientam o Smart Bidding.

### 7. Risco de duplicidade interna

O container tem dois caminhos ativos de `purchase` para `G-BNBJFTE5VT`:

- `purchase` → tag 199
- `purchase` → `capi_purchase` → tag 151

Ambos carregam `transaction_id`; o GA4 pode deduplicar no relatório, mas o desenho deve ser validado em uma compra real no Tag Assistant para evitar eventos/requisições redundantes.

## Origem confirmada do GA4 Hotelaria e Google Ads no Hospitalar

Tag Assistant confirmou que os disparos indevidos não vêm da lista de destinos da Google tag Hospitalar. Eles vêm de uma configuração embutida na página/Increazy:

- Nome mostrado: `Conamore Hotelaria Increazy`.
- Origem: `gtag('config') na página`.
- IDs da tag: `G-V0KMM7L6M6` e `GT-MK98TWV`.
- Destinos: `G-V0KMM7L6M6` e `AW-1041572367`.
- Hits observados: page_view para GA4 Hotelaria e Ads, `RD Popup e WhatsApp` para ambos, dados fornecidos pelo usuário e remarketing para Ads.

Correção: condicionar/remover essa configuração no app Hospitalar `211`, sem removê-la globalmente da Hotelaria. Buscar no template/configuração Increazy por `GT-MK98TWV`, `G-V0KMM7L6M6`, `AW-1041572367` ou `gtag('config'...)`.

## Status e plano recomendado

### P0 — corrigir imediatamente

1. Retirar o GTM de `onFirstScroll()` e carregar em Consent Initialization/Initialization no page load.
2. Implementar Consent Mode v2 com default denied antes de qualquer tag e banner com aceitar/recusar + `consent update`.
3. Bloquear Meta/Bing/Ads/Clarity até consentimento apropriado.

### P1 — atribuição

4. Remover o destino `G-V0KMM7L6M6` da página Hospitalar e identificar/remover ou justificar `G-4HC4FT0C7X`.
5. Migrar o endpoint server-side para `https://gtmserver.conamore.com.br` e configurar `transport_url` centralmente no Google tag.
6. Validar com a Increazy se o app Hospitalar `211` envia compras para `/purchase`; testar o payload e confirmar o evento no sGTM.
7. Importar `purchase` do GA4 Hospitalar no Ads como secundária por 7 dias; validar transaction_id/valor/deduplicação e, após aprovação estratégica, tornar primária se for objetivo de campanha.
8. Manter `contato_whatsapp` Hospitalar secundário até decidir se o Smart Bidding deve otimizar lead ou receita.

## Evidência final

- Diagnóstico live: concluído.
- GA4/Ads: leituras confirmadas por API.
- Alterações de produção: não executadas; exigem GTM/Increazy e aprovação sobre objetivo primário do Smart Bidding.
