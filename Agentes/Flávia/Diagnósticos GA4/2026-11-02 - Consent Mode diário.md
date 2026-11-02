# Consent Mode diário — 02/11/2026

**Site:** https://www.conamore.com.br/ · **GA4 Hotelaria:** `properties/379729087` / `G-V0KMM7L6M6` · **GTM:** `GTM-MMGX8ZL` · **Teste:** 08:00–08:05 BRT, Chromium headless.

## Teste ao vivo
- Cinco visitas sem preferência, com limpeza de cookies/storage entre navegações na mesma sessão de Chromium: banner visível, `gtag` presente e `consent default` negando analytics/ads em 5/5. `page_view` para `G-V0KMM7L6M6` e `G-CDCKFVTR5M`, `gcs=G100`, `pscdl=denied`, `npa=1` em 5/5. Default negado antes da escolha é esperado. Mesmo antes do aceite apareceram `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid` em 5/5; pedir revisão de disparos/CMP/LGPD. Presença do cookie sozinha não prova transmissão de dados.
- Clique real em **Aceitar Tudo**: `consent update` com `analytics_storage` e ads `granted`; `cc_consent_update`; `cc_cookie_consent_status=true`, preferências marketing/statistics `true`; `_ga` e `_ga_V0KMM7L6M6` surgiram. `user_engagement` para `G-V0KMM7L6M6` com `gcs=G111`. O `page_view` Hotelaria observado nessa visita foi pré-aceite (`G100`), portanto não comprova pageview pós-aceite nessa visita.
- Navegações subsequentes com consentimento salvo para `/`, `/quem-somos`, `/`, `/quem-somos`: `dataLayer` só continha `consent update` (sem `default`); beacon `G-CDCKFVTR5M` com `page_view`, `gcs=G111`, `pscdl=noapi`; **nenhum beacon `G-V0KMM7L6M6`** capturado após espera de 7–17 s por página. Reproduzido nesta sessão, sem isolar perfil novo para o fluxo consentido. Difere do teste de 01/11, que registrou pageview Hotelaria em reload consentido. Investigar regra/ordem de tags GTM/CMP e replicar em perfis independentes; não afirmar ausência global de coleta com base neste navegador.
- Console JS não capturado/classificado nesta rodada; não atribuir causa a scripts sem evidência.

## GA4 (timezone America/Sao_Paulo)
- D-3 30/10: **1.362 sessões, 835 engajadas, 38,69% rejeição**, 61,31% engajamento, duração média 220,6 s. 28/10: 37,71%; 29/10: 39,63%; 31/10: 39,88%. D-1 01/11: 39,77% preliminar (1.408 sessões), sujeito ao processamento GA4.
- Origens D-3: google 682 sessões, 35,04% rejeição; direto 235, 50,21%; rd-email 106, 40,57%; instagram 73, 43,84%; `(not set)` 18, 44,44%. Sem assinatura de colapso geral.

**Status:** consentimento inicial e atualização funcionam; **anomalia no percurso de visitante com consentimento persistido** (`default` ausente/`pscdl=noapi`, pageview Hotelaria ausente neste reteste) e cookies de marketing pré-escolha. Escalar investigação técnica a Matias/Increazy e avaliação LGPD a Adrian, sem alteração destrutiva de tags. Ver [[2026-11-01 - Consent Mode diário]].
