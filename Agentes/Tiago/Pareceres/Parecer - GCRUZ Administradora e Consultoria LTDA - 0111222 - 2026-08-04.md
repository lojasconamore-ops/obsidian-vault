# Parecer de Crédito — GCRUZ Administradora e Consultoria LTDA — Pedido 0111222

**Data:** 04/08/2026  
**Responsável:** Tiago — Financeiro  
**Cliente:** GCRUZ Administradora e Consultoria LTDA  
**Nome fantasia:** GCRUZ Administradora de Imóveis  
**CNPJ:** 12.615.003/0001-19  
**ID_DEBX:** 05459  
**Pedido/orçamento:** 0111222  
**Segmento/classe:** Airbnb / gestão e administração de propriedade imobiliária  

## Documentos analisados

1. `111222 GCRUZ.pdf` — orçamento de venda.
2. `ANÁLISE GCRUZ.pdf` — relatório Equifax/Boa Vista.

## Etapa 0 — Lista Negra Conamore

✅ **Não encontrado na Lista Negra Conamore** por CNPJ, razão social ou nome fantasia.

## Etapa 1 — Histórico interno Conamore

**Fonte consultada:** SQL Server Hotel Finder (`conamore.Customers`, `debx.PDV_Detalhes`, `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`).

- Cadastro localizado no Hotel Finder:
  - ID_DEBX: 05459
  - Status: 0
  - Cadastro: 08/07/2026
  - Endereço: Rua Belém, 48, Sala 01, Centro, Piên/PR
- Pedido atual localizado como **Orçamento**.
- Não há venda/faturamento confirmado para o CNPJ 12.615.003/0001-19.
- A busca por mesmo endereço retornou apenas a própria GCRUZ; sem grupo econômico interno identificado pelo endereço.

**Atenção:** o ID_DEBX 05459 retornou registros antigos de outra razão social (`SIMONE TIBAU LIMA MENEZES 01282219766`). Por divergência de razão social/CNPJ, esses registros foram tratados como colisão/migração de ID e **não foram usados como histórico de pagamento da GCRUZ**.

**Classificação interna:** primeira compra efetiva / sem histórico faturado próprio.

## Etapa 2 — Score / Bureau

**Fonte:** Equifax | Boa Vista — consulta de 04/08/2026 08:37:16.

- Score PJ: **876 / 1000** — muito forte.
- Probabilidade de inadimplência: **1,0%** — excelente.
- Pendências e restrições financeiras: **Nada consta**.
- Cheques sem fundo/sustados/devolvidos: **Nada consta**.
- Protestos: **Nada consta**.
- Cadastro Positivo: consumidor não participante; o score não considera Cadastro Positivo.
- CNPJ: ativo.
- Fundação: 20/09/2010.
- Natureza jurídica: Sociedade Empresária Limitada.
- CNAE principal: gestão e administração da propriedade imobiliária — 6822-6/00.

**Leitura:** bureau forte e limpo. Mesmo sem Cadastro Positivo, não há negativação, protesto ou pendência que impeça faturamento.

## Etapa 3 — Coerência operacional do pedido

**Pedido:** enxoval de cama, banho e protetores para operação tipo Airbnb/administração de imóveis.

Itens principais:
- Fronhas, lençóis solteiro/casal/queen com e sem elástico.
- Protetores de travesseiro e colchão.
- Toalhas de banho e rosto.

**Coerência:** positiva. O mix é compatível com gestão de imóveis, locação por temporada ou operação de hospedagem/Airbnb.

## Etapa 4 — Exposição real da Conamore

**PDF/orçamento como fonte comercial principal:**

- Total do pedido com frete/desconto: **R$ 9.612,62**.
- Entrada prevista: **R$ 4.806,31**.
- Saldo previsto: **R$ 2.403,15 em 30 dias + R$ 2.403,15 em 60 dias**.
- Soma das parcelas: **R$ 9.612,61** — diferença residual de R$ 0,01 por arredondamento.
- **Exposição líquida financiada:** **R$ 4.806,31**.
- Entrada: **50,00%** do total.

**Observações de sistema:**
- No Hotel Finder/PDV, o pedido aparece com condição `A DEFINIR` e valor de R$ 17.757,10, divergente do PDF.
- Para decisão de crédito, o PDF foi tratado como fonte comercial autoritativa.
- Recomenda-se corrigir a condição no DEBX antes do faturamento.

## Etapa 5 — Validação operacional online

Fontes consultadas:
- Receita WS / dados públicos de CNPJ.
- DuckDuckGo Lite para presença pública e registros empresariais.
- Google Maps direto.

Achados:
- CNPJ ativo desde 2010.
- Capital social declarado: R$ 1.570.000,00.
- Atividade principal e secundárias compatíveis com administração/corretagem/gestão de imóveis e serviços relacionados.
- Sócios-administradores: Giberson José da Cruz e Clediane Aparecida Rudnick da Cruz.
- Presença pública encontrada principalmente em bases cadastrais/empresariais: CNPJ.biz, Diário Cidade, QuitaCondo, Cadastro Empresa, Econodata, CNPJá, Casa dos Dados etc.
- Não foi localizada presença operacional forte em Google Maps, Instagram, Booking/Airbnb próprio ou site institucional claro.

**Classificação:** 🟡 operação parcial — existência cadastral forte, mas pouca evidência pública direta da operação/hospedagem.

## Parecer

✅ **Aprovar o faturamento conforme condição do PDF:** 50% de entrada + saldo em boletos 30/60 dias.

**Nível de risco:** baixo a moderado.

## Condição recomendada

- **Aprovar somente após compensação da entrada de R$ 4.806,31.**
- Saldo: 2 boletos de R$ 2.403,15 em 30/60 dias.
- Corrigir no DEBX/PDV a condição de pagamento que consta como `A DEFINIR`.
- Ajustar/validar a divergência de valor entre PDF e PDV antes do faturamento.

## Justificativa técnica objetiva

Apesar de ser primeira compra efetiva sem histórico próprio na Conamore, o risco está bem controlado porque:

1. Cliente não está na Lista Negra.
2. Bureau é muito forte: score 876, inadimplência estimada 1,0%, sem protestos, restrições ou cheques.
3. Empresa é ativa desde 2010, com capital social relevante e CNAE compatível com administração de imóveis.
4. Pedido é coerente com operação de imóveis/Airbnb.
5. A entrada de 50% reduz a exposição real para R$ 4.806,31, valor baixo/moderado para o risco apresentado.

**Ponto de controle:** a validação operacional online é apenas parcial; por isso, não recomendo boleto puro nem flexibilização além de 30/60 neste primeiro faturamento.
