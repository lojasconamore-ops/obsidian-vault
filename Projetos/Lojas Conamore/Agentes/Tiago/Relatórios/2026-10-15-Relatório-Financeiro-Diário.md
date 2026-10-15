# Relatório Financeiro Diário — 15/10/2026

**Ao DigitalCEO**  
**Corte:** 15/10/2026, 08:02 BRT. Vendas de 14/10; vencimentos de 15 a 22/10, inclusive (hoje + 7 dias).

## Resumo financeiro
- **Vendas aprovadas (SQL Server `conamore.CAIXA_PERIODO_COM_ORIGEM`, 14/10): 49 pedidos | R$ 164.850,25 | ticket médio R$ 3.364,29.** Fonte atualizada até 14/10; `Status_Pedido='Aprovado'`. Outros 4 pedidos em `Expedição` somam R$ 4.106,10 e não foram somados às aprovações.
- **Pagar.me (`paid_at` 14/10): 28 cobranças aprovadas | R$ 98.139,53 | ticket médio R$ 3.504,98 | 28 OK, 0 SUSPEITO, 0 REVISAR.** BRG 11 / R$ 69.143,10; SSL 11 / R$ 24.015,25; ACL 6 / R$ 4.981,18; GCL 0. PIX 18 / R$ 71.746,97; cartão 9 / R$ 17.713,00; boleto 1 / R$ 8.679,56. Aprovação não é liquidação; não somar ao SQL.
- **DEBX/Oracle ACL (sobreposição não somável):** PED A 17 / R$ 33.604,93; PED X (expedido) 98 / R$ 8.662,21; PED N 1 / R$ 4.000,00. Loja física (`F_MOVTO`, `MOV_NATIND=100`): 224 movimentos / R$ 8.482,05. PED não é venda física.

## Vencimentos e inadimplência
- **Contas a pagar a fornecedores (15–22/10): base atual não localizada nos arquivos acessíveis; montante e vencimentos não verificáveis, não zero.** E-mail não acessado por restrição do perfil.
- **Contas a receber ACL (15–22/10): 839 títulos | R$ 105.592,24**, saldo positivo e sem data de pagamento. Por vencimento: 15/10 174 / R$ 19.613,49; 16/10 81 / R$ 8.937,61; 17/10 2 / R$ 1.194,97; 18/10 2 / R$ 146,58; 19/10 326 / R$ 42.337,85; 20/10 91 / R$ 9.924,05; 21/10 82 / R$ 14.859,93; 22/10 81 / R$ 8.577,76. Não equivale a entrada confirmada de caixa.
- **Vencidos ACL antes de 15/10:** 4.001 títulos | R$ 335.103,37 (24,58% do saldo aberto ACL de R$ 1.363.135,29). Mais de 90 dias: 3.698 / R$ 284.493,18. Indicador operacional sujeito a conciliação de baixas/abatimentos, não inadimplência contábil consolidada.

## Recomendações
1. Conferir baixas dos R$ 19.613,49 vencendo hoje e preparar cobrança preventiva dos R$ 42.337,85 para 19/10.
2. Conciliar R$ 284.493,18 acima de 90 dias antes de escalar cobrança.
3. Obter posição oficial de contas a pagar antes de projetar caixa.

**Fontes:** Pagar.me consolidado gerado nesta execução, XLSX relido; SQL Server `hotel-finder`/`hotelfinder` com sessão, colunas e atualização validadas; Oracle `conamore`/`TEST_ACL` com sessão e colunas validadas. Títulos: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo, saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`. Consultas somente leitura.
