# Consent Mode GA4 — Teste diário 2026-09-02

- **Executado:** 02/09/2026, 08:01–08:06 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless em contexto novo, sem cookies ou armazenamento prévios

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Banner com ações **Rejeitar** e **Aceitar Tudo** visível; `gtag` function; `dataLayer` com 10 entradas; sem `cc_cookie_*` persistido |
| Consentimento inicial | `consent default` no índice 2: analytics, ads, personalização e dados de anúncios = `denied`; funcionalidade e segurança = `granted`; `wait_for_update=500` |
| Coleta antes da escolha | Request `PageView` para `gtmserver.conamore.com.br/g/collect`, `tid=G-V0KMM7L6M6`, `gcs=G100`, `npa=1`, `pscdl=denied`, `gcd=13p3p3p3p5l1` |
| Escolha real | Clique em **Aceitar Tudo** |
| Pós-escolha | `consent update` com analytics/ads/personalização = `granted`; evento `cc_consent_update` com analytics e marketing = `granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={marketing:true, statistics:true}`; cookies `_ga`, `_ga_V0KMM7L6M6` e `_ga_CDCKFVTR5M` presentes |
| Recarregamento consentido | Request `PageView` ao sGTM com `tid=G-V0KMM7L6M6`, `npa=0`, `en=PageView` |

## Eventos observados

- `gtm.js`
- `consent default` (`denied`) na primeira carga
- `another_page`, `gtm.dom`, `gtm.load`
- `gtm.click`
- `consent update` (`granted`)
- `cc_consent_update`
- `gtm.scrollDepth`
- `PageView` na coleta server-side

## GA4 consolidado — D-3

> D-1 não é usado como dado consolidado por causa da janela de processamento de 24–48 horas do GA4.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 30/08/2026 | 2.020 | 1.167 | 57,77% | **42,23%** | 3m17,2s |

Principais fontes: Google 1.466 sessões / 40,04% bounce; direto 214 / 59,35%; Instagram 123 / 44,72%; Facebook 45 / 31,11%. Não há padrão de 95%+ de bounce em todas as fontes no D-3.

## Anomalias e interpretação

1. **D-3 normal:** bounce consolidado de 42,23%, duração de 3m17,2s e engajamento normal nas principais fontes.
2. **Alerta provisório em 01/09 (D-1):** 1.817 sessões, apenas 29 engajadas, bounce de 98,40%, engagement de 1,60% e duração média de 11m49,2s. A anomalia aparece em todas as fontes relevantes — `(not set)` 100%, Google 97,37%, direto 97,91%, RD Station 100% e Instagram 100% — assinatura de falha de medição/consentimento, não de bot isolado. Como D-1 ainda está na janela de processamento, tratar como alerta e revalidar quando 01/09 virar D-3 em 04/09.
3. **Live atual funcionando:** em 02/09 o fluxo voltou a apresentar `consent default` negado, banner real, `consent update` concedido e `PageView` pós-consentimento. Isto indica funcionamento no momento do teste, mas não elimina possível intermitência em 01/09.
4. **Risco técnico de ordem persiste:** `gtm.js` aparece antes do `consent default` no `dataLayer`; o beacon inicial respeitou a negação, mas a ordem ainda é sujeita a race condition.
5. **Marketing antes do aceite — anomalia LGPD:** antes de qualquer escolha foram criados `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid` e `li_adsId`. Revisão permanece com Matias/Increazy e ciência de Adrian.
6. **Console:** sem erros JavaScript não capturados (`pageErrors=[]`). Falhas CORS de Reclame Aqui e Veels e aviso de moeda do Meta Pixel são ocorrências de terceiros, sem causalidade demonstrada com GA4.

## Status

- **Consent Mode ao vivo:** **FUNCIONANDO no teste de 02/09**, com default negado, escolha explícita, update concedido, persistência e `PageView` confirmado.
- **Métrica D-3:** normal — bounce **42,23%**.
- **Alerta:** D-1 em **98,40%** de bounce, ainda não consolidado; monitorar e revalidar em 04/09.
- **Pendências:** corrigir ordem do `consent default` antes do GTM e bloquear fornecedores de marketing antes do aceite.
