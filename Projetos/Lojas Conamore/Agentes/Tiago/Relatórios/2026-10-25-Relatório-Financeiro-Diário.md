# Relatório Financeiro Diário — 25/10/2026

**Ao DigitalCEO | Corte:** 25/10/2026, 08h BRT. Aprovações e pedidos de 24/10; títulos de 25/10 a 01/11.

## Resumo financeiro
- **Pagar.me, `paid_at` 24/10:** 5 cobranças aprovadas / **R$ 16.771,78**, ticket R$ 3.354,36. SSL 5/R$ 16.771,78; ACL, GCL e BRG 0. PIX 2/R$ 9.452,84; cartão 3/R$ 7.318,94. **5 OK; 0 REVISAR/SUSPEITO.** Aprovação não equivale à liquidação nem à receita consolidada.
- **Oracle DEBX/ACL, 24/10:** PED A 15/R$ 7.647,28; PED X (**expedido**) 62/R$ 8.900,64. Loja física `F_MOVTO`, `MOV_NATIND=100`: 139 movimentos/R$ 8.821,32. Recortes não somáveis ao Pagar.me ou entre si.
- **SQL Server:** fontes `conamore.CAIXA_PERIODO_COM_ORIGEM` e `debx.PDV_Detalhes` atualizadas somente até **22/10**. Sem posição para vendas aprovadas de 24/10; não interpretar consulta vazia como venda zero.

## Vencimentos e inadimplência
- **Contas a receber ACL sem baixa registrada, hoje 25/10:** 58 títulos / **R$ 7.962,29**.
- **Próximos 7 dias, 26/10–01/11:** 539 títulos / **R$ 66.246,81**; pico **26/10: 236 / R$ 30.710,23**. Janela completa 25/10–01/11: 597 / R$ 74.209,10. São *recebíveis*, não contas a pagar.
- **Vencidos ACL antes de 25/10:** 3.855 títulos / **R$ 314.015,84**, ou **23,10%** dos R$ 1.359.588,16 em aberto; acima de 90 dias: 3.698 / **R$ 283.544,48**. Indicador de ausência de baixa, sujeito a conciliação; não inadimplência contábil consolidada.
- **Contas a pagar a fornecedores, 25/10–01/11:** base atual de vencimentos não localizada nos arquivos acessíveis; montante **não verificável, não zero**. E-mail não acessado por restrição do perfil.

## Recomendações
1. Confirmar baixas/cobranças de **R$ 7.962,29** hoje e preparar o pico de **R$ 30.710,23** amanhã; auditar primeiro os **R$ 283.544,48** com mais de 90 dias.
2. Obter posição oficial de contas a pagar e saldo bancário antes de projetar caixa ou autorizar desembolsos.
3. Verificar a defasagem do SQL Server (última venda 22/10) e conciliar Pagar.me com o ERP; não somar recortes.

**Fontes/método:** Pagar.me consolidado gerado nesta execução, XLSX relido; SQL Server `hotel-finder` sessão/colunas/data máxima verificadas; Oracle `conamore` sessão `TEST_PED` e colunas `TEST_ACL.F_PEDVENDA`, `F_MOVTO`, `F_TITULOS` validadas. Títulos ACL: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`; vencimento em `TIT_DATVEN`. Consultas somente leitura.
