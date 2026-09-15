# Consent Mode GA4 — Teste diário 2026-09-15

- **Executado:** 15/09/2026, 08:01–08:07 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contexto novo, sem cookies/preferências; clique real em **Aceitar Tudo** e recarga consentida

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner visível com **Rejeitar** e **Aceitar Tudo**; `gtag=function`; `dataLayer` com 10 entradas |
| Consentimento inicial | `consent default` presente; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| GA4 antes da escolha | sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=denied`, `npa=1`, `gcs=G100`, `gcd=13p3p3p3p5l1`: ping restrito compatível com Consent Mode avançado |
| Cookies antes da escolha | Somente `_gcl_au` entre os identificadores monitorados; `_ga` ainda ausente |
| Aceitar Tudo | Clique real; `consent update` concedeu analytics/ads/personalização; `cc_consent_update` com analytics/marketing `granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}`; banner oculto |
| Coleta consentida | Após recarga, sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`, `gcs=G111`, `npa=0`; cookies `_ga`, `_ga_V0KMM7L6M6` e `_ga_CDCKFVTR5M` presentes |
| Console | Nenhum erro JavaScript não capturado. CORS/Reclame Aqui e aviso de moeda do Meta Pixel são terceiros, sem causalidade comprovada com GA4 |

## Eventos observados

### Teste ao vivo
- `consent default` — negado antes da escolha
- `PageView` pré-escolha — ping restrito (`pscdl=denied`, `npa=1`)
- `consent update` — concedido após **Aceitar Tudo**
- `cc_consent_update` — analytics/marketing `granted`
- `PageView` consentido após recarga — `tid=G-V0KMM7L6M6`, `gcs=G111`

### GA4 consolidado — D-3 (12/09/2026)
Principais eventos: `page_view` 6.191; `view_item_list` 2.502; `user_engagement` 1.757; `session_start` 1.752; `view_item` 1.197; `first_visit` 1.169; `scroll` 886; `add_to_cart` 209; `begin_checkout` 65; `purchase` 28; `contato_whatsapp` 4; `compra_erp` 3; `purchase_erp` 2.

## GA4 — D-3 e janela de frescor

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **12/09/2026 (D-3)** | **1.765** | **1.005** | **56,94%** | **43,06%** | **3m15,4s** |
| 13/09/2026 (D-2) | 1.909 | 1.170 | 61,29% | 38,71% | 3m46,0s |
| 14/09/2026 (D-1, provisório) | 2.114 | 64 | 3,03% | 96,97% | 11m16,2s |

Principais fontes do D-3: Google 1.159 sessões / 38,91% bounce; direto 280 / 62,86%; Instagram 124 / 43,55%; LinkedIn 29 / 82,76%; `(not set)` 24 / 29,17%; Facebook 22 / 36,36%; ChatGPT 21 / 14,29%; Bing 20 / 20,00%. Não há colapso global no D-3.

## Anomalias e conclusão

1. **GA4 pré-consentimento voltou ao comportamento restrito:** diferente de 12/09, o teste limpo de hoje mostrou `pscdl=denied`, `npa=1` e ausência de `_ga` antes da escolha. A regressão específica de coleta GA4 plena pré-clique não foi reproduzida.
2. **Consent Mode GA4 funcionando no fluxo testado:** default negado, banner real, atualização após aceite, persistência e `PageView` consentido foram confirmados.
3. **Risco LGPD de marketing permanece:** `_gcl_au` e requisições de Google Ads/DoubleClick, LinkedIn e Clarity apareceram antes da escolha. O Consent Mode do GA4 estar correto não torna esses disparos automaticamente conformes.
4. **D-3 normal:** bounce 43,06%, sem assinatura de falha sistêmica por origem.
5. **D-1 crítico, mas provisório:** 96,97% bounce, só 64 sessões engajadas e 11m16s de duração; Google, direto, Instagram e `(not set)` estão simultaneamente em ~97–100% bounce. A assinatura é compatível com atraso/falha de mensuração, porém 14/09 ainda está dentro da janela de processamento de 24–48h. Não fechar causa antes da consolidação.

## Status

- **Consent Mode GA4:** **FUNCIONANDO** no teste limpo e no fluxo pós-aceite.
- **LGPD/tags de marketing:** **FALHA PARCIAL / NÃO CONFORME** — disparos e `_gcl_au` antes da decisão.
- **Métrica D-3:** **NORMAL** — bounce **43,06%**.
- **D-1:** **ALERTA CRÍTICO PROVISÓRIO** — revalidar 14/09 quando estiver consolidado.
- **Dono da correção LGPD:** Matias/Increazy no GTM/CMP; Adrian para avaliação jurídica.
