# 📊 GA4 diário — Loja Casa | 08/11/2026

**Propriedade:** `394358599` · `G-5709GFVVBK` · lojas.conamore.com.br  
**Dados:** 05/11/2026 (D-3) vs 04/11/2026 (D-4) · fuso America/Sao_Paulo · receita em BRL.

## Resumo executivo
- Em 05/11, 147 usuários ativos (-3,9%) e 180 sessões (+1,7%) ante 04/11.
- Engajamento subiu de 71,2% para 75,0% (+3,8 p.p.); eventos passaram de 1.970 a 2.215 (+12,4%).
- **E-commerce zerado em 05/11:** 0 transações e R$ 0,00, ante 2 e R$ 834,65 em 04/11; conferir pedidos reais e tagueamento, sem concluir falha apenas pela API.
- Em 05/11, direto (42 usuários), Google CPC (40) e ig / paid (19) lideraram as origens/mídias.
- Landing page `(not set)` teve 8 usuários, 9 sessões e engajamento 0% (5,4% dos usuários totais): sinal de ruído de atribuição/consentimento a investigar.

## 📈 Comparativo geral

| Indicador | 05/11 (D-3) | 04/11 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 147 | 153 | -6 (-3,9%) |
| Sessões | 180 | 177 | +3 (+1,7%) |
| Usuários novos | 105 | 109 | -4 (-3,7%) |
| Visualizações de página/tela | 1.014 | 824 | +190 (+23,1%) |
| Engajamento | 75,0% | 71,2% | +3,8 p.p. |
| Rejeição | 25,0% | 28,8% | -3,8 p.p. |
| Duração média da sessão | 4m 38s | 4m 04s | +13,8% |
| Eventos | 2.215 | 1.970 | +245 (+12,4%) |
| Transações | **0** | 2 | -2 |
| Receita de compras | **R$ 0,00** | R$ 834,65 | -R$ 834,65 |

## 👥 Novos vs recorrentes — 05/11

| Categoria `newVsReturning` | Usuários ativos | Sessões | Engajamento | Rejeição | Duração média |
|---|---:|---:|---:|---:|---:|
| new | 109 | 109 | 83,5% | 16,5% | 3m 51s |
| returning | 51 | 71 | 62,0% | 38,0% | 5m 51s |

Não houve linha `(not set)` nessa dimensão. Usuários por categoria não são aditivos (um mesmo usuário pode figurar em mais de uma categoria no período); não somar os 109 + 51 ao total de 147.

## 🔎 Origens/mídias — 05/11 (até 15, ordenadas por usuários)

| Origem / mídia | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| (direct) / (none) | 42 | 54 | 72,2% |
| google / cpc | 40 | 44 | 65,9% |
| ig / paid | 19 | 20 | 95,0% |
| google / organic | 15 | 17 | 94,1% |
| instagram / paid | 14 | 15 | 60,0% |
| linktr.ee / referral | 5 | 5 | 80,0% |
| chatgpt.com / ai-assistant | 4 | 4 | 100,0% |
| app.octadesk.com / referral | 3 | 13 | 61,5% |
| fb / paid | 3 | 3 | 100,0% |
| l.instagram.com / referral | 2 | 2 | 50,0% |
| (not set) | 1 | 1 | 100,0% |
| IGShopping / Social | 1 | 1 | 100,0% |
| an / paid | 1 | 1 | 100,0% |

A API retornou 13 origens/mídias. `ig / paid` e `instagram / paid` estão separadas pelo padrão de UTM: padronizar somente após validar campanhas.

## 📄 Top 10 landing pages — 05/11

| Landing page | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| `/` | 52 | 60 | 90,0% |
| `/lencois/linha-de-produto/avulsos.html` | 22 | 22 | 95,5% |
| `/hotel-em-casa` | 9 | 9 | 55,6% |
| `(not set)` | 8 | 9 | 0,0% |
| `/promocoes-lojas` | 6 | 6 | 66,7% |
| `/lencois` | 5 | 5 | 80,0% |
| `/jogo-de-lencol-queen-amore-40cm-4-pcs-150-fios-100-algod-o-rose-e-floral-ibiza-4` | 4 | 4 | 50,0% |
| `/jogo-de-lencol-queen-amore-40cm-4-pcs-150-fios-100-algodao-cor-azul-e-miami` | 3 | 3 | 33,3% |
| `/colchas` | 2 | 2 | 50,0% |
| `/edredom-king-amore-2-50x2-80-coracoes-e-preto-e-branco` | 2 | 2 | 50,0% |

Top 10 de 58 linhas existentes no relatório da API; não representa todas as páginas.

## 📱 Dispositivos — 05/11

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição | Duração média |
|---|---:|---:|---:|---:|---:|
| mobile | 103 | 116 | 76,7% | 23,3% | 3m 43s |
| desktop | 45 | 65 | 72,3% | 27,7% | 6m 12s |
| tablet | — | — | — | — | — |

Não retornou linha para tablet. Usuários de categorias de dispositivo não devem ser somados como usuários únicos; há pequena diferença também em sessões de detalhamento (181) frente ao total (180), a conferir em nova extração se persistir.

## 🚨 Observações e encaminhamentos

- **Vendas GA4 zeradas no varejo:** comparar os pedidos efetivamente faturados/fechados em 05/11 com o disparo do evento `purchase` e o valor enviado. O dia 04/11 registrou 2 transações, então não presumir ausência permanente de tracking.
- A qualidade agregada melhorou (+3,8 p.p. de engajamento), apesar de ligeira queda de usuários; visualizações (+23,1%) e eventos (+12,4%) cresceram mais que sessões (+1,7%).
- Landing page `(not set)` apresenta 9 sessões sem engajamento. Inspecionar consent mode, `page_location`/`session_start` e navegação PWA; o sinal é compatível com ruído de medição, mas não prova a causa. `newVsReturning` não apresentou `(not set)` relevante.
- `app.octadesk.com / referral`: 13 sessões para 3 usuários; checar se o domínio deve ser referência indesejada/cross-domain, sem alterar configuração sem validar.
- `ig / paid` e `instagram / paid` fragmentam a leitura do Instagram pago. Rever nomenclatura UTM nas campanhas.

**Fonte:** Google Analytics Data API via Composio, `GOOGLE_ANALYTICS_RUN_REPORT`, propriedade `properties/394358599`; 5 consultas: data, `newVsReturning`, `sessionSourceMedium`, `landingPage` e `deviceCategory`. Metadados da API: `timeZone=America/Sao_Paulo`, `currencyCode=BRL` na consulta geral. O percentual de variação compara D-3 a D-4; taxas em pontos percentuais.
