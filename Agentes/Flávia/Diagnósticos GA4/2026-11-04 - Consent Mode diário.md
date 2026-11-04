# Consent Mode diário — 04/11/2026

**Site:** https://www.conamore.com.br/ · **GA4 Hotelaria:** `properties/379729087` / `G-V0KMM7L6M6` · **Teste:** 08:00–08:03 BRT, Chromium headless, perfil novo e limpeza de cookies/storage entre visitas.

## Teste ao vivo
- `gtag` disponível; banner `cc-banner-modal` visível antes da escolha. Cinco cargas sem preferência: `consent default` presente, analytics/ads `denied` (5/5); beacons `page_view` / `PageView` para `G-V0KMM7L6M6` com `gcd=13p3p3p3p5l1`, `gcs=G100`, `pscdl=denied`, `npa=1` (5/5). O default negado é esperado.
- Em visita inicial anterior à limpeza, houve `consent default` negado no dataLayer, porém beacons `page_view` com `gcd=13l3l3l3l1l1`, `pscdl=noapi`, `npa=0`, e cookies `_ga`/`_fbp`; **não reproduzido nas cinco cargas limpas**. Contexto inicial potencialmente contaminado por estado do navegador; não concluir race condition com essa observação isolada.
- Cinco cargas limpas pré-escolha criaram `_gcl_au` e `_fbp` mesmo com analytics/ads negados. Outra carga limpa registrou requisições para `px.ads.linkedin.com/collect` e `bat.bing.com/action/0` antes do clique. Isso exige auditoria de finalidade/payload/consentimento por TI e Jurídico; mera presença de cookie ou request não basta para afirmar violação jurídica.
- Clique no botão real **Aceitar Tudo**: `consent update` analytics/ads `granted`, evento `cc_consent_update`, localStorage `cc_cookie_consent_status=true` e preferências `marketing/statistics=true`; `user_engagement` para `G-V0KMM7L6M6`, `gcs=G111`, `gcd=13r3r3r3r5l1`. Em navegação após aceite, `page_view` e `PageView` para `G-V0KMM7L6M6`, `gcs=G111`. Nesse retorno, dataLayer tinha apenas `consent update`, sem `default`, e beacon `gcd=13n3n3n3n5l1` / `pscdl=noapi`: revisar a implementação de consentimento persistido, sem confundir `n` nessa visita consentida com o estado das cinco visitas novas.
- O pageview pós-aceite foi capturado hoje, diferindo do teste de [[2026-11-02 - Consent Mode diário]], que não capturou beacon Hotelaria em páginas consentidas. Não há prova de falha generalizada da coleta hoje. Console JS não capturado/classificado nesta rodada.

## GA4 (America/Sao_Paulo)
- D-3 01/11: **1.409 sessões, 877 engajadas, 37,76% rejeição**, duração média 196,25 s. 31/10: 39,88%; 02/11: 37,91%. D-1 03/11: **35,31% rejeição, 2.260 sessões, 1.462 engajadas**, preliminar por processamento GA4.
- Origens D-3: google 851 sessões, 37,37% rejeição; direto 208, 58,17%; ig 86, 29,07%; instagram 86, 26,74%; `(not set)` 8, 75% (amostra pequena). Sem colapso simultâneo das origens.

**Status:** fluxo inicial e pós-aceite operacional nas provas de hoje. **Pendências:** cookies/beacons publicitários pré-escolha e ausência de `consent default` na visita de retorno com preferência salva. Encaminhar investigação técnica a Matias/Increazy e avaliação de conformidade a Adrian, sem alterar tags sem diagnóstico.
