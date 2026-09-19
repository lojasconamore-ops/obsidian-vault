# Consent Mode GA4 — Teste diário 2026-09-19

- **Executado:** 19/09/2026, 08:05 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contexto novo, sem cookies/preferências; clique real em **Aceitar Tudo** e recarga consentida

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP 200; `gtag=function`; `dataLayer` com 10 entradas; botão **Aceitar Tudo** visível e acionável |
| Ordem inicial | `dataLayer`: `set` → `gtm.js` → `consent`; portanto o `consent default` entrou depois do início do GTM |
| Consentimento inicial | `consent default` presente; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Coleta pré-escolha | sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=noapi`, `npa=0`, sem `gcs`; cookies `_ga`, `_ga_V0KMM7L6M6` e `_ga_CDCKFVTR5M` já existiam |
| Aceitar Tudo | Clique real; `consent update` concedeu analytics/ads/personalização; `cc_consent_update` com analytics/marketing `granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Coleta consentida | Após recarga, sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`, `gcs=G111`; cookies GA presentes |
| Console | Nenhum erro JavaScript não capturado. CORS/Reclame Aqui e aviso de moeda do Meta Pixel são terceiros, sem causalidade comprovada com GA4 |

## Eventos observados

- Inicial: `gtm.js`, `consent default`, `another_page`, `gtm.dom`, `gtm.load`, comandos `js`, `config` e `event`.
- Rede pré-escolha: `PageView` enviado ao sGTM para `G-V0KMM7L6M6`.
- Após aceite: `gtm.click`, `consent update`, `cc_consent_update`.
- Após recarga consentida: `cc_consent_update` e `PageView` com `gcs=G111`.

## GA4 consolidado — D-3

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 12/09/2026 | 1.765 | 1.005 | 56,94% | 43,06% | 3m15s |
| 13/09/2026 | 1.909 | 1.170 | 61,29% | 38,71% | 3m46s |
| 14/09/2026 | 2.179 | 1.194 | 54,80% | 45,20% | 4m42s |
| 15/09/2026 | 2.373 | 1.385 | 58,36% | 41,64% | 5m26s |
| **16/09/2026 (D-3)** | **2.016** | **1.141** | **56,60%** | **43,40%** | **3m49s** |

Principais fontes do D-3: Google 1.166 sessões / 39,11% bounce; direto 375 / 61,33%; Instagram 205 / 39,51%; ChatGPT 37 / 32,43%; Facebook 37 / 24,32%; `(not set)` 20 / 55,00%. Não há colapso global por origem.

## Anomalias e conclusão

1. **Fluxo de escolha e atualização funciona:** default negado, botão real, update concedido, persistência e PageView consentido foram confirmados.
2. **Falha parcial antes da escolha:** embora o default exista, ele aparece depois de `gtm.js`; o beacon inicial usa `pscdl=noapi`/`npa=0`, envia `PageView` e cria cookies GA antes do aceite. A ordem indica corrida/configuração tardia do Consent Mode, não ausência total do comando.
3. **Risco LGPD de marketing:** Google Ads/DoubleClick, LinkedIn, Clarity e cookies de marketing também apareceram antes da escolha. Requer revisão técnica de GTM/CMP e avaliação jurídica.
4. **D-3 normal:** bounce 43,40%, alinhado à janela consolidada de 38,71%–45,20%; sem assinatura de falha sistêmica de mensuração.

## Status

- **Consent Mode GA4:** **FALHA PARCIAL** — pós-aceite funciona; proteção inicial não está sendo aplicada a tempo.
- **GA4 D-3:** **NORMAL** — bounce **43,40%**.
- **Próxima ação:** Matias/Increazy devem mover o `consent default` para antes da inicialização do GTM e bloquear tags/cookies não essenciais até a escolha; Adrian deve validar o impacto LGPD.
