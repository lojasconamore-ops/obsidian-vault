# Relatório Financeiro Diário — 29/10/2026

**Ao DigitalCEO | Corte:** 29/10/2026, 08h03 BRT. Vendas/aprovações de 28/10; títulos com vencimento de 29/10 a 04/11 (7 dias corridos, hoje incluso).

## Resumo financeiro
- **SQL Server `hotel-finder`, `conamore.CAIXA_PERIODO_COM_ORIGEM`, 28/10:** 35 pedidos aprovados / **R$ 94.007,22**; 2 em expedição / R$ 188,60 em separado. Fonte atualizada até 28/10. A visão bruta `debx.PDV_Detalhes` contém 22 cancelados / R$ 307.811,21; não somar como venda. Divergência de definição/recorte entre visões, conferir no ERP.
- **Pagar.me (`paid_at` 28/10):** 18 cobranças aprovadas / **R$ 74.564,53**, ticket R$ 4.142,47. SSL 12/R$ 60.166,05; GCL 6/R$ 14.398,48; ACL/BRG 0. Cartão 9/R$ 58.416,39; PIX 8/R$ 14.212,84; boleto 1/R$ 1.935,30. 18 OK; 0 REVISAR/SUSPEITO. Aprovação não equivale à liquidação; bases não somáveis.
- **Oracle DEBX/ACL, 28/10:** PED A 14/R$ 6.312,57; PED X (expedido) 82/R$ 7.480,68; PED F 1/R$ 80,00. Loja física `F_MOVTO`, `MOV_NATIND=100`: 182 movimentos/R$ 7.456,78. PED e loja física são recortes distintos.

## Vencimentos e inadimplência
- **Contas a receber ACL sem baixa registrada, 29/10–04/11:** 636 títulos / **R$ 85.628,33**. Hoje, 29/10: 154/R$ 15.459,79; 30/10: 65/R$ 7.614,36; 31/10: 1/R$ 269,45; 01/11: 1/R$ 199,80; pico 02/11: 251/R$ 42.495,73; 03/11: 95/R$ 9.316,13; 04/11: 69/R$ 10.273,07. Saldo = valor original menos pagamentos parciais. São recebíveis ACL, não contas a pagar.
- **Vencidos ACL antes de 29/10:** 3.839 títulos / **R$ 321.742,16**, **23,52%** do saldo aberto ACL de R$ 1.367.800,74; mais de 90 dias: 3.699 / **R$ 283.664,42**. Indicador de títulos sem baixa; não é inadimplência contábil consolidada sem conciliação.
- **Contas a pagar a fornecedores:** posição atual 29/10–04/11 não localizada nos arquivos acessíveis; valor **não verificável (não zero)**. E-mail vedado a este perfil. Sem saldo bancário atualizado para projeção líquida de caixa.

## Recomendações
1. Conciliar baixas dos R$ 15.459,79 com vencimento hoje e iniciar cobrança dos títulos ACL efetivamente vencidos, priorizando a revisão dos R$ 283.664,42 com mais de 90 dias.
2. Preparar cobrança/recebimento do pico de 02/11 (R$ 42.495,73), sem assumir entrada bancária na data antes da confirmação do calendário e das liquidações.
3. Obter contas a pagar e saldos bancários oficiais antes de comprometer desembolsos; reconciliar diferença entre pedidos aprovados SQL, cobranças Pagar.me e PED sem somar visões heterogêneas.

**Fontes/método:** Pagar.me consolidado gerado nesta execução e XLSX relido; SQL Server sessão `hotel-finder`/`hotelfinder`, colunas e atualização verificadas; Oracle `conamore`/`TEST_ACL` validado com `select 1` e `sys_context`, colunas descobertas. `F_TITULOS`: `TIT_NUMPAR` não nulo, `TIT_DATPGT` nulo e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`; janela por `TIT_DATVEN`. Somente leitura nas fontes de dados.
