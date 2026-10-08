# Diagnóstico diário GA4 Consent Mode — 2026-10-08

- **Execução:** 08/10/2026, 08:01–08:08 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** property `379729087`, measurement ID `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`

## Resultado executivo

**Status: ALERTA — fluxo do Consent Mode funciona, mas a condição de corrida/enforcement pré-consentimento permanece.**

Em 5 contextos limpos, o banner apareceu e o `consent default` declarou analytics e publicidade como `denied`. O clique real em **Aceitar Tudo** produziu `consent update` para `granted`, evento `cc_consent_update`, persistência das preferências e coleta GA4 para `G-V0KMM7L6M6`.

Porém, antes de qualquer escolha, cookies `_ga` já estavam presentes em **3/5** cargas; `_gcl_au` e cookies do LinkedIn apareceram em **5/5**. Em uma sexta execução com captura detalhada de rede, o beacon GA4 pré-escolha saiu corretamente como negado (`pscdl=denied`, `gcs=G100`, `gcd=13p3p3p3p5l1`, `npa=1`) e, após o aceite, mudou para concedido (`gcs=G111`, `gcd=13r3r3r3r5l1`, `pscdl=noapi`, `npa=0`). A mistura entre cargas confirma que o enforcement ainda não é estável.

## Estado inicial — antes da escolha

- Banner de privacidade: visível, com **Rejeitar** e **Aceitar Tudo**.
- `window.gtag`: função presente.
- `dataLayer`: `consent default` presente nas 5/5 cargas:
  - `analytics_storage: denied`
  - `ad_storage: denied`
  - `ad_user_data: denied`
  - `ad_personalization: denied`
  - `personalization_storage: denied`
  - `functionality_storage: granted`
  - `security_storage: granted`
  - `wait_for_update: 500`
- Eventos observados: `gtm.js`, `another_page`, `gtm.dom`, `gtm.load` e `RD Popup e WhatsApp` (`viewed`).
- Beacon GA4 detalhado pré-escolha: `page_view`, `tid=G-V0KMM7L6M6`, HTTP 204, `pscdl=denied`, `gcs=G100`, `gcd=13p3p3p3p5l1`, `npa=1`.
- Cookies pré-escolha:
  - `_ga` / `_ga_V0KMM7L6M6`: 3/5 cargas.
  - `_gcl_au`: 5/5 cargas.
  - LinkedIn `bcookie`/`bscookie`: 5/5 cargas.

## Caminho de aceite

- Clique real em **Aceitar Tudo** executado.
- `consent update`: analytics e publicidade → `granted`.
- Evento customizado: `cc_consent_update`.
- Persistência: `cc_cookie_consent_status=true`; preferências `marketing=true` e `statistics=true`.
- Coletas pós-escolha confirmadas para `G-V0KMM7L6M6`:
  - `page_view`
  - `user_engagement`
  - evento server-side `PageView`
- Parâmetros pós-escolha: `gcs=G111`, `gcd=13r3r3r3r5l1`, `pscdl=noapi`, `npa=0`; respostas HTTP 204/200.

## GA4 consolidado — D-3 (05/10/2026)

- Sessões: **2.232**
- Sessões engajadas: **1.045**
- Taxa de engajamento: **46,82%**
- Bounce rate: **53,18%**
- Duração média: **2m42,5s**

Comparação com 04/10: bounce caiu de **55,06%** para **53,18%** (**-1,88 p.p.**). Sessões subiram de 1.718 para 2.232 (**+29,92%**). Não há assinatura de colapso global de tracking.

Principais origens em 05/10:
- Google: 1.471 sessões, bounce **54,18%**.
- Direto: 452 sessões, bounce **55,97%**.
- Instagram: 36 sessões, bounce **41,67%**.
- RD Email: 35 sessões, bounce **48,57%**.
- Bing: 28 sessões, bounce **42,86%**.
- LinkedIn: 24 sessões, bounce **95,83%** — anomalia isolada de baixo volume, não global.

## Anomalias e classificação

1. **Condição de corrida/enforcement persiste:** `consent default=denied` está presente, mas cookies analytics aparecem antes da escolha em 3/5 cargas.
2. **Risco LGPD permanece:** `_gcl_au` e cookies do LinkedIn foram gravados antes da escolha em 5/5 cargas.
3. **Fluxo GA4 após aceite está funcional:** `consent update`, `cc_consent_update`, `page_view` e `user_engagement` confirmados.
4. **GA4 D-3 saudável:** bounce geral de 53,18%, sem queda simultânea de engajamento em todas as origens.
5. **Console:** sem exceção JavaScript não capturada. Erros CORS do selo Reclame Aqui e alerta de formato de moeda do Meta Pixel são ocorrências de terceiros, sem causalidade comprovada no GA4.

## Próxima ação recomendada

- Matias/Increazy: revisar a ordem CMP → GTM/gtag e o consent enforcement das tags GA4, Google Ads e LinkedIn, impedindo cookies antes da escolha.
- Adrian: manter a sinalização LGPD enquanto cookies de analytics/marketing forem gravados pré-consentimento.
- Continuar o reteste diário com múltiplos contextos limpos e registrar a proporção de cargas com cookies pré-escolha.
