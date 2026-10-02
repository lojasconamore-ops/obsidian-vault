# Relatório Financeiro Diário — 02/10/2026

**Ao DigitalCEO**  
**Base:** 02/10/2026, BRT; vendas de 01/10; vencimentos de 02/10 a 09/10 (hoje + 7 dias).

## Resumo financeiro
- **Vendas aprovadas, SQL Server:** 42 pedidos | **R$ 69.808,37** | ticket médio **R$ 1.662,10**. Fonte: `hotel-finder.conamore.CAIXA_PERIODO_COM_ORIGEM`, `Status_Pedido='Aprovado'`; data máxima da base 01/10. Inclui vendas a prazo; não é caixa recebido.
- **Pagamentos aprovados, Pagar.me:** 39 cobranças | **R$ 52.132,50** | ticket médio **R$ 1.336,73**. ACL: 5 | R$ 8.388,61; SSL: 34 | R$ 43.743,89; GCL/BRG: 0. Cartão: 21 | R$ 32.499,60; PIX: 18 | R$ 19.632,90. **39 OK, 0 REVISAR, 0 SUSPEITO** nesta janela.
- **Diferença SQL menos Pagar.me:** **R$ 17.675,87**. Escopos diferentes; não representa quebra de caixa sem conciliação por pedido.
- **Oracle/DEBX, leitura separada:** PED X/expedido 90 | R$ 11.194,40; PED A 5 | R$ 8.175,14; PED F 2 | R$ 3.754,45. Loja física `F_MOVTO/MOV_NATIND=100`: 184 movimentos | R$ 9.582,72. Não somar PED à loja física nem aos totais de SQL/Pagar.me.

## Alertas de vencimentos
- **Contas a pagar (fornecedores):** base oficial corrente não localizada no Vault; valor/vencimentos indisponíveis, **não zero**. E-mail não acessado por restrição do perfil.
- **Contas a receber ACL, títulos sem data de pagamento:** **751 | R$ 135.632,94**, vencimento 02/10–09/10. 02/10: 134 | **R$ 24.198,93**; 03/10: 1 | R$ 4.427,15; 05/10: 266 | **R$ 57.248,65**; 06/10: 119 | R$ 17.836,85; 07/10: 65 | R$ 8.969,77; 08/10: 72 | R$ 12.113,62; 09/10: 94 | R$ 10.837,97. Sem vencimento em 04/10 nesta consulta. Não é previsão de liquidação e não inclui outras lojas.

## Inadimplência operacional — ACL
- **Vencidos sem data de pagamento:** **3.778 títulos | R$ 295.299,70**, **22,98%** do valor bruto aberto ACL (R$ 1.285.259,79). Até 30 dias: 69 | R$ 6.140,41; acima de 90 dias: 3.696 | **R$ 286.585,58**. Valor bruto `TIT_VALORI` pode incluir pagamentos parciais e baixas pendentes; não é saldo contábil consolidado.

## Recomendações
1. Confirmar cobrança e baixa dos **R$ 24.198,93** de 02/10 e antecipar contato para os **R$ 57.248,65** de 05/10.
2. Conciliar pedido a pedido a diferença de **R$ 17.675,87** entre venda aprovada SQL e cobranças Pagar.me; não igualar as duas bases automaticamente.
3. Revisar o legado vencido acima de 90 dias (**R$ 286.585,58**) com abatimentos e baixas antes de definir recuperação.
4. Obter a posição oficial de contas a pagar de 02/10–09/10 para projetar caixa; recebíveis não substituem saídas.

## Fontes e limites
- Pagar.me v5: relatório consolidado gerado nesta execução para `paid_at` em 01/10; XLSX relido para totalizar meios, lojas e flags.
- SQL Server `hotel-finder`: sessão, colunas e data máxima validadas; consulta somente de leitura.
- Oracle `conamore`: sessão `TEST_ACL`, schema e colunas validados; `F_TITULOS` filtrado por `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e `TIT_VALORI` positivo; somente ACL. PED e loja física consultados em separado.
- Contas a pagar: nenhuma base oficial atual localizada na pesquisa local; sem consulta a e-mail.
