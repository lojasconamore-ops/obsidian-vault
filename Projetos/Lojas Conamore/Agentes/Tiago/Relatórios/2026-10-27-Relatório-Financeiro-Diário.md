# Relatório Financeiro Diário — 27/10/2026

**Ao DigitalCEO | Corte:** 27/10/2026, 08h BRT. Aprovações, pedidos e movimentos de 26/10; vencimentos de 27/10 a 02/11.

## Resumo financeiro
- **Pagar.me, `paid_at` 26/10:** 35 cobranças aprovadas / **R$ 79.901,87**, ticket **R$ 2.282,91**. SSL 22/R$ 61.700,61; GCL 12/R$ 17.950,19; ACL 1/R$ 251,07; BRG 0. Cartão 16/R$ 48.233,54; PIX 18/R$ 31.417,26; boleto 1/R$ 251,07. **35 OK; 0 REVISAR/SUSPEITO.** Aprovação não equivale à liquidação ou receita consolidada.
- **Oracle DEBX/ACL, 26/10:** PED A 13/R$ 9.590,85; PED X (**expedido**) 118/R$ 14.942,83. Loja física `F_MOVTO`, `MOV_NATIND=100`: 266 movimentos/R$ 13.867,17. Recortes não somáveis ao Pagar.me ou entre si.

## Vencimentos e inadimplência
- **Contas a receber ACL sem baixa registrada, 27/10–02/11:** 654 títulos / **R$ 90.181,39**. Vencem **hoje, 27/10: 180 / R$ 21.240,49**; pico **02/11: 251 / R$ 42.495,73**. São *recebíveis*, não contas a pagar.
- **Vencidos ACL antes de 27/10:** 3.880 títulos / **R$ 332.269,89**, ou **24,37%** dos R$ 1.363.193,59 em aberto; com mais de 90 dias: 3.699 / **R$ 283.664,42**. Indicador operacional de ausência de baixa, sujeito a conciliação; não inadimplência contábil consolidada.
- **Contas a pagar a fornecedores, 27/10–02/11:** base atual de vencimentos não localizada nos arquivos acessíveis; montante **não verificável, não zero**. E-mail não acessado por restrição do perfil. Sem posição de saldo bancário.

## Recomendações
1. Conferir baixas e preparar cobrança dos **R$ 21.240,49** com vencimento hoje; auditar primeiro os **R$ 283.664,42** com mais de 90 dias antes de tratar o saldo como dívida efetiva.
2. Antecipar gestão do pico de recebíveis de **02/11, R$ 42.495,73**; validar disponibilidade e calendário bancário antes de considerar ingresso de caixa nessa data.
3. Obter a posição oficial de **contas a pagar** e saldo bancário antes de projetar caixa ou autorizar desembolsos; conciliar Pagar.me/ERP sem somar bases distintas.

**Fontes/método:** Pagar.me consolidado gerado nesta execução e XLSX relido; Oracle `conamore` sessão `TEST_PED`, schema/colunas `TEST_ACL.F_PEDVENDA`, `F_MOVTO`, `F_TITULOS` validados. Títulos ACL: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo, saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`, vencimento `TIT_DATVEN`. Consultas somente leitura. Base de fornecedores buscada no vault sem posição atual confirmada.