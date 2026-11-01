# Consent Mode diário — 01/11/2026

**Site:** https://www.conamore.com.br/ · **GA4:** `properties/379729087` / `G-V0KMM7L6M6` · **GTM:** `GTM-MMGX8ZL` · **Horário:** 08:00–08:06 BRT, Chromium headless.

## Ao vivo

- Primeiro carregamento sem preferência: banner `cc-banner-modal` visível; `gtag` presente; `consent default` com `analytics_storage`, `ad_storage`, `ad_user_data` e `ad_personalization` `denied` (comportamento esperado antes da escolha). `page_view` e `PageView` para `G-V0KMM7L6M6`: `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`.
- Clique real em **Aceitar Tudo**: `consent update` analytics/ads `granted`; `cc_consent_update` com analytics/marketing `granted`; `cc_cookie_consent_status=true`, preferências `{marketing:true,statistics:true}`; beacon `user_engagement` para `G-V0KMM7L6M6`, `gcs=G111`, `gcd=13r3r3r3r5l1`. No reload consentido, `page_view` e `PageView` foram enviados `G111`, mas `consent default` ausente e `gcd=13n3n3n3n5l1`: revisar ordem no caminho de visitante recorrente.
- Antes de qualquer escolha havia cookies `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid`, `_clck`, `_clsk`. Presença não comprova envio de marketing, mas exige auditoria de tags/CMP e avaliação LGPD.
- Cinco reloads *na mesma aba/processo*, após `localStorage.clear()` e `Network.clearBrowserCookies`: banner visível e `consent default denied` nos cinco; runs 1 e 5 com beacon `G100`, `pscdl=denied`, `npa=1`; runs 2–4 com `pscdl=noapi`, `npa=0`, `_ga` pré-escolha e `gcd=13l3l3l3l1l1`, apesar do default visível. **Indício exploratório de estado residual/load-order**, não prova isolada de falha para cinco visitantes novos: o mesmo processo de navegador pode reter estado em memória. Reproduzir em cinco perfis/contextos de navegador realmente isolados com captura de Network antes de concluir race em produção.
- Console não auditado nesta rodada; sem atribuição causal a mensagens JS.

## GA4 consolidado (D-3, 29/10)

- 1.572 sessões, 949 engajadas, rejeição **39,63%**, duração média 221 s. 28/10: 1.578 sessões, 37,71% rejeição; 27/10: 1.719 sessões, 39,91% rejeição.
- Fontes 29/10: google 800 sessões, 39%; direto 218, 46,33%; rd-automacao 157, 47,77%; instagram 88, 39,77%; ig 79, 18,99%. `(not set)` 14 sessões, 78,57% — amostra pequena; não houve colapso generalizado.

**Status:** Coleta pós-aceite funcional; pendências de revisão na sequência de consentimento de recorrentes e cookies de marketing pré-escolha (Matias/Increazy + Adrian). Indício de inconsistência em reloads requer reteste isolado antes de classificar regressão.
