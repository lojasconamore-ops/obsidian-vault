# Relatório Financeiro Diário — 10/10/2026

**Ao DigitalCEO**
**Corte:** 10/10/2026, 08:06 BRT. Vendas/aprovações: 09/10; vencimentos: 10–17/10, inclusive.

## Resumo financeiro
- **SQL Server `conamore.CAIXA_PERIODO_COM_ORIGEM`: 38 pedidos aprovados | R$ 56.652,47 | ticket médio R$ 1.490,85.** Fonte atualizada até 09/10 (sem lag). Origem MAG: 17 / R$ 17.685,32; sem origem: 21 / R$ 38.967,15. Outros 2 pedidos em Expedição / R$ 163,22 não integram os aprovados.
- **Pagar.me `paid_at` de 09/10: 25 cobranças aprovadas | R$ 41.289,57 | ticket R$ 1.651,58; 25 OK, 0 SUSPEITO, 0 REVISAR.** SSL 16 / R$ 31.961,51; BRG 4 / R$ 7.373,19; ACL 5 / R$ 1.954,87; GCL 0. Cartão 11 / R$ 23.933,10; PIX 14 / R$ 17.356,47. Não somar à venda SQL: universos/estágios distintos; aprovação não comprova liquidação.
- **Sobreposição DEBX/Oracle ACL, não somar:** PED X (expedido) 105 / R$ 11.809,17; A 14 / R$ 10.358,32; F 2 / R$ 14.667,55. Loja física `F_MOVTO`, `MOV_NATIND=100`: 256 movimentos / R$ 11.669,57. PED não é venda física.
- **Nota de classificação:** `debx.PDV_Detalhes` registra em 09/10: Financeiro 3 / R$ 16.651,05 e Pendente 3 / R$ 11.589,68 (total R$ 28.240,73) — agregado bruto por status, **não perda financeira confirmada**; reconciliar com os 38 aprovados na fonte principal, sem somar universos.

## Vencimentos e inadimplência
- **Contas a pagar a fornecedores (10–17/10): base atual não localizada nos arquivos acessíveis.** Valor e datas não disponíveis, não zero. E-mail não acessado por restrição do perfil.
- **Contas a receber ACL, títulos com parcela e sem data de pagamento (10–17/10): 737 | R$ 106.640,46 de saldo.** 10/10: 85 / R$ 11.074,98; 11/10: 4 / R$ 5.530,38; 12/10: 275 / R$ 32.578,81; 13/10: 90 / R$ 18.913,68; 14/10: 96 / R$ 15.490,33; 15/10: 103 / R$ 10.638,16; 16/10: 82 / R$ 11.219,15; 17/10: 2 / R$ 1.194,97. Não inclui outras lojas nem comprova recebimento futuro.
- **Vencidos ACL, sem data de pagamento antes de 10/10: 3.766 | R$ 295.660,14**, 22,02% do saldo aberto bruto ACL de R$ 1.342.824,71. Acima de 90 dias: 3.697 | R$ 286.600,13. Indicador operacional, não inadimplência contábil consolidada; exige conciliação de baixas/abatimentos.

## Recomendações
1. Cobrar os R$ 11.074,98 vencendo hoje e preparar régua para R$ 32.578,81 em 12/10 (maior vencimento do período).
2. Conciliar os R$ 286.600,13 vencidos há mais de 90 dias antes de escalonar cobrança; confirmar saldo real.
3. Reconciliar Financeiro + Pendente (R$ 28.240,73) em `debx.PDV_Detalhes` por pedido/motivo, sem tratá-los como receita perdida.
4. Obter a posição oficial de contas a pagar para projeção de caixa; não inferir ausência de obrigações pela falta de base.

## Fontes e limites
- SQL Server `hotel-finder`: sessão `hotelfinder`, colunas e atualização até 09/10 verificadas; `Status_Pedido='Aprovado'` como venda aprovada.
- Pagar.me v5: consolidado gerado nesta execução, janela `paid_at` 09/10; XLSX relido e agrupado (loja e meio).
- Oracle `conamore`: sessão `TEST_PED`, colunas verificadas; `TEST_ACL.F_TITULOS` com `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo, `TIT_VALORI` positivo; saldo = `TIT_VALORI - NVL(TIT_VALPAG,0)`. PED e loja física separados.
- Não há posição atual de contas a pagar confirmada nesta execução.
