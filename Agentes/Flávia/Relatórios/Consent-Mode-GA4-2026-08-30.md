# Consent Mode GA4 — teste ao vivo — 30/08/2026

- **URL:** https://www.conamore.com.br/
- **Executado:** 30/08/2026, 08:01–08:03 BRT
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium com cookies e armazenamento do domínio removidos antes do teste

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner “Configure sua privacidade” visível; `gtag` function; `dataLayer` ativo; sem preferências `cc_cookie_*` persistidas |
| Consentimento inicial | `consent default`: analytics, ads, personalização e dados de anúncios = `denied`; funcionalidade e segurança = `granted`; `wait_for_update=500` |
| Coleta antes da escolha | Request `PageView` ao sGTM `gtmserver.conamore.com.br/g/collect`, `tid=G-V0KMM7L6M6`, `gcs=G100`, `npa=1`, `pscdl=denied` — sinal de negação aplicado |
| Aceitar Tudo | `consent update` com analytics/marketing = `granted`; evento `cc_consent_update` com `analytics_consent: granted` e `marketing_consent: granted`; localStorage `cc_cookie_consent_status=true` e preferências marketing/statistics=true; banner oculto |
| Coleta pós-escolha | Request GA4 com `tid=G-V0KMM7L6M6` e `gcs=G111`; nenhum erro JavaScript não tratado durante o clique |
| Recarregamento consentido | Preferência `granted` persistida; request `PageView` ao sGTM com `tid=G-V0KMM7L6M6` |

## Eventos observados

- `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`
- `config` de `G-V0KMM7L6M6`
- `RD Popup e WhatsApp` (`rd_action=viewed`)
- `gtm.click` no botão Aceitar Tudo
- `cc_consent_update`
- `PageView` na coleta server-side

## GA4 consolidado — D-3

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 27/08/2026 | 1.853 | 1.040 | 56,13% | **43,87%** | 2m52,6s |

Principais fontes: Google 1.208 sessões / 40,89% bounce; direto 305 / 60,00%; Instagram 130 / 40,77%; Bing 34 / 35,29%; Facebook 25 / 36,00%.

## Anomalias e interpretação

1. **Sem quebra global de tracking no D-3:** bounce total de 43,87% e principais fontes em faixas plausíveis; o padrão de 95%+ em todas as fontes não ocorreu.
2. **Ordem do dataLayer ainda invertida:** `gtm.js` apareceu no índice 1 e `consent default` no índice 2. Hoje o primeiro request GA4 carregou corretamente os sinais `G100`, `npa=1` e `pscdl=denied`, mas a ordem continua sendo uma race condition técnica e deve ser corrigida para o default entrar antes do GTM.
3. **LinkedIn:** 91,67% de bounce, porém somente 12 sessões; monitorar, sem evidência de falha sistêmica.
4. **Referências suspeitas de baixo volume:** domínios `homestead*` e `related.inspiredtoday.net` somaram 7 sessões (0,38% do total). Possível spam/referral bot; impacto irrelevante no consolidado, acompanhar recorrência antes de filtrar.

## Status

- **Fluxo de Consent Mode:** **funcionando** — default negado, atualização concedida, persistência e coleta GA4 confirmadas.
- **Implementação inicial:** **risco técnico persistente** — `consent default` permanece depois de `gtm.js` no dataLayer, apesar de o request testado ter respeitado a negação.
- **Métrica D-3:** normal, bounce 43,87%.
- **Próxima ação:** manter a correção de ordem com Increazy/TI em aberto e continuar o monitoramento diário.
