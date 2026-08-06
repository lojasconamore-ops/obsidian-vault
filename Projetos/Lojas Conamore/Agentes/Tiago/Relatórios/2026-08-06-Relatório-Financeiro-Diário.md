# Relatório Financeiro Diário — 2026-08-06

**Base BRT:** 06/08/2026, 08:01  
**Período de vendas:** 05/08/2026  
**Janela de vencimentos:** 06/08 a 13/08/2026

## Resumo financeiro

- **Pagar.me aprovado:** 37 cobranças | **R$ 55.002,56** | ticket médio **R$ 1.486,56**.
- **Conciliação limpa:** 35 cobranças | **R$ 49.720,88**.
- **Em revisão:** 2 cobranças | **R$ 5.281,68** | **9,6%** do valor aprovado.
- **Variação Pagar.me vs. 04/08:** **-R$ 18.414,72 (-25,1%)**.
- **Por loja:** SSL **R$ 34.191,78** (10); ACL **R$ 11.620,94** (20); BRG **R$ 9.189,84** (7); GCL **R$ 0,00**.
- **Por meio:** cartão **R$ 43.527,68** (24); PIX **R$ 11.474,88** (13).
- **SQL Server — pedidos aprovados:** 40 | **R$ 81.647,07** | ticket médio **R$ 2.041,18**. Fonte atualizada até 05/08. Não comparar diretamente com Pagar.me: escopos operacionais diferentes.
- **Oracle/DEBX — PED status X:** 62 | **R$ 8.455,82**. **Venda física F_MOVTO/MOV_NATIND=100:** 128 movimentos | **R$ 6.177,52**. PED e venda física mantidos separados.

## Alertas de vencimentos

- **Contas a vencer em 7 dias:** base atual de contas a pagar **não localizada** no Drive, vault ou arquivos locais pesquisados. Não significa saldo zero.
- **Pendências antigas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. Exposição carregada: **R$ 109.222,37** — valores históricos, não classificados como vencimentos atuais.
- **Pagar.me em revisão:** 2 PIX da BLUEHAUS, aprovados com 90 segundos de intervalo, pedidos distintos, valores de **R$ 2.738,98** e **R$ 2.542,70**. Total **R$ 5.281,68**.

## Inadimplência

- **Indicador atual:** não disponível.
- O proxy SQL não encontrou parcelas estimadas vencidas nos últimos 30 dias, mas a base não informa liquidação/baixa; portanto, **não usar como índice de inadimplência**.

## Recomendações

1. **Validar hoje os 2 PIX BLUEHAUS (R$ 5.281,68)** contra pedidos e intenção do cliente antes de qualquer ação.
2. **Obter/exportar a posição atual de contas a pagar** para 06–13/08; sem essa base, o risco de caixa da semana não é mensurável.
3. **Confirmar baixa das 3 pendências históricas (R$ 109.222,37)** e retirar do acompanhamento o que já estiver liquidado.
4. **Implantar indicador diário de inadimplência** com títulos vencidos, saldo aberto, aging e baixa recebida; o dado atual é insuficiente.

## Fontes validadas

- Pagar.me v5, aprovações de 05/08/2026; artefato consolidado gerado em 06/08/2026.
- SQL Server `hotel-finder`, sessão e colunas validadas; dados até 05/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`, schema e colunas validados; consultas somente leitura.
- Google Drive: 6 buscas de metadados financeiros recentes, sem resultados.
