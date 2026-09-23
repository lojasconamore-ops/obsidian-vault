# Relatório Financeiro Diário — 2026-09-23

**Ao DigitalCEO**  
**Base BRT:** 23/09/2026, 08:01  
**Vendas do dia anterior:** 22/09/2026  
**Janela de vencimentos:** 23–29/09/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas em 22/09:** **53 pedidos | R$ 88.190,71 | ticket médio R$ 1.663,98**.
- **Outros status no SQL:** Expedição **1 | R$ 140,68**. Não somado às vendas aprovadas.
- **Pagar.me — aprovações em 22/09:** **47 cobranças | R$ 76.663,53 | ticket médio R$ 1.631,14**.
- **Qualidade Pagar.me:** **45 OK | R$ 76.338,11**; **0 suspeitas**; **2 revisar | R$ 325,42** (**0,42%** do valor aprovado).
- **Por loja:** SSL **18 | R$ 43.382,38**; GCL **5 | R$ 19.822,74**; ACL **24 | R$ 13.458,41**; BRG **0**.
- **Por meio:** cartão **34 | R$ 61.157,40**; PIX **13 | R$ 15.506,13**.
- **SQL x Pagar.me:** diferença de escopo de **R$ 11.527,18**; fontes **não conciliadas** nesta execução.
- **Oracle/DEBX — PED em 22/09, separado:** status X/expedido **59 | R$ 7.666,17**; status A **27 | R$ 13.662,84**. Venda física `MOV_NATIND=100`: **129 movimentos | R$ 7.327,83**. PED não representa venda física.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual **não localizada no Vault nem no Google Drive**, após **6 buscas atuais**. Total confirmado indisponível; **não significa saldo zero**.
- **Contas a receber ACL — 23–29/09:** **600 títulos | R$ 79.249,69**.
- **Vencendo hoje, 23/09:** **104 títulos | R$ 13.966,96** — **17,62%** da janela semanal.
- Demais: 24/09 **67 | R$ 7.612,01**; 25/09 **69 | R$ 9.333,24**; 26/09 **3 | R$ 221,58**; 27/09 **3 | R$ 1.065,93**; 28/09 **271 | R$ 38.733,82**; 29/09 **83 | R$ 8.316,15**.
- **Maior concentração:** 28/09, **R$ 38.733,82** — **48,88%** da janela.
- **Pagar.me/ACL:** 2 cobranças do mesmo cliente, com pedidos e valores diferentes, total **R$ 325,42**. Classificação: **REVISAR**, sem duplicidade confirmada.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.788 | R$ 293.812,87**.
- **Índice bruto:** **22,58%** do saldo aberto ACL de **R$ 1.300.984,62**.
- **1–30 dias:** **82 | R$ 7.937,54**.
- **31–60 dias:** **4 | R$ 427,25**.
- **61–90 dias:** **12 | R$ 10.741,31**.
- **Acima de 90 dias:** **3.690 | R$ 274.706,77** — **93,50%** do vencido.
- **Vencidos em 22/09 ainda sem baixa:** **20 títulos | R$ 2.275,56**.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança imediata:** priorizar os **R$ 2.275,56** vencidos em 22/09 e os **R$ 7.937,54** da faixa de 1–30 dias.
2. **Preparar 28/09:** reforçar cobrança para a concentração de **R$ 38.733,82** em recebíveis.
3. **Revisar Pagar.me/ACL:** validar as 2 cobranças, total **R$ 325,42**, antes do fechamento da conciliação.
4. **Conciliar canais:** explicar a diferença SQL x Pagar.me de **R$ 11.527,18** por origem e forma de pagamento.
5. **Aging:** separar legado, atraso real e baixa pendente nos **R$ 274.706,77** acima de 90 dias.
6. **Contas a pagar:** obter a posição oficial antes de autorizar desembolsos; a base corrente não foi localizada.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 22/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 22/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: recebíveis e aging somente da ACL; não consolida outros schemas.
- Vault e Google Drive: buscas atuais sem base oficial de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
