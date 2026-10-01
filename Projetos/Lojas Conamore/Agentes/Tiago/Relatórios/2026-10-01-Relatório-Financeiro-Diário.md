# Relatório Financeiro Diário — 01/10/2026

**Ao DigitalCEO**  
**Base:** 01/10/2026, BRT; vendas de 30/09; vencimentos de 01/10 a 08/10 (hoje + 7 dias).

## Resumo financeiro
- **Vendas aprovadas, SQL Server:** 65 pedidos | **R$ 207.964,37** | ticket médio R$ 3.199,45. Fonte: `hotel-finder.conamore.CAIXA_PERIODO_COM_ORIGEM`, `Status_Pedido='Aprovado'`; data máxima da base 30/09. Inclui vendas a prazo; não é caixa recebido.
- **Pagamentos aprovados, Pagar.me:** 59 cobranças | **R$ 157.820,84** | ticket médio R$ 2.674,93. ACL: 10 | R$ 19.919,06; SSL: 49 | R$ 137.901,78; GCL/BRG: 0. Cartão: R$ 93.065,86; PIX: R$ 62.373,28; boleto: R$ 2.381,70.
- **Conciliação:** diferença SQL menos Pagar.me de **R$ 50.143,53**; escopos diferentes, **não conciliado**. No Pagar.me: 57 OK | R$ 153.175,04; **2 REVISAR | R$ 4.645,80** (mesmo cliente, pedidos e valores diferentes, aprovações próximas; não afirmar duplicidade sem conferência).
- **Oracle/DEBX, leitura separada:** PED X/expedido 108 | R$ 14.392,49; venda física `F_MOVTO/MOV_NATIND=100` 261 movimentos | R$ 13.323,97. Não somar PED à venda física nem ao SQL/Pagar.me.

## Alertas de vencimentos
- **Contas a pagar (fornecedores):** posição oficial atual não localizada no Vault; valor e vencimentos **indisponíveis, não zero**. E-mail não acessado por restrição do perfil.
- **Contas a receber ACL, títulos sem data de pagamento:** **748 | R$ 139.094,87**, vencimento 01/10–08/10. 01/10: 154 | **R$ 26.887,97**; 02/10: 70 | R$ 11.115,48; 03/10: 1 | R$ 4.427,15; 05/10: 267 | **R$ 57.744,03**; 06/10: 119 | R$ 17.836,85; 07/10: 65 | R$ 8.969,77; 08/10: 72 | R$ 12.113,62. Sem título em 04/10 nesta consulta. Não equivale à previsão de liquidação nem inclui outras lojas.

## Inadimplência operacional — ACL
- **Vencidos sem data de pagamento:** **3.807 títulos | R$ 303.399,46**, ou **23,26%** do valor bruto aberto ACL (R$ 1.304.249,68). 1–30 dias: 99 | R$ 14.323,51; 31–60: 6 | R$ 2.085,35; 61–90: 6 | R$ 405,02; acima de 90: 3.696 | **R$ 286.585,58**. Indicador operacional bruto baseado em `TIT_VALORI`, sujeito a pagamentos parciais/baixas posteriores; não é inadimplência contábil consolidada.

## Recomendações
1. Priorizar cobrança/baixa dos **R$ 26.887,97** de hoje e preparar os **R$ 57.744,03** de 05/10.
2. Conciliar pedido a pedido os **R$ 50.143,53** de diferença SQL/Pagar.me; verificar as 2 cobranças marcadas **REVISAR** antes de concluir duplicidade.
3. Segregar o legado vencido acima de 90 dias (**R$ 286.585,58**) entre saldo real, pagamentos parciais e baixas pendentes.
4. Obter a posição oficial de **contas a pagar** para projetar caixa da semana; recebíveis não a substituem.

## Fontes e limites
- Pagar.me v5: relatório consolidado **gerado nesta execução** para `paid_at` de 30/09, ACL/SSL/GCL/BRG; planilha consolidada relida para totalizar lojas, meios e flags.
- SQL Server `hotel-finder`: sessão `hotelfinder`, schema/colunas e data máxima validados; consulta somente de leitura.
- Oracle `conamore`: sessão `TEST_ACL` e colunas `F_TITULOS` validadas; `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e `TIT_VALORI` positivo; somente ACL. PED e loja física consultados em separado.
- Contas a pagar: nenhuma base oficial corrente localizada na pesquisa local; sem consulta a e-mail.
