# Consent Mode GA4 — Teste diário 2026-09-08

- **Executado:** 08/09/2026, 08:01–08:10 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contextos novos sem cookies/armazenamento prévios

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP 200; banner com “Aceitar Tudo”, “Rejeitar” e “Personalizar” visível; `gtag` = function; `dataLayer` = object, 10 entradas |
| Consentimento inicial | `consent default` no índice 2: analytics, ads, dados de anúncios e personalização = `denied`; funcionalidade e segurança = `granted`; `wait_for_update=500` |
| Ordem | `gtm.js` aparece no índice 1 e o `consent default` somente no índice 2: ordem incorreta e sujeita a corrida |
| Escolha real | Clique em **Aceitar Tudo** |
| Pós-escolha | `consent update` com analytics/ads/personalização = `granted`; evento `cc_consent_update` com analytics e marketing = `granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={marketing:true, statistics:true}`; cookies `_ga` e `_ga_V0KMM7L6M6` criados após a escolha no fluxo principal |
| Coleta consentida | Após recarregar com consentimento persistido, beacon sGTM com `tid=G-V0KMM7L6M6`, `en=PageView`, `gcs=G111`, `gcd=13n3n3n3n5l1`, `npa=0` |
| Teste de repetibilidade | 3 sessões limpas adicionais: todas exibiram banner e `consent default=denied`, mas 1/3 beacons iniciais saiu como `pscdl=noapi`, `gcd=13l3l3l3l1l1`, `npa=0`; 2/3 saíram como `pscdl=denied`, `gcs=G100`, `gcd=13p3p3p3p5l1`, `npa=1` |
| Cookies pré-escolha | Mesmo com default negado, foram observados `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid` e identificador de LinkedIn antes do aceite |

## Eventos observados

- `gtm.js`
- `consent default` (`denied`)
- `another_page`, `gtm.dom`, `gtm.load`
- `gtm.click`
- `consent update` (`granted`)
- `cc_consent_update`
- `PageView` no sGTM, inclusive confirmado após consentimento/recarregamento
- Comando gtag `event: RD Popup e WhatsApp` presente no `dataLayer`

## GA4 consolidado — D-3

> D-3 = 05/09/2026. D-1 não foi tratado como consolidado por causa da janela de processamento de 24–48 horas do GA4.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 05/09/2026 | 1.545 | 875 | 56,63% | **43,37%** | 3m17,4s |

Principais fontes no D-3: Google 989 sessões / 42,37% bounce; direto 286 / 55,94%; Instagram 91 / 40,66%; `(not set)` 36 / 47,22%; Facebook 30 / 33,33%; Linktree 25 / 8,00%. Não há padrão de 95%+ em todas as fontes no período consolidado.

### Tendência recente

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 03/09 | 1.519 | 776 | 51,09% | 48,91% | 3m48,6s |
| 04/09 | 1.401 | 774 | 55,25% | 44,75% | 3m38,6s |
| 05/09 | 1.545 | 875 | 56,63% | 43,37% | 3m17,4s |
| 06/09 | 1.390 | 836 | 60,14% | 39,86% | 3m50,0s |
| 07/09* | 1.421 | 44 | 3,10% | **96,90%** | 11m11,6s |

\* 07/09 é D-1 e ainda não consolidado. O padrão aparece em todas as origens dominantes — `(not set)` 100%, Google 96,25%, direto 96,20%, Instagram 98,97%, Facebook 95,24% — portanto é assinatura provisória de falha de medição, não de bot, mas deve ser reconfirmada fora da janela de processamento.

## Anomalias e interpretação

1. **D-3 normal:** bounce de 43,37%, engagement de 56,63% e duração de 3m17,4s; sem quebra global consolidada.
2. **Fluxo explícito funciona:** banner, default negado, clique real, update concedido, persistência e `PageView` pós-consentimento foram confirmados.
3. **Falha intermitente na carga inicial persiste:** o GTM é inserido antes do `consent default`; em 1/3 repetições o `PageView` saiu como `pscdl=noapi`/`npa=0`. A corrida explica por que algumas sessões respeitam o default e outras não.
4. **Risco LGPD permanece:** tags/identificadores de Ads, Meta, Microsoft e LinkedIn foram criados antes da escolha apesar do default negado.
5. **D-1 com anomalia provisória severa:** 96,90% de bounce e só 44 sessões engajadas em 1.421, em todas as fontes. Não classificar como incidente consolidado antes da atualização de 24–48h; repetir no monitor diário.
6. **Console:** nenhum erro JavaScript não capturado. Ocorreram CORS/falhas de terceiros do Reclame Aqui e Veels e aviso de moeda do Meta Pixel, sem causalidade comprovada com GA4.

## Status

- **Consent Mode:** **PARCIAL / NÃO CONFORME DE FORMA INTERMITENTE NA CARGA INICIAL**.
- **Coleta após aceite:** **FUNCIONANDO** — `PageView` com `G-V0KMM7L6M6` confirmado.
- **Métrica D-3:** **NORMAL** — bounce **43,37%**.
- **Anomalia D-1:** **ALERTA PROVISÓRIO** — bounce **96,90%**, aguardando consolidação.
- **Ação necessária:** Matias/Increazy devem executar o `consent default` antes do snippet GTM e bloquear GA4/Ads/Meta/Microsoft/LinkedIn até a escolha; Adrian deve permanecer informado pelo risco LGPD.
