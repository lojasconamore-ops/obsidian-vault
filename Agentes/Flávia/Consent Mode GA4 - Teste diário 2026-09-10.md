# Consent Mode GA4 — Teste diário 2026-09-10

- **Executado:** 10/09/2026, 08:01–08:09 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contextos novos sem cookies/armazenamento prévios; caminhos Aceitar Tudo e Rejeitar testados separadamente

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | Página carregou; banner com **Aceitar Tudo** e **Rejeitar** visível; `gtag=function`; `dataLayer` com 10 entradas |
| Consentimento inicial | `consent default` no índice 2: analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Ordem | `gtm.js` ocorre antes do `consent default` — ordem incorreta e sujeita a corrida |
| Pré-escolha | Beacon sGTM `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=noapi`, `gcd=13l3l3l3l1l1`, `npa=0` observado antes da escolha |
| Cookies pré-escolha | Em uma execução apareceram `_ga` e `_ga_V0KMM7L6M6`; em ambas apareceram identificadores de marketing como `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid` e Clarity antes da decisão. A variação entre execuções reforça condição de corrida |
| Aceitar Tudo | `consent update` concedeu analytics/ads/personalização; `cc_consent_update`; preferências persistidas como `{marketing:true, statistics:true}` |
| Coleta consentida | Após recarregar com consentimento persistido, beacon sGTM `tid=G-V0KMM7L6M6`, `en=PageView` confirmado |
| Rejeitar | `consent update` manteve analytics/ads/personalização `denied`; preferências persistidas como `{marketing:false, statistics:false}`; porém identificadores de marketing criados antes da escolha permaneceram |
| Console | Nenhum erro JavaScript não capturado. CORS/falhas de terceiros Reclame Aqui/Veels e aviso de moeda Meta observados, sem causalidade comprovada com GA4 |

## Eventos observados

- `gtm.js`
- `consent default` (`denied`)
- `another_page`, `gtm.dom`, `gtm.load`
- `RD Popup e WhatsApp`
- `gtm.click`
- `consent update` (`granted` no aceite; `denied` na rejeição)
- `cc_consent_update`
- `PageView` no sGTM antes da escolha e novamente após aceite + recarregamento

## GA4 consolidado — D-3

> D-3 = 07/09/2026. D-1 não é usado como referência conclusiva por causa da janela de processamento de 24–48 horas.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **07/09/2026 (D-3)** | **1.448** | **868** | **59,94%** | **40,06%** | **3m52,2s** |
| 08/09/2026 (D-2) | 1.620 | 961 | 59,32% | 40,68% | 4m19,7s |
| 09/09/2026 (D-1, provisório) | 1.530 | 38 | 2,48% | 97,52% | 10m53,4s |

Principais fontes do D-3: Google 915 sessões / 40,44% bounce; direto 237 / 48,95%; Instagram 144 / 34,72%; Facebook 38 / 18,42%; ChatGPT 25 / 12,00%; `(not set)` 25 / 40,00%. Não há colapso global no dia consolidado.

## Anomalia provisória — 09/09

O D-1 mostra a assinatura conhecida de processamento incompleto/falha de tracking: engajadas caíram 96,0% versus D-2, bounce subiu 56,84 p.p. e a duração média aumentou 151,6%. A anomalia atravessa as principais fontes: `(not set)` 100% bounce, Google 96,11%, direto 95,71%, Instagram/Facebook/Bing 100%. Como 09/09 ainda está dentro de 24–48h, **não classificar como retorno da falha por enquanto**; revalidar quando for D-3 em 12/09.

## Status

- **Consent Mode:** **PARCIAL / NÃO CONFORME NA CARGA INICIAL**.
- **Fluxos explícitos de aceite e rejeição:** **FUNCIONANDO no dataLayer**.
- **Coleta pós-aceite:** **FUNCIONANDO** — `PageView` com `G-V0KMM7L6M6` confirmado após recarga.
- **Métrica D-3:** **NORMAL** — bounce **40,06%**.
- **D-1:** **ALERTA PROVISÓRIO** — 97,52% bounce; aguardar consolidação.
- **Risco atual:** GTM inicia antes do `consent default`; PageView e identificadores de marketing aparecem antes da escolha, inclusive no caminho de rejeição. Risco LGPD e medição intermitente persistem.
- **Ação necessária:** Matias/Increazy devem colocar o `consent default` antes do snippet GTM e bloquear GA4/Ads/Meta/Microsoft/LinkedIn/Clarity até a escolha. Adrian deve permanecer informado sobre o risco LGPD.

## Evidências técnicas locais

- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/consent_test_20260910.json`
- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/consent_paths_20260910.json`
- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/consent_initial_20260910.png`
- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/consent_post_20260910.png`
