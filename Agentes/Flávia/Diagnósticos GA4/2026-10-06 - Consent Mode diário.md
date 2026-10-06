# Diagnóstico diário GA4 Consent Mode — 2026-10-06

- **Execução:** 06/10/2026, 08:01–08:14 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** property `379729087`, measurement ID `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`

## Resultado executivo

**Status: ALERTA — fluxo visual e comandos de consentimento operantes, mas a aplicação prática pré-escolha continua inconsistente/suspeita.**

Em 2 cargas com armazenamento limpo, o banner apareceu e o `consent default` foi registrado com analytics e publicidade como `denied`. Não houve `consent update granted` sem interação nessas cargas. O caminho de aceite confirmou `consent update` para `granted`, `cc_consent_update` e coleta `page_view` para `G-V0KMM7L6M6`.

Apesar do default denied, os beacons pré-escolha vieram com `gcd=13l3l3l3l1l1`, mas também `pscdl=noapi` e `npa=0`, além da presença de `_ga`, `_gcl_au`, `_fbp` e `_uet*` antes da escolha. Isso mantém o alerta de ordem de carregamento/enforcement e o risco LGPD já observado em dias anteriores. O teste de intermitência de hoje ficou limitado a 2/5 cargas por limite do navegador remoto.

## Estado inicial — antes da escolha

- Banner: visível, com controles de privacidade.
- `window.gtag`: função presente.
- `dataLayer`: 11 entradas nas cargas limpas.
- `consent default`:
  - `analytics_storage: denied`
  - `ad_storage: denied`
  - `ad_user_data: denied`
  - `ad_personalization: denied`
  - `personalization_storage: denied`
  - `functionality_storage: granted`
  - `security_storage: granted`
  - `wait_for_update: 500`
- Beacon pré-escolha: `PageView`, `tid=G-V0KMM7L6M6`, `gcd=13l3l3l3l1l1`, `pscdl=noapi`, `npa=0`.
- Cookies observados antes da escolha: `_ga`, `_ga_V0KMM7L6M6`, `_gcl_au`, `_fbp`, `_uetsid`, `_uetvid`.
- Não foi observado `cc_consent_update` para granted sem escolha nas duas cargas limpas.

## Caminho de aceite

- Ação real **Aceitar Tudo** exercitada no teste principal.
- `consent update`: analytics e publicidade → `granted`.
- Evento customizado: `cc_consent_update`.
- Persistência observada: `cc_cookie_consent_status=true`.
- Coleta pós-escolha confirmada: evento `page_view`/`PageView` com `tid=G-V0KMM7L6M6` em requisição de coleta.

## GA4 consolidado — D-3 (03/10/2026)

- Sessões: **1.685**
- Sessões engajadas: **816**
- Taxa de engajamento: **48,43%**
- Bounce rate: **51,57%**
- Duração média: **2m34s**

Comparação: 02/10 bounce **51,51%**; 03/10 **51,57%** — variação de apenas **+0,06 p.p.**, sem assinatura de colapso global.

## Anomalias e classificação

1. **Enforcement pré-consentimento ainda suspeito:** default denied existe, porém `pscdl=noapi`, `npa=0` e cookies de analytics/publicidade aparecem antes da escolha.
2. **Intermitência não encerrada hoje:** as 2 cargas limpas foram consistentes entre si, mas o protocolo de 5 cargas não foi concluído. O histórico de 05/10 reproduziu mistura `pscdl=denied`/`noapi` em 5 cargas.
3. **D-3 saudável/moderado:** bounce de 51,57% e engajamento de 48,43%.
4. **D-1 provisório (05/10):** 2.078 sessões, 22 engajadas, bounce **98,94%**, engajamento **1,06%** e duração média **6m07s**, com colapso em todas as principais origens. O padrão parece falha de tracking, mas 05/10 ainda está dentro das 24–48h de processamento e não pode ser classificado como incidente consolidado.
5. **Processamento confirmado como fator relevante:** o dia 04/10 aparecia ontem com bounce **99,34%**; hoje consolidou em **55,06%** (revisão de **-44,28 p.p.**). Portanto, o alerta de 05/10 deve ser rechecado após consolidação, não escalado isoladamente.
6. **Console:** nenhuma exceção não capturada foi registrada após ativação do listener; a captura não cobre erros ocorridos antes do listener.

## Próxima ação recomendada

- Manter o alerta técnico com Matias/Increazy sobre ordem de carregamento e bloqueio real de cookies antes da escolha.
- Manter o risco LGPD sinalizado ao Adrian enquanto cookies de publicidade/analytics surgirem antes do consentimento.
- Revalidar 05/10 em **07/10/2026**, após a janela de processamento.
- Repetir o protocolo completo de 5 cargas limpas quando o navegador remoto permitir, registrando `gcs`, `gcd`, `pscdl`, `npa` e cookies por carga.
