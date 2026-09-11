# Consent Mode GA4 — Teste diário 2026-09-11

- **Executado:** 11/09/2026, 08:00–08:04 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contexto novo sem cookies/armazenamento prévios; caminho **Aceitar Tudo** e recarga com consentimento persistido

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Página carregou; banner com **Aceitar Tudo** e **Rejeitar** visível; `gtag=function`; `dataLayer` com 10 entradas |
| Consentimento inicial | `consent default`: analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Pré-escolha | Beacon sGTM `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=denied`, `gcd=13p3p3p3p5l1`, `npa=1`: ping sem consentimento, compatível com Consent Mode avançado |
| Cookies/tags pré-escolha | Antes da decisão já existiam `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid`, Clarity e cookies/requests do LinkedIn; `_ga` ainda não existia |
| Aceitar Tudo | `consent update` concedeu analytics/ads/personalização; `cc_consent_update` com analytics/marketing `granted`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Coleta consentida | Após recarga com preferência persistida: sGTM `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=noapi`, `npa=0`; `_ga`, `_ga_V0KMM7L6M6` e `_ga_CDCKFVTR5M` criados |
| Console | Nenhum erro JavaScript não capturado. CORS/falhas do Reclame Aqui e aviso de moeda do Meta Pixel observados como terceiros, sem causalidade comprovada com GA4 |

## Eventos observados

- `gtm.js`
- `consent default` (`denied` na sessão limpa)
- `PageView` no sGTM antes da escolha como ping consent-mode (`pscdl=denied`, `npa=1`)
- `consent update` (`granted` após Aceitar Tudo)
- `cc_consent_update`
- `another_page`, `gtm.dom`, `gtm.load`
- `PageView` consentido após recarga (`tid=G-V0KMM7L6M6`, `pscdl=noapi`, `npa=0`)

## GA4 consolidado — D-3

> D-3 = 08/09/2026. D-1 permanece provisório por causa do processamento de 24–48h.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **08/09/2026 (D-3)** | **1.620** | **961** | **59,32%** | **40,68%** | **4m19,7s** |
| 09/09/2026 (D-2) | 1.635 | 949 | 58,04% | 41,96% | 4m07,6s |
| 10/09/2026 (D-1, provisório) | 1.775 | 47 | 2,65% | 97,35% | 10m25,1s |

Principais fontes do D-3: Google 954 sessões / 40,99% bounce; direto 317 / 48,26%; Instagram 93 / 46,24%; `(not set)` 38 / 57,89%; Facebook 30 / 6,67%. Não há colapso global no dia consolidado.

## Anomalias

1. **O alerta provisório de 09/09 não se confirmou:** no teste de 10/09 o D-1 aparecia com 97,52% de bounce e 38 sessões engajadas; após consolidação, 09/09 corrigiu para 41,96% e 949 engajadas. Confirma atraso de processamento do GA4, não uma nova falha naquele dia.
2. **10/09 repete provisoriamente o padrão de dado incompleto:** 97,35% de bounce, 47 engajadas, 10m25s; `(not set)` representa 66,54% das sessões e tem 99,92% de bounce. Não classificar como retorno da falha até D-3.
3. **Risco LGPD permanece:** identificadores/pixels de Google Ads, Meta, Microsoft, LinkedIn e Clarity aparecem antes da escolha, embora o `consent default` esteja `denied` e o GA4 use ping sem consentimento. GTM/CMP deve bloquear tags de marketing até aceite.

## Status

- **Consent Mode GA4:** **FUNCIONANDO no fluxo técnico** — default negado, atualização após aceite e coleta `PageView` consentida confirmados.
- **Conformidade pré-consentimento:** **PARCIAL / NÃO CONFORME** — tags e identificadores de marketing são ativados antes da decisão.
- **Métrica D-3:** **NORMAL** — bounce **40,68%**.
- **D-1:** **ALERTA PROVISÓRIO**, não conclusivo — revalidar 10/09 quando virar D-3 em 13/09.
- **Ação necessária:** Matias/Increazy devem revisar bloqueio pré-consentimento de Google Ads/Meta/Microsoft/LinkedIn/Clarity; Adrian deve permanecer informado sobre o risco LGPD.
