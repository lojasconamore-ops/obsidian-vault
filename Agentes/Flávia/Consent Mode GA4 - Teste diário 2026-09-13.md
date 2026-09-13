# Consent Mode GA4 — Teste diário 2026-09-13

- **Executado:** 13/09/2026, 08:01–08:07 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** Chromium headless em contexto novo, sem armazenamento prévio; fluxo real **Aceitar Tudo**

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | HTTP 200; banner visível com **Rejeitar** e **Aceitar Tudo**; `gtag=function`; `dataLayer` presente |
| Ordem real | `gtm.js` entrou no dataLayer em **374,8 ms**; `consent default` só entrou em **2.009,5 ms**. A coleta GA4 ocorreu por volta de **1,51 s**, portanto antes do default |
| Consentimento inicial | `consent default`: analytics/ads/personalização `denied`; funcionalidade/segurança `granted`; `wait_for_update=500` |
| Coleta antes da escolha | sGTM enviou `tid=G-V0KMM7L6M6`, `en=PageView`, `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1`; houve também ping para `stats.g.doubleclick.net` |
| Cookies antes da escolha | `_ga`, `_ga_V0KMM7L6M6`, `_ga_CDCKFVTR5M`, `_gcl_au`, `FPLC`, `_fbp`, UET/Bing e Clarity já criados antes do clique |
| Aceitar Tudo | Clique real confirmado; `consent update` concedeu analytics/ads/personalização e disparou `cc_consent_update`; preferências `cc_cookie_*` persistidas |
| Pós-escolha | Nenhuma nova requisição GA4 observada nos 12 segundos após o clique; o `PageView` já havia sido enviado antes da decisão |
| Console | Nenhum erro JavaScript não capturado. Falhas externas do Reclame Aqui/CORS e aviso de formato de moeda do Meta Pixel, sem nexo demonstrado com o Consent Mode |

## Eventos observados

- `gtm.js`
- `consent default` (`denied`, porém tardio)
- `another_page`
- `gtm.dom` / `gtm.load`
- `PageView` no sGTM **antes da escolha**
- `config` para `G-V0KMM7L6M6`
- `RD Popup e WhatsApp` (`rd_action=viewed`)
- `gtm.click`
- `consent update` (`granted`)
- `cc_consent_update`

## GA4 — D-3 e janela de frescor

> D-3 = 10/09/2026. D-1 ainda está na janela de processamento de 24–48h.

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| 09/09/2026 | 1.635 | 949 | 58,04% | 41,96% | 4m07,6s |
| **10/09/2026 (D-3)** | **1.871** | **1.023** | **54,68%** | **45,32%** | **4m10,6s** |
| 11/09/2026 (D-2) | 1.839 | 1.023 | 55,63% | 44,37% | 3m09,3s |
| 12/09/2026 (D-1, provisório) | 1.717 | 40 | 2,33% | 97,67% | 8m43,9s |

Principais fontes do D-3: Google 965 sessões / 38,34% bounce; direto 355 / 48,17%; `(not set)` 171 / 93,57%; Instagram 156 / 41,03%; Facebook 31 / 29,03%. Não há colapso global no D-3, mas `(not set)` permanece anormal.

## Conclusão e status

1. **Causa raiz ao vivo comprovada:** o `consent default` é disparado cerca de **1,63 s depois do `gtm.js`** e depois da coleta GA4 inicial. O comando existe, mas chega tarde demais para bloquear a primeira coleta.
2. **Fluxo de aceite funciona:** `consent update=granted` e `cc_consent_update` são enviados após o clique.
3. **D-3 consolidado normal:** bounce **45,32%**, sem falha global por origem.
4. **Anomalia segmentada:** `(not set)` em D-3 com **171 sessões**, só **11 engajadas** e **93,57% bounce**.
5. **D-1 crítico, mas provisório:** 97,67% bounce; o dia anterior (11/09) também apareceu quebrado em D-1 e normalizou em D-2, reforçando que não se deve fechar diagnóstico antes de D-3.

- **Consent Mode GA4:** **FALHA PARCIAL / ORDEM INCORRETA**
- **LGPD:** **NÃO CONFORME** — cookies e coleta de analytics/marketing antes da decisão
- **Métrica D-3:** **NORMAL NO TOTAL**, com alerta em `(not set)`
- **Ação necessária:** Matias/Increazy devem mover o `consent default` para antes do carregamento do `GTM-MMGX8ZL` e bloquear tags/cookies até a escolha; Adrian deve acompanhar a exposição LGPD.
