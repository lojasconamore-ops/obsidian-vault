# Consent Mode diário — 09/11/2026

**Site:** https://www.conamore.com.br/ · **GA4 Hotelaria:** `properties/379729087` / `G-V0KMM7L6M6` · **GTM:** `GTM-MMGX8ZL` · **Teste:** 08:01–08:03 BRT, Chromium headless. Cookies do navegador e dados da origem apagados antes da recarga; sem preferência salva na primeira visita.

## Teste ao vivo
- Primeira visita: banner `cc-banner-modal` visível, `gtag` ativo, `consent default` presente com `analytics_storage`, `ad_storage`, `ad_user_data` e `ad_personalization=denied` (privacidade esperada antes da escolha). `page_view` em google-analytics.com e `PageView` em gtmserver para `G-V0KMM7L6M6`, `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`.
- Antes do aceite, `document.cookie` já continha `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid` e `_clck`, entre outros. A mera presença não comprova coleta de dados nem infração; Matias/Increazy devem apurar escrita/origem/finalidade e Adrian avaliar LGPD. Pendência também registrada em [[2026-11-08 - Consent Mode diário]].
- Clique real **Aceitar Tudo**: `consent update` analytics/ads `granted`; evento `cc_consent_update` com analytics/marketing `granted`; localStorage `cc_cookie_consent_status=true`, preferências marketing/statistics `true`; banner oculto. `user_engagement` de `G-V0KMM7L6M6` coletado em analytics.google.com com `gcs=G111`, `gcd=13r3r3r3r5l1`, `pscdl=noapi`, `npa=0`. Cookies `_ga` surgiram depois da escolha. O `pscdl=noapi` pós-escolha não equivale à ausência de default, pois o default e o update foram observados.
- Eventos observados: `page_view` e `PageView` pré-escolha sob consentimento negado; `cc_consent_update` e `user_engagement` após aceite. Não houve captura sistemática de console nesta execução, portanto sem classificação de erros. O caminho de rejeição e o retorno consentido não foram testados hoje.

## GA4 — America/Sao_Paulo
- **D-3 (06/11):** 1.413 sessões, 790 engajadas, **44,09% rejeição**, duração média 247,16 s. 04/11: 1.776 sessões / 47,35%; 05/11: 1.576 / 39,91%; 07/11: 1.302 / 39,40%. D-1 (08/11) deliberadamente não usado por processamento.
- 06/11 por origem: google 783 sessões / 39,46% rejeição; direto 305 / 63,28%; instagram 61 / 45,90%; ig 54 / 22,22%; `(not set)` 24 / 91,67% (2 sessões engajadas). Não há colapso simultâneo nas principais origens. O `(not set)` é sinal localizado a investigar se persistir, não evidência de pane geral.

**Status:** Fluxo de Consent Mode da primeira visita e coleta GA4 pós-aceite funcionando. Sem anomalia geral de rejeição em D-3. Pendência recorrente de cookies publicitários pré-escolha requer verificação técnica e jurídica; não atribuir causalidade sem inspeção da origem dos cookies.