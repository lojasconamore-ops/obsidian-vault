---
tags: [gtm, sgtm, stape, inventario, descoberta, api]
gerado: 2026-09-02
fonte: "Google Tag Manager API (service account conamore-hotelaria-firestore)"
---

# Inventário do Container Server-side (via GTM API) — DESCOBERTA: container vazio

> Acesso concluído via GTM API. Service account: `conamore-hotelaria-firestore@agile-kite-392211.iam.gserviceaccount.com` (reaproveitada do power-up serviceAccount da Stape).

## IDs mapeados
| Item | Valor |
|---|---|
| Conta GTM | `6100042948` — "Conamore Hotelaria" |
| Container | `196967926` — `GTM-N7Z62R96` "CONAMORE Hotelaria (Server)" |
| Workspace | `30` — "Default Workspace" |

## Inventário do container (VERIFICADO via API)
| Recurso | Qtde |
|---|---|
| Clients | **0** |
| Tags | **0** |
| Triggers | **0** |
| Variables | **0** |
| Transformations | **0** |
| Templates | **0** |
| Built-in variables | **0** |
| Versões publicadas | **0** (nenhuma) |
| Live version | inexistente (`containerVersionId: None`) |

## Conclusão (importante)
**O container server-side `GTM-N7Z62R96` está VAZIO** — nunca teve nenhum client/tag/trigger configurado e nenhuma versão publicada.

Isso **contradiz** o que estava documentado em [[Diagnóstico e Plano — Atribuição de Vendas Google Ads 2026-08-29]] ("sGTM dispara GA4 + Ads + CAPI + LinkedIn"). A Stape hospeda e responde (healthz 200), mas **não há lógica nenhuma dentro do container** para processar os webhooks `/purchase_erp` e `/purchase`.

## Hipóteses para o `compra_erp` (R$530k/30d no Ads)
1. A **Increazy envia direto pro Google Ads** (API de conversão própria), NÃO via sGTM.
2. Há outro container/server-side em outra conta GTM ou outra Stape (a service account só enxerga a conta `6100042948`).
3. Outro mecanismo (n8n, Lambda, etc.) fora do GTM/Stape.

## Obs
- O container web `GTM-MMGX8ZL` (client-side) NÃO está nesta conta GTM — deve estar em outra conta, à qual a service account atual não tem acesso.
- Próximo passo: confirmar com a Increazy (ou via Google Ads API/GAQL) **de onde vem a `compra_erp`**.

## Status
- [x] Acesso GTM API concluído (ata- lho via service account existente)
- [x] Inventário do container server mapeado → VAZIO
- [ ] Investigar origem real do `compra_erp` (Increazy x sGTM x outro)
- [ ] (se aplicável) pedir acesso à conta GTM do web container `GTM-MMGX8ZL`
