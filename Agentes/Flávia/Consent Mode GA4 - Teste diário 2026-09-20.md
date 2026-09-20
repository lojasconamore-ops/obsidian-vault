# Consent Mode GA4 — Teste diário 2026-09-20

- **Executado:** 20/09/2026, 08:00–08:07 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contexto novo; teste inicial sem preferências persistidas e clique real em **Aceitar Tudo**

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner visível com **Personalizar**, **Rejeitar** e **Aceitar Tudo**; `gtag=function`; `dataLayer` com 10 entradas |
| Consentimento inicial | `consent default` presente; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| GA4 antes da escolha | Foram observados `page_view` e `PageView` com `tid=G-V0KMM7L6M6`; endpoint sGTM `gtmserver.conamore.com.br/g/collect`; sinais `gcd=13l3l3l3l1l1`, `npa=0`, `pscdl=noapi` |
| Cookies antes da escolha | Já estavam presentes `_ga`, `_ga_V0KMM7L6M6`, `_ga_CDCKFVTR5M`, `_gcl_au`, `_fbp`, LinkedIn, Bing/Clarity e outros identificadores, apesar do default negado |
| Aceitar Tudo | Clique real; `consent update` concedeu analytics/ads/personalização; `cc_consent_update` com analytics/marketing `granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Coleta pós-escolha | `user_engagement` observado para `G-V0KMM7L6M6`, com `gcs=G111`, `gcd=13r3r3r3r5l1`, via endpoint próprio `/metrics/ag/g/c` |
| Console | Erros CORS do Reclame Aqui e aviso de moeda do Meta Pixel; sem erro JavaScript não capturado ligado ao GA4 |

## Eventos observados no teste

- `consent default` — categorias de analytics/ads/personalização negadas
- `page_view` / `PageView` — disparados antes da escolha, inclusive para `G-V0KMM7L6M6`
- `consent update` — categorias concedidas após **Aceitar Tudo**
- `cc_consent_update` — analytics/marketing `granted`
- `user_engagement` — disparado após o aceite para `G-V0KMM7L6M6`
- Beacons adicionais pré-escolha: Google Ads/DoubleClick, LinkedIn e Microsoft Clarity

## GA4 — D-3 e janela de frescor

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **17/09/2026 (D-3)** | **2.077** | **1.219** | **58,69%** | **41,31%** | **3m46s** |
| 18/09/2026 (D-2) | 1.921 | 1.107 | 57,63% | 42,37% | 6m14s |
| 19/09/2026 (D-1, provisório) | 1.786 | 41 | 2,30% | 97,70% | 8m47s |

Principais fontes do D-3: Google 1.229 sessões / 36,53% bounce; direto 419 / 60,86%; Instagram 159 / 32,08%; `(not set)` 39 / 41,03%; Facebook 33 / 21,21%; Linktree 25 / 32,00%; ChatGPT 22 / 18,18%; Bing 20 / 35,00%. Não há colapso global no D-3.

No D-1 provisório, a anomalia aparece simultaneamente em `(not set)` (1.016 sessões / 100% bounce), Google (552 / 97,64%), direto (342 / 97,95%) e Instagram (67 / 95,52%). É assinatura de mensuração/processamento, não de uma única origem, mas a data ainda está dentro da janela de 24–48h.

## Anomalias e conclusão

1. **Fluxo visual e comandos do Consent Mode estão presentes:** banner real, default negado, update após aceite e persistência foram confirmados.
2. **Coleta GA4 pós-aceite funciona:** `user_engagement` para `G-V0KMM7L6M6` foi confirmado.
3. **Falha de governança pré-consentimento:** cookies analytics/marketing e beacons publicitários aparecem antes da decisão. O default negado existe, mas não está bloqueando integralmente armazenamento/disparos de terceiros.
4. **D-3 normal:** bounce 41,31%, engajamento 58,69%, sem assinatura de falha sistêmica.
5. **D-1 crítico, porém provisório:** bounce 97,70% em todas as principais origens. Revalidar após consolidação; não concluir retorno da falha apenas com D-1.

## Status

- **Consent Mode — fluxo de escolha:** **FUNCIONANDO**.
- **Coleta GA4 consentida:** **FUNCIONANDO**.
- **LGPD/tags antes da escolha:** **FALHA PARCIAL / NÃO CONFORME**.
- **Métrica D-3:** **NORMAL** — bounce **41,31%**.
- **D-1:** **ALERTA CRÍTICO PROVISÓRIO** — revalidar 19/09 após 24–48h.
- **Encaminhamento:** Matias/Increazy devem revisar consent checks e disparos pré-consentimento no GTM/CMP; Adrian deve avaliar o risco LGPD.
