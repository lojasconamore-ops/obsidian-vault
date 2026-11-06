# Consent Mode diário — 06/11/2026

**Site:** https://www.conamore.com.br/ · **GA4 Hotelaria:** `properties/379729087` / `G-V0KMM7L6M6` · **Teste:** 08:02–08:03 BRT, Chromium headless com perfil novo.

## Teste ao vivo
- Antes da escolha: banner `cc-banner-modal` visível, nenhuma preferência salva em localStorage, `gtag` disponível, `consent default` presente no dataLayer com analytics e publicidade `denied`. `page_view` para `G-V0KMM7L6M6` em `www.google-analytics.com`, `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`. Default negado é a configuração esperada de privacidade.
- Apesar de publicidade negada, cookies `_gcl_au` e `_fbp` estavam presentes antes da escolha; mesma pendência observada em [[2026-11-04 - Consent Mode diário]]. A presença isolada não comprova disparo indevido nem violação jurídica: auditar origem/finalidade/payload com Matias/Increazy e Adrian.
- Clique real em **Aceitar Tudo**: `consent update` com analytics/ads `granted`; `cc_consent_update` com analytics/marketing `granted`; preferências salvas `marketing=true`, `statistics=true`; banner oculto. Coleta `user_engagement` para `G-V0KMM7L6M6`, `gcs=G111`, `gcd=13r3r3r3r5l1`.
- Navegação após aceite: `page_view` em `analytics.google.com` e `PageView` em `gtmserver.conamore.com.br`, ambos para `G-V0KMM7L6M6`, `gcs=G111`. No retorno consentido, dataLayer continha `consent update` mas não `default`; beacon `gcd=13n3n3n3n5l1`, `pscdl=noapi`. Repetição da pendência do consentimento persistido (04/11); não confundir com ausência de default na visita limpa inicial. Console JS não coletado/classificado nesta rodada.

## GA4 — fuso America/Sao_Paulo
- D-3 03/11: **2.255 sessões, 1.485 engajadas, 34,15% rejeição**, duração média 259,26 s. Dias anteriores: 02/11 37,91% (1.807 sessões, 1.122 engajadas), 01/11 37,76% (1.409 sessões, 877 engajadas). D-1 05/11 deliberadamente não usado por processamento pendente.
- Origens 03/11: google 951 sessões / 37,22% rejeição; direto 283 / 48,06%; facebook.com 168 / 19,05%; rd-email 162 / 37,04%; lm.facebook.com 148 / 11,49%; `(not set)` 71 / 30,99%. Sem colapso simultâneo das origens.

**Status:** coleta GA4 pós-aceite e default negado inicial funcionando neste teste; pendências recorrentes de cookies publicitários pré-escolha e de `default` ausente no retorno consentido. Nenhuma alteração executada em GTM/CMP.
