# Relatório Diário — Template Oracle DEBX

**Base oficial:** SQL Oracle DEBX
**Janela fixa:** últimos **15 dias**
**Fuso:** `America/Sao_Paulo`
**Janela operacional do Oracle DEBX:** disponível de **08:00 às 18:00 (BRT)**

## Abertura padrão
Rodei o relatório diário no padrão combinado: **gerencial** e **tabela de NFs por hora (BRT)**, considerando **somente os últimos 15 dias**.

## 1) Versão gerencial
- Total de registros
- Total de pedidos
- Total de NFs
- Faturamento
- Frete total
- Ticket médio por NF
- Pedidos com NF
- Pedidos sem NF
- NFs sem pedido
- Leitura executiva de concentração, status e frete

## 2) Versão operacional
- Série diária por data
- Picos e vales do período
- Principais pedidos com NF
- Principais pedidos sem NF
- Transportadoras / clientes destacados quando houver cruzamento
- Observações sobre parciais ou inconsistências

## 3) Versão consolidada
- Resumo final do período
- Top pedidos por valor
- Top NFs por valor
- Top fretes
- Origem / canal quando disponível
- Notas de consistência

## Conexão com o padrão oficial

- [[Relatório Diário - Padrão Oracle DEBX|Padrão Oracle DEBX]] — versão oficial consolidada

## Regras do padrão
- Não misturar períodos maiores com a janela fixa.
- Não substituir NF e faturamento por agregado de pedido.
- Se o cruzamento vier parcial, sinalizar claramente.
- Preferir nomes legíveis de cliente e transportadora.
- Se houver falta de vínculo entre NF, pedido e cadastro, informar como parcialidade.

## Estrutura recomendada da resposta
1. Abertura curta
2. Versão gerencial
3. Versão operacional
4. Versão consolidada
5. Observações finais, se houver
