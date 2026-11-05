# 📊 GA4 Diário — Loja Casa | 05/11/2026

**Property:** `394358599` · `G-5709GFVVBK` · lojas.conamore.com.br  
**Dados:** 02/11/2026 (D-3) vs 01/11/2026 (D-4), fuso America/Sao_Paulo. Fonte: GA4 Data API via Composio; moeda BRL.

## Resumo executivo
- Usuários ativos: **123 vs 118** (+4,2%); sessões: **136 vs 125** (+8,8%).
- Engajamento: **78,7% vs 80,0%** (-1,3 p.p.); rejeição: **21,3% vs 20,0%** (+1,3 p.p.).
- Eventos: **2.565 vs 1.972** (+30,1%); visualizações: **1.213 vs 904** (+34,2%).
- E-commerce: **5 transações / R$ 1.844,17** em 02/11, contra **0 / R$ 0,00** em 01/11; conferir rastreamento e vendas reais do dia zerado antes de atribuir causa.
- Mobile respondeu por **113/123 usuários (91,9%)**; `instagram / paid` teve **53,6% de rejeição** (28 sessões), ponto de atenção para tráfego pago.

## 📈 Comparativo geral

| Indicador | 02/11 (D-3) | 01/11 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 123 | 118 | +4,2% |
| Sessões | 136 | 125 | +8,8% |
| Usuários novos | 98 | 91 | +7,7% |
| Visualizações de página/tela | 1.213 | 904 | +34,2% |
| Taxa de engajamento | 78,7% | 80,0% | -1,3 p.p. |
| Taxa de rejeição | 21,3% | 20,0% | +1,3 p.p. |
| Duração média da sessão | 6m 45s | 4m 42s | +43,7% |
| Eventos | 2.565 | 1.972 | +30,1% |
| Transações | 5 | 0 | base zero |
| Receita de compras | R$ 1.844,17 | R$ 0,00 | base zero |

## 👥 Novos vs Recorrentes — 02/11

| Classificação (`newVsReturning`) | Usuários ativos | Sessões | Engajamento | Rejeição | Duração média |
|---|---:|---:|---:|---:|---:|
| new | 99 | 99 | 83,8% | 16,2% | 7m 43s |
| returning | 31 | 37 | 64,9% | 35,1% | 4m 10s |

`(not set)` não retornou nesse recorte. Usuários ativos por classificação não são aditivos (uma pessoa pode figurar em mais de um grupo no período); sessões somam 136.

## 🔎 Canais — origem/mídia, 02/11 (até 15, ordenado por usuários ativos)

| Origem / mídia | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| (direct) / (none) | 36 | 41 | 90,2% | 9,8% |
| instagram / paid | 25 | 28 | 46,4% | 53,6% |
| google / cpc | 23 | 26 | 76,9% | 23,1% |
| google / organic | 17 | 18 | 94,4% | 5,6% |
| linktr.ee / referral | 13 | 13 | 92,3% | 7,7% |
| ig / paid | 5 | 5 | 80,0% | 20,0% |
| chatgpt.com / ai-assistant | 3 | 3 | 66,7% | 33,3% |
| ig / social | 2 | 2 | 100,0% | 0,0% |

A API retornou 8 origens/mídias (rowCount=8). `instagram / paid` e `ig / paid` aparecem separadamente: revisar padronização de UTMs, sem somar usuários únicos entre linhas.

## 📄 Landing pages — top 10, 02/11 (ordenadas por usuários ativos)

| Página de entrada | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| `/` | 69 | 71 | 90,1% | 9,9% |
| `/jogo-de-lencol-casal-amore-4-pcs-150-fios-100-algod-o-cinza-e-floral-vermelho-1` | 3 | 3 | 33,3% | 66,7% |
| `/lencois` | 3 | 3 | 100,0% | 0,0% |
| `/capa-para-edredom-king-250x280` | 2 | 2 | 50,0% | 50,0% |
| `/edredom-casal-amore-2-20x2-50-chicago-e-argila` | 2 | 2 | 0,0% | 100,0% |
| `/edredom-queen-amore-2-50x2-60-floral-ibiza-e-rose` | 2 | 4 | 50,0% | 50,0% |
| `/edredom-queen-amore-2-50x2-60-zuda-palha` | 2 | 2 | 50,0% | 50,0% |
| `/fronha-uso-profissional-hotelaria-400-fios-100-algodao-1` | 2 | 2 | 50,0% | 50,0% |
| `/jogo-de-lencol-queen-amore-40cm-4-pcs-150-fios-100-algodao-cor-azul-e-miami` | 2 | 2 | 50,0% | 50,0% |
| `/lencois.html` | 2 | 2 | 50,0% | 50,0% |

Top 10 dentre 48 linhas reportadas; as demais não estão listadas. Não extrapolar as taxas das páginas com apenas 2–3 sessões.

## 📱 Dispositivos — 02/11

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| mobile | 113 | 121 | 77,7% | 22,3% |
| desktop | 10 | 15 | 86,7% | 13,3% |
| tablet | 0* | 0* | — | — |

\* Tablet não retornou como linha da API; usuários e sessões de mobile + desktop fecham os totais do dia. Não há taxa a calcular.

## 🚨 Observações e encaminhamentos
- O dia 01/11 teve **zero transações e receita GA4**; validar no Magento/ERP e no disparo de `purchase` antes de concluir se houve ausência de vendas ou falha de mensuração. Em 02/11, há 5 transações capturadas.
- A rejeição de `instagram / paid` (53,6%, 28 sessões) supera a taxa geral do dia (21,3%); revisar campanha, criativo e destino, observando amostra pequena.
- Padronizar UTMs `instagram` e `ig` para evitar fragmentação da leitura de mídia paga.
- Não apareceu `(not set)` em `newVsReturning` no dia; monitorar recorrência de ruído de consent mode sem presumir que esteja resolvido.
- O ganho de visualizações e eventos supera o de sessões; verificar continuidade do padrão em dias consolidados. Comparação entre segunda-feira e domingo também pode refletir sazonalidade semanal.

**Status:** concluído; dados D-3/D-4 confirmados pela API, sem consulta de vendas transacionais externas.
