# Consent Mode diário — 07/11/2026

**Site:** https://www.conamore.com.br/ · **GA4 Hotelaria:** `properties/379729087` / `G-V0KMM7L6M6` · **Teste:** 08:01–08:04 BRT, Chromium headless, perfil novo.

## Teste ao vivo
- Primeira visita limpa: banner `cc-banner-modal` visível; sem preferências salvas; `gtag` ativo; `consent default` presente com analytics/ads `denied` (correto antes da escolha). Beacons `page_view` / `PageView` para `G-V0KMM7L6M6`: `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`.
- Repeti cinco ciclos de limpeza de cookies/localStorage sem escolher: todos mantiveram default `denied`, banner visível, beacon negado e **cookies `_gcl_au` e `_fbp` antes do consentimento**. Não havia `_ga` nesses ciclos. Presença dos cookies de publicidade pré-aceite é pendência recorrente; verificar a origem/finalidade com Matias/Increazy e avaliação LGPD com Adrian, sem concluir infração apenas pelo nome do cookie.
- Clique real **Aceitar Tudo**: `consent update` analytics/ads `granted`; `cc_consent_update` com analytics/marketing `granted`; localStorage `cc_cookie_consent_status=true`, preferências `marketing=true, statistics=true`. Evento `user_engagement` para `G-V0KMM7L6M6` com `gcs=G111`, `gcd=13r3r3r3r5l1`.
- Reabertura da home após aceite: `page_view` via analytics.google.com e `PageView` via gtmserver.conamore.com.br para `G-V0KMM7L6M6`, `gcs=G111`. Porém a visita consentida persistida traz apenas `consent update`, sem `consent default`, e `gcd=13n3n3n3n5l1`, `pscdl=noapi`. Pendência recorrente (ver [[2026-11-06 - Consent Mode diário]]); não confundir com o default presente na primeira visita limpa. Console JS não foi capturado/classificado.

## GA4 — America/Sao_Paulo
- **D-3 (04/11):** 1.776 sessões, 935 engajadas, **47,35% rejeição**, duração média 208,53 s. 03/11: 2.255 sessões, 1.485 engajadas, 34,15% rejeição; 05/11: 1.576 sessões, 947 engajadas, 39,91% rejeição. D-1 (06/11) não consultado por processamento pendente.
- 04/11 por origem: google 833 sessões / 36,13%; direto 492 / 75,41%; ig 75 / 25,33%; instagram 72 / 37,50%; rd-email 37 / 54,05%; `(not set)` 24 / 79,17%. A alta de 13,21 p.p. contra 03/11 é concentrada sobretudo em direto; não é colapso simultâneo de todas as origens.

**Status:** Coleta GA4 pós-aceite funcionando na visita testada; duas pendências persistentes: cookies publicitários pré-escolha e ausência de `default` no retorno já consentido. Sem mudança em GTM/CMP. Prioridade: Matias/Increazy revisar ordenação do default no retorno e origem de `_gcl_au`/`_fbp`; Adrian avaliar implicação LGPD.
