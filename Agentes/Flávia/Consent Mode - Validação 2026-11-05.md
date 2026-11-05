# Consent Mode — validação 05/11/2026

**Site:** https://www.conamore.com.br/ · **GA4:** `properties/379729087` / `G-V0KMM7L6M6` · **GTM:** `GTM-MMGX8ZL`  
**Horário:** 08:01–08:03 BRT. Chromium headless, perfil novo sem consentimento persistido, inspeção do dataLayer, cookies e recursos de rede. O banner apareceu no teste; console não auditado.

## Teste ao vivo

- Primeiro acesso: `gtag` presente, 9 entradas no dataLayer; `consent default` presente, com `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` e `personalization_storage` = `denied`. Banner `cc-banner-modal` visível e `cc_cookie_*` ausentes no localStorage. Default negado antes da escolha é esperado.
- Antes da escolha: `page_view` em `www.google-analytics.com` e `PageView` em `gtmserver.conamore.com.br`, ambos para `G-V0KMM7L6M6`, `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`. São pings sob consentimento negado, não prova de engajamento coletado.
- **Anomalia de privacidade recorrente:** cookies `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid`, `_clck` e `_clsk` presentes antes da escolha, apesar de consentimento de ads negado. A presença isolada não prova envio de dados; atribuir origem das tags e verificar adequação LGPD com Matias/Increazy e Adrian. Também constatado em 03/11.
- Clique real em **Aceitar Tudo**: `consent update` alterou analytics e ads para `granted`; `cc_consent_update` com `analytics_consent=granted` e `marketing_consent=granted`; `cc_cookie_consent_status=true` e preferências `marketing=true`, `statistics=true`; banner oculto; cookies `_ga` e `_ga_V0KMM7L6M6` surgiram. Beacon `user_engagement` em `analytics.google.com` para `G-V0KMM7L6M6`, `gcs=G111`, `gcd=13r3r3r3r5l1`.
- Reload após aceite: `page_view` em `analytics.google.com` e `PageView` no `gtmserver` para o mesmo ID, `gcs=G111`, `pscdl=noapi`; dataLayer com `consent update` sem `default` e `gcd=13n3n3n3n5l1`. Coleta pós-aceite funciona, mas revisar a ordem do default/update no retorno. Não confundir esse retorno com primeiro acesso limpo.

## GA4 — D-3 consolidado (02/11/2026, America/Sao_Paulo)

- **1.807 sessões**, **1.122 engajadas**, **37,91% de rejeição**, duração média **215,30 s**. Comparação: 01/11, 1.409 sessões / 877 engajadas / 37,76%; 31/10, 1.043 / 627 / 39,88%.
- Origens principais em 02/11: google 1.085 sessões / 38,62% rejeição; direto 241 / 50,21%; ig 111 / 24,32%; instagram 110 / 23,64%; rd-automacao 64 / 51,56%. `(not set)` 11 / 72,73%, amostra pequena. Sem colapso transversal de engajamento.
- D-1 (04/11) não usado para diagnóstico por processamento pendente do GA4.

**Conclusão:** Consent Mode de primeiro acesso presente, atualização após escolha e `page_view` pós-aceite confirmados; GA4 D-3 estável. Persistem cookies publicitários pré-escolha e retorno com update sem default. Console não auditado; não atribuir erros de terceiros ao consentimento sem evidência. [[Consent Mode - Validação 2026-11-03]]
