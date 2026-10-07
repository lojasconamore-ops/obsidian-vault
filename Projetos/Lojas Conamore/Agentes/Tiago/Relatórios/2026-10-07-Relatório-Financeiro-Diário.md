# Relatório Financeiro Diário — 07/10/2026

**Ao DigitalCEO**  
**Período:** vendas/aprovações em 06/10/2026; vencimentos de 07/10 a 14/10/2026 (BRT, hoje + 7 dias).

## Resumo financeiro
- **Vendas aprovadas, SQL Server `conamore.CAIXA_PERIODO_COM_ORIGEM`: 46 pedidos | R$ 278.250,26 | ticket R$ 6.048,92.** Base atualizada até 06/10. Um pedido, `0109123`, responde por R$ 193.044,86 (69,38%); consta como Aprovado também em `debx.PDV_Detalhes`. Origem MAG: 27 / R$ 19.283,50; sem origem informada: 19 / R$ 258.966,76. Venda aprovada não é caixa liquidado.
- **Pagar.me, cobranças aprovadas em 06/10 (`paid_at`): 20 | R$ 38.825,43 | ticket R$ 1.941,27.** ACL: 6 / R$ 8.691,98; SSL: 14 / R$ 30.133,45; GCL/BRG: 0. PIX: 8 / R$ 11.773,86; cartão: 12 / R$ 27.051,57. 18 OK / R$ 31.145,40; **2 REVISAR / R$ 7.680,03**; 0 SUSPEITO. Pedidos sinalizados: `493OI2KSO7` (R$ 3.238,93) e `L6VRFX3A5R` (R$ 4.441,10). Não somar Pagar.me à venda SQL: universos e estágios diferentes. Cobrança aprovada não prova liquidação financeira.
- **Oracle/DEBX ACL (não somar):** PED X/expedido 110 / R$ 10.039,24; A 26 / R$ 50.060,22; F 3 / R$ 28.357,70. Loja física `F_MOVTO`, `MOV_NATIND=100`: 230 movimentos / R$ 9.960,44. PED não é venda física.

## Vencimentos e inadimplência
- **Contas a pagar a fornecedores, 07–14/10:** base atual não localizada nos arquivos locais; posição, valor e datas **não disponíveis, não zero**. E-mail não acessado por restrição de perfil.
- **Contas a receber ACL, títulos sem data de pagamento, 07–14/10:** **804 | R$ 114.820,18**. 07/10: 161 / R$ 18.126,89; 08/10: 74 / R$ 12.411,57; 09/10: 93 / R$ 10.717,64; 10/10: 4 / R$ 2.472,85; 11/10: 4 / R$ 5.530,38; 12/10: 283 / **R$ 33.756,84**; 13/10: 89 / R$ 16.313,68; 14/10: 96 / R$ 15.490,33. Não é previsão de liquidação e não inclui outras lojas.
- **Vencidos ACL sem data de pagamento antes de 07/10:** **3.804 | R$ 298.635,16 (22,79% do bruto aberto ACL, R$ 1.310.096,38)**. Mais de 90 dias: **3.697 | R$ 286.600,13**. Indicador operacional, não inadimplência contábil consolidada; baixas/abatimentos exigem conciliação.

## Recomendações
1. Confirmar baixas dos **R$ 18.126,89** vencendo hoje; antecipar cobrança dos **R$ 33.756,84** de 12/10.
2. Conciliar os **R$ 286.600,13** vencidos há mais de 90 dias antes de priorizar cobrança.
3. Revisar as **2 cobranças Pagar.me / R$ 7.680,03** por pedido e cliente; não classificar como duplicidade sem confirmação.
4. Validar a origem e a realização do pedido **R$ 193.044,86**; obter a posição oficial de contas a pagar para projetar caixa.

## Fontes e limites
- SQL Server `hotel-finder`: sessão e colunas verificadas; agregados de `Status_Pedido='Aprovado'` em 06/10.
- Pagar.me v5: consolidado desta execução, janela `paid_at` de 06/10, XLSX relido para somas e flags.
- Oracle `conamore`: sessão `TEST_ACL` e colunas verificadas; `F_TITULOS` ACL com `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e `TIT_VALORI` positivo. Valor bruto coincide com saldo calculado (`TIT_VALORI-TIT_VALPAG`) nesse subconjunto. PED e loja física separados.
- Não há posição atual de contas a pagar confirmada nesta execução.
