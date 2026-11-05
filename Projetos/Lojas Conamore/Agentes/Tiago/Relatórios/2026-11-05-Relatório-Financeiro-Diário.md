# Relatório Financeiro Diário — 05/11/2026

**Ao DigitalCEO | Corte:** 05/11/2026, 08h BRT. Vendas de 04/11; recebíveis de 05/11 a 11/11, inclusive.

## Resumo financeiro
- **Vendas aprovadas — SQL Server `hotel-finder`, 04/11:** `conamore.CAIXA_PERIODO_COM_ORIGEM`: **46 pedidos / R$ 68.366,47**. Visão atualizada até 04/11; outros 3 pedidos em Expedição/R$ 256,82 não incluídos. `debx.PDV_Detalhes` registra 21 aprovados/R$ 39.753,35 em seu próprio recorte; não somar as bases.
- **Oracle DEBX/ACL, 04/11:** PED status A **18 pedidos/R$ 10.239,15**; PED status X **141/R$ 15.602,72** (**X = expedido**); status P 1/R$ 137,75. Loja física (`F_MOVTO`, `MOV_NATIND=100`): **331 movimentos/R$ 14.514,39**. PED e venda física são recortes distintos, não receita consolidada.

## Vencimentos e inadimplência
- **Contas a receber ACL sem baixa registrada, 05/11–11/11:** **736 títulos / R$ 130.602,23**. 05/11: 198/R$ 49.141,75; 06/11: 78/R$ 15.323,64; 07/11: 0; 08/11: 4/R$ 1.141,89; 09/11: 280/R$ 39.114,78; 10/11: 103/R$ 16.037,29; 11/11: 73/R$ 9.842,88. Recebíveis, não contas a pagar; sem confirmação de compensação bancária.
- **Vencidos antes de 05/11 — ACL:** **4.192 títulos / R$ 364.093,07**, **25,94%** do saldo aberto de R$ 1.403.426,72. Mais de 90 dias: **3.701 / R$ 283.971,69**. Indicador operacional de títulos sem baixa, sujeito à conciliação; não é inadimplência contábil consolidada.
- **Contas a pagar a fornecedores, 05/11–11/11:** fonte atual não confirmada; valor **não verificável (não zero)**. Saldo bancário indisponível. E-mail não acessado por restrição do perfil.

## Recomendações
1. Priorizar conferência de baixas e cobrança dos **R$ 49.141,75** com vencimento hoje e **R$ 39.114,78** em 09/11.
2. Conciliar os **R$ 364.093,07** vencidos, especialmente **R$ 283.971,69** acima de 90 dias, antes de provisão ou cobrança.
3. Obter posição oficial de contas a pagar e saldos bancários antes de projetar caixa; não tratar recebíveis sem baixa como recebimento certo.

**Fontes/método:** SQL Server `hotel-finder` (sessão `hotelfinder`, colunas e data máxima verificadas); Oracle `conamore` (sessão `TEST_PED`, colunas verificadas em `ALL_TAB_COLUMNS`), `TEST_ACL.F_PEDVENDA`, `F_MOVTO`, `F_TITULOS`. Títulos: parcela identificada (`TIT_NUMPAR`), `TIT_DATPGT` nula e saldo positivo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)`; janela `[05/11, 12/11)`. Consultas somente leitura; sem conciliação bancária.
