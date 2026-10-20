# Relatório Financeiro Diário — 20/10/2026

**Ao DigitalCEO**  
**Corte:** 20/10/2026, 08h BRT. Vendas e aprovações de 19/10; vencimentos hoje e nos 7 dias seguintes (21–27/10).

## Resumo financeiro
- **SQL Server, vendas aprovadas em 19/10:** 40 pedidos | **R$ 65.898,37** | ticket médio **R$ 1.647,46**. `conamore.CAIXA_PERIODO_COM_ORIGEM`, fonte atualizada até 19/10; outros 4 pedidos em Expedição (R$ 4.009,37) não somados. Escopo da fonte não equivale a toda a receita da empresa.
- **Pagar.me, `paid_at` 19/10:** 29 cobranças aprovadas | **R$ 58.015,68** | ticket médio **R$ 2.000,54**. ACL 4/R$ 1.646,68; SSL 18/R$ 49.758,39; BRG 7/R$ 6.610,61; GCL 0. PIX 11/R$ 16.053,13; cartão 18/R$ 41.962,55. **27 OK/R$ 52.996,28; 2 REVISAR/R$ 5.019,40**, ambas SSL; revisão heurística, não duplicidade comprovada. Aprovação não é liquidação e não se soma ao SQL.
- **Oracle DEBX ACL, recortes não somáveis de 19/10:** PED A 15/R$ 8.648,10; PED X (**expedido**) 99/R$ 11.107,95; venda física `F_MOVTO`/`MOV_NATIND=100`: 233 movimentos/R$ 10.189,66. PED não é venda física.

## Vencimentos e inadimplência
- **Contas a receber ACL vencendo hoje (20/10):** 163 títulos | **R$ 35.872,43** sem baixa registrada.
- **Contas a receber ACL nos próximos 7 dias (21–27/10):** 557 títulos | **R$ 71.232,10**. Pico em 26/10: 240 títulos/R$ 33.563,53. Janela completa 20–27/10: 720/R$ 107.104,53. *São recebíveis, não contas a pagar.*
- **Vencidos ACL antes de 20/10:** 3.865 títulos | **R$ 308.495,52** (**23,23%** dos R$ 1.327.725,28 em aberto). Mais de 90 dias: 3.699/R$ 284.660,08. Indicador operacional de ausência de baixa, sujeito à conciliação; não é inadimplência contábil consolidada nem cobre outras lojas.
- **Contas a pagar a fornecedores, 20–27/10:** base atual não localizada nos arquivos acessíveis; montante e vencimentos **não verificáveis, não zero**. E-mail não acessado por restrição do perfil. O export de títulos localizado é de junho e não foi usado como posição atual.

## Recomendações
1. Conciliar as 2 cobranças SSL marcadas REVISAR (R$ 5.019,40) com pedido e transação antes de considerar duplicidade.
2. Priorizar as baixas/cobranças de R$ 35.872,43 que vencem hoje e dos R$ 33.563,53 de 26/10; validar os R$ 284.660,08 acima de 90 dias.
3. Obter a posição oficial de contas a pagar e baixas antes de projetar caixa ou autorizar desembolsos com este relatório.

**Fontes:** Pagar.me consolidado gerado nesta execução e XLSX relido (janela `paid_at` 19/10); SQL Server `hotel-finder` com sessão, colunas e data máxima verificadas; Oracle `conamore`/`TEST_ACL` com sessão e colunas verificadas. Títulos `TEST_ACL.F_TITULOS`: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`. Consultas somente leitura.
