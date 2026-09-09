# Consent Mode GA4 — Teste diário 2026-09-09

- **Executado:** 09/09/2026, 08:00–08:07 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contexto novo sem cookies/armazenamento prévios

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP 200; banner com **Aceitar Tudo** visível; `gtag=function`; `dataLayer` com 10 entradas |
| Consentimento inicial | `consent default` no índice 2: analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Ordem | `gtm.js` no índice 1 e `consent default` somente no índice 2 — ordem incorreta e sujeita a corrida |
| Pré-escolha | Beacon sGTM `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=noapi`, `gcd=13l3l3l3l1l1`, `npa=0`; cookies/IDs `_gcl_au`, `_ga`, `_ga_V0KMM7L6M6`, `_fbp`, `_uetsid`, `_uetvid`, Clarity e LinkedIn já presentes |
| Escolha real | Clique em **Aceitar Tudo** |
| Pós-escolha | `consent update` concedeu analytics/ads/personalização; `cc_consent_update` com analytics e marketing `granted`; banner ocultado |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={marketing:true, statistics:true}` |
| Coleta consentida | Após recarregar com consentimento persistido, beacon sGTM `tid=G-V0KMM7L6M6`, `en=PageView` confirmado |
| Console | Nenhum erro JavaScript não capturado; CORS/falhas de terceiros Reclame Aqui/Veels e aviso de moeda Meta observados em uma execução, sem causalidade comprovada com GA4 |

## Eventos observados

- `gtm.js`
- `consent default` (`denied`)
- `another_page`, `gtm.dom`, `gtm.load`
- `RD Popup e WhatsApp` (`viewed`)
- `gtm.click`
- `consent update` (`granted`)
- `cc_consent_update`
- `PageView` no sGTM, antes da escolha e confirmado novamente após aceite/recarregamento

## GA4 consolidado — D-3

> D-3 = 06/09/2026. D-1 não foi usado como referência por causa da janela de processamento de 24–48 horas.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 04/09/2026 | 1.401 | 774 | 55,25% | 44,75% | 3m38,6s |
| 05/09/2026 | 1.545 | 875 | 56,63% | 43,37% | 3m17,4s |
| **06/09/2026 (D-3)** | **1.390** | **836** | **60,14%** | **39,86%** | **3m50,0s** |

Principais fontes do D-3: Google 889 sessões / 39,03% bounce; direto 208 / 50,96%; Instagram 133 / 39,10%; Facebook 37 / 29,73%; ChatGPT 27 / 14,81%; `(not set)` 20 / 25,00%. Não há colapso global de engajamento.

## Rechecagem do alerta anterior — 07/09

O valor provisório de 96,90% de bounce reportado quando 07/09 ainda era D-1 foi corrigido pelo processamento do GA4. Na consulta de hoje: 1.448 sessões, 868 engajadas, **40,06% bounce** e 3m52,2s de duração média. Fontes principais também normais: Google 40,44%, direto 48,95%, Instagram 34,72% e Facebook 18,42%.

## Status

- **Consent Mode:** **PARCIAL / NÃO CONFORME NA CARGA INICIAL**.
- **Fluxo explícito de aceite:** **FUNCIONANDO**.
- **Coleta pós-aceite:** **FUNCIONANDO** — `PageView` com `G-V0KMM7L6M6` confirmado.
- **Métrica D-3:** **NORMAL** — bounce **39,86%**.
- **Anomalia anterior de 07/09:** **DESCARTADA** após consolidação; era atraso de processamento.
- **Risco atual:** GTM inicia antes do `consent default`; PageView, tags e identificadores de marketing aparecem antes da escolha. Há risco LGPD e medição intermitente.
- **Ação necessária:** Matias/Increazy devem executar o `consent default` antes do snippet GTM e bloquear GA4/Ads/Meta/Microsoft/LinkedIn/Clarity até a escolha; Adrian deve permanecer informado sobre o risco LGPD.
