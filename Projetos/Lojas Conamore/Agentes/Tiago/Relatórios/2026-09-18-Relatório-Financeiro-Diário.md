# Relatório Financeiro Diário — 2026-09-18

**Ao DigitalCEO**  
**Base BRT:** 18/09/2026, 08:02  
**Vendas do dia anterior:** 17/09/2026  
**Janela de vencimentos:** 18–25/09/2026

## Resumo financeiro

- **SQL Server — vendas confirmadas em 17/09:** **52 pedidos | R$ 87.273,40 | ticket médio R$ 1.678,33**. Status: Aprovado **47 | R$ 85.142,04**; Expedição **5 | R$ 2.131,36**.
- **Pagar.me — aprovações em 17/09:** **47 cobranças | R$ 85.779,06 | ticket médio R$ 1.825,09**.
- **Qualidade Pagar.me:** **47 OK | 0 suspeitas | 0 revisar**.
- **Por loja/Pagar.me:** SSL **16 | R$ 54.293,53**; GCL **10 | R$ 22.702,59**; ACL **21 | R$ 8.782,94**; BRG **0**.
- **Por meio/Pagar.me:** cartão **26 | R$ 44.021,70**; PIX **21 | R$ 41.757,36**.
- **Diferença SQL x Pagar.me:** Pagar.me **R$ 1.494,34 abaixo** (**-1,71%** sobre SQL). **Não somar as fontes**: escopos e status distintos.
- **Oracle/DEBX — PED em 17/09, separado:** status **A 25 | R$ 12.278,65**; status **X/expedido 114 | R$ 11.787,03**. Venda física `MOV_NATIND=100`: **223 movimentos | R$ 10.366,53**.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual **não localizada no Vault**; Google Drive **sem autenticação disponível nesta execução**. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL — 18–25/09:** **708 títulos | R$ 82.987,31**.
- **Vencendo hoje, 18/09:** **164 títulos | R$ 17.040,10**.
- **Maior concentração:** **21/09 | 262 títulos | R$ 29.901,13**.
- Demais: 19/09 **2 | R$ 1.801,44**; 20/09 **4 | R$ 306,54**; 22/09 **77 | R$ 8.577,36**; 23/09 **63 | R$ 8.863,40**; 24/09 **67 | R$ 7.164,10**; 25/09 **69 | R$ 9.333,24**.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.801 | R$ 296.311,56**.
- **Índice bruto:** **23,29%** do saldo aberto ACL de **R$ 1.272.044,27**.
- **1–30 dias:** **96 | R$ 10.436,27**.
- **31–60 dias:** **4 | R$ 594,11**.
- **61–90 dias:** **16 | R$ 20.823,07**.
- **Acima de 90 dias:** **3.685 | R$ 264.458,11 — 89,25% do vencido**.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança hoje:** atuar sobre **R$ 10.436,27** vencidos até 30 dias e acompanhar **R$ 17.040,10** com vencimento em 18/09.
2. **Preparar 21/09:** priorizar cobrança/baixa de **R$ 29.901,13**.
3. **Aging:** separar atraso real, baixa pendente e legado nos **R$ 264.458,11** acima de 90 dias.
4. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos da semana.
5. **Conciliação:** explicar a diferença de **R$ 1.494,34** entre SQL e Pagar.me por competência, canal e status; não somar bases.
6. **Pagar.me:** movimento de 17/09 sem flags; manter conciliação diária por loja e método.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 17/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 17/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Vault: nenhuma base oficial atual de contas a pagar localizada; somente relatórios históricos.
- Google Drive: autenticação indisponível nesta execução.
- Gmail/e-mail não utilizado por restrição do perfil.
