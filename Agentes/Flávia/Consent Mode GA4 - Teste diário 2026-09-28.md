# Consent Mode GA4 — Teste diário 2026-09-28

- **Executado:** 28/09/2026, 08:01–08:10 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** navegador em nuvem; caminho controlado de aceite + 5 contextos independentes sem escolha

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Teste controlado após limpeza | Banner **Aceitar Tudo** apareceu; foi observado `consent default` com analytics/ads/personalização `denied`; após o clique houve `consent update=granted` e `cc_consent_update` |
| Intermitência — 5 contextos limpos | `consent default` **ausente em 5/5**; `consent update=granted` e `cc_consent_update` ocorreram automaticamente, sem ação do visitante |
| Banner nos 5 contextos | Detectado em 2/5 e ausente em 3/5 — comportamento inconsistente |
| Cookies antes da escolha | `_ga`, `_gcl_au` e `_fbp` presentes em 5/5 contextos |
| Coleta antes da escolha | `page_view`/`PageView` enviados para `G-V0KMM7L6M6`; `pscdl=noapi`, `npa=0`; quatro execuções mostraram `gcd=13n3n3n3n5l1` e uma `gcd=13l3l3l3l1l1` |
| Caminho pós-aceite | `cc_cookie_consent_status=true`, preferências de marketing/estatísticas persistidas e coleta GA4 observada |

## Eventos observados

- Sem escolha: `consent update` automático, `cc_consent_update`, `page_view` e `PageView`.
- Após aceite no teste controlado: `consent update`, `cc_consent_update` e `PageView`.

## GA4 — D-3 consolidado

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **25/09/2026 (D-3)** | **2.151** | **1.140** | **53,00%** | **47,00%** | **2m38s** |

Principais fontes: Google 1.454 sessões / 45,19% bounce; direto 351 / 60,11%; Bing 65 / 35,38%; Instagram 62 / 38,71%; `(not set)` 40 / 57,50%. Não há colapso simultâneo nas origens em D-3.

## Alerta de dado recente

- **27/09/2026 (D-1, ainda em processamento):** 1.757 sessões, 13 engajadas, bounce **99,26%**, duração média **9m12s**.
- A assinatura é compatível com falha de mensuração, mas D-1 não deve ser fechado antes da consolidação de 24–48h. Revalidar quando a data virar D-3.

## Conclusão

1. **Regressão/intermitência confirmada ao vivo:** o fluxo correto apareceu no teste controlado, porém 5/5 novos contextos não apresentaram `consent default` e concederam consentimento automaticamente.
2. **Não conformidade pré-consentimento:** cookies analíticos/marketing e `page_view`/`PageView` ocorreram antes de escolha do visitante.
3. A mistura entre o fluxo correto e os cinco contextos quebrados indica **condição de corrida/ordem de carregamento**, não uma correção estável.
4. **GA4 D-3 está normal**, com bounce de 47,00%; o D-1 está anômalo, mas ainda não consolidado.

## Status

- **Consent Mode:** **FALHA INTERMITENTE/REGRESSÃO ATIVA**.
- **LGPD pré-consentimento:** **NÃO CONFORME**.
- **GA4 D-3:** **NORMAL** — bounce **47,00%**.
- **Encaminhamento:** Matias/Increazy — revisar ordem CMP → GTM web → sGTM e impedir `update=granted`, cookies e coleta antes da escolha; Adrian — manter avaliação LGPD.
