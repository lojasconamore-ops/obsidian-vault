# Consent Mode diário — 19/11/2026

**Site:** https://www.conamore.com.br/ · **GA4 Hotelaria:** `properties/379729087` / `G-V0KMM7L6M6` · **GTM:** `GTM-MMGX8ZL`  
**Teste:** 08:01–08:02 BRT, Chromium headless em perfil limpo, sem preferência `cc_cookie_*` antes da visita.

## Teste ao vivo

- Primeira visita: banner `cc-banner-modal` visível; `gtag` ativo; `dataLayer` com 12 entradas; `consent default` presente com `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` e `personalization_storage=denied`, além de `functionality_storage`/`security_storage=granted` e `wait_for_update=500`. Default negado antes da escolha é comportamento esperado de privacidade.
- Antes do aceite, houve `page_view` para `G-V0KMM7L6M6` em `www.google-analytics.com` e `gtmserver.conamore.com.br`, com `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`. São pings sob consentimento negado; não provam engajamento completo.
- **Anomalia de privacidade recorrente:** antes da escolha, `document.cookie` já continha `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid`, `_clck`, `_clsk`, `mm_tracker`, entre outros. A presença isolada não prova envio indevido, mas exige Matias/Increazy identificarem origem/finalidade e Adrian avaliar aderência LGPD.
- Clique real em **Aceitar Tudo**: `consent update` alterou analytics e ads para `granted`; `cc_consent_update` registrou `analytics_consent=granted` e `marketing_consent=granted`; localStorage passou a conter `cc_cookie_consent_status=true` e `cc_cookie_preferences={"marketing":true,"statistics":true}`; banner ocultado; cookies `_ga` e `_ga_V0KMM7L6M6` criados.
- Após o aceite, houve `user_engagement` para `G-V0KMM7L6M6` em `analytics.google.com`, com `gcs=G111`, `gcu=1`, `npa=0`. O `pscdl=noapi` pós-escolha não indica ausência do Consent Mode neste teste, pois o `consent default` inicial e o `consent update` foram observados.
- Eventos observados: `gtm.js`, `gtm.dom`, `gtm.load`, `page_view`, `PageView`, `consent default`, `consent update`, `cc_consent_update` e `user_engagement`. Console não foi auditado sistematicamente nesta execução; não classificar avisos de terceiros como causa.

## GA4 — D-3 consolidado (16/11/2026, America/Sao_Paulo)

- **1.575 sessões**, **954 engajadas**, **39,43% de rejeição**, duração média **390,30 s**.
- Origens principais no D-3: google 881 sessões / 37,12% rejeição; `(direct)` 329 / 54,71%; instagram 78 / 25,64%; ig 38 / 26,32%; bing 37 / 24,32%; app.octadesk.com 35 / 20,00%.
- `(not set)` teve 17 sessões / 70,59% de rejeição e duração média anômala de 11.461 s; amostra pequena e localizada, não evidência de pane geral.
- Não há colapso transversal: as principais origens permanecem com sessões engajadas e rejeição muito abaixo de 95%. O D-3 não indica falha geral de tracking.

**Status:** Consent Mode **funcionando** no caminho de primeira visita + aceite, com `default denied`, atualização para `granted` e coleta GA4 pós-aceite confirmadas. **Limitação/anomalia:** cookies publicitários presentes antes da escolha continuam recorrentes e devem ser investigados tecnicamente/juridicamente. GA4 D-3 estável; `(not set)` localizado merece monitoramento, sem ação corretiva imediata.
