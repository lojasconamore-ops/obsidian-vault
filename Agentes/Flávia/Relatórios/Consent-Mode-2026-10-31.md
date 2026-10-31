# Consent Mode — 31/10/2026, 08:00–08:02 BRT

**Site:** https://www.conamore.com.br/ · **GA4:** `properties/379729087` / `G-V0KMM7L6M6` · **GTM:** `GTM-MMGX8ZL`.

## Teste ao vivo (Chromium headless, perfil novo)
- Primeira visita: `gtag` presente; banner `cc-banner-modal` visível; sem preferências locais; `consent default` presente (`analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` = `denied`). Beacons `page_view` do GA4: `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`.
- Antes do aceite, cookies `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid`, `_clck`/`_clsk` já presentes. Merecem auditoria de marketing/LGPD; cookie isolado não prova transmissão indevida. Banner headless visível nesta execução.
- Clique real em **Aceitar Tudo**: `consent update` com analytics e ads `granted`; `cc_consent_update` com analytics/marketing `granted`; banner oculto; `cc_cookie_consent_status=true`, preferências `{marketing:true,statistics:true}`. Beacon `user_engagement` para `G-V0KMM7L6M6` em `analytics.google.com`, `gcs=G111`, `gcd=13r3r3r3r5l1`, `npa=0`. Cookies `_ga` e `_ga_V0KMM7L6M6` presentes após aceite.
- Recarregamento após aceite: `page_view` a `analytics.google.com` e `PageView` a `gtmserver.conamore.com.br` para `G-V0KMM7L6M6`, `gcs=G111`. Nesse caminho persistido houve `consent update` sem `default`, `gcd=13n3n3n3n5l1`, `pscdl=noapi`; confirmar ordem/estado inicial para visitantes recorrentes. Não caracterizar interrupção de coleta nesta amostra: page_view concedido saiu efetivamente. Console JS não auditado.

## GA4 D-3 (28/10/2026, America/Sao_Paulo)
- 1.578 sessões; 983 engajadas; rejeição **37,7%**, engajamento **62,3%**, duração média 242,9 s. Em 27/10: 1.719 sessões, 1.033 engajadas, rejeição 39,9%.
- Fontes 28/10: google 807 sessões/rejeição 39,2%; direto 260/42,7%; instagram 175/36,0%; ig 106/21,7%; `(not set)` 16/68,8%. Sem colapso transversal.
- A resposta por fontes contém `rowCount=32`; apenas as 30 maiores foram solicitadas. Não é um inventário completo das fontes, mas suficiente para a leitura das principais.

## Conclusão
Fluxo de primeira visita e aceite funcional; rejeição D-3 normal, sem assinatura de falha geral. Ressalvas recorrentes: cookies de marketing pré-escolha e ausência de `default` no retorno com aceite persistido. Solicitar auditoria GTM/CMP ao Matias/Increazy e avaliação LGPD ao Adrian pelo canal apropriado. Comparar com [[Consent Mode - Validação 2026-10-30]].
