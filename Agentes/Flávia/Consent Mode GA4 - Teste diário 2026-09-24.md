# Consent Mode GA4 — Teste diário 2026-09-24

- **Executado:** 24/09/2026, 08:00–08:07 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, 5 contextos novos sem escolha + caminho **Aceitar Tudo**

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Site carregou; `gtag=function`; GTM `GTM-MMGX8ZL` e GA4 `G-V0KMM7L6M6` carregados; banner com **Rejeitar** e **Aceitar Tudo** visível |
| Consentimento inicial | `consent default` presente em 5/5 repetições; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Aceitar Tudo | `consent update` mudou analytics/ads/personalização para `granted`; `cc_consent_update` disparou; preferências persistidas em `cc_cookie_consent_status=true` e `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Repetição sem escolha | Beacons para `www.google-analytics.com/g/s/collect` ocorreram nas 5/5 cargas. O endpoint usa transporte POST agrupado e não expôs `tid`, `en`, `gcs`, `gcd`, `pscdl` e `npa` no payload capturável deste teste |
| Cookies pré-escolha | `_gcl_au` apareceu em 5/5 cargas; cookies `_ga`, `_ga_V0KMM7L6M6` e `_ga_CDCKFVTR5M` apareceram antes da escolha em 3/5 cargas, apesar do default `denied` |
| Console | Nenhum JavaScript não capturado. Erros CORS/servidor do widget Reclame Aqui são de terceiro e não sustentam causalidade sobre Consent Mode |

## Eventos observados

- `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`
- `RD Popup e WhatsApp`
- `consent default`
- `gtm.click`, `consent update`, `cc_consent_update`
- Coleta GA4 agrupada em `/g/s/collect`; o nome do evento não ficou legível no transporte capturado, portanto `page_view` não foi afirmado sem prova do payload

## GA4 — D-3 consolidado

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **21/09/2026 (D-3)** | **2.044** | **1.206** | **59,00%** | **41,00%** | **3m47s** |

Principais fontes: Google 1.198 sessões / 38,65% bounce; direto 400 / 57,00%; Instagram 189 / 34,39%; Facebook 39 / 33,33%; Bing 31 / 32,26%. Não existe colapso simultâneo nas origens.

## Conclusão

1. **Comando e interface do Consent Mode funcionam:** default negado, banner e atualização após aceite foram comprovados.
2. **Aplicação pré-consentimento permanece intermitente e não conforme:** cookies analíticos surgiram antes da escolha em 3/5 contextos, e `_gcl_au` em 5/5, apesar do estado negado.
3. **Coleta pré-escolha existe em 5/5 cargas.** Parte pode ser ping sem cookies do Consent Mode avançado, mas a criação intermitente de `_ga` sob `analytics_storage=denied` indica condição de corrida/ordem de carregamento.
4. **GA4 D-3 está normal:** bounce 41,00%, engajamento 59,00% e duração 3m47s. Sem assinatura consolidada de quebra sistêmica.

## Status

- **Consent default + escolha:** **FUNCIONANDO**.
- **Aplicação pré-consentimento:** **FALHA INTERMITENTE / NÃO CONFORME**.
- **GA4 D-3:** **NORMAL** — bounce **41,00%**.
- **Encaminhamento mantido:** Matias/Increazy — revisar corrida entre CMP, GTM web e tags Google; Adrian — manter avaliação LGPD sobre cookies pré-consentimento.
