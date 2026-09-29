# Consent Mode GA4 — Teste diário 2026-09-29

- **Executado:** 29/09/2026, 08:00–08:05 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`
- **Ambiente:** sessão nova em navegador cloud; carga inicial sem escolha + caminho **Aceitar Tudo** acionado por JavaScript porque o banner estava oculto

## Evidência ao vivo

| Etapa | Evidência |
|---|---|
| Carga inicial | `gtag` e `dataLayer` presentes; dataLayer com 11 entradas; `GTM-MMGX8ZL` e `G-V0KMM7L6M6` identificados |
| Banner | `#cc-widget-container` presente no DOM, porém oculto na carga inicial |
| Consentimento inicial | `consent default` **não encontrado**; havia `consent update` com analytics/ads em `granted` antes de interação |
| Cookies antes da escolha | `_ga`, `_ga_V0KMM7L6M6`, `_gcl_au` e `_fbp` presentes antes da escolha |
| Aceitar Tudo | Como o botão estava oculto, foi acionado por JavaScript; novo `consent update` e evento `cc_consent_update` foram registrados |
| Persistência | `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}` |
| Coleta GA4 | `page_view` confirmado para `G-V0KMM7L6M6`; parâmetros observados: `gcs=G111` e `gcd=13r3r3r3r5` |
| Console | Nenhum erro JavaScript não capturado relacionado ao consentimento; avisos de Clarity/RD Station classificados como terceiros |

## Eventos observados

- Antes da escolha: `consent update` automático em estado concedido e coleta GA4 ativa.
- Após acionamento de **Aceitar Tudo**: novo `consent update`, `cc_consent_update` e `page_view` para `G-V0KMM7L6M6`.
- Limitação do executor: `pscdl` e `npa` não foram devolvidos no resumo final da automação.

## GA4 — consolidado e sinal recente

| Data | Sessões | Engajadas | Engagement | Bounce | Duração média |
|---|---:|---:|---:|---:|---:|
| **26/09/2026 (D-3)** | **1.785** | **970** | **54,34%** | **45,66%** | **2m47s** |
| 27/09/2026 (D-2) | 1.794 | 1.014 | 56,52% | 43,48% | 3m06s |
| 28/09/2026 (D-1, preliminar) | 2.031 | 32 | 1,58% | 98,42% | 11m36s |

No D-3, as principais fontes estavam em faixas normais: Google 1.232 sessões / 43,67% bounce; direto 314 / 61,46%; Instagram 63 / 22,22%; Bing 37 / 51,35%. Não houve colapso simultâneo.

Em 28/09, ainda dentro da janela de processamento de 24–48h, houve assinatura sistêmica: `(not set)` 1.208 sessões / 100% bounce, Google 629 / 98,09%, `(data not available)` 626 / 98,88%, direto 354 / 96,61%, Bing e Instagram 100%. Engajadas caíram 96,84% contra 27/09. O dado D-1 é preliminar, mas coincide com a falha comprovada no teste ao vivo.

## Conclusão

1. **Regressão ativa do Consent Mode:** o `consent default` sumiu novamente e o CMP iniciou a sessão com `granted` automático.
2. **Não conformidade LGPD:** cookies analíticos e de marketing estavam presentes antes de qualquer escolha; o banner existia, mas estava oculto.
3. **Caminho de atualização funciona**, mas não corrige o estado inicial: `cc_consent_update` e persistência foram confirmados após o aceite forçado.
4. **GA4 D-3 está normal**, com bounce de 45,66%. O D-1 mostra 98,42% e precisa ser revalidado quando consolidar, porém a evidência ao vivo torna o alerta técnico imediato.

## Status

- **Consent Mode inicial:** **FALHOU — sem default, auto-grant**.
- **Banner:** **FALHOU — oculto**.
- **Atualização após aceite:** **FUNCIONANDO**.
- **Coleta GA4:** **ATIVA**, inclusive em estado pré-escolha.
- **GA4 D-3:** **NORMAL** — bounce **45,66%**.
- **Anomalia D-1:** **ALERTA CRÍTICO PRELIMINAR** — bounce **98,42%** em todas as principais origens.
- **Encaminhamento:** Matias/Increazy — restaurar `consent default=denied`, tornar o banner visível e bloquear tags antes da escolha; Adrian — avaliar a exposição LGPD por cookies/marketing pré-consentimento.
