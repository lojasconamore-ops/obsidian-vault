# Consent Mode GA4 — Teste diário 2026-09-12

- **Executado:** 12/09/2026, 08:01–08:05 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, perfil novo; sessão sem preferência `cc_cookie_*`; fluxo real **Aceitar Tudo** e recarga

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner visível com **Rejeitar** e **Aceitar Tudo**; `gtag=function`; `dataLayer` com 10 entradas no reteste limpo |
| Consentimento inicial | `consent default` presente: analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Coleta antes da escolha | sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1` e client ID antes do clique |
| Cookies/tags antes da escolha | `_ga`, `_ga_V0KMM7L6M6`, `_ga_CDCKFVTR5M`, `_gcl_au`, `_fbp`, UET/Bing, Clarity e LinkedIn já ativos; requisições Google Ads, Meta, Microsoft, Clarity e LinkedIn presentes |
| Aceitar Tudo | Clique real no botão; `consent update` concedeu analytics/ads/personalização; `cc_consent_update` com analytics/marketing `granted`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Recarga consentida | `PageView` confirmado no sGTM com `tid=G-V0KMM7L6M6`, `gcs=G111`, `gcd=13n3n3n3n5l1`, `npa=0` |
| Console | Nenhum erro JavaScript não capturado observado no reteste controlado |

## Eventos observados

- `consent default` (`denied` na sessão sem preferência)
- `PageView` no sGTM **antes da escolha**, mas como coleta plena aparente (`pscdl=noapi`, `npa=0`)
- `config` para `G-V0KMM7L6M6`
- `RD Popup e WhatsApp` (`rd_action=viewed`)
- `consent update` (`granted` após Aceitar Tudo)
- `cc_consent_update`
- `PageView` após recarga consentida

## GA4 — D-3 e janela de frescor

> D-3 = 09/09/2026. D-1 ainda está na janela de processamento de 24–48h.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **09/09/2026 (D-3)** | **1.635** | **949** | **58,04%** | **41,96%** | **4m07,6s** |
| 10/09/2026 (D-2) | 1.871 | 1.023 | 54,68% | 45,32% | 4m10,6s |
| 11/09/2026 (D-1, provisório) | 1.806 | 38 | 2,10% | 97,90% | 10m02,8s |

Principais fontes do D-3: Google 932 sessões / 38,41% bounce; direto 336 / 54,17%; Instagram 110 / 39,09%; `(not set)` 52 / 73,08%; Facebook 36 / 16,67%. Não há colapso global no D-3 consolidado.

## Anomalias e conclusão

1. **Regressão ao vivo confirmada no bloqueio pré-consentimento:** embora o `consent default=denied` e o banner estejam presentes, GA4 e tags de marketing coletam e criam identificadores antes da escolha. Ontem o GA4 pré-escolha aparecia como ping restrito (`pscdl=denied`, `npa=1`); hoje apareceu `pscdl=noapi`, `npa=0` com `_ga` criado.
2. **Fluxo de atualização funciona:** aceitar dispara `consent update=granted`, `cc_consent_update` e mantém preferência. Isso não corrige a coleta já ocorrida antes do consentimento.
3. **D-3 normal:** bounce de 41,96%; D-2 também normalizou em 45,32%.
4. **D-1 anômalo, ainda provisório:** bounce 97,90%, 38 sessões engajadas (queda de 96,29% contra D-2), duração de 10m02,8s e `(not set)` com 1.091 sessões (60,41% do total) e 100% bounce. O padrão é compatível com falha global de mensuração, mas não deve ser fechado até consolidar em D-3.

## Status

- **Consent Mode GA4:** **FALHA PARCIAL / REGRESSÃO ATIVA** — comandos default/update existem, porém a coleta pré-consentimento não está respeitando o estado negado.
- **LGPD:** **NÃO CONFORME** — identificadores e pixels de marketing antes da decisão.
- **Métrica D-3:** **NORMAL** — bounce **41,96%**.
- **D-1:** **ALERTA CRÍTICO PROVISÓRIO** — revalidar 11/09 quando virar D-3 em 14/09.
- **Ação necessária:** Matias/Increazy devem revisar imediatamente ordem de disparo, Consent Mode e bloqueios das tags no `GTM-MMGX8ZL`; Adrian deve ser informado sobre a exposição LGPD.
