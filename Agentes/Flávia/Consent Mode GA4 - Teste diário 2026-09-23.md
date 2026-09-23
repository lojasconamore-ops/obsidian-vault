# Consent Mode GA4 — Teste diário 2026-09-23

- **Executado:** 23/09/2026, 08:01–08:09 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contextos novos; caminhos **Aceitar Tudo**, **Rejeitar** e 5 repetições sem escolha

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP carregado sem erro; banner visível; `gtag=function`; IDs `G-V0KMM7L6M6` e `GTM-MMGX8ZL` presentes |
| Consentimento inicial | `consent default` presente em 5/5 repetições; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Aceitar Tudo | `consent update` mudou analytics/ads/personalização para `granted`; `cc_consent_update` registrou analytics/marketing `granted`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Rejeitar | `consent update` manteve analytics/ads/personalização `denied`; `cc_consent_update` disparou; `cc_cookie_preferences={"marketing":false,"statistics":false}` |
| Repetição sem escolha | Em 2/5 cargas, o beacon sGTM saiu como `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1` e cookies `_ga` foram criados. Em 3/5, saiu como `pscdl=denied`, `npa=1`, `gcs=G100`, `gcd=13p3p3p3p5l1`; porém uma dessas três ainda criou cookies `_ga` |
| Cookies pré-escolha | `_gcl_au` e `_fbp` apareceram em 5/5 cargas. Cookies `_ga` apareceram de forma intermitente antes da escolha. No caminho de rejeição, cookies publicitários já criados permaneceram |
| Coleta | `PageView` para `G-V0KMM7L6M6` via `gtmserver.conamore.com.br` ocorreu antes da escolha em 5/5 cargas. No aceite houve tráfego adicional de coleta, mas o `page_view` identificável já havia sido disparado antes da escolha |
| Console | Nenhum erro JavaScript não capturado. CORS do Reclame Aqui, warning de moeda do Meta Pixel e avisos WebGL/fontes são terceiros ou independentes da conclusão de consentimento |

## Eventos observados

- `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`
- `consent default`
- GA4/sGTM `PageView`
- `gtm.click`, `consent update`, `cc_consent_update`

## GA4 — dados consolidados

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 18/09/2026 | 1.921 | 1.107 | 57,63% | 42,37% | 6m14s |
| 19/09/2026 | 1.826 | 991 | 54,27% | 45,73% | 2m46s |
| **20/09/2026 (D-3)** | **1.872** | **1.074** | **57,37%** | **42,63%** | **4m12s** |
| 21/09/2026 (D-2) | 2.044 | 1.208 | 59,10% | 40,90% | 3m47s |
| 22/09/2026 (D-1, provisório) | 2.066 | 42 | 2,03% | 97,97% | 9m12s |

Principais fontes do D-3: Google 1.113 sessões / 38,72% bounce; direto 355 / 62,25%; Instagram 201 / 34,33%; Facebook 41 / 21,95%. Não há colapso global nas origens do período consolidado.

## Anomalias e conclusão

1. **O comando de Consent Mode e a interface de escolha funcionam:** banner e `consent default` negado aparecem; aceite e rejeição geram os updates esperados.
2. **Há falha intermitente de aplicação na carga inicial:** apesar do mesmo `consent default`, parte das cargas usa `pscdl=noapi`/`npa=0` e grava `_ga` antes da escolha. Outras usam o estado negado, mas cookies de marketing continuam sendo criados.
3. **D-3 normal:** bounce 42,63%, engajamento 57,37% e duração 4m12s; sem assinatura consolidada de quebra sistêmica.
4. **D-1 mostra a assinatura clássica de falha de tracking** — bounce 97,97%, somente 42 sessões engajadas e duração 9m12s — mas ainda está dentro da janela de processamento de 24–48h. Não classificar como retorno confirmado da quebra até consolidar; revalidar quando 22/09 chegar a D-3, em 25/09/2026.

## Status

- **Consent Mode — default e escolhas:** **FUNCIONANDO**.
- **Aplicação pré-consentimento:** **FALHA INTERMITENTE / NÃO CONFORME**.
- **Coleta GA4:** **ATIVA**, inclusive antes da escolha; revisar consent checks.
- **GA4 D-3:** **NORMAL** — bounce **42,63%**.
- **Alerta provisório:** D-1 em **97,97% bounce**, aguardando consolidação.
- **Encaminhamento:** Matias/Increazy devem investigar condição de corrida/ordem de carregamento entre CMP, GTM web e sGTM; Adrian deve manter avaliação LGPD sobre cookies e identificadores pré-consentimento.
