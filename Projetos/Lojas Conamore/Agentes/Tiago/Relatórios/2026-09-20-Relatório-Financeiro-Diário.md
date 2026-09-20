# Relatório Financeiro Diário — 2026-09-20

**Ao DigitalCEO**  
**Base BRT:** 20/09/2026, 08:02  
**Vendas do dia anterior:** 19/09/2026  
**Janela de vencimentos:** 20–26/09/2026

## Resumo financeiro

- **SQL Server — vendas confirmadas em 19/09:** **17 pedidos | R$ 49.861,50 | ticket médio R$ 2.933,03**. Status: **17 aprovados**.
- **Pagar.me — aprovações em 19/09:** **17 cobranças | R$ 49.861,54 | ticket médio R$ 2.933,03**.
- **Qualidade Pagar.me:** **17 OK | R$ 49.861,54**; **0 suspeitas**; **0 revisar**.
- **Por loja/Pagar.me:** SSL **6 | R$ 43.566,77**; ACL **11 | R$ 6.294,77**; GCL **0**; BRG **0**.
- **Por meio/Pagar.me:** PIX **6 | R$ 32.610,96**; cartão **11 | R$ 17.250,58**.
- **Conciliação SQL x Pagar.me:** diferença residual de **R$ 0,04**; bases praticamente conciliadas.
- **Oracle/DEBX — PED em 19/09, separado:** status **X/expedido 95 | R$ 13.827,09**; status **A 10 | R$ 5.647,64**. Venda física `MOV_NATIND=100`: **248 movimentos | R$ 13.136,10**.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual **não localizada no Vault nem no Google Drive**. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL — 20–26/09:** **602 títulos | R$ 67.232,49**.
- **Vencendo hoje, 20/09:** **68 títulos | R$ 7.922,58**.
- **Maior concentração:** **21/09 | 256 títulos | R$ 25.261,35**.
- Demais: 22/09 **77 | R$ 8.577,36**; 23/09 **62 | R$ 8.752,28**; 24/09 **67 | R$ 7.164,10**; 25/09 **69 | R$ 9.333,24**; 26/09 **3 | R$ 221,58**.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.867 | R$ 300.980,74**.
- **Índice bruto:** **23,41%** do saldo aberto ACL de **R$ 1.285.526,79**.
- **1–30 dias:** **162 | R$ 15.105,45**.
- **31–60 dias:** **3 | R$ 427,21**.
- **61–90 dias:** **17 | R$ 20.989,97**.
- **Acima de 90 dias:** **3.685 | R$ 264.458,11 — 87,87% do vencido**.
- **Variação diária:** os **80 títulos | R$ 8.295,20** que venceram em 19/09 migraram para a faixa vencida sem baixa.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança imediata:** atuar nos **R$ 15.105,45** vencidos até 30 dias, com prioridade para os **R$ 8.295,20** vencidos ontem.
2. **Preparar 21/09:** monitorar cobrança e baixa de **R$ 25.261,35**, maior concentração da semana.
3. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos; a base atual não foi localizada.
4. **Aging:** separar atraso real, baixa pendente e legado nos **R$ 264.458,11** acima de 90 dias.
5. **Conciliação:** manter SQL x Pagar.me como conciliado; diferença de **R$ 0,04** é residual de arredondamento/precisão.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 19/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 19/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: recebíveis e aging somente da ACL; não consolida outros schemas.
- Vault e Google Drive: nenhuma base oficial atual de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
