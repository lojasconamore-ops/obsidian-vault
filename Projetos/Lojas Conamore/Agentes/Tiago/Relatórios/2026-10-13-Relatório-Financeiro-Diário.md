# Relatório Financeiro Diário — 13/10/2026

**Ao DigitalCEO**  
**Corte:** 13/10/2026, 08:04 BRT. Vendas de 12/10; vencimentos de 13 a 20/10, inclusive (hoje + 7 dias).

## Resumo financeiro
- **Vendas aprovadas (SQL Server `conamore.CAIXA_PERIODO_COM_ORIGEM`, 12/10): 20 pedidos | R$ 13.686,33 | ticket médio R$ 684,32.** Fonte atualizada até 12/10; `Status_Pedido='Aprovado'`.
- **Pagar.me (`paid_at` 12/10): 7 cobranças aprovadas | R$ 5.141,98 | ticket médio R$ 734,57 | 7 OK, 0 SUSPEITO, 0 REVISAR.** ACL: 5 PIX / R$ 1.549,63; SSL: 2 cartão / R$ 3.592,35; GCL/BRG: 0. Aprovação não é liquidação nem pode ser somada às vendas SQL.
- **DEBX/Oracle ACL (sobreposição não somável):** PED A 15 / R$ 9.299,50; PED X não registrado em 12/10; loja física (`F_MOVTO`, `MOV_NATIND=100`) 0 movimentos. PED não equivale à venda física. Espelho `debx.PDV_Detalhes` atualizado só até 10/10; ausência de 12/10 é defasagem, não zero.

## Alertas de vencimentos e inadimplência
- **Contas a pagar a fornecedores (13–20/10): base atual não localizada nos arquivos acessíveis; montante e vencimentos não verificáveis, não zero.** E-mail não acessado por restrição do perfil.
- **Contas a receber ACL (13–20/10): 796 títulos | R$ 110.731,07**, saldo positivo e sem data de pagamento. Por vencimento: 13/10 94 / R$ 20.275,80; 14/10 97 / R$ 15.677,84; 15/10 103 / R$ 10.638,16; 16/10 82 / R$ 11.219,15; 17/10 2 / R$ 1.194,97; 18/10 2 / R$ 146,58; 19/10 326 / R$ 42.337,85; 20/10 90 / R$ 9.240,72. Não equivale a entrada confirmada de caixa.
- **Vencidos ACL antes de 13/10:** 4.225 títulos | R$ 354.163,11 (25,67% do saldo aberto ACL de R$ 1.379.759,19). Mais de 90 dias: 3.698 / R$ 286.635,36. Indicador operacional sujeito a conciliação de baixas/abatimentos, não inadimplência contábil consolidada.

## Recomendações
1. Confirmar baixas dos R$ 20.275,80 vencendo hoje e priorizar cobrança; preparar régua de R$ 42.337,85 para 19/10.
2. Conciliar os R$ 286.635,36 acima de 90 dias antes de escalar cobrança.
3. Obter posição oficial de contas a pagar e conferir atraso do espelho `debx.PDV_Detalhes` antes de projetar caixa.

**Fontes:** Pagar.me consolidado gerado nesta execução e XLSX relido; SQL Server `hotel-finder`/`hotelfinder` com sessão e colunas validadas; Oracle `conamore`/`TEST_ACL` com sessão e colunas validadas. Títulos: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo, saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`. Consultas somente leitura.
