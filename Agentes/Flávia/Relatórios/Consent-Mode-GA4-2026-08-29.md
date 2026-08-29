# Consent Mode GA4 — teste ao vivo — 29/08/2026

- **URL:** https://www.conamore.com.br/
- **Executado:** 29/08/2026, 08:00–08:07 BRT
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium limpo, cookies e localStorage removidos antes do teste

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner visível; `gtag` function; `dataLayer` ativo; `consent default` com `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` e `personalization_storage = denied`; sem preferências persistidas |
| Ordem inicial | `gtm.js` entrou no `dataLayer` no índice 1 e o `consent default` somente no índice 3 |
| Coleta antes da escolha | Cookies `_ga`, `_ga_V0KMM7L6M6` e `_ga_CDCKFVTR5M` já presentes. Requests `page_view`/`PageView` para `metrics/ag/g/c` e `gtmserver.conamore.com.br/g/collect`, `tid=G-V0KMM7L6M6`, sem `gcs`, com `npa=0` e `cid` presente |
| Aceitar Tudo | `consent update` com analytics/marketing = `granted`; evento `cc_consent_update` com `analytics_consent: granted` e `marketing_consent: granted`; localStorage `cc_cookie_consent_status=true` e preferências `marketing/statistics=true`; banner oculto |
| Evento pós-escolha | Request `user_engagement` para `metrics/ag/g/c`, `tid=G-V0KMM7L6M6`, `gcs=G111` |
| Recarregamento consentido | Preferência `granted` persistida; requests `page_view`/`PageView` para `metrics/ag/g/c` e `gtmserver.conamore.com.br/g/collect`, `tid=G-V0KMM7L6M6`, `gcs=G111` |

## GA4 consolidado

| Data | Janela | Sessões | Engajadas | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 24/08/2026 | D-5 | 2.214 | 1.151 | 48,01% | 2m55s |
| 25/08/2026 | D-4 | 2.291 | 1.213 | 47,05% | 2m51s |
| 26/08/2026 | **D-3 consolidado** | **1.900** | **1.112** | **41,47%** | **3m15s** |
| 27/08/2026 | D-2, em consolidação | 1.853 | 1.040 | 43,87% | 2m53s |
| 28/08/2026 | D-1 provisório | 1.819 | 49 | 97,31% | 9m21s |

## Anomalias e interpretação

1. **D-3 normal:** 26/08 consolidou em 41,47% de bounce. Principais fontes também normais: Google 40,29%, direto 48,59%, Instagram 46,21%. Não há quebra global de tracking no dado confiável.
2. **Anomalia provisória de 26/08 foi processamento:** em 27/08, o mesmo dia aparecia com 98,83% de bounce; hoje consolidou em 41,47%. Confirma que D-1 não deve ser usado para diagnóstico conclusivo.
3. **D-1 novamente anômalo, mas não confiável:** 28/08 mostra 97,31% de bounce e 9m21s; `(not set)` tem 1.104 sessões, 0 engajadas e 100% bounce. O padrão afeta várias fontes, porém ainda está na janela de processamento de 24–48h. Revalidar em 31/08, quando virar D-3.
4. **Race condition reproduzida:** `gtm.js` precedeu o `consent default`; houve cookies GA e coleta `page_view` com `npa=0`, `cid` e sem sinal `gcs` antes da escolha. O caminho pós-aceite funciona, mas a ordem inicial está incorreta e requer correção técnica no carregamento do Consent Mode antes do GTM.
5. **Console:** nenhum erro JavaScript não tratado ou rejeição de Promise. Foram observados erro de resposta do Reclame Aqui, aviso de moeda do Meta Pixel e um `console.error {}` de terceiro, sem evidência de bloqueio do GA4/GTM.

## Status

- **Fluxo pós-aceite:** funcionando e confirmado por `consent update`, `cc_consent_update`, `user_engagement` e `page_view` consentido.
- **Implementação inicial:** **falha de ordem/race condition reproduzida**; coleta e cookies ocorrem antes do `consent default` ser aplicado.
- **Métrica D-3:** normal, bounce 41,47%.
- **Próxima ação:** escalar à Increazy/TI a correção para executar o `consent default` antes do snippet do GTM; revalidar 28/08 em 31/08/2026.
