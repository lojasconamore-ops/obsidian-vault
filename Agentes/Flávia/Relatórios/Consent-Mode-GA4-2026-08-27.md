# Consent Mode GA4 — teste ao vivo — 27/08/2026

- **URL:** https://www.conamore.com.br/
- **Executado:** 27/08/2026, 08:01–08:05 BRT
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** perfil Chromium novo, sem persistência prévia de consentimento

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner visível; `gtag` function; `dataLayer` ativo; consent default com `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` e `personalization_storage` = `denied` |
| Aceitar Tudo | `consent update` com `analytics_storage: granted`; evento `cc_consent_update`; localStorage `cc_cookie_consent_status=true` e preferências marketing/statistics=true |
| Recarregamento consentido | `consent update` persistido; config `G-V0KMM7L6M6`; request para `gtmserver.conamore.com.br/g/collect` com `tid=G-V0KMM7L6M6`, `gcs=G111` e `en=PageView` |
| Eventos observados | `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`, config GA4, `RD Popup e WhatsApp`, `gtm.click`, `cc_consent_update`, `PageView` na coleta |

## GA4

| Data | Janela | Sessões | Engajadas | Bounce | Engajamento | Duração média |
|---|---:|---:|---:|---:|---:|---:|
| 24/08/2026 | D-3 consolidado | 2.214 | 1.151 | **48,01%** | 51,99% | 2,91 min |
| 26/08/2026 | D-1 provisório | 1.797 | 21 | **98,83%** | 1,17% | 8,51 min |

### Anomalias

1. **D-1 apresenta sinal global de tracking/consent:** `(not set)` 100% bounce (1.152 sessões, 0 engajadas), Google 98,20%, direto 97,56% e `(data not available)` 99,42%. Como afeta todas as fontes, não tem perfil de bot isolado. Porém D-1 ainda está dentro da janela de processamento de 24–48h; revalidar quando virar D-3.
2. **Ordem inicial suspeita:** no `dataLayer`, `gtm.js` apareceu antes de `consent default`. Antes de qualquer escolha já existiam cookies `_ga` e request `gtmserver.../g/collect` com `tid=G-V0KMM7L6M6` e `en=PageView`. Isso sugere disparo prematuro/race condition antes da aplicação do default-denied e merece correção técnica, apesar de o caminho pós-aceite estar funcional.

## Status

- **Fluxo pós-aceite:** funcionando.
- **Implementação inicial:** atenção — possível ordem incorreta entre Consent Mode e GTM, com coleta/cookies antes da escolha.
- **Métrica consolidada (D-3):** normal.
- **Métrica D-1:** anômala, mas provisória; monitorar até consolidação em 29/08/2026.
