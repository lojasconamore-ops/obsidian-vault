# Relatório Financeiro Diário — 08/11/2026

**Ao DigitalCEO | Corte:** 08/11/2026, 08h BRT. Vendas e cobranças aprovadas em 07/11; vencimentos de 08/11 a 14/11, inclusive.

## Resumo financeiro
- **Vendas aprovadas, SQL Server `hotel-finder`, 07/11:** `conamore.CAIXA_PERIODO_COM_ORIGEM`: **18 pedidos / R$ 25.333,14**, ticket médio **R$ 1.407,40**. Fonte atualizada até 07/11. A visão `debx.PDV_Detalhes` contém 1 aprovado/R$ 1.068,70 e 1 cancelado/R$ 680,50 no seu recorte distinto; não somar à visão principal.
- **Pagar.me v5, 07/11:** **8 cobranças aprovadas / R$ 21.052,31**, ticket médio **R$ 2.631,54**. SSL: 7/R$ 18.197,31; GCL: 1/R$ 2.855,00; ACL/BRG: nenhuma cobrança aprovada encontrada. Cartão: 5/R$ 13.534,84; PIX: 3/R$ 7.517,47. **6 OK/R$ 18.914,91; 2 SUSPEITO/R$ 2.137,40.** Cobrança aprovada não é liquidação bancária nem deve ser somada às vendas do SQL.
- **Oracle DEBX/ACL, 07/11:** PED status X (**expedido**) 94/R$ 10.834,53; A 15/R$ 8.730,51. Venda física (`F_MOVTO`, `MOV_NATIND=100`): 234 movimentos/R$ 10.749,83. PED e movimento físico são recortes distintos; não somar à receita SQL.

## Vencimentos e inadimplência
- **Recebíveis ACL sem baixa registrada, 08/11–14/11:** **692 parcelas / R$ 96.744,67**. 08/11: 82/R$ 10.983,43; **09/11: 280/R$ 39.114,78**; 10/11: 98/R$ 10.513,66; 11/11: 73/R$ 9.842,88; 12/11: 61/R$ 9.312,04; 13/11: 95/R$ 15.549,10; 14/11: 3/R$ 1.428,78. Indicador operacional de contas a receber, não contas a pagar nem recebimento confirmado.
- **Vencidos antes de 08/11, ACL:** **4.551 parcelas / R$ 427.031,50**, **29,53%** do saldo aberto de R$ 1.446.182,62. Acima de 90 dias: **3.701/R$ 283.971,69**. São títulos sem baixa no ERP, sujeitos à conciliação; não equivalem à inadimplência contábil consolidada.
- **Contas a pagar a fornecedores, 08/11–14/11:** base atual não localizada/confirmada; montante **não verificável (não zero)**. Saldo bancário indisponível. E-mail não acessado por restrição do perfil.

## Alertas e recomendações
1. **Pagar.me SSL:** dois pagamentos de R$ 1.068,70 da mesma cliente, em pedidos distintos (`ZDPGSK7B80` e `RZ46C77CEQ`), aprovados com ~15 minutos de intervalo: **R$ 2.137,40 sob revisão**, sem afirmar duplicidade. Conferir pedido, expedição e adquirente antes de qualquer ajuste/estorno.
2. **Crédito:** conciliar baixas dos R$ 427.031,50 vencidos; priorizar R$ 283.971,69 acima de 90 dias antes de cobrança/provisão.
3. **Caixa:** preparar recebimentos previstos de R$ 39.114,78 em 09/11; obter posição de fornecedores a pagar e saldo/extrato para calcular fluxo líquido. Não pressupor compensação.

**Fontes/método:** Pagar.me v5, consolidado gerado nesta execução; SQL Server `hotel-finder` (sessão, colunas e data máxima verificadas); Oracle `conamore` (sessão validada, colunas verificadas), `TEST_ACL.F_PEDVENDA`, `F_MOVTO`, `F_TITULOS`. Títulos: `TIT_NUMPAR` identificado, `TIT_DATPGT` nula e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`, janela [08/11,15/11). Consultas somente leitura; sem conciliação bancária.
