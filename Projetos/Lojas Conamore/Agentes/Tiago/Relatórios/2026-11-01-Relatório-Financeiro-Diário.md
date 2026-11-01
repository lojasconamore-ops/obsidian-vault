# Relatório Financeiro Diário — 01/11/2026

**Ao DigitalCEO | Corte:** 01/11/2026, manhã BRT. Vendas/aprovações de 31/10; vencimentos de 01/11 a 07/11, inclusive.

## Resumo financeiro
- **Pagar.me, 31/10, quatro lojas:** 2 cobranças aprovadas, **R$ 9.137,00**, ticket médio **R$ 4.568,50**; SSL 2/R$ 9.137,00 (PIX); ACL, GCL e BRG sem aprovações encontradas. 2 OK, 0 suspeitas, 0 revisar. Aprovações de cobrança não equivalem a venda consolidada nem a liquidação bancária.
- **Oracle DEBX/ACL, 31/10:** PED status A 9 pedidos / **R$ 2.940,95**; PED X 0; loja física (`F_MOVTO`, `MOV_NATIND=100`) 0 movimentos. PED e loja física são recortes distintos e não se somam; status A não deve ser equiparado a receita faturada.
- **SQL Server `hotel-finder`:** `conamore.CAIXA_PERIODO_COM_ORIGEM` e `debx.PDV_Detalhes` atualizadas somente até **29/10**. Sem registros de 31/10 nessas visões por defasagem; não interpretar como zero de vendas.

## Vencimentos e inadimplência
- **Contas a receber ACL sem baixa registrada, 01/11–07/11:** 587 títulos / **R$ 89.960,00**. Por dia: 01/11 3/R$ 551,40; **02/11 249/R$ 39.347,69**; 03/11 95/R$ 9.316,13; 04/11 69/R$ 10.273,07; 05/11 94/R$ 13.561,28; 06/11 76/R$ 14.983,42; 07/11 1/R$ 1.927,01. São recebíveis, não pagamentos a fornecedores.
- **Vencidos antes de 01/11:** 3.929 títulos / **R$ 331.145,46**, **24,76%** do saldo aberto ACL de R$ 1.337.169,06. Com mais de 90 dias: 3.699 / **R$ 283.664,42**. Indicador de ausência de baixa no ERP, sujeito à conciliação; não é inadimplência contábil consolidada.
- **Contas a pagar a fornecedores, 01/11–07/11:** posição atual não localizada/confirmada, valor **não verificável (não zero)**. Saldos bancários atuais não disponíveis. E-mail não acessado por restrição deste perfil.

## Recomendações
1. Conciliar baixas dos **R$ 331.145,46** vencidos, priorizando os **R$ 283.664,42** >90 dias antes de cobrança ou provisão.
2. Preparar cobrança/recebimento dos **R$ 39.347,69** previstos para 02/11; confirmar compensação efetiva no banco.
3. Obter a posição oficial de contas a pagar e saldos bancários; corrigir/validar a atualização do SQL Server antes de projetar caixa consolidado.

**Fontes/método:** Pagar.me v5, relatório consolidado gerado nesta execução para 31/10 (ACL/SSL/GCL/BRG); Oracle `conamore`, sessão validada (usuário retornado `TEST_PED`), objetos `TEST_ACL.F_PEDVENDA`, `F_MOVTO` e `F_TITULOS` com colunas verificadas; títulos com `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e saldo positivo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)`. SQL Server `hotel-finder` validado quanto à sessão, colunas e data máxima. Consultas somente leitura; não houve conciliação bancária.
