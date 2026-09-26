# Consent Mode GA4 — Teste diário 2026-09-26

- **Executado:** 26/09/2026, 08:01–08:05 BRT
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
| Recarga pós-aceite | Preferência concedida persistiu; `PageView` confirmado para `G-V0KMM7L6M6` via `gtmserver.conamore.com.br`, com `gcd=13n3n3n3n5l1` |
| Console | Nenhum JavaScript não capturado. CORS/servidor do Reclame Aqui e warning de moeda do Meta Pixel são terceiros e não sustentam causalidade sobre Consent Mode |

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
| **23/09/2026 (D-3)** | **2.282** | **1.219** | **53,42%** | **46,58%** | **2m55s** |

Principais fontes: Google 1.385 sessões / 46,06% bounce; direto 426 / 56,57%; Instagram 210 / 37,14%; Facebook 30 / 43,33%; Linktree 27 / 11,11%. `(not set)` teve 21 sessões / 33,33% bounce. Não existe colapso simultâneo nas origens.

## Conclusão

1. **Interface e caminho pós-aceite funcionam:** banner, default negado, atualização, persistência e `PageView` após a recarga consentida foram comprovados.
2. **Aplicação inicial continua não conforme e consistente:** 5/5 contextos dispararam `PageView` e criaram cookies analíticos/publicitários antes da escolha, com `pscdl=noapi` apesar do `consent default=denied` no dataLayer.
3. **A condição se manteve igual ao teste de 25/09:** a falha pré-consentimento permanece reproduzível em 100% das cargas limpas.
4. **GA4 D-3 está operacional:** bounce 46,58%, engajamento 53,42% e duração 2m55s. Sem assinatura de quebra sistêmica em todas as origens.

## Status

- **Consent default + escolha:** **FUNCIONANDO**.
- **Caminho pós-aceite:** **FUNCIONANDO** — `PageView` confirmado.
- **Aplicação pré-consentimento:** **FALHA CONSISTENTE / NÃO CONFORME**.
- **GA4 D-3:** **OPERACIONAL** — bounce **46,58%**.
- **Encaminhamento mantido:** Matias/Increazy — corrigir prioridade/ordem entre CMP, GTM web e tags Google; Adrian — manter avaliação LGPD sobre cookies e coleta antes do consentimento.
