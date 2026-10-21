# Relatório Financeiro Diário — 21/10/2026

**Ao DigitalCEO**  
**Corte:** 21/10/2026, 08h02 BRT. Ontem = 20/10; janela de vencimentos hoje 21/10 e sete dias seguintes 22–28/10.

## Resumo financeiro
- **Oracle DEBX, ACL, PED de 20/10:** status A 16 pedidos/R$ 9.410,89; status X (**expedido**) 109 pedidos/R$ 11.157,25. São recortes por status de pedido, não receita financeira consolidada.
- **Loja física ACL de 20/10:** `F_MOVTO`, `MOV_NATIND=100`: 244 movimentos/R$ 10.782,22. Não somar à PED como se fosse a mesma base. SQL Server de vendas aprovadas e Pagar.me não foram consultados nesta execução; não há total consolidado ou liquidação confirmada.

## Vencimentos e inadimplência
- **Títulos ACL sem baixa registrada vencendo hoje, 21/10:** 145/R$ 15.199,70.
- **Próximos sete dias, 22–28/10:** 545 títulos/R$ 73.675,96. Pico 26/10: 240/R$ 33.563,53. **Janela 21–28/10:** 690/R$ 88.875,66. Referem-se a títulos ACL (proxy de contas a receber), não a obrigações com fornecedores.
- **Vencidos antes de 21/10:** 3.786 títulos/R$ 296.597,55, **22,80%** dos R$ 1.300.732,44 em aberto ACL. Acima de 90 dias: 3.699/R$ 284.660,08. Indicador operacional sujeito a conciliação, não inadimplência contábil consolidada; apenas ACL.
- **Contas a pagar a fornecedores, 21–28/10:** posição atual não verificada; montante desconhecido, **não zero**. E-mail não acessado por restrição do perfil.

## Recomendações
1. Priorizar conciliação/cobrança dos R$ 15.199,70 de hoje e do pico de R$ 33.563,53 em 26/10.
2. Auditar os R$ 284.660,08 vencidos há mais de 90 dias, separando baixa pendente de inadimplência real.
3. Solicitar posição oficial de contas a pagar e extratos/baixas antes de projetar caixa; obter base consolidada de vendas aprovadas para substituir os recortes ACL.

**Fonte e método:** Oracle `conamore`, sessão `TEST_PED` validada com `select` e `sys_context`; esquema e colunas de `TEST_ACL.F_PEDVENDA`, `F_MOVTO`, `F_TITULOS` validados em `ALL_TAB_COLUMNS`. Filtro dos títulos: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`; janela por `TIT_DATVEN`. Consultas somente leitura. Tipos de títulos não foram conciliados com razão financeiro.