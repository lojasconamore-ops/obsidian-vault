# Relatório Financeiro Diário — 31/10/2026

**Ao DigitalCEO | Corte:** 31/10/2026, 08h BRT. Operações de 30/10; recebíveis de 31/10 a 06/11 (7 dias corridos, hoje incluso).

## Resumo financeiro
- **Oracle DEBX/ACL, 30/10:** PED A 11 pedidos / **R$ 5.799,43**; PED X (**expedido**) 104 / **R$ 12.009,79**; PED F 1 / R$ 80,00. Loja física (`F_MOVTO`, `MOV_NATIND=100`): 221 movimentos / **R$ 10.817,37**. PED e loja física são recortes distintos e não devem ser somados como receita consolidada.
- **SQL Server `hotel-finder`:** último `Data_Venda` em 29/10 nas visões `conamore.CAIXA_PERIODO_COM_ORIGEM` e `debx.PDV_Detalhes`; **30/10 sem dados nessas visões**. Não interpretar como vendas zeradas. PED e loja física acima são a fonte disponível para o dia anterior.

## Vencimentos e inadimplência
- **Contas a receber ACL sem baixa registrada, 31/10–06/11:** 664 títulos / **R$ 94.213,44**. 31/10: 81/R$ 7.367,59; 01/11: 1/R$ 199,80; **02/11: 248/R$ 38.512,15**; 03/11: 95/R$ 9.316,13; 04/11: 69/R$ 10.273,07; 05/11: 94/R$ 13.561,28; 06/11: 76/R$ 14.983,42. São *recebíveis*, não pagamentos a fornecedores.
- **Vencidos antes de 31/10:** 3.848 títulos / **R$ 323.777,87**, **24,28%** do saldo aberto ACL de R$ 1.333.372,38. Vencidos há mais de 90 dias: 3.699 / **R$ 283.664,42**. Indicador de ausência de baixa, sujeito a conciliação; não inadimplência contábil consolidada.
- **Contas a pagar a fornecedores (31/10–06/11):** posição atual de vencimentos não confirmada nesta execução; montante **não verificável (não zero)**. Sem saldo bancário atualizado para projeção líquida de caixa. E-mail não acessado por restrição do perfil.

## Recomendações
1. Conciliar baixas dos **R$ 7.367,59** que vencem hoje e validar os **R$ 283.664,42** com mais de 90 dias antes de acionar cobrança ou classificar perda.
2. Preparar carteira do pico de **02/11 (R$ 38.512,15)** e confirmar calendário bancário/compensação antes de projetar entrada no caixa.
3. Obter contas a pagar e saldos bancários oficiais; cobrar atualização do espelho SQL de 30/10 e não somar PED com venda física.

**Fontes/método:** Oracle `conamore`/`TEST_ACL`: sessão validada (`select 1`/`sys_context`), schema e colunas confirmados; `F_PEDVENDA` por `PDV_DATPED`/`PDV_STATUS`, `F_MOVTO` por `MOV_DATMOV`/`MOV_NATIND=100`, `F_TITULOS` com `TIT_NUMPAR` não nulo, `TIT_DATPGT` nulo e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`, janela por `TIT_DATVEN`. SQL Server: sessão `hotel-finder`/`hotelfinder`, colunas e atualização verificadas. Somente leitura nas fontes de dados.
