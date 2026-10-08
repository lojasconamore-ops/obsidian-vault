# Relatório Financeiro Diário — 08/10/2026

**Ao DigitalCEO**  
**Corte:** 08/10/2026, 08:04 BRT. Vendas/aprovações: 07/10; vencimentos: 08–15/10, inclusive.

## Resumo financeiro
- **SQL Server `conamore.CAIXA_PERIODO_COM_ORIGEM`: 40 pedidos aprovados | R$ 74.407,22 | ticket médio R$ 1.860,18.** Fonte atualizada até 07/10. Origem MAG: 17 / R$ 15.853,10; sem origem: 23 / R$ 58.554,12. Outros 3 pedidos em Expedição / R$ 530,64 não integram os aprovados.
- **Pagar.me `paid_at` de 07/10: 33 cobranças aprovadas | R$ 45.207,19 | ticket R$ 1.369,91; 33 OK, 0 SUSPEITO, 0 REVISAR.** SSL 23 / R$ 32.729,35; BRG 3 / R$ 7.395,90; ACL 7 / R$ 5.081,94; GCL 0. Cartão 16 / R$ 24.246,40; PIX 16 / R$ 19.427,39; boleto 1 / R$ 1.533,40. Não somar à venda SQL: universos/estágios distintos; aprovação não comprova liquidação.
- **Sobreposição DEBX/Oracle ACL, não somar:** PED X (expedido) 143 / R$ 15.573,07; A 16 / R$ 11.208,08; F 1 / R$ 80,24. Loja física `F_MOVTO`, `MOV_NATIND=100`: 313 movimentos / R$ 14.988,93. PED não é venda física.
- **Alerta de classificação:** `debx.PDV_Detalhes` registra 35 pedidos Cancelado / R$ 188.170,90 em 07/10; este é agregado bruto por status, **não perda financeira confirmada**. Conferir concentração/causas e reconciliar com os 40 aprovados na fonte principal, sem somar universos.

## Vencimentos e inadimplência
- **Contas a pagar a fornecedores (08–15/10): base atual não localizada nos arquivos acessíveis.** Valor e datas não disponíveis, não zero. E-mail não acessado por restrição do perfil.
- **Contas a receber ACL, títulos com parcela e sem data de pagamento (08–15/10): 852 | R$ 116.730,56 de saldo.** 08/10: 180 / R$ 20.977,06; 09/10: 93 / R$ 11.551,26; 10/10: 4 / R$ 2.472,85; 11/10: 4 / R$ 5.530,38; 12/10: 283 / R$ 33.756,84; 13/10: 89 / R$ 16.313,68; 14/10: 96 / R$ 15.490,33; 15/10: 103 / R$ 10.638,16. Não inclui outras lojas nem comprova recebimento futuro.
- **Vencidos ACL, sem data de pagamento antes de 08/10: 3.770 | R$ 295.786,35**, 22,13% do saldo aberto bruto ACL de R$ 1.336.674,90. Acima de 90 dias: 3.697 | R$ 286.600,13. Indicador operacional, não inadimplência contábil consolidada; exige conciliação de baixas/abatimentos.

## Recomendações
1. Conciliar baixas e cobrar os R$ 20.977,06 vencendo hoje; preparar régua para R$ 33.756,84 em 12/10.
2. Auditar os R$ 286.600,13 vencidos há mais de 90 dias antes de escalonar cobrança; confirmar saldo real.
3. Investigar o agregado Cancelado de R$ 188.170,90 por pedido/motivo, sem tratá-lo como receita perdida.
4. Obter a posição oficial de contas a pagar para projeção de caixa; não inferir ausência de obrigações pela falta de base.

## Fontes e limites
- SQL Server `hotel-finder`: sessão, colunas e atualização verificadas; `Status_Pedido='Aprovado'` como venda aprovada.
- Pagar.me v5: consolidado gerado nesta execução, janela `paid_at` 07/10; XLSX relido e agrupado.
- Oracle `conamore`: sessão `TEST_ACL` e colunas verificadas; `F_TITULOS` ACL com `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo, `TIT_VALORI` positivo; saldo = `TIT_VALORI - NVL(TIT_VALPAG,0)`. Valores bruto e saldo coincidem no recorte de vencimentos e vencidos. PED e loja física separados.
- Não há posição atual de contas a pagar confirmada nesta execução.
