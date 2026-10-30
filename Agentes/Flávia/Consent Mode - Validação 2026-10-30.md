# Consent Mode — validação 30/10/2026

**Site:** https://www.conamore.com.br/ · **GA4:** `properties/379729087` / `G-V0KMM7L6M6` · **GTM:** `GTM-MMGX8ZL`  
**Horário:** 08:00–08:03 BRT, navegador Chromium headless, armazenamento limpo.

## Teste ao vivo

- Em cinco carregamentos limpos sem escolha, o banner `cc-banner-modal` esteve visível, `gtag` presente, `consent default` presente com analytics/ad_storage/ad_user_data/ad_personalization `denied`. Sem preferência persistida.
- Beacons antes da escolha para `G-V0KMM7L6M6`: `page_view` e `PageView`, `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`. Não houve mistura `pscdl=noapi` nesses cinco testes.
- Após clicar **Aceitar Tudo**, `consent update` com analytics/ads `granted`, `cc_consent_update` com analytics/marketing `granted`, `cc_cookie_consent_status=true`, preferências `{marketing:true,statistics:true}`. `user_engagement` enviado a `analytics.google.com` com `gcs=G111`, `gcd=13r3r3r3r5l1`.
- Após recarregar com aceite persistido, `page_view` para `G-V0KMM7L6M6` enviado a `analytics.google.com` e `PageView` a `gtmserver.conamore.com.br`, ambos `gcs=G111`. Nesse caminho de visitante recorrente, dataLayer exibiu `consent update` sem `default`, com `gcd=13n3n3n3n5l1` e `pscdl=noapi`; avaliar ordem da atualização no GTM, sem concluir falha de coleta porque os beacons saíram granted.
- **Atenção LGPD:** antes de qualquer clique, cookies `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid`, `_clck`/`_clsk` apareceram nos cinco testes, apesar do default denied e beacon GA4 denied. Cookie isolado não comprova transmissão de dados nem falha de engajamento; pedir auditoria das tags de marketing/CMP ao Matias/Increazy e avaliação jurídica ao Adrian.

## GA4 consolidado (D-3, 27/10)

- 1.719 sessões; 1.033 engajadas; rejeição **39,9%**; engajamento 60,1%.
- 26/10: 1.536 sessões, rejeição 41,9%; 25/10: 1.391, rejeição 41,7%. Sem colapso transversal como em agosto.
- Fontes em 27/10: google 816 sessões/40,8% rejeição; direto 275/51,3%; instagram 184/32,1%; rd-email 166/31,3%. `(not set)` 11 sessões/54,5%.

**Conclusão:** fluxo inicial e pós-aceite funcional para visitantes novos; ressalva dos cookies pré-escolha e da sequência de consentimento no retorno. Console não auditado neste teste. Repetir auditoria com Matias e Adrian se não houver registro anterior de correção.
