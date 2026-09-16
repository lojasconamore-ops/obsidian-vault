# Consent Mode GA4 — Teste diário 2026-09-16

- **Executado:** 16/09/2026, 08:01–08:05 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless, contexto novo, sem cookies/preferências; clique real em **Aceitar Tudo** e recarga consentida

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP 200; banner visível com **Rejeitar** e **Aceitar Tudo**; `gtag=function`; `dataLayer` ativo |
| Consentimento inicial | `consent default` presente; analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Coleta antes da escolha | sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1`; também houve Google Ads/DoubleClick, LinkedIn e Clarity |
| Cookies antes da escolha | Já presentes `_ga`, `_ga_V0KMM7L6M6`, `_ga_CDCKFVTR5M`, `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid`, entre outros |
| Aceitar Tudo | Clique real; `consent update` concedeu analytics/ads/personalização; `cc_consent_update` com analytics/marketing `granted` |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}`; banner oculto |
| Coleta pós-aceite | Após recarga, sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`; preferências permaneceram concedidas |
| Console | Dois `pageerror` genéricos serializados como `Object`, sem origem identificada; CORS/Reclame Aqui, 503 e aviso de moeda do Meta Pixel também apareceram e foram classificados separadamente, sem causalidade comprovada com GA4 |

## Eventos observados

### Teste ao vivo
- `consent default` — negado antes da escolha
- `PageView` pré-escolha — enviado pelo sGTM com `pscdl=noapi` e `npa=0`
- `gtm.click` — clique em **Aceitar Tudo**
- `consent update` — concedido após aceite
- `cc_consent_update` — analytics/marketing `granted`
- `gtm.scrollDepth` — observado no teste de rolagem
- `PageView` após recarga consentida — `tid=G-V0KMM7L6M6`

### GA4 consolidado — D-3 (13/09/2026)
Principais eventos: `page_view` 7.457; `view_item_list` 3.279; `user_engagement` 2.136; `session_start` 1.910; `view_item` 1.320; `first_visit` 1.307; `scroll` 1.069; `add_to_cart` 283; `view_search_results` 250; `form_start` 143; `view_cart` 131; `begin_checkout` 60; `purchase_fastbuy` 22; `purchase_website` 22; `purchase` 21; `contato_whatsapp` 5.

## GA4 — D-3 e janela de frescor

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **13/09/2026 (D-3)** | **1.909** | **1.170** | **61,29%** | **38,71%** | **3m46,0s** |
| 14/09/2026 (D-2) | 2.179 | 1.194 | 54,80% | 45,20% | 4m41,9s |
| 15/09/2026 (D-1, provisório) | 2.240 | 39 | 1,74% | 98,26% | 8m57,0s |

Principais fontes do D-3: Google 1.194 sessões / 36,35% bounce; direto 302 / 55,30%; Instagram 217 / 30,88%; Facebook 39 / 28,21%; `(not set)` 27 / 33,33%; ChatGPT 27 / 22,22%; Bing 18 / 38,89%. Não há colapso global no D-3.

## Anomalias e conclusão

1. **Regressão real no bloqueio pré-consentimento:** o `consent default` voltou a existir e está negado, mas o navegador recebeu cookies GA4/marketing e o sGTM enviou `PageView` com `pscdl=noapi`/`npa=0` antes da decisão. Isso difere do teste de 15/09, que mostrou ping restrito (`pscdl=denied`, `npa=1`) e `_ga` ausente.
2. **Fluxo de escolha funciona:** banner, `consent update`, evento `cc_consent_update`, persistência e `PageView` após recarga foram confirmados. O update funcionar não corrige o disparo indevido anterior à escolha.
3. **Risco LGPD alto:** GA4 e tags de marketing estão criando identificadores/disparando antes do aceite, apesar do estado declarado como `denied`. Escalar para Matias/Increazy (GTM/CMP) e Adrian (Jurídico).
4. **D-3 normal:** bounce 38,71%, com engajamento distribuído nas principais origens.
5. **D-1 crítico, mas provisório:** 98,26% bounce em todas as principais origens, 39 sessões engajadas e 8m57s de duração média. Porém 14/09 também apareceu ontem com 96,97% provisório e hoje normalizou para 45,20%, confirmando forte efeito da janela de processamento. Não fechar falha com D-1; revalidar quando chegar a D-3.

## Status

- **Consent Mode — comandos/default/update:** **FUNCIONANDO**.
- **Aplicação do consentimento antes da escolha:** **FALHOU / REGRESSÃO REPRODUZIDA**.
- **LGPD/tags de marketing:** **NÃO CONFORME no teste limpo** — cookies e coleta antes da decisão.
- **Métrica D-3:** **NORMAL** — bounce **38,71%**.
- **D-1:** **ALERTA CRÍTICO PROVISÓRIO**, provavelmente influenciado por processamento; aguardar consolidação.
- **Dono da correção:** Matias/Increazy no GTM/CMP; Adrian para avaliação jurídica.
