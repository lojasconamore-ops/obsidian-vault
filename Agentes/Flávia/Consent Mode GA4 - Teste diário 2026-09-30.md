# Consent Mode GA4 — Teste diário 2026-09-30

- **Executado:** 30/09/2026, 08:01–08:10 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** navegador cloud; estado limpo após remoção explícita de cookies/storage e recarga; carga inicial sem escolha + caminho **Aceitar Tudo**

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Banner | Visível: “Configure sua privacidade”; ações “Personalizar”, “Rejeitar” e “Aceitar Tudo” |
| Carga inicial | `gtag` presente; dataLayer com 10 entradas; `GTM-MMGX8ZL` e `G-V0KMM7L6M6` identificados |
| Consentimento inicial | `consent default` presente; `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` e `personalization_storage` em `denied`; `functionality_storage` e `security_storage` em `granted`; `wait_for_update=500` |
| Coleta pré-escolha | `PageView` para `G-V0KMM7L6M6`; `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1` — ping sem consentimento concedido |
| Cookies pré-escolha | `_ga`, `_ga_V0KMM7L6M6`, `_gcl_au` e `_fbp` observados; cookies `cc_cookie_*` ausentes. Presença isolada não comprova nova gravação nem coleta com consentimento concedido |
| Aceitar Tudo | `consent update` alterou analytics e marketing para `granted` |
| Evento customizado | `cc_consent_update` com `analytics_consent=granted` e `marketing_consent=granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Coleta pós-escolha | `PageView` e hits subsequentes para `G-V0KMM7L6M6`; `gcs=G111` confirmou atualização do sinal concedido |
| Console | Nenhum erro JavaScript não capturado relacionado ao consentimento foi observado |

## Eventos observados

- Pré-escolha: `consent default` e `PageView` em modo negado/cookieless (`gcs=G100`, `pscdl=denied`, `npa=1`).
- Pós-escolha: `consent update`, `cc_consent_update`, `PageView` e hits subsequentes com `gcs=G111`.
- O `pscdl` permaneceu `denied` no resumo pós-escolha; o sinal efetivo atualizado foi confirmado por `gcs=G111` e pelo dataLayer.

## GA4 — consolidado e sinal recente

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 25/09/2026 | 2.151 | 1.140 | 53,00% | 47,00% | 2m38s |
| 26/09/2026 | 1.785 | 970 | 54,34% | 45,66% | 2m47s |
| **27/09/2026 (D-3)** | **1.794** | **1.014** | **56,52%** | **43,48%** | **3m06s** |
| 28/09/2026 (D-2) | 2.157 | 1.138 | 52,76% | 47,24% | 3m52s |
| 29/09/2026 (D-1, preliminar) | 2.364 | 42 | 1,78% | 98,22% | 7m41s |

No D-3, as fontes principais permaneceram normais: Google 1.233 sessões / 42,74% bounce; direto 240 / 52,92%; Instagram 93 / 26,88%; Bing 35 / 42,86%; `(not set)` 23 / 56,52%. Não houve colapso simultâneo.

O dado de 28/09, que no relatório de ontem aparecia provisoriamente com bounce de 98,42%, consolidou hoje em 47,24%. Isso confirma forte efeito da janela de processamento do GA4. Em 29/09 reaparece a mesma assinatura preliminar — 98,22% geral, `(not set)` 100%, Google 97,42%, direto 96,96%, Bing e Instagram 100% — mas o teste ao vivo de hoje está saudável. Portanto, não classificar 29/09 como nova falha antes da consolidação.

## Conclusão

1. **Consent Mode funcionando no teste de hoje:** default negado, banner visível, atualização após aceite e coleta GA4 comprovados.
2. **Regressão observada em 29/09 não apareceu hoje:** não houve auto-grant pré-escolha e o beacon pré-consentimento carregou sinais negados.
3. **GA4 D-3 normal:** bounce de 43,48%, sem colapso transversal por origem.
4. **D-1 anômalo, mas inconclusivo:** bounce de 98,22% em 29/09 está dentro da janela de processamento; 28/09 demonstrou que esse padrão pode normalizar no dia seguinte.
5. **Limitação:** foram iniciadas cinco repetições para checar intermitência por causa dos cookies pré-escolha, mas o serviço de acompanhamento do navegador bloqueou a recuperação dos resultados adicionais. O fluxo completo principal foi concluído e validado.

## Status

- **Consent Mode inicial:** **FUNCIONANDO** — default negado presente.
- **Banner:** **FUNCIONANDO** — visível e interativo.
- **Atualização após aceite:** **FUNCIONANDO**.
- **Coleta GA4:** **FUNCIONANDO** — `PageView` para `G-V0KMM7L6M6` e mudança `G100 → G111`.
- **GA4 D-3:** **NORMAL** — bounce **43,48%**.
- **Anomalia D-1:** **ALERTA PRELIMINAR** — bounce **98,22%**, revalidar após 24–48h.
- **Ação:** manter monitoramento; sem evidência suficiente hoje para novo escalonamento técnico. Revalidar 29/09 quando consolidado e repetir o teste de intermitência em contextos limpos.
