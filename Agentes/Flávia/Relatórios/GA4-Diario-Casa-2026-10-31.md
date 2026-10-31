# 📊 GA4 Diário — Loja Casa — 31/10/2026

**Dados: 28/10/2026 (D-3) vs 27/10/2026 (D-4)** · Property `394358599` · `G-5709GFVVBK` · fuso America/Sao_Paulo · moeda BRL.

## Resumo executivo
- Usuários ativos: **286 vs 265** (+7,9%); sessões: **314 vs 305** (+3,0%).
- Engajamento: **72,6% vs 69,5%** (+3,1 p.p.); rejeição caiu para 27,4%.
- Eventos: **3.239 vs 3.221** (+0,6%); pageviews: 1.298 vs 1.325 (-2,0%).
- **Alerta e-commerce:** 0 transações e R$ 0,00 em 28/10, ante 2 e R$ 1.764,37 em 27/10; investigar se houve venda real e instrumentação Magento/GA4.
- Instagram pago domina a aquisição (duas UTMs, `instagram / paid` e `ig / paid`); mobile concentra 255 dos 286 usuários ativos (contagem não aditiva por dimensão).

## Comparativo geral

| Indicador | 28/10 (D-3) | 27/10 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 286 | 265 | +7,9% |
| Sessões | 314 | 305 | +3,0% |
| Novos usuários | 203 | 176 | +15,3% |
| Visualizações de página/tela | 1.298 | 1.325 | -2,0% |
| Taxa de engajamento | 72,6% | 69,5% | +3,1 p.p. |
| Taxa de rejeição | 27,4% | 30,5% | -3,1 p.p. |
| Tempo médio da sessão | 3m 00s | 2m 55s | +2,8% |
| Eventos | 3.239 | 3.221 | +0,6% |
| Transações | **0** | 2 | -100% |
| Receita de compras | **R$ 0,00** | R$ 1.764,37 | -100% |

## Novos vs recorrentes — 28/10

| Perfil (`newVsReturning`) | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio da sessão |
|---|---:|---:|---:|---:|---:|
| new | 203 | 202 | 85,1% | 14,9% | 3m 39s |
| returning | 93 | 110 | 50,9% | 49,1% | 1m 53s |
| (not set) | 0 | 3 | 0,0% | 100,0% | 0s |

`(not set)` é pequeno (3 sessões; ~1,0% do total), mas compatível com ruído de mensuração/consent mode. As somas por dimensão não devem ser interpretadas como usuários únicos globais; há discrepâncias de sessões entre alguns recortes e o total, como retornado pela API.

## Canais — origem/mídia, top 15 por usuários ativos — 28/10

| Origem / mídia | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| instagram / paid | 145 | 150 | 61,3% |
| ig / paid | 50 | 53 | 83,0% |
| (direct) / (none) | 30 | 37 | 78,4% |
| google / cpc | 16 | 17 | 88,2% |
| google / organic | 16 | 17 | 82,4% |
| linktr.ee / referral | 13 | 14 | 92,9% |
| fb / paid | 6 | 6 | 83,3% |
| (not set) | 2 | 2 | 50,0% |
| app.octadesk.com / referral | 2 | 5 | 100,0% |
| l.facebook.com / referral | 2 | 4 | 50,0% |
| l.instagram.com / referral | 2 | 2 | 100,0% |
| RD Station / email | 1 | 2 | 50,0% |
| chatgpt.com / ai-assistant | 1 | 1 | 100,0% |
| facebook / cpc | 1 | 1 | 100,0% |
| ig / social | 1 | 2 | 50,0% |

GA4 retornou 17 linhas para o recorte; a tabela exibe as 15 primeiras solicitadas. `instagram / paid` e `ig / paid` são rótulos distintos; padronizar UTMs para leitura de campanha. Não somar usuários únicos de linhas como total deduplicado.

## Landing pages — top 10 por usuários ativos — 28/10

| Página de entrada | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| `/` | 60 | 66 | 87,9% |
| `/lencois/linha-de-produto/avulsos.html` | 55 | 56 | 87,5% |
| `/jogo-de-lencol-casal-amore-4-pcs-150-fios-100-algod-o-cinza-e-floral-vermelho-1` | 17 | 17 | 52,9% |
| `/jogo-de-lencol-queen-amore-40cm-4-pcs-150-fios-100-algod-o-rose-e-floral-ibiza-1` | 17 | 17 | 76,5% |
| `/jogo-de-lencol-queen-amore-40cm-4-pcs-150-fios-100-algodao-cor-azul-e-miami` | 12 | 12 | 83,3% |
| `/jogo-de-lencol-king-amore-40cm-4-pcs-150-fios-100-algodao-cor-azul-e-miami` | 11 | 11 | 45,5% |
| `/jogo-de-lencol-king-amore-40cm-4-pcs-150-fios-100-algodao-cor-zuda-e-palha` | 6 | 6 | 33,3% |
| `/edredom-solteiro-amore-1-60x2-50-cor-barcelona-e-azul-motorista` | 5 | 5 | 60,0% |
| `/edredom-solteiro-amore-1-60x2-50-cor-chevron-bege-e-bege` | 5 | 5 | 80,0% |
| `/jogo-de-lencol-king-amore-40cm-4-pcs-150-fios-100-algodao-cor-azul-e-miami-4` | 5 | 5 | 60,0% |

## Dispositivos — 28/10

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| mobile | 255 | 272 | 72,1% | 27,9% |
| desktop | 31 | 43 | 74,4% | 25,6% |
| tablet | 1 | 1 | 100,0% | 0,0% |

## Observações e encaminhamentos
- **Prioridade:** cruzar pedidos confirmados no Magento com `purchase`/transações GA4 de 28/10; zero não prova ausência de vendas. A série anterior tinha 2 transações, então acompanhar os próximos dias e verificar implementação se houver divergência.
- Revisar padronização das UTMs de Instagram pago (`instagram` vs `ig`) e possíveis referrals próprios de Octadesk, sem alterar tags antes de validação.
- Recorrentes têm rejeição de 49,1% frente a 14,9% dos novos; avaliar com mais dias antes de concluir causa.
- Há `(not set)` em perfil e origem; monitorar consent mode, mas o volume isolado de hoje é baixo.
- Fonte: Google Analytics Data API via Composio, `GOOGLE_ANALYTICS_RUN_REPORT`, cinco consultas independentes. Dados sujeitos a revisões posteriores do GA4. Nenhum dado D-1/D-0 foi usado.
