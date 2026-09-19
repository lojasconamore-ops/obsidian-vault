# Mercado Livre — análise inicial real

**Data da coleta:** 18/09/2026 (BRT)  
**Responsável:** Flávia / Marketing  
**Status:** primeira análise concluída; DRE por SKU e estoque Oracle pendentes

## Resumo executivo

A entrada no Mercado Livre faz sentido, mas o piloto não deve competir como commodity doméstica. Os dados internos confirmam demanda forte em lençóis, banho, protetores, fronhas e travesseiros, especialmente nos segmentos Airbnb, hotel, administradores e pousadas. No marketplace, os anúncios de entrada usam “hotel” como palavra-chave em produtos baratos de poliéster/microfibra; a Conamore precisa disputar por especificação profissional, durabilidade, kits operacionais e reputação.

A primeira onda recomendada é de **12 famílias de produto**, transformadas em aproximadamente **20–30 anúncios por tamanho e composição**, priorizando kits. Não publicar itens avulsos de baixo tíquete antes da DRE completa.

## 1. Base interna analisada

**Fonte:** SQL Server `hotel-finder`, visão `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`.  
**Atualização encontrada:** dados até 17/09/2026.  
**Filtros:** `Data_Venda >= 20/06/2026`; status `Expedição` e `Aprovado`.  
**Receita:** soma de `Valor_Bruto`. `Valor` é preço unitário e não deve ser somado como faturamento.  
**Preço e disponibilidade pública:** conferidos no ecommerce Hotelaria da Conamore em 18/09/2026.[2]

### Categorias — últimos 90 dias

| Categoria | Pedidos distintos na categoria | Quantidade | Receita bruta dos itens |
|---|---:|---:|---:|
| Lençóis | 2.002 | 36.523 | R$ 2.213.112,49 |
| Banho | 1.398 | 48.299 | R$ 1.228.752,83 |
| Cobertura/edredom | 1.174 | 9.380 | R$ 839.488,39 |
| Fronhas | 1.716 | 42.083 | R$ 561.390,15 |
| Protetores | 682 | 8.489 | R$ 268.517,55 |
| Travesseiros/porta-travesseiros | 538 | 4.554 | R$ 185.564,16 |
| Amenities | 95 | 304 kits | R$ 44.294,90 |

**Nota:** um mesmo pedido pode aparecer em mais de uma categoria; as contagens não devem ser somadas como total de pedidos da empresa.

### Segmentos — 2026 até 17/09

| Classe | Pedidos | Receita bruta |
|---|---:|---:|
| Airbnb | 1.544 | R$ 2.961.581,86 |
| Hotel | 627 | R$ 2.357.690,92 |
| Administradores | 612 | R$ 2.141.119,11 |
| Pousada | 651 | R$ 1.985.899,44 |
| Varejo Casa | 753 | R$ 458.410,11 |
| Clínica | 144 | R$ 398.169,28 |

**Conclusão:** a oportunidade de marketplace não é somente Casa. O público profissional autônomo já representa demanda relevante na operação da Conamore.

## 2. Produtos internos com maior aderência

### Prioridade A — lançar após validar margem e estoque

| SKU | Produto | Evidência interna 2026 | Preço público atual | Formato indicado |
|---|---|---|---:|---|
| `16429` | Lençol Queen sem elástico Confort 180 fios misto | 718 pedidos; R$ 1,00 mi YTD | R$ 74,90 | kit 2 e kit 5 |
| `17689` | Lençol Casal sem elástico Confort 180 fios misto | 814 pedidos; R$ 495,3 mil YTD | R$ 66,90 | kit 2 e kit 5 |
| `19348` | Lençol Casal com elástico Confort 180 fios misto | 825 pedidos; R$ 320,5 mil YTD | R$ 62,90 | kit 2 e composição de quarto |
| `18082` | Toalha Banho Quality 70x140, 410 g/m² | 821 pedidos; R$ 618,2 mil YTD | R$ 37,90 | kits 4, 6 e 10 |
| `4230003` | Toalha Banho Select 80x140, 440 g/m² | 451 pedidos; R$ 329,8 mil YTD | R$ 47,90 | kits 2, 4 e 6 |
| `1080002` | Protetor impermeável Casal | 661 pedidos; R$ 251,2 mil YTD | R$ 75,90 | individual e kit com travesseiro |
| `1080003` | Protetor impermeável Queen | 692 pedidos; R$ 140,3 mil YTD | R$ 89,90 | individual e kit com travesseiro |
| `15709` | Protetor impermeável de travesseiro 50x70 | 1.195 pedidos; R$ 178,1 mil YTD | R$ 15,90 | somente kits 4 e 10 |
| `42213003` | 500 sabonetes Capim-Limão 10 g | 141 pedidos; R$ 40,3 mil YTD | R$ 225,60 | caixa profissional |
| `42213024` | 250 sachês shampoo + condicionador 30 ml | 90 pedidos; R$ 24,7 mil YTD | R$ 175,90 | caixa profissional/combo |

### Prioridade B — testar seletivamente

| SKU | Produto | Diagnóstico |
|---|---|---|
| `27160003` | Travesseiro Ecopluma 50x70 | Forte internamente, mas preço público de R$ 139,90 enfrenta concorrentes de marca entre aproximadamente R$ 49,90 e R$ 123. Precisa provar superioridade. |
| `2140019` | Capa para enchimento de edredom Queen | Boa receita e diferenciação; exige simulação de frete por volume. |
| `16446` | Fronha Confort 180 fios | Líder absoluto de volume, mas tíquete unitário baixo; deve entrar em kits, nunca isolada. |

### Bloqueio encontrado

O travesseiro Suporte Médio `27118004`, um dos mais fortes internamente, aparece **esgotado** no site público por R$ 49,90. Ele seria competitivo contra o Camesa Neo Prime, também anunciado a R$ 49,90 e com mais de 10 mil vendidos no Mercado Livre.[5] Deve entrar no piloto somente após reposição confirmada.

## 3. Mercado Livre — realidade competitiva

O Mercado Livre informa tarifa por categoria de aproximadamente **10%–14% no Clássico e 15%–19% no Premium**.[1]

### Lençóis

- Há forte pressão de produtos domésticos baratos apresentados como “hotel”. Um jogo Queen de três peças, anunciado como 400 fios mas composto em 100% poliéster, aparece a R$ 67 e com mais de 1.000 vendas.[3]
- No lado superior, um jogo Queen de quatro peças, 400 fios e 100% algodão, aparece a R$ 193,90.[8]
- A Conamore não deve disputar o primeiro grupo por preço. Deve explicar composição, lavagem profissional, resistência e custo por uso.

### Protetores

- A busca mostra kit com quatro capas de solteiro por R$ 71,01 e mais de 500 vendidos, além de protetores domésticos Queen próximos de R$ 36,90.[4]
- Os protetores Conamore Casal e Queen custam R$ 75,90 e R$ 89,90 por unidade. A venda precisa ser posicionada como proteção profissional e não como capa doméstica barata.

### Travesseiros

- O Camesa Neo Prime 50x70 aparece a R$ 49,90, avaliação 4,7 e mais de 10 mil vendidos.[5]
- O Travesseiro Suporte Médio Conamore está exatamente nessa faixa, mas esgotado.
- O Ecopluma a R$ 139,90 deve ser tratado como premium, com prova clara de peso, enchimento, capa, suporte e durabilidade.

### Toalhas

- A Loja Oficial Toalha Show anuncia quatro toalhas 70x130 por R$ 69,82 e duas toalhas 520 g/m² por R$ 78,90.[7]
- A Quality Conamore custa R$ 37,90 por peça, enquanto a Select custa R$ 47,90. A Conamore é competitiva no segmento profissional intermediário/premium, mas não no kit de entrada extremamente barato.

### Amenities

- O kit concorrente de 500 sachês shampoo 2x1 de 10 ml + 500 sabonetes de 10 g aparece a R$ 278,90 e mais de 1.000 vendidos.[6]
- A Conamore vende 500 sabonetes 10 g por R$ 225,60. Não é comparação idêntica, mas sinaliza forte pressão de preço e necessidade de lançar combo shampoo + sabonete.
- A amostra de sete anúncios de amenities variou de R$ 39,90 a R$ 359,89; a mediana calculada da amostra foi R$ 59,90, refletindo mistura de kits pequenos e caixas profissionais.

## 4. Simulação preliminar de tarifa

Esta conta considera **apenas comissão**, sem frete, imposto, embalagem, custo, devolução ou Ads. Portanto, não é margem.

| Exemplo usando preço atual | Preço | Líquido após 14% | Líquido após 19% |
|---|---:|---:|---:|
| 2 Lençóis Queen `16429` | R$ 149,80 | R$ 128,83 | R$ 121,34 |
| 4 Toalhas Quality `18082` | R$ 151,60 | R$ 130,38 | R$ 122,80 |
| 6 Toalhas Quality `18082` | R$ 227,40 | R$ 195,56 | R$ 184,19 |
| 10 Protetores de travesseiro `15709` | R$ 159,00 | R$ 136,74 | R$ 128,79 |
| 500 sabonetes `42213003` | R$ 225,60 | R$ 194,02 | R$ 182,74 |

**Leitura:** itens avulsos de baixo valor são inadequados. Kits aumentam tíquete, diluem embalagem e permitem absorver melhor comissão e frete.

## 5. Oportunidade principal

Na amostra analisada, não apareceu um concorrente dominante reunindo cama, banho, proteção e amenities em um único produto operacional para anfitriões. A principal tese para diferenciação é:

1. **Kit Airbnb 1 quarto — reposição básica**
2. **Kit Airbnb 1 quarto — giro profissional**
3. **Kit para 3 quartos**
4. **Kit para 5 quartos**
5. **Kit Toalhas para Pousada — 10 unidades**
6. **Kit Cama Hotel Queen — lençóis + fronhas + protetores**
7. **Kit Amenities por 100, 250 e 500 hospedagens**

Os kits devem declarar número de quartos/estadias atendidos, composição, gramatura, fios, material, instruções de lavagem e custo por uso.

## 6. Riscos e pendências

- **Custo e margem:** ainda não existe DRE por SKU com custo real.
- **Estoque Oracle:** tentativa realizada às 22:44 BRT; o Oracle retornou `ORA-01033`, coerente com a janela operacional documentada de 08:00–18:00 BRT.
- **Frete:** itens volumosos, sobretudo travesseiros, edredons e kits grandes, precisam de cotação simulada por CEP.
- **Preço:** os preços públicos da Conamore não podem ser simplesmente copiados; é necessário preço específico do canal.
- **Dados cadastrais:** o mesmo SKU aparece no banco com sufixos operacionais como “NÃO ENVIAR”, nomes de cliente e observações. O catálogo deve usar a descrição canônica do produto.
- **Concorrência:** parte dos preços do Mercado Livre pode variar por Pix, variante, localização ou benefício de primeira compra.

## 7. Decisão recomendada

**Avançar para a fase econômica e operacional**, sem publicar ainda.

Próximos gates:

1. consultar estoque disponível no Oracle durante a janela operacional;
2. obter custo real dos 12 candidatos;
3. simular frete para cinco CEPs representativos;
4. fechar DRE Clássico e Premium;
5. montar os primeiros 20–30 anúncios a partir das 12 famílias;
6. testar três compras completas antes da abertura pública.

## Sources

[1] https://www.mercadolivre.com.br/ajuda/870 — Mercado Livre — Quanto custa vender um produto
[2] https://www.conamore.com.br — Conamore Hotelaria
[3] https://www.mercadolivre.com.br/jogo-de-lencol-queen-3-pcs-completo-400-fios-hotel-cor-branco/p/MLB47716624 — Jogo de lençol Queen 3 peças 400 fios
[4] https://lista.mercadolivre.com.br/kit-de-protetor-de-colchao — Mercado Livre — kits de protetor de colchão
[5] https://www.mercadolivre.com.br/travesseiro-camesa-neo-prime-50-x-70-cm-cor-branco/p/MLB19766384 — Travesseiro Camesa Neo Prime
[6] https://www.mercadolivre.com.br/kit-shampoo-2em1-sache-10ml-500un--500un-mini-sabonete-10g/up/MLBU605411986 — Kit 500 shampoos + 500 sabonetes
[7] https://www.mercadolivre.com.br/loja/toalha-show — Loja Oficial Toalha Show no Mercado Livre
[8] https://www.mercadolivre.com.br/jogo-lencol-queen-4-pecas-400-fios-100-algodao-colchao-alto/up/MLBU3804201836 — Jogo Queen 4 peças 400 fios 100% algodão
