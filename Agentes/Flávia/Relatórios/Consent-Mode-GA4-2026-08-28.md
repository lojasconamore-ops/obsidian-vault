# Consent Mode GA4 — teste ao vivo — 28/08/2026

- **URL:** https://www.conamore.com.br/
- **Executado:** 28/08/2026, 08:00–08:04 BRT
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium limpo, sem cookies nem localStorage de consentimento

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner visível; `gtag` function; `dataLayer` ativo com 10 entradas; `consent default` com `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` e `personalization_storage = denied`; sem cookies `_ga` e sem preferências persistidas |
| Coleta antes da escolha | Ping cookieless `PageView` para `gtmserver.conamore.com.br/g/collect`, `tid=G-V0KMM7L6M6`, `gcs=G100`, `npa=1`; comportamento compatível com Consent Mode em estado negado |
| Aceitar Tudo | `consent update` com todos os storages de analytics/marketing = `granted`; evento `cc_consent_update` com `analytics_consent: granted` e `marketing_consent: granted`; localStorage `cc_cookie_consent_status=true` e preferências `marketing/statistics=true`; banner oculto |
| Recarregamento consentido | Estado `granted` persistido; request `PageView` para `gtmserver.conamore.com.br/g/collect` com `tid=G-V0KMM7L6M6`, `gcs=G111`, `npa=0`; cookies `_ga`, `_ga_V0KMM7L6M6` e `_ga_CDCKFVTR5M` presentes |

## GA4 consolidado

| Data | Janela | Sessões | Engajadas | Bounce | Engajamento | Duração média |
|---|---:|---:|---:|---:|---:|---:|
| 23/08/2026 | D-5 | 1.368 | 826 | 39,62% | 60,38% | 3m17s |
| 24/08/2026 | D-4 | 2.214 | 1.151 | 48,01% | 51,99% | 2m55s |
| 25/08/2026 | **D-3 consolidado** | **2.291** | **1.213** | **47,05%** | **52,95%** | **2m51s** |

## Anomalias

1. **Sem anomalia global de tracking em D-3.** Bounce de 47,05%, 0,96 pp abaixo de D-4; fontes principais em faixas plausíveis: Google 46,71%, direto 56,97%, Instagram 41,54%.
2. **LinkedIn com qualidade crítica:** 21 sessões, 1 engajada, bounce 95,24% e duração média 2,6s. Sinal localizado de canal/campanha, não de falha geral do Consent Mode.
3. **Console:** nenhum `pageerror` JavaScript não tratado. Falhas CORS/fetch do Reclame Aqui e Veels e aviso de moeda do Meta Pixel foram observados, mas são terceiros e não bloquearam GA4/GTM.
4. **Race condition não reproduzida hoje:** ao contrário do teste de 27/08, a sessão limpa iniciou sem cookies `_ga`; o primeiro `PageView` ocorreu em modo negado/cookieless (`G100`, `npa=1`).

## Status

- **Consent Mode:** funcionando no caminho inicial e pós-aceite.
- **Coleta GA4:** confirmada para `G-V0KMM7L6M6`, inclusive `PageView` consentido (`G111`).
- **Métrica D-3:** normal; sem sinal global de quebra de tracking.
- **Atenção:** investigar origem/campanha de LinkedIn pelo baixo engajamento localizado.
