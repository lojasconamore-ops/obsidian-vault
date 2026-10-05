# Diagnóstico diário GA4 Consent Mode — 2026-10-05

- **Execução:** 05/10/2026, 08:00–08:09 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** property `379729087`, measurement ID `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`

## Resultado executivo

**Status: ALERTA — interface e caminho de aceite funcionam, mas a race condition de Consent Mode persiste e foi reproduzida em 4/5 cargas limpas.**

Em 5/5 contextos limpos, o `consent default` apareceu com `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` e `personalization_storage` como `denied`; o banner com **Rejeitar** e **Aceitar Tudo** apareceu em 5/5.

Apesar disso, 4/5 beacons pré-escolha foram enviados como `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1`, e criaram `_ga` antes da escolha. Apenas 1/5 ficou coerente com o default denied: `gcs=G100`, `pscdl=denied`, `npa=1`, `gcd=13p3p3p3p5l1`. A mistura sob o mesmo default visível confirma condição de corrida/load-order.

## Caminho de aceite

- Clique real em **Aceitar Tudo** executado.
- `consent update`: analytics e publicidade → `granted`.
- Evento customizado: `cc_consent_update`.
- Eventos observados no dataLayer: `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`, `gtm.click`, `cc_consent_update`.
- Persistência: `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}`.
- Coleta pós-escolha confirmada para `G-V0KMM7L6M6`: evento `PageView` após recarga. O sinal de consentimento pós-recarga também oscilou entre `gcs=G111`/granted e `pscdl=noapi`/`npa=0` em execuções separadas, reforçando problema de ordem de carregamento.

## GA4 consolidado — D-3 (02/10/2026)

- Sessões: **1.922**
- Sessões engajadas: **932**
- Taxa de engajamento: **48,49%**
- Bounce rate: **51,51%**
- Duração média: **2m41s**

Comparação: 30/09 bounce **47,62%**; 01/10 **48,32%**; 02/10 **51,51%**. Alta de **3,18 p.p.** versus o dia anterior, mas ainda sem assinatura de colapso global no dado consolidado.

## Anomalias e classificação

1. **Race condition confirmada:** 4/5 cargas pré-escolha ignoraram na prática o default denied nos parâmetros do beacon (`noapi`/`npa=0`).
2. **Cookies antes do consentimento:** `_gcl_au`, `_fbp`, `_uet*`, Clarity e outros foram observados antes da escolha; `_ga*` apareceu em 4/5 cargas limpas.
3. **Dado D-3 saudável/moderado:** bounce de 51,51% e engajamento de 48,49%; Google 51,32%, direto 60,76% e RD Email 37,50% de bounce.
4. **Alerta provisório em D-1 (04/10):** 1.664 sessões, somente 11 engajadas, bounce **99,34%** e duração média **6m30s**, distribuído por todas as origens. O padrão é compatível com falha de tracking, mas 04/10 ainda está dentro da janela de processamento de 24–48h e não deve ser tratado como consolidado hoje.
5. **Console:** sem exceções JavaScript não capturadas. Falhas CORS do Reclame Aqui e warning de formato de moeda do Meta Pixel foram classificados como terceiros/não causais para o Consent Mode.

## Próxima ação recomendada

Manter escalonamento com Matias/Increazy para corrigir a ordem do `consent default` antes do GTM/sGTM e bloquear cookies de analytics/publicidade até a escolha. O risco LGPD persiste e deve continuar sinalizado ao Adrian. Revalidar o dado de 04/10 em 06/10/2026, quando estiver consolidado.

## Evidência técnica

- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/scratch/consent-test-20261005.json`
- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/scratch/consent-post-choice-20261005.json`
