# Relatório Financeiro Diário — 17/10/2026

**Ao DigitalCEO**  
**Corte:** 17/10/2026, 08:01 BRT. Vendas de 16/10; vencimentos de 17 a 24/10, inclusive.

## Resumo financeiro
- **Vendas aprovadas SQL Server (16/10): 39 pedidos | R$ 196.727,25 | ticket médio R$ 5.044,29.** Fonte `conamore.CAIXA_PERIODO_COM_ORIGEM`, atualizada até 16/10, `Status_Pedido='Aprovado'`. Outros 4 pedidos em Expedição: R$ 25.803,10; não somados.
- **Pagar.me (`paid_at` 16/10): 27 aprovações | R$ 138.197,16 | ticket médio R$ 5.118,41; 25 OK e 2 REVISAR.** SSL 8/R$ 75.344,75; BRG 10/R$ 59.759,49; ACL 9/R$ 3.092,92; GCL 0. Cartão 10/R$ 117.265,91; PIX 15/R$ 19.464,60; boleto 2/R$ 1.466,65. As duas marcações BRG totalizam R$ 12.974,56; são revisão heurística, não duplicidade comprovada. Aprovação não é liquidação e não se soma ao SQL.
- **Oracle DEBX ACL (sobreposição não somável, 16/10):** PED A 12/R$ 7.026,76; PED X (expedido) 124/R$ 16.348,76; PED F 1/R$ 1.304,00. Loja física `F_MOVTO`, `MOV_NATIND=100`: 269 movimentos/R$ 14.182,64. PED não é venda física.

## Vencimentos e inadimplência
- **Contas a receber ACL, 17–24/10:** 734 títulos abertos, **R$ 82.223,73**. 17/10: 91/R$ 9.983,33; 18/10: 4/R$ 646,19; 19/10: 315/R$ 33.917,78; 20/10: 90/R$ 9.894,87; 21/10: 78/R$ 9.672,92; 22/10: 81/R$ 8.577,76; 23/10: 74/R$ 9.397,75; 24/10: 1/R$ 133,13. Saldo sem data de pagamento; não representa recebimento confirmado.
- **Vencidos ACL antes de 17/10:** 3.779 títulos/R$ 295.629,57 (**22,57%** do saldo aberto ACL de R$ 1.310.068,82). Mais de 90 dias: 3.698/R$ 284.493,18. Indicador operacional sujeito à conciliação das baixas, não inadimplência contábil consolidada.
- **Contas a pagar a fornecedores, 17–24/10:** base atual não localizada nos arquivos acessíveis; montante e vencimentos **não verificáveis, não zero**. E-mail não acessado por restrição do perfil.

## Recomendações
1. Conciliar as 2 cobranças BRG marcadas REVISAR (R$ 12.974,56) antes de tratar como duplicidade ou receita limpa.
2. Conferir baixas dos R$ 9.983,33 de hoje e preparar cobrança preventiva dos R$ 33.917,78 de 19/10.
3. Conciliar os R$ 284.493,18 acima de 90 dias e obter posição oficial de contas a pagar antes de projetar caixa.

**Fontes:** Pagar.me consolidado gerado e XLSX relido nesta execução; SQL Server `hotel-finder` com sessão, colunas e data máxima verificadas; Oracle `conamore`/`TEST_PED` com sessão e colunas verificadas. Títulos `TEST_ACL.F_TITULOS`: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo, saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`. Consultas somente leitura.
