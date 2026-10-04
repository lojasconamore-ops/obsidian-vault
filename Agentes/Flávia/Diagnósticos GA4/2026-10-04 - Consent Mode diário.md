# Diagnóstico diário GA4 Consent Mode — 2026-10-04

- **Execução:** 04/10/2026, 08:01–08:07 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** property `379729087`, measurement ID `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`

## Resultado executivo

**Status: ALERTA — fluxo principal funciona, mas a corrida intermitente e cookies pré-consentimento persistem.**

Em 5/5 contextos limpos, o `consent default` apareceu com `analytics_storage`, `ad_storage`, `ad_user_data` e `ad_personalization` como `denied`; o banner apareceu em 5/5. Os beacons nessas repetições foram coerentes: `gcs=G100`, `gcd=13p3p3p3p5l1`, `pscdl=denied`, `npa=1`.

Porém, a primeira carga limpa do teste apresentou `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1`, apesar do mesmo default denied e banner visível. A mistura `denied`/`noapi` confirma que a condição de corrida/load-order ainda é intermitente, embora menos frequente nesta amostra.

## Caminho de aceite

- Clique real em **Aceitar Tudo** executado.
- `consent update`: analytics e publicidade → `granted`.
- Evento customizado: `cc_consent_update`.
- Eventos observados no dataLayer: `gtm.js`, `another_page`, `gtm.dom`, `gtm.load`, `gtm.click`, `cc_consent_update`.
- Persistência: `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}`.
- Coleta pós-escolha confirmada para `G-V0KMM7L6M6`: evento `user_engagement`, `gcs=G111`, `gcd=13r3r3r3r5l1`, `npa=0`.

## GA4 consolidado — D-3 (01/10/2026)

- Sessões: **2.059**
- Sessões engajadas: **1.064**
- Taxa de engajamento: **51,68%**
- Bounce rate: **48,32%**
- Duração média: **3m28s**

Comparação: 29/09 bounce **49,24%**; 30/09 **47,62%**; 01/10 **48,32%**. Dado estável, sem assinatura de colapso global de tracking.

## Anomalias e classificação

1. **Race condition ainda presente:** primeira carga retornou `pscdl=noapi`/`npa=0`; as 5 repetições seguintes ficaram corretamente em `pscdl=denied`/`npa=1`.
2. **Cookies de marketing antes da escolha:** `_gcl_au`, `_fbp`, `_uetsid` e `_uetvid` apareceram em 5/5 contextos limpos mesmo com ad storage negado. Em uma carga instrumental também foram vistos `_ga*` antes do clique.
3. **GA4 D-3 saudável:** bounce de 48,32% e engajamento de 51,68%; nenhuma origem principal apresentou o padrão simultâneo de 95%+ bounce.
4. **Fontes específicas:** LinkedIn teve 93,94% de bounce em 33 sessões; é anomalia localizada, não falha global. Google ficou em 44,97%, direto em 58,85% e RD Email em 38,89%.

## Próxima ação recomendada

Manter escalonamento com Matias/Increazy para revisar a ordem do `consent default` versus GTM/sGTM e bloquear cookies de publicidade até o aceite. O risco LGPD permanece e deve continuar sinalizado ao Adrian. Repetir 5 contextos limpos após a correção.

## Evidência técnica

- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/scratch/consent-test-20261004.json`
