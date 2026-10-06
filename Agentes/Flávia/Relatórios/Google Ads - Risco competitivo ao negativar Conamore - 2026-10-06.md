# Google Ads — Risco competitivo ao negativar “Conamore”

**Data da análise:** 06/10/2026, BRT  
**Período principal:** 01/06/2025 a 29/09/2026  
**Atualização de cobertura paga:** até 05/10/2026

## Conclusão executiva

Existe uma brecha competitiva real quando a Conamore reduz ou interrompe a compra da própria marca, mas os dados internos disponíveis **não mostram perda mensurável de pedidos ou faturamento** durante a fase de menor cobertura paga.

O melhor ponto estimado com os dados observados é: **não foi identificada perda líquida de vendas para concorrentes**. Pelo contrário, nos meses classificados como pausa, a média de pedidos e faturamento confirmado foi superior à fase ativa. Isso não prova que nenhum pedido individual tenha migrado para concorrentes, pois as fases têm sazonalidade diferente e o Oracle não registra compras feitas em outros fornecedores.

O risco atual decorre principalmente da cobertura incompleta do anúncio institucional. Entre agosto e setembro de 2026, a campanha deixou de participar de aproximadamente dois terços dos leilões elegíveis por limitação de orçamento, e não por baixa classificação. Nos primeiros cinco dias de outubro, a parcela de impressão foi 50,7%, com 48,4% perdida por orçamento e somente 0,9% perdida por ranking.

## Evidências observadas

### 1. Vendas durante marca ativa e reduzida

| Indicador mensal médio | Marca ativa | Marca reduzida/pausada |
|---|---:|---:|
| Cliques pagos + orgânicos de marca/dia | 259,8 | 198,6 |
| Pedidos confirmados Oracle | 338,2 | 366,0 |
| Faturamento confirmado Oracle | R$ 1.012.691,54 | R$ 1.145.672,94 |
| Sessões orgânicas + pagas + diretas | 25.193 | 27.207 |

A fase reduzida teve 27,8 pedidos e R$ 132.981,40 a mais por mês na média observada. Por sazonalidade, isso não deve ser tratado como ganho causado pela pausa; serve para mostrar que não houve colapso comercial quando a marca exata perdeu cobertura.

### 2. Recuperação do resultado orgânico

O CTR orgânico do termo exato `conamore` na Hotelaria passou de 20,9% durante a marca ativa para 72,9% na fase reduzida, mantendo posição orgânica próxima de 1.

Esse CTR de 72,9% indica que a maior parte da procura navegacional continuou chegando ao domínio da Conamore. Portanto, qualquer desvio para concorrentes ficou limitado ao tráfego residual da SERP — que também inclui Casa, outros resultados próprios, mapas, reputação e buscas sem clique.

### 3. Cobertura da campanha institucional

Dados da `keyword_view` e da campanha institucional:

| Mês | Parcela de impressão | Parcela no topo absoluto | Perda por orçamento | Perda por ranking |
|---|---:|---:|---:|---:|
| 2025-06 | 96,3% | 93,8% | 0,2% | 3,5% |
| 2026-06 | 65,5% | 62,7% | 33,8% | 0,7% |
| 2026-07 | 75,8% | 71,5% | 22,1% | 2,1% |
| 2026-08 | 22,1% | 19,5% | 66,3% | 11,6% |
| 2026-09 | 33,3% | 31,6% | 66,0% | 0,7% |
| 2026-10 até dia 5 | 50,7% | 49,6% | 48,4% | 0,9% |

A perda recente é predominantemente de orçamento. Quando a Conamore não participa, outro anunciante pode ocupar o espaço, mas a métrica de parcela de impressão não identifica quem ocupou o leilão nem prova que houve clique ou venda para um concorrente.

### 4. Concorrentes nomeados

A extração GAQL não fornece os domínios concorrentes do relatório de Informações do Leilão. A inspeção direta da SERP brasileira não pôde ser concluída nesta coleta porque o navegador de automação estava indisponível. Portanto, **nenhum concorrente específico está confirmado atualmente como comprador de “Conamore”**.

Também não foram encontrados termos de pesquisa históricos combinando `conamore` com ParaHotel, Teka, Karsten, Santista, Altenburg, Buddemeyer, Zelo, Camesa e outras marcas rastreadas. Isso não exclui lances concorrentes: termos vistos na conta da Conamore não revelam o anunciante que disputou o leilão.

## Estimativa de vendas potencialmente expostas

Quando a marca esteve ativa, o total pago + orgânico ficou aproximadamente 61,2 cliques/dia acima da fase reduzida. Isso equivale a 1.863 cliques/mês.

Para construir um teto conservador, foi usada uma taxa aproximada de pedidos sobre sessões de 1,34% e ticket médio de R$ 3.062. Essa taxa mistura canais e não é uma taxa causal da palavra de marca.

| Parcela dos cliques faltantes desviada para concorrentes | Cliques expostos/mês | Pedidos teóricos | Faturamento bruto teórico |
|---|---:|---:|---:|
| 10% | 186 | 2,5 | R$ 7.666 |
| 25% | 466 | 6,3 | R$ 19.164 |
| 50% | 931 | 12,5 | R$ 38.328 |
| 100% — teto extremo | 1.863 | 25,0 | R$ 76.656 |

Esses valores são **cenários de exposição**, não vendas comprovadamente perdidas. O teto de 25 pedidos/mês exigiria que todos os cliques líquidos adicionais da mídia fossem pessoas que, sem o anúncio, comprariam de concorrentes — hipótese incompatível com o forte CTR orgânico e sem suporte nos resultados do Oracle.

## Classificação do risco

- **Risco atual de ocupação publicitária:** médio/alto, porque a campanha cobre apenas cerca de metade dos leilões recentes e perde quase metade por orçamento.
- **Risco comprovado de perda de vendas:** baixo/inconclusivo; não houve queda de pedidos e faturamento na fase reduzida.
- **Risco para `conamore` isolado:** baixo a médio, pois o orgânico ocupa posição 1 e recupera CTR acima de 70% sem forte compra paga.
- **Risco para `conamore hotelaria`, produtos e intenção comercial:** médio, porque o usuário pode comparar fornecedores e o concorrente pode apresentar oferta específica antes do resultado orgânico.
- **Risco reputacional/local:** baixo para venda incremental; anúncio defensivo tende a comprar tráfego navegacional que já buscava a Conamore.

## Recomendação

Não voltar a comprar indiscriminadamente toda busca de marca. Usar defesa seletiva:

1. Manter `conamore` isolado pausado ou com orçamento mínimo quando não houver concorrentes visíveis.
2. Manter campanha separada para `conamore hotelaria`, produtos e termos comerciais de alta intenção.
3. Negativar todas as variações da marca nas campanhas genéricas.
4. Monitorar diariamente a SERP e semanalmente as Informações do Leilão, registrando domínio concorrente, posição, texto, oferta e página de destino.
5. Acionar defesa somente quando concorrente confirmado aparecer, buscando 85%–95% de parcela de impressão para os termos defensivos prioritários.
6. Medir em semanas alternadas os pedidos totais, faturamento e margem — não o ROAS atribuído pelo Ads.

## Status

- **Executado:** cruzamento de Search Console, Ads, GA4, Oracle e nova consulta de parcela de impressão até 05/10/2026.
- **Evidência:** recuperação orgânica para 72,9%; vendas sem queda na fase reduzida; campanha institucional com 50,7% de parcela de impressão e 48,4% perdida por orçamento em outubro.
- **Status:** risco competitivo confirmado como possibilidade operacional; perda de vendas para concorrentes não comprovada. Cenário máximo de exposição estimado em 25 pedidos/R$ 76,7 mil por mês, com faixa prudente de estresse entre 2,5 e 6,3 pedidos/R$ 7,7 mil a R$ 19,2 mil mensais.
