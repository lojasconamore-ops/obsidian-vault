# Relatório Financeiro Diário — 2026-09-19

**Ao DigitalCEO**  
**Base BRT:** 19/09/2026, 08:01  
**Vendas do dia anterior:** 18/09/2026  
**Janela de vencimentos:** 19–26/09/2026

## Resumo financeiro

- **SQL Server — vendas confirmadas em 18/09:** **48 pedidos | R$ 141.709,89 | ticket médio R$ 2.952,29**. Status: Aprovado **47 | R$ 141.684,29**; Expedição **1 | R$ 25,60**.
- **Pagar.me — aprovações em 18/09:** **46 cobranças | R$ 130.885,88 | ticket médio R$ 2.845,35**.
- **Qualidade Pagar.me:** **42 OK | R$ 118.050,64**; **0 suspeitas**; **4 revisar | R$ 12.835,24**.
- **Por loja/Pagar.me:** SSL **20 | R$ 95.067,17**; GCL **11 | R$ 26.673,03**; ACL **15 | R$ 9.145,68**; BRG **0**.
- **Por meio/Pagar.me:** cartão **28 | R$ 96.491,73**; PIX **16 | R$ 30.798,70**; boleto **2 | R$ 3.595,45**.
- **Diferença SQL x Pagar.me:** Pagar.me **R$ 10.824,01 abaixo** (**-7,64%** sobre SQL). **Não somar as fontes**: escopos e status distintos.
- **Oracle/DEBX — PED em 18/09, separado:** status **X/expedido 107 | R$ 13.029,64**; status **A 16 | R$ 10.969,99**. Venda física `MOV_NATIND=100`: **251 movimentos | R$ 11.702,80**.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual **não localizada no Vault**; Google Drive **sem autenticação disponível nesta execução**. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL — 19–26/09:** **616 títulos | R$ 67.114,05**.
- **Vencendo hoje, 19/09:** **80 títulos | R$ 8.295,20**.
- **Maior concentração:** **21/09 | 254 títulos | R$ 24.463,75**.
- Demais: 20/09 **4 | R$ 306,54**; 22/09 **77 | R$ 8.577,36**; 23/09 **62 | R$ 8.752,28**; 24/09 **67 | R$ 7.164,10**; 25/09 **69 | R$ 9.333,24**; 26/09 **3 | R$ 221,58**.
- **Pagar.me/GCL:** 4 aprovações do mesmo cliente no mesmo segundo, em pedidos e valores diferentes, totalizando **R$ 12.835,24**. Classificação: **REVISAR**, não duplicidade confirmada.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.787 | R$ 292.685,54**.
- **Índice bruto:** **23,12%** do saldo aberto ACL de **R$ 1.265.754,29**.
- **1–30 dias:** **82 | R$ 6.810,25**.
- **31–60 dias:** **3 | R$ 427,21**.
- **61–90 dias:** **17 | R$ 20.989,97**.
- **Acima de 90 dias:** **3.685 | R$ 264.458,11 — 90,36% do vencido**.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Revisar imediatamente os R$ 12.835,24 no GCL**: confirmar se os 4 pedidos simultâneos são compras legítimas antes da conciliação final.
2. **Cobrança hoje:** atuar sobre **R$ 6.810,25** vencidos até 30 dias e acompanhar **R$ 8.295,20** com vencimento em 19/09.
3. **Preparar 21/09:** priorizar cobrança/baixa de **R$ 24.463,75**.
4. **Aging:** separar atraso real, baixa pendente e legado nos **R$ 264.458,11** acima de 90 dias.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos da semana.
6. **Conciliação:** explicar a diferença de **R$ 10.824,01** entre SQL e Pagar.me por competência, canal e status; não somar bases.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 18/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 18/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Vault: nenhuma base oficial atual de contas a pagar localizada; somente relatórios históricos.
- Google Drive: autenticação indisponível nesta execução.
- Gmail/e-mail não utilizado por restrição do perfil.
