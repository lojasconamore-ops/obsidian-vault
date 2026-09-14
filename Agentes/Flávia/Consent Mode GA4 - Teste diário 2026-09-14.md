# Consent Mode GA4 — Teste diário 2026-09-14

- **Executado:** 14/09/2026, 08:00–08:06 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless/Playwright, múltiplos contextos limpos, sem preferência `cc_cookie_*`; fluxo real **Aceitar Tudo** e recarga

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner visível; `gtag=function`; `dataLayer` com 10 entradas; sem preferência `cc_cookie_*` |
| Consentimento inicial | `consent default` presente: analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Execução limpa A | Antes do clique, sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1`; cookies `_ga`, `_ga_V0KMM7L6M6`, `_ga_CDCKFVTR5M` e `_gcl_au` já existiam |
| Execução limpa B | Antes do clique, sGTM enviou ping restrito `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=denied`, `npa=1`, `gcd=13p3p3p3p5l1`; `_gcl_au` já existia, mas `_ga` ainda não |
| Tags de terceiros pré-escolha | Requisições de LinkedIn (`px.ads.linkedin.com`/`linkedin.com`) e Microsoft Clarity ocorreram antes do clique nas duas execuções precisas |
| Aceitar Tudo | `consent update` concedeu analytics/ads/personalização; `cc_consent_update` com analytics/marketing `granted`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Recarga consentida | sGTM confirmou `PageView` com `tid=G-V0KMM7L6M6`, `pscdl=noapi`, `npa=0`, `gcd=13n3n3n3n5l1` |
| Console | Nenhuma exceção JavaScript não capturada. Erro CORS do Reclame Aqui e alertas de Meta Pixel/WebGL/fontes classificados como terceiros e sem causalidade comprovada com GA4 |

## Eventos observados

- `consent default` (`denied` na sessão limpa)
- `PageView` do GA4/sGTM antes da escolha: uma execução restrita e outra plena aparente
- `page_view`/config do Google Ads
- requisições de LinkedIn e Clarity antes da escolha
- `consent update` (`granted` após Aceitar Tudo)
- `cc_consent_update`
- `PageView` GA4/sGTM após recarga consentida

## GA4 — D-3 e janela de frescor

> D-3 = 11/09/2026. D-1 (13/09) permanece na janela de processamento de 24–48h.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 09/09/2026 | 1.635 | 949 | 58,04% | 41,96% | 4m07,6s |
| 10/09/2026 | 1.871 | 1.023 | 54,68% | 45,32% | 4m10,6s |
| **11/09/2026 (D-3)** | **1.839** | **1.023** | **55,63%** | **44,37%** | **3m09,3s** |
| 12/09/2026 (D-2) | 1.765 | 1.005 | 56,94% | 43,06% | 3m15,4s |
| 13/09/2026 (D-1, provisório) | 1.854 | 26 | 1,40% | 98,60% | 10m21,1s |

Fontes principais do D-3: Google 1.048 sessões / 37,88% bounce; direto 418 / 64,59%; Instagram 135 / 37,78%; `(not set)` 41 / 53,66%; ChatGPT 31 / 32,26%. Não houve colapso global no dado consolidado.

## Anomalias e conclusão

1. **Comportamento pré-consentimento intermitente confirmado:** em uma sessão limpa, o GA4 enviou ping restrito (`pscdl=denied`, `npa=1`); em outra, enviou coleta plena aparente (`pscdl=noapi`, `npa=0`) e criou `_ga` antes da escolha. O `consent default` estava presente em ambas.
2. **Pixels de terceiros continuam antes da escolha:** LinkedIn e Clarity dispararam antes do aceite; `_gcl_au` também foi criado. Há risco LGPD ativo independentemente de o fluxo Google alternar entre restrito e pleno.
3. **Fluxo pós-aceite funciona:** update, persistência e `PageView` consentido foram verificados.
4. **D-3 normalizou:** 11/09 havia aparecido provisoriamente em 12/09 com 97,90% bounce e apenas 38 sessões engajadas; consolidou agora em 44,37% e 1.023 engajadas. Isso confirma que o alerta anterior era efeito de processamento/frescor, não colapso consolidado.
5. **D-1 repete a assinatura provisória:** 98,60% bounce, 26 engajadas e 10m21s. Não classificar como nova falha até 13/09 virar D-3 em 16/09.

## Status

- **Consent Mode GA4:** **FALHA PARCIAL / INTERMITENTE** — default e update presentes, mas o comportamento pré-escolha varia entre ping restrito e coleta plena aparente.
- **Fluxo pós-consentimento:** **FUNCIONANDO**.
- **LGPD:** **ALERTA CRÍTICO** — LinkedIn/Clarity e `_gcl_au` antes da decisão.
- **Métrica D-3:** **NORMAL** — bounce **44,37%**.
- **D-1:** **ANOMALIA PROVISÓRIA DE FRESCOR** — revalidar como D-3 em 16/09.
- **Ação necessária:** Matias/Increazy devem revisar a ordem e o bloqueio das tags no `GTM-MMGX8ZL`, especialmente LinkedIn/Clarity/Ads e a intermitência do sGTM; Adrian deve acompanhar o risco LGPD.
