---
tags: [stape, sgtm, infra, diagnostico, api]
gerado: 2026-09-02
fonte: "Stape API v2 (X-AUTH-TOKEN) — conta lojasconamore@gmail.com"
---

# Retrato da Stape — container server-side (via API)

> Acesso obtido via **Stape API v2** (Account API key "Hermes_agents", criada 02/09). Sem login web (que tem CAPTCHA).

## Container (único)
| Campo | Valor |
|---|---|
| Nome | `SERVER Conamore Increazy` |
| identifier | `vtutlczq` |
| sGTM | `GTM-N7Z62R96` |
| Status | 🟢 Running |
| Zona | SA East (Brasil/SP) — IP `35.199.84.11` |
| stapeDomain | `vtutlczq.san.stape.io` |
| Domínio first-party | `gtmserver.conamore.com.br` (Ready; DNS A + AAAA OK) |
| Plano | Pro — US$20/mês, pago ok |
| Limite | 500.000 req/mês |

## Power-ups (o que está ligado)
- ✅ **serviceAccount** — ÚNICO ativo (há service account do Google associada; credencial de ~2,4KB presente)
- ❌ Tudo o resto **OFF**: cookieKeeper, adBlocker, anonymizer, botDetection, customLoader, enricher, clickIdRestorer, geoHeaders, storage, schedule, fileProxy, xmlToJson, botIndex, etc.

## Recursos desligados (limitações p/ diagnóstico)
- **Analytics** OFF (`dataCollecting: null`)
- **Logs de saída** NÃO habilitados (`outgoingLogsEnabledAt: null` → API de logs retorna 409)
- **Debug mode** OFF
- **Storage** OFF
- `todayUsage: 0` (sem analytics não há contagem de uso visível)

## API keys da conta
| Nome | Criada | Observação |
|---|---|---|
| Legacy | ~2024 | token ...f40f9 |
| Hermes_agents | 02/09/2026 | token ...9943b ← em uso |

## Conclusões
1. **Infra saudável e enxuta**: 1 container Pro, domínio first-party OK, 1 power-up ativo (serviceAccount). Nada de mecânica complexa na Stape.
2. **A Stape API dá o contorno, não o interior**: confirmado que ela NÃO expõe tags/clients/triggers — isso vive no GTM (Via 1).
3. **Achado p/ acelerar a Via 1**: já existe uma **service account do Google** ativa no container (power-up `serviceAccount`). Reaproveitar/estender essa service account para leitura do container GTM pode eliminar o passo de "criar service account do zero" no pedido ao Matias.

## Status
- [x] Retrato da Stape mapeado via API
- [ ] Reaproveitar service account existente para a Via 1 (GTM API) — alinhar com Matias
- [ ] (opcional) Habilitar logs de saída p/ monitorar tráfego por API
