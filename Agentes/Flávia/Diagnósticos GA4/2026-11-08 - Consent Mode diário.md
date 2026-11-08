# Consent Mode diário — 08/11/2026

**Site:** https://www.conamore.com.br/ · **GA4 Hotelaria:** `properties/379729087` / `G-V0KMM7L6M6` · **GTM:** `GTM-MMGX8ZL` · **Teste:** 08:02–08:03 BRT, Chromium headless, perfil limpo.

## Teste ao vivo
- Primeira visita: sem preferências salvas, banner `cc-banner-modal` visível, `gtag` ativo, `consent default` com `analytics_storage` e `ad_storage=denied` (correto antes da escolha). `page_view` em google-analytics.com e `PageView` em gtmserver para `G-V0KMM7L6M6`, `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`. Cookies publicitários `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid` já constavam antes do aceite; origem/finalidade requerem validação, não é prova isolada de infração.
- Clique real **Aceitar Tudo**: `consent update` com analytics/ads `granted`; `cc_consent_update` analytics/marketing `granted`; localStorage `cc_cookie_consent_status=true` e `cc_cookie_preferences` com marketing/statistics `true`; banner oculto. `user_engagement` de `G-V0KMM7L6M6` com `gcs=G111`, `gcd=13r3r3r3r5l1`, `npa=0`.
- Reabertura após aceite: `page_view` em analytics.google.com e `PageView` em gtmserver de `G-V0KMM7L6M6`, `gcs=G111`, porém `consent default` ausente no novo carregamento e `gcd=13n3n3n3n5l1`, `pscdl=noapi`. O estado salvo é aplicado por `consent update`. Pendência recorrente, distinta do fluxo inicial limpo correto.
- Erros de console: não capturados nesta execução; não foi atribuída causalidade a scripts de terceiros. Intermitência não testada em cinco contextos hoje porque o beacon pré-escolha coincidiu com o default.

## GA4 — America/Sao_Paulo
- **D-3 (05/11):** 1.576 sessões, 947 engajadas, **39,91% rejeição**, duração média 251,53 s. 04/11: 1.776 sessões, 935 engajadas, 47,35%; 03/11: 2.255 sessões, 1.485 engajadas, 34,15%. D-1 não usado por processamento.
- 05/11 por origem: google 869 sessões / 35,44% rejeição; direto 323 / 61,30%; instagram 67 / 38,81%; ig 52 / 21,15%; `(not set)` 14 / 50%. Não há colapso simultâneo nas principais origens.

**Status:** Coleta GA4 pós-aceite validada. Sem anomalia de rejeição no D-3. Duas pendências recorrentes: cookies de marketing pré-escolha e ausência de default no retorno consentido. Revisão Matias/Increazy (ordem de tags e origem de cookies) + avaliação de finalidade/LGPD por Adrian. Comparar com [[2026-11-07 - Consent Mode diário]].
