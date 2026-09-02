# Relatório Financeiro Diário — 2026-09-02

**Ao DigitalCEO**  
**Base BRT:** 02/09/2026, 08:02  
**Vendas do dia anterior:** 01/09/2026  
**Janela financeira:** 02/09–09/09/2026 (hoje + 7 dias)

## Resumo financeiro

- **Pagar.me — 01/09:** **39 cobranças | R$ 105.063,09 | ticket médio R$ 2.693,93**.
- **Qualidade:** **37 OK | R$ 102.037,29**; **2 revisar | R$ 3.025,80**; **0 suspeitas**.
- **Exposição sinalizada:** **2 cobranças | R$ 3.025,80 — 2,88%** do valor aprovado.
- **Por loja:** SSL **13 | R$ 79.417,52**; ACL **26 | R$ 25.645,57**; BRG/GCL **0 | R$ 0,00**.
- **Por meio:** cartão **28 | R$ 91.934,16**; PIX **11 | R$ 13.128,93**.
- **Variação Pagar.me:** **-R$ 87.144,02 | -45,34%** versus 31/08.
- **SQL Server — vendas confirmadas:** **42 pedidos | R$ 118.796,30 | ticket médio R$ 2.828,48**; Aprovado **41 | R$ 107.367,56** e Expedição **1 | R$ 11.428,74**. Fonte atualizada até 01/09.
- **Variação SQL:** **-R$ 129.894,17 | -52,23%** versus 31/08.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** A **30 | R$ 21.573,96**; F **3 | R$ 9.096,93**; X/expedido **48 | R$ 6.646,37**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **90 movimentos | R$ 5.466,24**.

## Alertas de vencimentos

- **Contas a pagar 02/09–09/09:** base oficial atual **não localizada** no Vault nem no Google Drive após **6 buscas**. **Não significa saldo zero.**
- **Contas a receber ACL:** **764 títulos | R$ 97.286,53**.
- **Vencendo hoje:** **118 títulos | R$ 13.227,91 — 13,60%** da janela.
- **Pico:** **07/09 | 285 títulos | R$ 37.724,84**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 02/09 | 118 | R$ 13.227,91 |
| 03/09 | 93 | R$ 11.864,79 |
| 04/09 | 75 | R$ 7.335,94 |
| 05/09 | 4 | R$ 2.026,71 |
| 06/09 | 5 | R$ 2.147,88 |
| 07/09 | 285 | R$ 37.724,84 |
| 08/09 | 97 | R$ 14.116,26 |
| 09/09 | 87 | R$ 8.842,20 |

## Inadimplência

- **Títulos vencidos sem baixa:** **3.793 | R$ 303.038,47**.
- **1–30 dias:** **80 | R$ 15.580,00**.
- **31–60 dias:** **8 | R$ 584,65**.
- **61–90 dias:** **19 | R$ 23.268,84**.
- **Acima de 90 dias:** **3.686 | R$ 263.604,98**.
- **Índice bruto:** **25,15%** do saldo aberto ACL de **R$ 1.204.790,09**. Indicador operacional; sujeito a baixas ainda não processadas.
- **Variação diária:** exposição vencida caiu **207 títulos | R$ 40.412,41**; índice recuou **2,58 p.p.** versus 01/09.

## Recomendações

1. **Cobrança hoje:** atuar sobre **R$ 13.227,91** vencendo em 02/09 e validar baixas dos **R$ 15.580,00** vencidos há até 30 dias.
2. **Programar 07/09:** antecipar acompanhamento de **R$ 37.724,84**, considerando o feriado.
3. **Revisão Pagar.me:** validar **2 cartões | R$ 3.025,80**, mesmo cliente, valores de **R$ 1.512,80** e **R$ 1.513,00**, aprovados com **4min07s** de intervalo. **Não estornar sem confirmar pedidos.**
4. **Contas a pagar:** obter a posição oficial antes de programar desembolsos; a base corrente não foi localizada.
5. **Conciliação:** diferença de escopo de **R$ 13.733,21** entre SQL confirmado (**R$ 118.796,30**) e Pagar.me (**R$ 105.063,09**); **não somar as fontes**.
6. **Pendência anterior separada:** confirmar resolução das **4 cobranças sinalizadas em 31/08 | R$ 94.261,88**; não incorporadas à exposição atual por falta de evidência de status.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 01/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; 6 buscas financeiras concluídas, sem base atual candidata.
- Vault: nenhuma base atual de contas a pagar localizada; somente relatórios históricos.
- Gmail/e-mail não utilizado por restrição do perfil.
