# 📊 Resumo diário de tráfego GA4 — Loja Casa

**Geração:** 04/11/2026 (BRT) · **Dados:** 01/11/2026 (D-3) vs 31/10/2026 (D-4) · **Property:** `394358599` (`G-5709GFVVBK`) · lojas.conamore.com.br

## Resumo executivo
- Usuários ativos: **118 vs 88** (**+34,1%**); sessões: **125 vs 96** (**+30,2%**).
- Engajamento: **80,0% vs 65,6%** (**+14,4 p.p.**); rejeição: **20,0% vs 34,4%** (**−14,4 p.p.**).
- Eventos: **1.972 vs 1.043** (**+89,1%**); visualizações: **904 vs 444** (**+103,6%**); duração média **4m42s vs 2m15s**.
- E-commerce: **0 transações/R$ 0,00** em 01/11, ante **1/R$ 219,11** em 31/10. **Alerta:** conferir pedidos Magento e evento `purchase` antes de concluir falha de mensuração.
- Tráfego liderado por **(direct) / (none)** (34 usuários), com **mobile em 88,0% das sessões**; `(not set)` não apareceu em novos/recorrentes nem nas landing pages consultadas.

## Comparativo geral

| Métrica | 01/11 (D-3) | 31/10 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 118 | 88 | +34,1% |
| Sessões | 125 | 96 | +30,2% |
| Novos usuários | 91 | 66 | +37,9% |
| Visualizações de página/tela | 904 | 444 | +103,6% |
| Taxa de engajamento | 80,0% | 65,6% | +14,4 p.p. |
| Taxa de rejeição | 20,0% | 34,4% | −14,4 p.p. |
| Duração média da sessão | 4m42s | 2m15s | +2m27s |
| Eventos | 1.972 | 1.043 | +89,1% |
| Transações | 0 | 1 | −1 (−100%) |
| Receita de compras | R$ 0,00 | R$ 219,11 | −R$ 219,11 (−100%) |

**Alerta de e-commerce:** ausência de compras registradas em 01/11 não comprova ausência de pedidos. Conciliar Magento × GA4 `purchase`, incluindo valor e consentimento; não misturar receita GA4 com faturamento efetivo.

## Novos vs recorrentes — 01/11

| Categoria (`newVsReturning`) | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio da sessão |
|---|---:|---:|---:|---:|---:|
| new | 94 | 94 | 86,2% | 13,8% | 5m08s |
| returning | 28 | 31 | 61,3% | 38,7% | 3m24s |
| (not set) | — | — | — | — | — |

**Nota:** Não houve linha `(not set)` retornada para este dia; usuários por segmento não são aditivos, pois podem transitar entre categorias. Os **94** usuários na categoria `new` não são intercambiáveis com os **91** da métrica `newUsers`.

## Canais — origem/mídia, ordenados por usuários ativos em 01/11

| Origem / mídia | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| (direct) / (none) | 34 | 38 | 78,9% |
| google / cpc | 20 | 20 | 70,0% |
| google / organic | 20 | 20 | 90,0% |
| instagram / paid | 19 | 21 | 66,7% |
| linktr.ee / referral | 9 | 9 | 100,0% |
| ig / paid | 7 | 7 | 100,0% |
| (data not available) | 2 | 2 | 100,0% |
| facebook / cpc | 2 | 2 | 50,0% |
| similarsearch.net / referral | 2 | 2 | 50,0% |
| RD Station / email | 1 | 1 | 100,0% |
| bing / organic | 1 | 1 | 100,0% |
| chatgpt.com / ai-assistant | 1 | 1 | 100,0% |
| ig / social | 1 | 1 | 100,0% |

**Nota:** 13 origens/mídias retornadas, todas listadas (até top 15). `instagram / paid` e `ig / paid` permanecem separados na coleta; padronizar UTMs. Usuários por origem não são necessariamente aditivos.

## Landing pages — top 10 por usuários ativos em 01/11

| Landing page | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| `/` | 63 | 64 | 89,1% |
| `/lencois/linha-de-produto/avulsos.html` | 5 | 5 | 100,0% |
| `/jogo-de-lencol-queen-amore-40cm-4-pcs-150-fios-100-algod-o-rose-e-floral-ibiza-1` | 4 | 4 | 75,0% |
| `/jogo-de-lencol-queen-amore-40cm-4-pcs-150-fios-100-algod-o-rose-e-floral-ibiza-4` | 4 | 4 | 75,0% |
| `/toalha-de-banho-aura-70-140-cm-gramatura-100-algodao-azul` | 3 | 3 | 33,3% |
| `/jogo-de-lencol-casal-amore-4-pcs-150-fios-100-algod-o-cinza-e-floral-vermelho-1` | 2 | 2 | 100,0% |
| `/jogo-de-lencol-king-amore-40cm-4-pcs-150-fios-100-algodao-cor-zuda-e-palha` | 2 | 2 | 50,0% |
| `/lencois.html` | 2 | 2 | 100,0% |
| `/promocoes-lojas` | 2 | 2 | 50,0% |
| `/toalhas-de-banho-direto-fabrica` | 2 | 2 | 50,0% |

**Nota:** 45 landing pages retornadas no total; top 10 exibido. Consulta exata a `landingPage = (not set)` não retornou linhas. Home `/` respondeu por **64/125 sessões (51,2%)**; valores empatados no corte podem alterar a composição do top 10.

## Dispositivos — 01/11

| Dispositivo | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| mobile | 104 | 110 | 80,0% |
| desktop | 14 | 15 | 80,0% |
| tablet | — | — | — |

Mobile respondeu por **110/125 sessões (88,0%)**. A API não retornou linha para tablet; não equivale a auditar todos os eventos de dispositivos.

## 🚨 Observações e próximos passos

- O salto em usuários, sessões e profundidade ocorreu de **sábado (31/10) para domingo (01/11)**; dois dias não bastam para estabelecer tendência causal. Comparar domingos anteriores e calendário de campanhas antes de interpretar o crescimento.
- Apesar de **904 visualizações e 1.972 eventos**, GA4 não registrou transações em 01/11. Validar pedidos reais no Magento e disparos `purchase` por meio do fluxo de checkout, sem concluir que faturamento foi zero.
- `instagram / paid` teve **21 sessões/66,7% de engajamento** e `ig / paid` **7/100,0%**; amostras pequenas, mas UTMs devem ser uniformizadas para leitura consolidada.
- Segmentação `newVsReturning` e landing page não mostram `(not set)` em 01/11, diferente do ruído residual do dia anterior; continuar acompanhando o consent mode sem atribuir causa apenas a esse recorte.

**Fonte:** GA4 Data API via Composio `GOOGLE_ANALYTICS_RUN_REPORT`, `properties/394358599`; metadata confirmou timezone `America/Sao_Paulo` e moeda `BRL`. Datas absolutas D-3/D-4; segmentações apenas em 01/11.
