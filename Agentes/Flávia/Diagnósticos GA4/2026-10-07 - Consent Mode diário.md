# Diagnóstico diário GA4 Consent Mode — 2026-10-07

- **Execução:** 07/10/2026, 08:00–08:06 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** property `379729087`, measurement ID `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`

## Resultado executivo

**Status: ALERTA — comandos e caminho de aceite funcionam, mas o enforcement pré-consentimento apresenta condição de corrida reproduzida.**

Em todas as cargas limpas, o banner apareceu e o `consent default` declarou analytics e publicidade como `denied`. O aceite real produziu `consent update` para `granted`, evento `cc_consent_update`, persistência das preferências e requisição GA4 para `G-V0KMM7L6M6`.

Porém, 6 contextos limpos apresentaram resultados mistos antes da escolha: em **5/6**, o `PageView` saiu com `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1` e cookies `_ga` já presentes; em **1/6**, saiu corretamente como negado, com `pscdl=denied`, `npa=1`, `gcs=G100`, `gcd=13p3p3p3p5l1` e sem cookies `_ga`. Sob o mesmo default visual, essa mistura confirma comportamento intermitente/load-order race, não configuração estável.

## Estado inicial — antes da escolha

- Banner de privacidade: visível, botão **Aceitar Tudo** disponível.
- `window.gtag`: função presente.
- `dataLayer`: `consent default` presente:
  - `analytics_storage: denied`
  - `ad_storage: denied`
  - `ad_user_data: denied`
  - `ad_personalization: denied`
  - `personalization_storage: denied`
  - `functionality_storage: granted`
  - `security_storage: granted`
  - `wait_for_update: 500`
- Eventos observados: `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`, `RD Popup e WhatsApp` (`viewed`) e `PageView`.
- Intermitência de beacon/cookies:
  - 5 cargas: `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1`, `_ga` pré-escolha.
  - 1 carga: `pscdl=denied`, `npa=1`, `gcs=G100`, `gcd=13p3p3p3p5l1`, sem `_ga` pré-escolha.

## Caminho de aceite

- Clique real em **Aceitar Tudo** executado.
- `consent update`: analytics e publicidade → `granted`.
- Evento customizado: `cc_consent_update`, com `marketing_consent=granted` e `analytics_consent=granted`.
- Persistência: `cc_cookie_consent_status=true`; preferências `marketing=true` e `statistics=true`.
- Requisição pós-escolha para `tid=G-V0KMM7L6M6`, com `gcs=G111`, `gcd=13r3r3r3r5l1`, `npa=0`.

## GA4 consolidado — D-3 (04/10/2026)

- Sessões: **1.718**
- Sessões engajadas: **772**
- Taxa de engajamento: **44,94%**
- Bounce rate: **55,06%**
- Duração média: **2m19s**

Comparação: 03/10 bounce **51,57%**; 04/10 **55,06%** — alta de **+3,49 p.p.**. Desde 30/09 (**47,62%**), alta de **+7,44 p.p.**, mas sem assinatura de colapso global (>80%).

Principais origens em 04/10:
- Google: 1.134 sessões, bounce **53,53%**.
- Direto: 369 sessões, bounce **66,40%**.
- Bing: 49 sessões, bounce **59,18%**.
- Instagram: 39 sessões, bounce **33,33%**.

## Anomalias e classificação

1. **Condição de corrida confirmada:** o mesmo `consent default=denied` gera beacons `denied` ou `noapi` conforme a carga.
2. **Risco LGPD permanece:** em 5/6 cargas, analytics/publicidade receberam sinais e cookies antes da escolha.
3. **GA4 D-3 sem colapso:** bounce de 55,06% é moderado; principais origens não apresentam bounce simultâneo acima de 95%.
4. **Console:** nenhuma exceção JavaScript não capturada. Falhas CORS/Reclame Aqui e aviso de moeda do Meta Pixel são ocorrências de terceiros, sem causalidade atribuída ao Consent Mode.

## Próxima ação recomendada

- Matias/Increazy: revisar ordem de execução do CMP versus GTM/gtag e garantir que o default negado seja aplicado antes de qualquer tag/cookie.
- Adrian: manter sinalização LGPD enquanto houver cookies/beacons de marketing pré-consentimento.
- Repetir diariamente o protocolo de contextos limpos e registrar a proporção `denied` versus `noapi`.
