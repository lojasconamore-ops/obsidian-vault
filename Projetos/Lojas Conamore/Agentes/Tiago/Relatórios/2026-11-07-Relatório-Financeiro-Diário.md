# Relatório Financeiro Diário — 07/11/2026

**Ao DigitalCEO | Corte:** 07/11/2026, 08h BRT. Vendas e cobranças aprovadas em 06/11; títulos com vencimento de 07/11 a 13/11, inclusive.

## Resumo financeiro
- **Vendas aprovadas, SQL Server `hotel-finder`, 06/11:** `conamore.CAIXA_PERIODO_COM_ORIGEM`, status Aprovado: **65 pedidos / R$ 97.365,69** (ticket médio R$ 1.497,93). A fonte está atualizada até 06/11. Outros 3 pedidos em Expedição/R$ 3.113,23 não foram somados. A visão `debx.PDV_Detalhes` registra 35 aprovados/R$ 70.376,47 em recorte distinto; não somar.
- **Pagar.me v5, 06/11:** **24 cobranças aprovadas / R$ 60.793,72** (ticket médio R$ 2.533,07): SSL 13/R$ 35.357,19; GCL 11/R$ 25.436,53; ACL/BRG sem cobranças aprovadas encontradas. Cartão 21/R$ 52.741,78; PIX 3/R$ 8.051,94. **20 OK/R$ 50.142,81; 4 REVISAR/R$ 10.650,91** (duas duplas de mesmo cliente com pedidos e valores diferentes, próximas no tempo; não é duplicidade confirmada). Cobrança aprovada não é liquidação bancária nem se soma às vendas do SQL.
- **Oracle DEBX/ACL, 06/11:** PED status A 37/R$ 28.980,38; X 142/R$ 14.680,32 (**X = expedido**); F 7/R$ 9.485,40. Venda física (`F_MOVTO`, `MOV_NATIND=100`): 323 movimentos/R$ 13.418,46. PED e venda física são recortes distintos, sem soma à receita acima.

## Vencimentos e inadimplência
- **Títulos ACL sem baixa registrada e saldo positivo, 07/11–13/11:** **750/R$ 115.062,52**. 07/11: 136/R$ 27.798,91; 08/11: 7/R$ 2.931,15; 09/11: 280/R$ 39.114,78; 10/11: 98/R$ 10.513,66; 11/11: 73/R$ 9.842,88; 12/11: 61/R$ 9.312,04; 13/11: 95/R$ 15.549,10. Indicador operacional de recebíveis; não representa contas a pagar ou liquidação confirmada.
- **Vencidos antes de 07/11, ACL:** **4.413/R$ 398.772,79**, **27,93%** do saldo em aberto de R$ 1.427.763,59. Acima de 90 dias: **3.701/R$ 283.971,69**. São títulos sem baixa no ERP, sujeitos a conciliação; não é inadimplência contábil consolidada.
- **Contas a pagar a fornecedores, 07/11–13/11:** posição atual não confirmada; valor não verificável (não zero). Saldo bancário indisponível. Não houve acesso a e-mail por restrição de perfil.

## Recomendações
1. Revisar manualmente as 4 cobranças Pagar.me sinalizadas, R$ 10.650,91, por cliente/pedido antes de qualquer ajuste ou estorno.
2. Conciliar baixas e cobrar títulos vencidos de R$ 398.772,79; priorizar R$ 283.971,69 acima de 90 dias.
3. Preparar recebimentos de R$ 27.798,91 em 07/11 e R$ 39.114,78 em 09/11, sem assumir compensação. Obter contas a pagar e extrato/saldo para projeção de caixa.

**Fontes/método:** Pagar.me v5 consolidado gerado nesta execução; SQL Server `hotel-finder` (sessão, colunas e frescor verificados); Oracle `conamore` (sessão `TEST_ACL` validada, colunas verificadas), `TEST_ACL.F_PEDVENDA`, `F_MOVTO`, `F_TITULOS`. Títulos: `TIT_NUMPAR` identificado, `TIT_DATPGT` nula, saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`, janela `[07/11,14/11)`. Consultas somente leitura, sem conciliação bancária.
