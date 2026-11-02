# Relatório Financeiro Diário — 02/11/2026

**Ao DigitalCEO | Corte:** 02/11/2026, 08h03 BRT. Vendas de 01/11; aprovações Pagar.me de 30/10 a 01/11 (janela de segunda-feira); recebíveis de 02/11 a 08/11, inclusive.

## Resumo financeiro
- **SQL Server `hotel-finder`, 01/11:** `conamore.CAIXA_PERIODO_COM_ORIGEM`, status Aprovado: **9 pedidos / R$ 7.498,21**. Visão atualizada até 01/11. A visão bruta `debx.PDV_Detalhes` está defasada (até 31/10), portanto não serve para validar o dia 01/11.
- **Pagar.me, 01/11:** **3 cobranças aprovadas / R$ 7.315,88**, todas SSL (2 PIX/R$ 4.863,88; 1 cartão/R$ 2.452,00); 3 OK, 0 suspeitas/revisar. Aprovação de cobrança não é liquidação bancária nem deve ser somada ao valor de pedidos do SQL.
- **Pagar.me, janela 30/10–01/11:** **48 cobranças / R$ 114.342,76**; SSL 26/R$ 71.066,64; GCL 22/R$ 43.276,12; ACL e BRG sem aprovações encontradas. PIX 28/R$ 66.992,35; cartão 19/R$ 46.114,42; boleto 1/R$ 1.235,99. **2 suspeitas + 2 revisar, R$ 3.265,42**, todas GCL em 30/10 (exposição para análise; não é duplicidade confirmada).
- **Oracle DEBX/ACL, 01/11:** PED status A: **8 pedidos / R$ 3.407,56**; movimentação de loja física (`MOV_NATIND=100`): **0**. PED é recorte distinto da venda física e não é receita consolidada.

## Vencimentos e inadimplência
- **Contas a receber ACL sem baixa registrada, 02/11–08/11:** **589 títulos / R$ 90.831,19**. 02/11: 250/R$ 39.628,39; 03/11: 95/R$ 9.316,13; 04/11: 69/R$ 10.273,07; 05/11: 94/R$ 13.561,28; 06/11: 76/R$ 14.983,42; 07/11: 1/R$ 1.927,01; 08/11: 4/R$ 1.141,89. Recebíveis, **não** contas a pagar.
- **Vencidos antes de 02/11:** **3.932 títulos / R$ 331.696,86**, **24,76%** do saldo em aberto ACL (R$ 1.339.803,38). Mais de 90 dias: **3.700 / R$ 283.720,15**. Indicador de títulos sem baixa no ERP, sujeito à conciliação; não é inadimplência contábil consolidada.
- **Contas a pagar a fornecedores (02/11–08/11):** base atual não localizada/confirmada; valor **não verificável (não zero)**. Sem saldo bancário atual disponível. E-mail não acessado por restrição do perfil.

## Recomendações
1. Conciliar títulos vencidos, priorizando **R$ 283.720,15** com mais de 90 dias antes de cobrança/provisão; checar baixas efetivas.
2. Preparar recebimento dos **R$ 39.628,39** previstos para hoje (02/11), sem assumir compensação bancária no próprio dia.
3. Revisar as **4 cobranças GCL de R$ 3.265,42** sinalizadas no Pagar.me em 30/10 antes de qualquer estorno; obter posição oficial de contas a pagar e saldos bancários para projetar caixa.

**Fontes/método:** Pagar.me v5, consolidado gerado nesta execução; SQL Server `hotel-finder`, sessão/colunas/frescor validados; Oracle `conamore`, sessão `TEST_ACL` e colunas confirmadas, `TEST_ACL.F_PEDVENDA`, `F_MOVTO`, `F_TITULOS` (parcela identificada, `TIT_DATPGT` nula, saldo positivo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)`). Somente leitura nas fontes operacionais; nenhuma conciliação bancária efetuada.
