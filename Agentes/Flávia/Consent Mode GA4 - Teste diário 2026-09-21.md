# Consent Mode GA4 — Teste diário 2026-09-21

- **Executado:** 21/09/2026, 08:01–08:08 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contexto novo, clique real em **Aceitar Tudo** e recarga consentida

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP 200; banner visível com **Rejeitar** e **Aceitar Tudo**; `gtag=function`; `dataLayer` com 10 entradas |
| Consentimento inicial | `consent default` presente; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Coleta pré-escolha | sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`, sem `gcs`, com `gcd=13l3l3l3l1l1`, `pscdl=noapi`, `npa=0` |
| Cookies pré-escolha | `_ga`, `_ga_V0KMM7L6M6`, `_ga_CDCKFVTR5M`, `_gcl_au`, `_fbp`, Bing/Clarity e outros identificadores já existiam apesar do default negado |
| Aceitar Tudo | `consent update` concedeu analytics/ads/personalização; `cc_consent_update` registrou analytics/marketing `granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Coleta pós-escolha | Após recarga consentida, sGTM enviou `PageView` para `G-V0KMM7L6M6` com `gcs=G111`; coleta consentida confirmada |
| Console | Sem erro JavaScript não capturado. Erros CORS do Reclame Aqui são de terceiro, sem causalidade comprovada com GA4 |

## Eventos observados

- `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`
- `consent default` com armazenamento analítico/publicitário negado
- `PageView` para `G-V0KMM7L6M6` antes da escolha
- `gtm.click`, `consent update`, `cc_consent_update`
- `PageView` consentido após recarga, com `gcs=G111`
- Evento técnico `hermes_consent_test` entrou no `dataLayer`, mas não houve beacon dedicado claramente identificável na janela de observação; a comprovação de coleta pós-consentimento foi feita pelo `PageView` após recarga

## GA4 — dados consolidados e janela de frescor

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 16/09/2026 | 2.016 | 1.141 | 56,60% | 43,40% | 3m49s |
| 17/09/2026 | 2.077 | 1.219 | 58,69% | 41,31% | 3m46s |
| **18/09/2026 (D-3)** | **1.921** | **1.107** | **57,63%** | **42,37%** | **6m14s** |
| 19/09/2026 (D-2) | 1.826 | 991 | 54,27% | 45,73% | 2m46s |
| 20/09/2026 (D-1, provisório) | 1.818 | 21 | 1,16% | 98,84% | 8m34s |

Principais fontes do D-3: Google 1.093 sessões / 38,98% bounce; direto 387 / 56,85%; Instagram 195 / 33,33%; Facebook 32 / 31,25%; `(not set)` 30 / 50,00%; Linktree 25 / 12,00%; ChatGPT 19 / 15,79%. Não há colapso global no D-3.

A anomalia provisória deslocou-se com a janela de processamento: em 20/09, o dia 19/09 aparecia com 97,70% de bounce e apenas 41 sessões engajadas; hoje, consolidou em 45,73% e 991 sessões engajadas. Isso confirma atraso de processamento de 24–48h, e não falha sistêmica naquele dia. O dia 20/09 agora aparece com 98,84%, mas permanece D-1 e não deve ser usado para diagnóstico definitivo.

## Anomalias e conclusão

1. **Fluxo de consentimento funciona:** banner, default negado, update após aceite, persistência e coleta consentida foram confirmados.
2. **Falha parcial de governança/LGPD continua:** `PageView`, cookies analíticos e identificadores de marketing aparecem antes da decisão, apesar do default negado.
3. **D-3 normal:** bounce 42,37% e engajamento 57,63%, sem assinatura de falha de tracking em todas as origens.
4. **D-1 crítico, porém provisório:** bounce 98,84% e apenas 21 sessões engajadas. O comportamento do D-2 demonstra que essa leitura tende a ser processamento incompleto; revalidar após consolidação.

## Status

- **Consent Mode — fluxo de escolha:** **FUNCIONANDO**.
- **Coleta GA4 consentida:** **FUNCIONANDO**.
- **Proteção pré-consentimento/LGPD:** **FALHA PARCIAL / NÃO CONFORME**.
- **GA4 D-3:** **NORMAL** — bounce **42,37%**.
- **D-1:** **ALERTA PROVISÓRIO** — não escalar como nova quebra antes de 24–48h.
- **Encaminhamento mantido:** Matias/Increazy devem revisar a ordem do `consent default`, consent checks e disparos/cookies pré-escolha; Adrian deve avaliar o risco LGPD.
