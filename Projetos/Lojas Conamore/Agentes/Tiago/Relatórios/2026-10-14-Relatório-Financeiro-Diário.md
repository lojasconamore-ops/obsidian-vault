# Relatório Financeiro Diário — 14/10/2026

**Ao DigitalCEO**  
**Corte:** 14/10/2026, 08:03 BRT. Vendas de 13/10; vencimentos de 14 a 21/10, inclusive (hoje + 7 dias).

## Resumo financeiro
- **Vendas aprovadas (SQL Server `conamore.CAIXA_PERIODO_COM_ORIGEM`, 13/10): 39 pedidos | R$ 59.269,42 | ticket médio R$ 1.519,73.** Fonte atualizada até 13/10; `Status_Pedido='Aprovado'`.
- **Pagar.me (`paid_at` 13/10): 30 cobranças aprovadas | R$ 41.743,12 | ticket médio R$ 1.391,44 | 30 OK, 0 SUSPEITO, 0 REVISAR.** SSL: 16 / R$ 30.799,13; BRG: 5 / R$ 8.036,23; ACL: 9 / R$ 2.907,76; GCL: 0. Cartão R$ 26.857,80; PIX R$ 14.885,32. Aprovação não é liquidação; não somar ao SQL.
- **DEBX/Oracle ACL (sobreposição não somável):** PED A 21 / R$ 11.096,28; PED X (expedido) 113 / R$ 10.888,79; PED P 1 / R$ 593,70; PED F 1 / R$ 361,40. Loja física (`F_MOVTO`, `MOV_NATIND=100`): 216 movimentos / R$ 9.674,30. PED não é venda física.

## Vencimentos e inadimplência
- **Contas a pagar a fornecedores (14–21/10): base atual não localizada nos arquivos acessíveis; valores e vencimentos não verificáveis, não zero.** E-mail não acessado por restrição do perfil.
- **Contas a receber ACL (14–21/10): 870 títulos | R$ 108.427,35**, saldo positivo e sem data de pagamento. Por vencimento: 14/10 R$ 21.410,36 (192); 15/10 R$ 10.299,33 (95); 16/10 R$ 8.937,61 (81); 17/10 R$ 1.194,97 (2); 18/10 R$ 146,58 (2); 19/10 R$ 42.337,85 (326); 20/10 R$ 9.240,72 (90); 21/10 R$ 14.859,93 (82). Não é entrada confirmada de caixa.
- **Vencidos ACL antes de 14/10:** 3.954 títulos | R$ 328.242,53 (24,20% do saldo aberto ACL de R$ 1.356.178,26). Mais de 90 dias: 3.699 / R$ 286.643,86. Indicador operacional sujeito a conciliação de baixas/abatimentos, não inadimplência contábil consolidada.

## Recomendações
1. Confirmar baixas e priorizar cobrança de R$ 21.410,36 vencendo hoje; preparar régua de R$ 42.337,85 para 19/10.
2. Conciliar R$ 286.643,86 acima de 90 dias antes de escalar cobrança.
3. Obter posição oficial de contas a pagar antes de projetar caixa.

**Fontes:** Pagar.me consolidado gerado nesta execução, XLSX relido; SQL Server `hotel-finder`/`hotelfinder` com sessão e colunas validadas; Oracle `conamore`/`TEST_ACL` com sessão e colunas validadas. Títulos: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo, saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`. Consultas somente leitura.
