# Relatório Financeiro Diário — 11/10/2026

**Ao DigitalCEO**  
**Corte:** 11/10/2026, 08:02 BRT. Vendas/aprovações de 10/10; vencimentos de 11 a 18/10, inclusive.

## Resumo financeiro
- **Vendas aprovadas (SQL Server `conamore.CAIXA_PERIODO_COM_ORIGEM`, 10/10): 7 pedidos | R$ 2.879,78 | ticket médio R$ 411,40.** Fonte atualizada até 10/10; filtro `Status_Pedido='Aprovado'`.
- **Pagar.me, `paid_at` de 10/10: 1 cobrança aprovada | R$ 203,52 | PIX ACL | 1 OK, 0 SUSPEITO, 0 REVISAR.** Aprovação não é liquidação; não somar às vendas SQL por diferença de universo/estágio.
- **DEBX/Oracle ACL, sobreposição não somável:** PED X (expedido) 118 / R$ 14.835,35; PED A 8 / R$ 3.436,88; loja física `F_MOVTO`, `MOV_NATIND=100`: 276 movimentos / R$ 14.191,32. PED não é venda física. `debx.PDV_Detalhes` registrou 6 pedidos em status Cancelado / R$ 9.006,10; não tratar automaticamente como perda ou abater da fonte aprovada sem conciliação por pedido.

## Vencimentos e inadimplência
- **Contas a pagar a fornecedores (11–18/10): base atual não localizada** nos arquivos acessíveis; valor e vencimentos não verificáveis, não zero. E-mail não acessado por restrição do perfil.
- **Contas a receber ACL, títulos parcelados sem data de pagamento e saldo positivo (11–18/10): 741 | R$ 103.233,93.** 11/10: 91 / R$ 13.052,25; 12/10: 275 / R$ 32.578,81; 13/10: 90 / R$ 18.913,68; 14/10: 96 / R$ 15.490,33; 15/10: 103 / R$ 10.638,16; 16/10: 82 / R$ 11.219,15; 17/10: 2 / R$ 1.194,97; 18/10: 2 / R$ 146,58. Somente ACL; não implica recebimento futuro confirmado.
- **Vencidos ACL antes de 11/10, com saldo positivo e sem data de pagamento: 3.855 | R$ 307.138,62**, ou 22,58% do saldo aberto bruto ACL de R$ 1.360.285,41. Mais de 90 dias: 3.697 / R$ 286.600,13. Proxy operacional de inadimplência, sujeito à conciliação de baixas/abatimentos; não é indicador contábil consolidado.

## Recomendações
1. Priorizar cobrança/conciliação dos R$ 13.052,25 com vencimento em 11/10 e preparar a régua para 12/10 (R$ 32.578,81).
2. Validar baixas e saldo real dos R$ 286.600,13 com atraso acima de 90 dias antes de escalonar cobranças.
3. Obter posição oficial de contas a pagar e conciliar, por pedido, os 6 cancelados no overlay DEBX; não projetar caixa nem perda sem essas validações.

## Fontes e limites
- SQL Server `hotel-finder`: sessão `hotelfinder`, colunas confirmadas e máxima `Data_Venda` de 10/10 nas duas tabelas consultadas.
- Pagar.me: relatório consolidado gerado nesta execução; XLSX relido, janela interna `paid_at` de 10/10.
- Oracle `conamore`: sessão `TEST_ACL`, colunas verificadas; `TEST_ACL.F_TITULOS`, `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e saldo `TIT_VALORI - NVL(TIT_VALPAG,0)>0`; PED e loja física separados.
- Sem base confirmada de contas a pagar fornecedores; indicador de inadimplência limitado aos títulos ACL sem baixa registrada.
