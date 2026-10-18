# Relatório Financeiro Diário — 18/10/2026

**Ao DigitalCEO**  
**Corte:** 18/10/2026, 08:01 BRT. Vendas/aprovações de 17/10; vencimentos hoje e de 19 a 25/10 (7 dias seguintes).

## Resumo financeiro
- **SQL Server, vendas aprovadas em 17/10:** 4 pedidos | **R$ 2.350,64** | ticket médio **R$ 587,66**. Fonte `conamore.CAIXA_PERIODO_COM_ORIGEM`, atualizada até 18/10, `Status_Pedido='Aprovado'`. Origem MAG: 2/R$ 719,50; origem não preenchida: 2/R$ 1.631,14. Escopo da fonte não equivale a toda a receita da empresa.
- **Pagar.me, `paid_at` 17/10:** 10 cobranças aprovadas | **R$ 5.822,72** | ticket médio **R$ 582,27**; 10 OK, 0 SUSPEITO, 0 REVISAR. ACL 8/R$ 4.191,58; SSL 2/R$ 1.631,14; GCL e BRG sem aprovações. Meio: PIX 10/R$ 5.822,72. Aprovação não é liquidação; não somar ao SQL.
- **Oracle DEBX ACL, recortes não somáveis de 17/10:** PED A 20/R$ 12.229,94; PED X **expedido** 79/R$ 10.160,84. Loja física `F_MOVTO`, `MOV_NATIND=100`: 192 movimentos/R$ 9.538,04. PED não é venda física.

## Vencimentos e inadimplência
- **Recebíveis ACL vencendo hoje, 18/10:** 71 títulos | **R$ 9.368,18** sem baixa registrada.
- **Recebíveis ACL nos próximos 7 dias, 19–25/10:** 642 títulos | **R$ 71.832,03**. Pico em 19/10: 317/R$ 34.109,98; 20/10: 90/R$ 9.894,87; 21/10: 78/R$ 9.672,92; 22/10: 81/R$ 8.577,76; 23/10: 74/R$ 9.397,75; 24/10: 1/R$ 133,13; 25/10: 1/R$ 45,62. Valores são **a receber, não contas a pagar**.
- **Vencidos ACL antes de 18/10:** 3.873 títulos | **R$ 305.911,60**, ou **22,96%** do saldo aberto ACL de R$ 1.332.167,83. Mais de 90 dias: 3.698/R$ 284.493,18. Indicador operacional de títulos sem baixa; conciliar pagamentos antes de classificá-lo como inadimplência contábil efetiva. Não consolida outras lojas.
- **Contas a pagar a fornecedores, 18–25/10:** base atual não localizada nos arquivos acessíveis; valores e vencimentos **não verificáveis, não zero**. E-mail não acessado por restrição do perfil.

## Recomendações
1. Conciliar baixas dos R$ 305.911,60 vencidos, começando pelos R$ 284.493,18 acima de 90 dias; separar atraso real de baixa pendente.
2. Conferir os R$ 9.368,18 de hoje e preparar cobrança preventiva dos R$ 34.109,98 de 19/10.
3. Obter posição oficial de contas a pagar antes de projetar caixa ou autorizar desembolsos com base neste relatório.

**Fontes:** Pagar.me consolidado gerado nesta execução e XLSX relido (janela `paid_at` 17/10); SQL Server `hotel-finder` com sessão, colunas e data máxima validadas; Oracle `conamore`/`TEST_PED` com sessão e colunas verificadas. Títulos `TEST_ACL.F_TITULOS`: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`. Somente leitura.
