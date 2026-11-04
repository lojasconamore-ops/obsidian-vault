# Relatório Financeiro Diário — 04/11/2026

**Ao DigitalCEO | Corte:** 04/11/2026, 08h02 BRT. Vendas/aprovações de 03/11; vencimentos de 04/11 a 10/11 (7 dias corridos, inclusive).

## Resumo financeiro
- **Vendas aprovadas — SQL Server `hotel-finder`, 03/11:** `conamore.CAIXA_PERIODO_COM_ORIGEM`, status Aprovado: **49 pedidos / R$ 99.605,98**. Visão atualizada até 03/11. Status D: 1 pedido/R$ 4.740,00, não incluído nas vendas aprovadas. A visão `debx.PDV_Detalhes` registra 24 aprovados/R$ 77.419,88 no seu próprio recorte; não somar as bases.
- **Pagar.me, 03/11 (ACL/SSL/GCL/BRG):** **28 cobranças aprovadas / R$ 87.841,56**, ticket médio R$ 3.137,20; SSL 19/R$ 75.300,23, GCL 7/R$ 11.788,66, ACL 2/R$ 752,67, BRG 0. PIX 12/R$ 50.246,44; cartão 15/R$ 36.922,45; boleto 1/R$ 672,67. **28 OK, 0 suspeitas/revisar.** Aprovação de cobrança não é liquidação bancária e não se soma às vendas do SQL.
- **Oracle DEBX/ACL, 03/11:** PED status A 23 pedidos/R$ 15.649,22; PED status X 115/R$ 8.765,09 (**X = expedido**); loja física (`F_MOVTO`, `MOV_NATIND=100`) 229 movimentos/R$ 8.559,03. PED e venda física são recortes distintos, não receita consolidada.

## Vencimentos e inadimplência
- **Contas a receber ACL sem baixa, 04/11–10/11:** **724 títulos / R$ 104.575,16**. 04/11: 164/R$ 16.939,01; 05/11: 96/R$ 14.431,76; 06/11: 76/R$ 14.983,42; 07/11: 1/R$ 1.927,01; 08/11: 4/R$ 1.141,89; **09/11: 280/R$ 39.114,78**; 10/11: 103/R$ 16.037,29. São recebíveis, não contas a pagar.
- **Vencidos antes de 04/11 — ACL:** **4.184 títulos / R$ 364.014,95**, ou **26,69%** do saldo aberto de R$ 1.363.883,37. Acima de 90 dias: **3.701 / R$ 283.971,69**. Indicador de títulos sem baixa no ERP, sujeito à conciliação; não é inadimplência contábil consolidada.
- **Contas a pagar a fornecedores, 04/11–10/11:** base atual não localizada/confirmada; valor **não verificável (não zero)**. Saldo bancário atual indisponível. E-mail não acessado por restrição do perfil.

## Recomendações
1. Conciliar baixas dos **R$ 364.014,95** vencidos; priorizar **R$ 283.971,69** com mais de 90 dias antes de cobrança/provisão.
2. Preparar a cobrança/recebimento dos **R$ 16.939,01** com vencimento hoje e dos **R$ 39.114,78** em 09/11; confirmar compensação efetiva no banco.
3. Obter posição oficial de contas a pagar e saldos bancários antes de projetar caixa; não confundir cobranças Pagar.me com liquidação.

**Fontes/método:** Pagar.me v5, consolidado gerado nesta execução para 03/11; SQL Server `hotel-finder`, sessão, colunas e atualização validadas; Oracle `conamore`, sessão `TEST_ACL` e colunas confirmadas, `TEST_ACL.F_PEDVENDA`, `F_MOVTO`, `F_TITULOS`. Para títulos: parcela identificada, `TIT_DATPGT` nula, saldo positivo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)` e vencimento de 04/11 inclusive a 11/11 exclusivo. Consultas operacionais somente de leitura; não houve conciliação bancária.
