# Relatório Financeiro Diário — 12/10/2026

**Ao DigitalCEO**  
**Corte:** 12/10/2026, 08:02 BRT. Vendas de 11/10; vencimentos de 12 a 19/10, inclusive (hoje + 7 dias).

## Resumo financeiro
- **Vendas aprovadas (SQL Server `conamore.CAIXA_PERIODO_COM_ORIGEM`, 11/10): 21 pedidos | R$ 15.363,94 | ticket médio R$ 731,62.** Base atualizada até 11/10; `Status_Pedido='Aprovado'`.
- **DEBX/Oracle ACL, não somar ao SQL:** PED A 16 pedidos / R$ 7.436,30 em 11/10; PED X (expedido) não registrado no dia. Loja física (`F_MOVTO`, `MOV_NATIND=100`): 0 movimentos. PED não é venda física nem receita aprovada da fonte SQL.
- `debx.PDV_Detalhes` está atualizado somente até 10/10: não serve para validar o movimento de 11/10.

## Vencimentos e inadimplência
- **Contas a pagar fornecedores (12–19/10): sem base atual verificável.** Não confundir ausência de dados com zero obrigações; e-mail não consultado por restrição de acesso.
- **Contas a receber ACL, títulos parcelados com saldo positivo e sem data de pagamento (12–19/10): 980 | R$ 133.912,96.** Por data: 12/10 279 / R$ 33.972,24; 13/10 90 / R$ 18.913,68; 14/10 96 / R$ 15.490,33; 15/10 103 / R$ 10.638,16; 16/10 82 / R$ 11.219,15; 17/10 2 / R$ 1.194,97; 18/10 2 / R$ 146,58; 19/10 326 / R$ 42.337,85. Somente ACL; não é previsão confirmada de entrada no caixa.
- **Vencidos ACL antes de 12/10, saldo positivo e sem data de pagamento: 3.946 | R$ 320.190,87 (23,38% do saldo aberto ACL de R$ 1.369.665,21).** Acima de 90 dias: 3.698 / R$ 286.635,36. Indicador operacional, sujeito à conciliação de baixas e abatimentos, não inadimplência contábil consolidada.

## Recomendações
1. Confirmar baixas e priorizar cobrança dos R$ 33.972,24 de 12/10; preparar cobrança de R$ 42.337,85 em 19/10.
2. Conciliar os R$ 286.635,36 com atraso superior a 90 dias antes de escalar cobranças.
3. Obter posição oficial de contas a pagar e checar defasagem da tabela `debx.PDV_Detalhes` antes de projetar caixa ou interpretar divergências.

**Fontes:** sessões read-only verificadas em SQL Server `hotel-finder`/`hotelfinder` e Oracle `conamore`/`TEST_ACL`; colunas essenciais validadas. Saldo de títulos = `TIT_VALORI - NVL(TIT_VALPAG,0)`, `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo.
