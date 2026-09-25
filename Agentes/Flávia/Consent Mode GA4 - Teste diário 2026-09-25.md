# Consent Mode GA4 — Teste diário 2026-09-25

- **Executado:** 25/09/2026, 08:03–08:06 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, 5 contextos novos sem escolha + caminho **Aceitar Tudo** e recarga pós-aceite

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Site carregou; `gtag=function`; banner com **Rejeitar** e **Aceitar Tudo** visível; GTM e GA4 carregados |
| Consentimento inicial | `consent default` presente em 5/5 repetições; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Aplicação pré-escolha | Em 5/5 cargas, o `PageView` para `G-V0KMM7L6M6` saiu via `gtmserver.conamore.com.br` com `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1`; cookies `_ga`, `_ga_V0KMM7L6M6`, `_ga_CDCKFVTR5M` e `_gcl_au` foram criados antes da escolha |
| Aceitar Tudo | `consent update` mudou analytics/ads/personalização para `granted`; `cc_consent_update` disparou; preferências persistidas em `cc_cookie_consent_status=true` e `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Recarga pós-aceite | Preferência concedida persistiu; novo `PageView` foi coletado para `G-V0KMM7L6M6` via sGTM. O caminho pós-aceite está operacional |
| Console | Nenhum JavaScript não capturado na recarga pós-aceite. CORS/servidor do Reclame Aqui e warning de moeda do Meta Pixel são terceiros e não sustentam causalidade sobre Consent Mode |

## Eventos observados

- `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`
- `RD Popup e WhatsApp`
- `consent default`
- sGTM/GA4 `PageView` pré-escolha
- `gtm.click`, `consent update`, `cc_consent_update`
- sGTM/GA4 `PageView` após aceite e recarga

## GA4 — D-3 consolidado

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **22/09/2026 (D-3)** | **2.120** | **1.191** | **56,18%** | **43,82%** | **3m25s** |

Principais fontes: Google 1.267 sessões / 41,20% bounce; direto 385 / 58,18%; Instagram 187 / 39,04%; Facebook 33 / 15,15%; Bing 32 / 46,88%. `(not set)` teve 28 sessões / 46,43% bounce. Não existe colapso simultâneo nas origens.

## Conclusão

1. **Interface e update funcionam:** banner, default negado, aceite, persistência e coleta pós-aceite foram comprovados.
2. **Aplicação inicial está não conforme e hoje foi consistente, não intermitente:** 5/5 contextos dispararam `PageView` e criaram cookies analíticos/publicitários antes da escolha, com beacon `pscdl=noapi` apesar do `consent default=denied` no dataLayer. A assinatura indica ordem de carregamento/corrida: o comando existe, mas não governa as tags a tempo.
3. **O alerta provisório de 22/09 não se confirmou:** ao chegar a D-3, o bounce consolidou em 43,82%, engajamento em 56,18% e duração em 3m25s. Sem quebra sistêmica do GA4.
4. **Comparação com 24/09:** a ocorrência pré-consentimento passou de cookies `_ga` em 3/5 contextos para 5/5, e os beacons sGTM ficaram legíveis como `pscdl=noapi` em todas as repetições.

## Status

- **Consent default + escolha:** **FUNCIONANDO**.
- **Caminho pós-aceite:** **FUNCIONANDO** — `PageView` confirmado.
- **Aplicação pré-consentimento:** **FALHA CONSISTENTE / NÃO CONFORME**.
- **GA4 D-3:** **NORMAL** — bounce **43,82%**.
- **Encaminhamento:** Matias/Increazy — corrigir prioridade/ordem entre CMP, GTM web e tags Google; Adrian — manter avaliação LGPD sobre cookies e coleta antes do consentimento.
