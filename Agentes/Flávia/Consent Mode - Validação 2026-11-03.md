# Consent Mode — validação 03/11/2026

**Site:** https://www.conamore.com.br/ · **GA4:** `properties/379729087` / `G-V0KMM7L6M6` · **GTM:** `GTM-MMGX8ZL`  
**Horário:** 08:00–08:05 BRT. Inspeção via Chromium/CDP, contexto de navegador isolado e sem preferência persistida.

## Teste ao vivo

- Primeiro acesso no contexto limpo: `gtag` presente; `consent default` presente com `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` e `personalization_storage` = `denied`; banner com botão **Aceitar Tudo** visível; sem `cc_cookie_*` no localStorage. Este default denied é o comportamento esperado antes da escolha.
- Beacons pré-escolha para `G-V0KMM7L6M6`: `page_view` em `www.google-analytics.com` e `PageView` em `gtmserver.conamore.com.br`; ambos `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`.
- **Anomalia de privacidade recorrente:** antes da escolha, cookies `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid`, `_clck`, `_clsk` já existiam, embora o default fosse denied. Cookie isolado não demonstra transmissão de dados; investigar origem das tags e política LGPD com Matias/Increazy e Adrian. Anteriormente, em 30/10, reproduzido em cinco contextos limpos.
- Após clicar **Aceitar Tudo**, `consent update` com analytics e ads `granted`; evento `cc_consent_update` com `analytics_consent` e `marketing_consent` = `granted`; `cc_cookie_consent_status=true` e `cc_cookie_preferences={"marketing":true,"statistics":true}`. Cookies `_ga` e `_ga_V0KMM7L6M6` apareceram. Beacon `user_engagement` para `G-V0KMM7L6M6` em `analytics.google.com`, `gcs=G111` / `gcd=13r3r3r3r5l1`.
- Após reload com aceite persistido: `page_view` para `G-V0KMM7L6M6` em `analytics.google.com` e `PageView` em `gtmserver.conamore.com.br`, `gcs=G111`; nesse fluxo recorrente o dataLayer tem `consent update` sem `default`, com `gcd=13n3n3n3n5l1` e `pscdl=noapi`. Coleta pós-aceite funciona; revisar ordem do default/update na volta, sem confundir com o primeiro acesso.
- Console de erros não auditado. Tentativa de repetir via Playwright/CDP no navegador automatizado bloqueada por restrição de endereço interno; teste de 03/11 tem **um contexto limpo**, não cinco.

## GA4 — D-3 consolidado (31/10/2026, America/Sao_Paulo)

- 1.043 sessões; 627 engajadas; rejeição **39,88%**; duração média 209,77 s. 29/10: 1.572 sessões, 949 engajadas, rejeição 39,63%; 30/10: 1.362 sessões, 835 engajadas, rejeição 38,69%.
- Fontes de 31/10: google 607 sessões/40,69% rejeição; direto 164/49,39%; instagram 54/42,59%; ig 49/14,29%; rd-email 47/48,94%; `(not set)` 7/57,14%. Sem colapso transversal nas principais origens.
- D-1 (02/11) não consultado para diagnóstico porque ainda sujeito a processamento de 24–48 h.

**Conclusão:** fluxo de Consent Mode no primeiro acesso e coleta pós-aceite verificados neste teste; sem anomalia de bounce no D-3. Persistem cookies publicitários pré-escolha e sequência sem default no retorno. Seguir auditoria GTM/CMP com Matias/Increazy e avaliação jurídica com Adrian, caso ainda não haja correção documentada. [[Consent Mode - Validação 2026-10-30]]
