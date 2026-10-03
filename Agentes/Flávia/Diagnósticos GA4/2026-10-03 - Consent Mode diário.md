# Diagnóstico diário GA4 Consent Mode — 2026-10-03

- **Execução:** 03/10/2026, 08:01–08:08 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** property `379729087`, measurement ID `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`

## Resultado executivo

**Status: ALERTA — fluxo de aceite funciona, mas há corrida intermitente antes da escolha.**

O `consent default` apareceu em 5/5 contextos limpos com `analytics_storage`, `ad_storage`, `ad_user_data` e `ad_personalization` como `denied`. O banner apareceu em 5/5. Porém, os beacons divergiram do default em 3/5 execuções: `pscdl=noapi`, `npa=0`, `gcd=13l3l3l3l1l1` e cookies de analytics/marketing antes da escolha. Em 2/5, o sinal foi coerente com negação: `gcs=G100`, `pscdl=denied`, `npa=1`, `gcd=13p3p3p3p5l1`.

Pela regra do diagnóstico, resultados mistos `pscdl=denied` e `pscdl=noapi` sob o mesmo default visível indicam **load-order/race condition**.

## Caminho de aceite

- Clique real em **Aceitar Tudo** executado.
- `consent update`: analytics e marketing → `granted`.
- Evento: `cc_consent_update` com `analytics_consent=granted` e `marketing_consent=granted`.
- Persistência: `cc_cookie_consent_status=true`; `cc_cookie_preferences={"marketing":true,"statistics":true}`.
- Após reload: beacon para `gtmserver.conamore.com.br/g/collect`, `tid=G-V0KMM7L6M6`, `en=PageView`, `gcs=G111`.

## GA4 consolidado — D-3 (30/09/2026)

- Sessões: **2.081**
- Sessões engajadas: **1.090**
- Taxa de engajamento: **52,38%**
- Bounce rate: **47,62%**
- Duração média: **3m14s**

Principais eventos: `page_view` 6.342; `view_item_list` 2.373; `session_start` 2.080; `user_engagement` 1.735; `first_visit` 1.392; `view_item` 1.067; `scroll` 1.034; `add_to_cart` 208; `purchase` 74; `compra_erp` 55; `purchase_erp` 40.

## Anomalias e classificação

1. **Race condition de Consent Mode:** 3/5 cargas pré-escolha processaram tags como `noapi`/`npa=0`, apesar do default denied presente.
2. **Cookies antes do consentimento:** `_gcl_au`, `_fbp`, `_uet*`, Clarity e outros foram observados antes da escolha; em parte das execuções também `_ga*` e `FPLC`.
3. **Console:** sem exceções JavaScript não capturadas. Falhas CORS do Reclame Aqui e warning de currency do Meta Pixel foram classificados como terceiros/não causais para o Consent Mode.
4. **Dado GA4 D-3 saudável:** bounce de 47,62% e engajamento de 52,38%; sem assinatura de colapso global no dia consolidado.
5. **02/10/2026 não consolidado:** apresentou ~98% de bounce em múltiplas origens, mas está dentro da janela de processamento de 24–48h e não deve ser usado para conclusão hoje.

## Próxima ação recomendada

Escalar para Matias/Increazy revisar a ordem de carregamento do `consent default` versus GTM/sGTM e bloquear tags/cookies de marketing até o estado de consentimento estar efetivamente aplicado. Sinalizar o risco LGPD ao Adrian. Repetir o teste de 5 contextos após correção.

## Evidências técnicas

- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/scratch/consent-test-20261003.json`
- `/home/sergio-ladeira/.hermes/profiles/marketing/cache/scratch/consent-postaccept-reload-20261003.json`
