# Consent Mode GA4 — Teste diário 2026-09-01

- **Executado:** 01/09/2026, 08:00–08:06 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless em contexto novo, sem cookies ou armazenamento prévios

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner “Configure sua privacidade” visível; `gtag` function; `dataLayer` com 10 entradas; sem `cc_cookie_*` persistido |
| Consentimento inicial | `consent default` no índice 2: analytics, ads, personalização e dados de anúncios = `denied`; funcionalidade e segurança = `granted`; `wait_for_update=500` |
| Coleta antes da escolha | Request `PageView` para `gtmserver.conamore.com.br/g/collect`, `tid=G-V0KMM7L6M6`, `gcs=G100`, `npa=1`, `pscdl=denied` |
| Escolha real | Clique em **Aceitar Tudo** |
| Pós-escolha | `consent update` com analytics/ads/personalização = `granted`; evento `cc_consent_update` com analytics e marketing = `granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={marketing:true, statistics:true}`; cookies `_ga`, `_ga_V0KMM7L6M6` e `_ga_CDCKFVTR5M` presentes |
| Recarregamento consentido | Request `PageView` ao sGTM com `tid=G-V0KMM7L6M6`, `gcs=G111`, `npa=0`, evento `en=PageView` |

## Eventos observados

- `gtm.js`
- `consent default` (`denied`) na primeira carga
- `another_page`, `gtm.dom`, `gtm.load`
- `config` de `G-V0KMM7L6M6`
- `RD Popup e WhatsApp`
- `consent update` (`granted`)
- `cc_consent_update`
- `PageView` na coleta server-side

## GA4 consolidado — D-3

> D-1 não foi usado por causa da janela de processamento de 24–48 horas do GA4.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 29/08/2026 | 1.686 | 999 | 59,25% | **40,75%** | 3m38,2s |

Principais fontes: Google 1.315 sessões / 39,54% bounce; direto 177 / 51,41%; Instagram 64 / 42,19%; Facebook 22 / 22,73%. Não há padrão de 95%+ de bounce em todas as fontes.

## Anomalias e interpretação

1. **Sem quebra sistêmica de tracking:** bounce consolidado de 40,75%, com engajamento normal nas principais fontes.
2. **Risco técnico de ordem persiste:** na sessão limpa, `gtm.js` aparece antes do `consent default` (índices 1 e 2). O request observado respeitou a negação (`G100`, `npa=1`, `pscdl=denied`), mas a ordem continua sujeita a race condition e deve ser corrigida para o default entrar antes do GTM.
3. **Marketing antes do aceite — anomalia LGPD:** ainda na carga inicial, antes de qualquer escolha, foram criados identificadores/cookies de marketing (`_gcl_au`, `_fbp`, `_uetsid`, `_uetvid` e `li_adsId`) e houve request do LinkedIn Pixel. O default negado foi respeitado pelo beacon GA4/Ads testado, mas não bloqueou todos os fornecedores. Encaminhar a Matias/Increazy para revisar os gatilhos de Meta, Microsoft Ads e LinkedIn; manter Adrian informado pelo risco de consentimento.
4. **Recarregamento consentido sem default:** com a preferência já concedida, o dataLayer registrou `gtm.js` no índice 1 e somente `consent update` no índice 2; o beacon trouxe `gcs=G111`, porém `gcd=13n3n3n3n5l1` e `pscdl=noapi`. A coleta funcionou, mas reforça o risco estrutural de ordem/ausência do default nessa navegação.
5. **Console:** sem erros JavaScript não capturados (`pageErrors=[]`). Falhas CORS do Reclame Aqui e Veels são de terceiros; sem causalidade demonstrada com GA4.

## Status

- **Consent Mode:** **FUNCIONANDO**, com default negado, escolha explícita, update concedido, persistência e `PageView` confirmado.
- **Métrica D-3:** normal — bounce **40,75%**.
- **Pendência:** corrigir a ordem para executar `consent default` antes de `gtm.js` em toda navegação; manter monitoramento diário.
