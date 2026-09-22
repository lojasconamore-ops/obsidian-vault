# Consent Mode GA4 — Teste diário 2026-09-22

- **Executado:** 22/09/2026, 08:00–08:06 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contextos novos; caminhos sem escolha, **Aceitar Tudo** e **Rejeitar**

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP 200; banner visível com **Rejeitar** e **Aceitar Tudo**; `gtag=function`; `dataLayer` com 10 entradas |
| Consentimento inicial | `consent default` presente; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Sem escolha | `page_view` e `PageView` enviados para `G-V0KMM7L6M6`, inclusive pelo sGTM; `gcd=13l3l3l3l1l1`, `pscdl=noapi`, `npa=0` |
| Cookies pré-escolha | `_ga`, `_ga_V0KMM7L6M6`, `_gcl_au`, `_fbp`, `IDE`, Bing/Clarity e identificadores do LinkedIn já existiam antes de qualquer escolha |
| Aceitar Tudo | `consent update` concedeu analytics/ads/personalização; `cc_consent_update` registrou analytics/marketing `granted`; preferências persistidas |
| Rejeitar | `consent update` manteve analytics/ads/personalização `denied`; `cc_cookie_preferences={"marketing":false,"statistics":false}`; cookies já criados permaneceram |
| Coleta comprovada | `page_view`, `PageView` e `user_engagement` para `G-V0KMM7L6M6`; sGTM em `gtmserver.conamore.com.br` |
| Console | Nenhum erro JavaScript não capturado. Erros CORS do Reclame Aqui e warning de moeda do Meta Pixel são terceiros/independentes |

## Eventos observados

- `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`
- `consent default`
- GA4 `page_view` / sGTM `PageView`
- `user_engagement`
- `gtm.click`, `consent update`, `cc_consent_update`
- `gtm.scrollDepth` no caminho de aceite

## GA4 — dados consolidados

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 17/09/2026 | 2.077 | 1.219 | 58,69% | 41,31% | 3m46s |
| 18/09/2026 | 1.921 | 1.107 | 57,63% | 42,37% | 6m14s |
| **19/09/2026 (D-3)** | **1.826** | **991** | **54,27%** | **45,73%** | **2m46s** |
| 20/09/2026 (D-2) | 1.872 | 1.074 | 57,37% | 42,63% | 4m12s |

Principais fontes do D-3: Google 1.118 sessões / 42,75% bounce; direto 374 / 60,43%; Instagram 139 / 30,94%; Facebook 29 / 31,03%; `(not set)` 22 / 54,55%. Não há colapso global nas origens.

## Anomalias e conclusão

1. **Fluxo de escolha funciona:** banner, default negado, updates de aceite/rejeição e persistência foram confirmados.
2. **Falha parcial de governança/LGPD permanece:** GA4/sGTM coletam `PageView` e cookies analíticos/publicitários são criados antes da escolha; ao rejeitar, os cookies já existentes não foram removidos.
3. **D-3 normal:** bounce 45,73%, engajamento 54,27%; sem assinatura de quebra sistêmica do tracking.
4. A anomalia provisória de D-1 observada no relatório anterior consolidou normalmente em D-2 (42,63% bounce), confirmando atraso de processamento de 24–48h.

## Status

- **Consent Mode — comando default e fluxo de escolha:** **FUNCIONANDO**.
- **Coleta GA4:** **FUNCIONANDO**.
- **Proteção pré-consentimento/LGPD:** **FALHA PARCIAL / NÃO CONFORME**.
- **GA4 D-3:** **NORMAL** — bounce **45,73%**.
- **Encaminhamento mantido:** Matias/Increazy devem revisar consent checks, disparos e gravação/remoção de cookies antes da escolha; Adrian deve avaliar o risco LGPD.
