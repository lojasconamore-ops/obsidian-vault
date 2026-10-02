# Google Ads × tráfego orgânico — análise completa de canibalização da marca

**Período integrado:** 01/01/2024 a 29/09/2026  
**Search Console comparável:** 01/06/2025 a 29/09/2026  
**Coleta:** 02/10/2026, BRT

## Fontes utilizadas

- Google Ads API — termos contendo Conamore e variações.
- Google Search Console — propriedades `https://www.conamore.com.br/` e `sc-domain:lojas.conamore.com.br`.
- GA4 Hotelaria — property `379729087`.
- GA4 Casa — property `394358599`.
- Oracle DEBX — `TEST_PED.I_PEDVENDA_INTERFACE` confirmada (`IPV_STATUS=3`) ligada a `TEST_PED.F_PEDVENDA` por número do pedido.

## Conclusão executiva

**Existe canibalização forte e mensurável no termo de marca da Hotelaria.** Quando o investimento na marca exata aumenta, o CTR e os cliques orgânicos de “conamore” caem de forma quase espelhada. A correlação mensal entre gasto exato e CTR orgânico exato foi **r = -0,72**, associação inversa muito forte.

Nos meses de marca pausada, o CTR orgânico exato da Hotelaria foi **72,9%**, contra **20,9%** nos meses comparáveis de marca ativa. A posição orgânica permaneceu próxima de 1, demonstrando que a queda de CTR não foi causada por perda relevante de ranking.

## Comparação das fases

| Indicador | Marca ativa | Marca pausada | Variação ao pausar |
|---|---:|---:|---:|
| Gasto Ads de marca por fase | R$ 16.917,95 | R$ 9.277,59 | — |
| Gasto de marca exata | R$ 4.788,24 | R$ 0,56 | — |
| CTR orgânico exato “conamore” — Hotelaria | 20,9% | 72,9% | 249,0% |
| CTR orgânico de todas as buscas de marca — Hotelaria | 16,3% | 46,9% | 188,3% |
| Cliques orgânicos de marca/dia — Hotelaria + Casa | 62,3 | 174,0 | 179,2% |
| Cliques pagos de marca/dia | 197,5 | 24,6 | -87,5% |
| Cliques pagos + orgânicos de marca/dia | 259,8 | 198,6 | -23,6% |
| Sessões orgânicas GA4/mês | 6.711 | 11.093 | 65,3% |
| Sessões Paid Search GA4/mês | 10.221 | 8.383 | -18,0% |
| Pedidos confirmados Oracle/mês | 338,2 | 366,0 | 8,2% |
| Faturamento confirmado Oracle/mês | R$ 1.012.691,54 | R$ 1.145.672,94 | 13,1% |

**Definição das fases:** ativa = junho/2025 e junho–agosto/2026; pausada = agosto–dezembro/2025 e janeiro–abril/2026. Julho/2025 e maio/2026 foram excluídos como meses de transição. Setembro/2026 foi tratado separadamente porque o gasto caiu e o CTR orgânico se recuperou.

## Estimativa da canibalização de cliques

- A marca ativa acrescentou aproximadamente **172,9 cliques pagos/dia** em relação ao período pausado.
- Ao mesmo tempo, houve perda aproximada de **111,7 cliques orgânicos de marca/dia**.
- Relação estimada: **64,6% dos cliques pagos adicionais substituíram cliques orgânicos**, em vez de criar tráfego líquido.
- O ganho líquido estimado ficou em **61,2 cliques de marca/dia**.
- O total pago + orgânico foi 30,8% maior com a marca ativa, mas essa alta de tráfego não apareceu como aumento de pedidos ou faturamento total no Oracle.

> Esta estimativa é observacional, não um experimento aleatório. Sazonalidade, mudanças de campanhas, tracking e comportamento do mercado também influenciam. Ainda assim, a relação inversa é consistente, forte e repetida nos dois ciclos.

## Série mensal — Search Console × Ads

| Mês | Ads gasto | Cliques pagos marca | CTR orgânico “conamore” Hotelaria | Cliques orgânicos marca H+C | Cliques orgânicos totais H+C |
|---|---:|---:|---:|---:|---:|
| 2025-06 | R$ 4.963,59 | 9.198 | 12,8% | 2.151 | 5.517 |
| 2025-07 | R$ 1.941,25 | 2.106 | 59,7% | 6.397 | 9.942 |
| 2025-08 | R$ 1.858,15 | 1.202 | 72,9% | 5.862 | 9.415 |
| 2025-09 | R$ 490,42 | 262 | 74,3% | 4.800 | 7.687 |
| 2025-10 | R$ 1.144,81 | 555 | 74,3% | 5.027 | 8.026 |
| 2025-11 | R$ 1.432,61 | 867 | 74,1% | 6.107 | 9.531 |
| 2025-12 | R$ 827,00 | 716 | 72,7% | 4.510 | 7.232 |
| 2026-01 | R$ 1.467,06 | 1.267 | 76,9% | 6.728 | 10.193 |
| 2026-02 | R$ 509,06 | 481 | 76,1% | 4.908 | 7.344 |
| 2026-03 | R$ 828,76 | 816 | 69,7% | 5.293 | 8.231 |
| 2026-04 | R$ 719,72 | 552 | 64,1% | 4.272 | 7.379 |
| 2026-05 | R$ 1.544,46 | 1.967 | 60,0% | 4.019 | 7.090 |
| 2026-06 | R$ 3.747,17 | 5.049 | 20,9% | 1.523 | 4.414 |
| 2026-07 | R$ 4.278,71 | 5.064 | 26,7% | 1.765 | 4.809 |
| 2026-08 | R$ 3.928,48 | 4.784 | 31,1% | 2.164 | 5.158 |
| 2026-09 | R$ 1.865,28 | 2.310 | 56,3% | 4.271 | 7.823 |

## Leitura do Search Console

### Hotelaria — termo exato “conamore”

- Junho/2025, antes da retirada: CTR orgânico de **12,8%**.
- Agosto–novembro/2025, marca pausada: CTR entre **72,9% e 74,3%**.
- Janeiro/2026: CTR de **76,9%**.
- Junho–agosto/2026, após a reativação: CTR entre **20,9% e 31,1%**.
- Setembro/2026, com redução do gasto: CTR recuperou para **56,3%**.
- A posição média ficou aproximadamente entre 1,0 e 1,5 durante praticamente toda a série. A mudança principal ocorreu no clique, não no ranking.

### Casa

O domínio Casa não apresentou a mesma recuperação para o termo genérico “conamore”. Seu CTR permaneceu baixo porque a SERP distribui a intenção da marca entre Hotelaria, Casa e outros resultados. Já a consulta específica “conamore casa” apresentou CTR orgânico muito superior. Isso confirma que as duas unidades devem ser analisadas separadamente.

### Principais consultas orgânicas — Hotelaria

| Consulta | Cliques | Impressões | CTR | Posição |
|---|---:|---:|---:|---:|
| conamore | 57.546 | 98.620 | 58,4% | 1,27 |
| conamore hotelaria | 4.742 | 38.221 | 12,4% | 1,03 |
| canamore | 565 | 2.209 | 25,6% | 1,31 |
| comamore | 393 | 702 | 56,0% | 1,87 |
| consmore | 364 | 661 | 55,1% | 1,31 |
| loja conamore | 280 | 2.193 | 12,8% | 1,17 |
| conamorr | 260 | 480 | 54,2% | 1,14 |
| conamore cama mesa e banho | 258 | 2.117 | 12,2% | 1,25 |
| conamore roupa de cama | 194 | 1.503 | 12,9% | 1,13 |
| conamore campinas | 159 | 2.444 | 6,5% | 2,40 |
| conamore casa | 158 | 6.161 | 2,6% | 2,37 |
| conamore valinhos | 141 | 1.279 | 11,0% | 1,39 |

### Principais consultas orgânicas — Casa

| Consulta | Cliques | Impressões | CTR | Posição |
|---|---:|---:|---:|---:|
| conamore casa | 1.747 | 6.133 | 28,5% | 1,29 |
| conamore | 1.507 | 94.989 | 1,6% | 1,16 |
| conamore hotelaria | 162 | 32.647 | 0,5% | 1,24 |
| conamore lençol | 113 | 1.474 | 7,7% | 2,92 |
| lojas conamore | 88 | 313 | 28,1% | 1,12 |
| conamore cama mesa e banho | 60 | 2.116 | 2,8% | 1,37 |
| loja conamore | 53 | 2.168 | 2,4% | 1,26 |
| lençol conamore | 50 | 647 | 7,7% | 1,51 |
| conamore campinas | 39 | 2.423 | 1,6% | 2,95 |
| conamore indaiatuba | 34 | 1.138 | 3,0% | 3,48 |
| edredom conamore | 27 | 400 | 6,8% | 2,19 |
| loja conamore casa | 26 | 78 | 33,3% | 1,00 |

## GA4 — comportamento por canal

Nos meses pausados, a média mensal de sessões orgânicas das propriedades Hotelaria + Casa foi **11.093**, contra **6.711** nos meses de marca ativa, aumento de **65,3%**. As sessões de Paid Search caíram **18,0%**.

Esse movimento confirma a transferência de aquisição entre pago e orgânico. Entretanto, o GA4 possui mudanças de implementação ao longo do período e uma anomalia conhecida de Consent Mode a partir de 29/08/2026. Por isso, Search Console e Oracle têm maior peso para a conclusão.

## Oracle — pedidos e faturamento confirmados

A análise do Oracle usou pedidos da interface Increazy com `IPV_STATUS=3`, ligados à PED pelo número exato do pedido. A série começa em junho/2024 porque não houve registros confirmados anteriores nesse recorte da interface.

Nos meses comparáveis de marca ativa, a média foi **338,2 pedidos** e **R$ 1.012.691,54 por mês**. Nos meses pausados, foi **366,0 pedidos** e **R$ 1.145.672,94 por mês**. Isso representa **8,2% em pedidos** e **13,1% em faturamento**, mesmo sem compra relevante da marca exata.

### Limitação do Oracle

O número representa pedidos confirmados da interface ligada à PED. Não é margem e não identifica, sozinho, se cada venda veio de orgânico, Ads, acesso direto ou atuação comercial. Ele serve como controle de resultado total: as vendas não entraram em colapso quando a palavra de marca foi retirada.

## Diagnóstico final

1. **Canibalização confirmada no clique:** o gasto de marca exata tem associação inversa muito forte com o CTR orgânico exato.
2. **A posição orgânica permaneceu em primeiro lugar:** a perda não foi causada por piora de SEO.
3. **A maior parte do crescimento pago substituiu orgânico:** estimativa de 64,6% de substituição.
4. **O Ads trouxe algum aumento de tráfego total de marca**, mas muito menor que o volume pago comprado.
5. **Pedidos e faturamento não foram maiores nos períodos ativos:** no recorte comparável, foram superiores durante a pausa.
6. **“Conamore hotelaria” tem comportamento distinto:** deve ser controlado separadamente por possuir intenção B2B e maior potencial incremental.
7. **Casa e Hotelaria não devem compartilhar a mesma leitura de marca:** a SERP e a intenção são diferentes.
8. **ROAS de marca superestima aquisição:** ele atribui vendas de pessoas que já conheciam a empresa.

## Recomendação prática

### Manter

- Campanha de marca separada e com orçamento limitado.
- Defesa seletiva de `conamore hotelaria`, se concorrentes estiverem aparecendo acima ou junto da Conamore.
- Monitoramento diário de parcela de impressão, concorrentes e CPC.
- Marca negativada em todas as campanhas genéricas.

### Reduzir ou pausar

- Palavra isolada `conamore` em períodos sem pressão competitiva.
- Termos reputacionais: Reclame Aqui, avaliações e “é confiável”.
- Termos locais quando o objetivo da campanha é ecommerce ou geração de lead.
- Variações de marca nas campanhas de produtos genéricos.

### Teste definitivo

Executar experimento de quatro semanas, mantendo as campanhas genéricas com negativas de marca:

1. sete dias com marca exata ativa;
2. sete dias pausada;
3. repetir uma vez;
4. comparar Search Console, GA4, Google Ads e Oracle;
5. usar pedidos e faturamento total como critério principal.

### Critério de decisão

Manter a palavra de marca somente se o aumento de pedidos, faturamento ou margem total for superior ao custo da campanha. ROAS atribuído dentro do Ads não é suficiente.

## Limitações

- Search Console disponível a partir de junho/2025 neste relatório; não há série orgânica equivalente para 2024.
- Consultas anonimizadas ou de baixo volume podem não aparecer no Search Console.
- Google Ads também omite parte dos termos de baixa frequência.
- Junho/2025 e junho–agosto/2026 foram usados como meses ativos comparáveis; julho/2025 e maio/2026 foram classificados como transição.
- Setembro/2026 teve redução do gasto e recuperação orgânica; foi analisado separadamente.
- O GA4 teve mudanças de tracking e anomalia de Consent Mode a partir de 29/08/2026.
- O Oracle não possui atribuição de canal completa nesse recorte e não fornece margem na consulta utilizada.

Arquivo mensal consolidado: `Google Ads x Orgânico - Série mensal canibalização - 2024 a 2026-09.csv`

## Evidências técnicas

- Linhas Google Ads analisadas: 8.834.
- Consultas de marca únicas no Ads: 143.
- Período final Search Console: 01/06/2025 a 29/09/2026.
- Pedidos confirmados Oracle no período disponível: 10.124; faturamento R$ 28.090.728,15.