# Consent Mode GA4 — Teste diário 2026-09-06

- **Executado:** 06/09/2026, 08:00–08:05 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless em contexto novo, sem cookies ou armazenamento prévios

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP 200; banner “Configure sua privacidade” visível; `gtag` function; `dataLayer` com 10 entradas; sem `cc_cookie_*` persistido |
| Consentimento inicial | `consent default` no índice 2: analytics, ads, personalização e dados de anúncios = `denied`; funcionalidade e segurança = `granted`; `wait_for_update=500` |
| Ordem | `gtm.js` no índice 1, portanto executado antes do `consent default` no índice 2 |
| Coleta antes da escolha | Request `PageView` para `gtmserver.conamore.com.br/g/collect`, `tid=G-V0KMM7L6M6`, `gcd=13l3l3l3l1l1`, `npa=0`, `pscdl=noapi` |
| Cookies antes da escolha | `_ga`, `_ga_V0KMM7L6M6`, `_ga_CDCKFVTR5M`, `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid` e identificadores de LinkedIn já presentes |
| Escolha real | Clique em **Aceitar Tudo** |
| Pós-escolha | `consent update` com analytics/ads/personalização = `granted`; evento `cc_consent_update` com analytics e marketing = `granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={marketing:true, statistics:true}` |
| Recarregamento consentido | Request `PageView` ao sGTM com `tid=G-V0KMM7L6M6`, `en=PageView`, `gcd=13n3n3n3n5l1`, `npa=0`, `pscdl=noapi` |

## Eventos observados

- `gtm.js`
- `consent default` (`denied`) na primeira carga
- `another_page`, `gtm.dom`, `gtm.load`
- `gtm.click`
- `consent update` (`granted`)
- `cc_consent_update`
- `PageView` na coleta server-side, antes da escolha e no recarregamento consentido

## GA4 consolidado — D-3

> D-1 não foi usado como dado consolidado por causa da janela de processamento de 24–48 horas do GA4.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 03/09/2026 | 1.519 | 776 | 51,09% | **48,91%** | 3m48,6s |

Principais fontes: Google 814 sessões / 39,31% bounce; direto 370 / 66,49%; `(not set)` 78 / **87,18%**; Instagram 69 / 50,72%; RD Station 30 / 66,67%. Não há padrão de 95%+ de bounce em todas as fontes.

### Tendência consolidada

| Data | Sessões | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|
| 01/09 | 1.915 | 57,13% | 42,87% | 3m56,4s |
| 02/09 | 1.732 | 51,15% | 48,85% | 3m07,7s |
| 03/09 | 1.519 | 51,09% | 48,91% | 3m48,6s |

## Anomalias e interpretação

1. **Tracking agregado normal no D-3:** bounce de 48,91%, engagement de 51,09% e duração de 3m48,6s. A quebra sistêmica de ~98% de bounce não aparece nos dados consolidados.
2. **Fluxo da CMP funciona:** banner, default negado, clique explícito, update concedido e persistência foram confirmados; a coleta GA4 com `G-V0KMM7L6M6` e `PageView` também foi confirmada após consentimento/recarregamento.
3. **Falha de ordem e privacidade persiste:** `gtm.js` antecede o `consent default`. Na sessão limpa, o beacon inicial saiu com `npa=0` e `pscdl=noapi`, e cookies/identificadores de GA4, Ads, Meta, Microsoft e LinkedIn foram criados antes da escolha. Isso não é comportamento compatível com o default negado e mantém risco LGPD.
4. **Fonte `(not set)` degradada:** 87,18% de bounce em 78 sessões, mas restrita a uma fonte; não caracteriza falha global.
5. **Console:** sem erros JavaScript não capturados (`pageErrors=[]`). Há falhas CORS do Reclame Aqui e Veels e aviso de moeda do Meta Pixel; são ocorrências de terceiros, sem causalidade comprovada com GA4.

## Status

- **Consent Mode:** **PARCIAL / NÃO CONFORME NA CARGA INICIAL** — UI e update funcionam, mas GTM/tags/cookies executam antes da escolha.
- **Métrica D-3:** normal — bounce **48,91%**.
- **Ação necessária:** Matias/Increazy devem colocar `consent default` antes do snippet GTM e bloquear GA4/Ads/Meta/Microsoft/LinkedIn até a escolha; manter Adrian informado pelo risco LGPD.
