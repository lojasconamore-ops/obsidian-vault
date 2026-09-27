# Consent Mode GA4 — Teste diário 2026-09-27

- **Executado:** 27/09/2026, 08:00–08:03 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, 5 contextos novos sem escolha + caminho **Aceitar Tudo** e recarga

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP 200 em 5/5; `gtag=function`; banner com **Rejeitar** e **Aceitar Tudo** visível |
| Consentimento inicial | `consent default` presente em 5/5; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Coleta antes da escolha | Em 5/5 contextos, o sGTM recebeu `PageView` para `G-V0KMM7L6M6` com `pscdl=noapi`, `npa=0` e `gcd=13l3l3l3l1l1` antes de qualquer clique |
| Cookies antes da escolha | `_ga`, `_ga_V0KMM7L6M6`, `_ga_CDCKFVTR5M` e `_gcl_au` presentes em 5/5 contextos, apesar do default `denied` |
| Aceitar Tudo | Clique confirmado; `consent update` alterou analytics/ads/personalização para `granted`; `cc_consent_update` disparou; preferências persistidas em `cc_cookie_consent_status=true` e `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Recarga após aceite | `consent update=granted` restaurado; `PageView` enviado para `G-V0KMM7L6M6` com `gcs=G111` |
| Console | Nenhum JavaScript não capturado. Erros CORS/servidor do widget Reclame Aqui e alerta de moeda do Meta Pixel são ocorrências de terceiros, sem causalidade comprovada sobre o Consent Mode |

## Eventos observados

- Antes da escolha: `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`, `consent default`
- Ao aceitar: `gtm.click`, `consent update`, `cc_consent_update`
- Coleta: `PageView` no endpoint `gtmserver.conamore.com.br/g/collect`, measurement ID `G-V0KMM7L6M6`

## GA4 — D-3 consolidado

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **24/09/2026 (D-3)** | **2.189** | **1.189** | **54,32%** | **45,68%** | **3m32s** |

Principais fontes: Google 1.427 sessões / 45,55% bounce; direto 396 / 59,09%; Instagram 92 / 36,96%; Bing 71 / 36,62%; `(not set)` 29 / 48,28%. Não existe colapso simultâneo nas origens.

## Conclusão

1. **Interface e atualização após escolha funcionam:** banner, default negado, update concedido e persistência foram comprovados.
2. **Aplicação pré-consentimento está falhando de forma consistente:** 5/5 cargas enviaram `PageView` e criaram cookies analíticos/marketing antes da escolha, enquanto o dataLayer declarava `denied`.
3. A divergência estável entre `consent default=denied` e beacon `pscdl=noapi` indica que as tags/coleta não estão respeitando o estado inicial — provável ordem de carregamento/integração CMP → GTM web → sGTM.
4. **GA4 D-3 está normal:** bounce 45,68%, engajamento 54,32% e duração 3m32s; sem assinatura de quebra sistêmica de mensuração.

## Status

- **Consent default + escolha:** **FUNCIONANDO**.
- **Aplicação pré-consentimento/LGPD:** **FALHA CONSISTENTE / NÃO CONFORME**.
- **GA4 D-3:** **NORMAL** — bounce **45,68%**.
- **Encaminhamento:** Matias/Increazy — corrigir precedência e bloqueio das tags antes do consentimento; Adrian — manter avaliação LGPD sobre cookies e `PageView` pré-consentimento.

## Artefatos

- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/scratch/ga4_consent_live_20260927.json`
- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/scratch/ga4_d3_20260924_output.txt`
