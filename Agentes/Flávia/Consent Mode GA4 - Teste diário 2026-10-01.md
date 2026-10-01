# Consent Mode GA4 — Teste diário 2026-10-01

- **Executado:** 01/10/2026, 08:01–08:08 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** navegador cloud, contextos novos com cookies/storage limpos; teste principal completo + 5 repetições sem escolha para intermitência

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | `gtag` presente; dataLayer com 10 entradas; GTM e GA4 carregados |
| Consentimento inicial | `consent default` presente; analytics e marketing em `denied`; funcionalidade e segurança em `granted`; `wait_for_update=500` |
| Banner | Ação real **Aceitar Tudo** localizada e executada no teste principal |
| Pré-escolha — teste principal | `PageView` para `G-V0KMM7L6M6`: `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1` |
| Pós-escolha | `consent update` alterou analytics e marketing para `granted`; `cc_consent_update` registrou ambos como granted |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Coleta pós-escolha | hit para `G-V0KMM7L6M6` com `gcs=G111`, `gcd=13r3r3r3r5l1`, `npa=0`; cookies `_ga` e `_ga_V0KMM7L6M6` criados |
| Scroll | Nenhum beacon explícito `scroll`/`user_engagement` foi capturado na janela de 12 segundos; limitação do teste, não falha comprovada |
| Console | Nenhum erro JavaScript não capturado. Falhas CORS do Reclame Aqui, túnel de terceiros e aviso WebGL/fontes foram classificados como não relacionados |

## Teste de intermitência — 5 contextos limpos, sem escolha

- **5/5:** `consent default` apareceu com analytics/marketing `denied` e sem `cc_cookie_*` persistido.
- **4/5:** beacon GA4 coerente: `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`.
- **1/5:** beacon inconsistente apesar do default negado: `gcd=13l3l3l3l1l1`, `pscdl=noapi`, `npa=0`; também criou `_ga`, `_ga_V0KMM7L6M6` e `FPLC` antes da escolha.
- **5/5:** cookies de marketing/terceiros foram observados antes da escolha, incluindo `_gcl_au`, `_fbp`, `_uetsid` e `_uetvid`.

**Diagnóstico:** existe uma **condição de corrida/load-order intermitente**. O `consent default` está no dataLayer, porém em 20% das repetições o beacon não o utilizou (`pscdl=noapi`) e operou como consentimento implícito. Além disso, cookies de marketing são gravados antes do aceite em todas as repetições, o que exige revisão técnica e jurídica.

## GA4 — dados consolidados e recentes

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média | Leitura |
|---|---:|---:|---:|---:|---:|---|
| **28/09/2026 (D-3)** | **2.157** | **1.138** | **52,76%** | **47,24%** | **3m52s** | Consolidado/normal |
| 29/09/2026 (D-2) | 2.441 | 1.239 | 50,76% | 49,24% | 2m57s | Normalizou após processamento |
| 30/09/2026 (D-1) | 2.031 | 45 | 2,22% | 97,78% | 8m35s | Preliminar; dentro da janela 24–48h |

Fontes principais em 28/09: Google 1.356 sessões / 45,9% bounce; direto 407 / 57,2%; Instagram 91 / 42,9%; Bing 85 / 52,9%. Não houve colapso transversal. `(not set)` teve somente 29 sessões, bounce 41,4%, mas duração média atípica de 39m33s — outlier de baixo volume.

O padrão preliminar de 29/09 reportado ontem com bounce de 98,22% consolidou hoje em 49,24%. Isso confirma novamente o efeito de processamento do GA4. O 97,78% de 30/09 não deve ser classificado como falha antes de D-3.

## Eventos GA4 em 28/09

Principais registros: `page_view` 7.289; `session_start` 2.172; `user_engagement` 1.928; `scroll` 1.164; `add_to_cart` 233; `begin_checkout` 102; `purchase` 35; `purchase_erp` 18; `purchase_website` 18; `compra_erp` 17; `contato_whatsapp` 10.

## Status e ação

- **Fluxo funcional principal:** **FUNCIONANDO** — default negado, banner, update concedido e coleta pós-aceite comprovados.
- **Implementação geral:** **INTERMITENTE / REQUER CORREÇÃO** — 1/5 cargas com `pscdl=noapi` apesar do default e cookies de marketing pré-consentimento em 5/5.
- **GA4 D-3:** **NORMAL** — bounce 47,24%.
- **D-1:** **INCONCLUSIVO** — aguardar consolidação.
- **Responsável técnico:** Matias/Increazy devem revisar ordem de carregamento CMP → Consent Default → GTM/tags e bloqueio de cookies/pixels antes da escolha.
- **LGPD:** Adrian deve avaliar a gravação pré-consentimento de `_gcl_au`, `_fbp`, `_uetsid` e `_uetvid`.
- **Monitoramento:** repetir diariamente e confirmar se a taxa de corrida desaparece após correção.
