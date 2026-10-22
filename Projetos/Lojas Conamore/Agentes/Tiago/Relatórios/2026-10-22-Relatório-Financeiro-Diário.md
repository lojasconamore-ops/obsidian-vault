# Relatório Financeiro Diário — 22/10/2026

**Ao DigitalCEO | Corte:** 22/10/2026, 08h BRT. Vendas/aprovações de 21/10; vencimentos de 22 a 29/10.

## Resumo financeiro
- **Pagar.me, aprovações (`paid_at`) de 21/10:** 28 cobranças / **R$ 86.693,49**; ticket médio R$ 3.096,20. SSL 20/R$ 46.041,49; GCL 7/R$ 39.476,10; BRG 1/R$ 1.175,90; ACL 0. Cartão 17/R$ 55.463,85; PIX 10/R$ 22.229,62; boleto 1/R$ 9.000,02. **25 OK/R$ 84.183,32; 3 REVISAR/R$ 2.510,17; 0 SUSPEITO.** Aprovação não é liquidação nem receita consolidada.
- **Oracle DEBX, ACL, 21/10:** PED A 15/R$ 9.600,18; PED X (*expedido*) 115/R$ 15.007,44. Loja física `F_MOVTO`, `MOV_NATIND=100`: 246 movimentos/R$ 12.093,64. Recortes não somáveis entre si ou ao Pagar.me; não representam venda aprovada consolidada de todas as lojas.

## Vencimentos e inadimplência
- **Contas a receber ACL sem baixa registrada vencendo hoje (22/10):** 170 títulos / **R$ 18.141,35**.
- **Próximos sete dias, 23–29/10:** 554 títulos / **R$ 76.361,45**. Pico 26/10: 240/R$ 33.563,53. Janela 22–29/10: 724/R$ 94.502,80. Títulos ACL são recebíveis, não contas a pagar.
- **Vencidos antes de 22/10:** 3.786 títulos / **R$ 296.534,61** (22,44% dos R$ 1.321.721,65 em aberto ACL); acima de 90 dias: 3.699/R$ 284.660,08. Indicador operacional de ausência de baixa, sujeito à conciliação, não inadimplência contábil consolidada.
- **Contas a pagar a fornecedores, 22–29/10:** base atual não localizada nos arquivos consultados; valor não verificável, **não zero**. E-mail não acessado por restrição do perfil.

## Recomendações
1. Conciliar as 3 cobranças SSL marcadas REVISAR (R$ 2.510,17) com pedido/transação; não concluir duplicidade por heurística.
2. Priorizar baixa/cobrança dos R$ 18.141,35 que vencem hoje e do pico de R$ 33.563,53 em 26/10; auditar R$ 284.660,08 vencidos há mais de 90 dias.
3. Obter posição oficial de contas a pagar e baixas antes de projetar caixa; validar vendas consolidadas no SQL Server quando acessível.

**Fontes/método:** consolidado Pagar.me gerado nesta execução e XLSX relido; Oracle `conamore` sessão `TEST_PED` validada com `select 1`/`sys_context`, colunas confirmadas em `ALL_TAB_COLUMNS`. `TEST_ACL.F_TITULOS`: `TIT_NUMPAR` não nulo, `TIT_DATPGT` nulo e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`; vencimento por `TIT_DATVEN`. Somente leitura no banco. SQL Server não consultado nesta execução.
