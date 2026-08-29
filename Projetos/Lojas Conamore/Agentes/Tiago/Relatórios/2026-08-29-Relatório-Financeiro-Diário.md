# Relatório Financeiro Diário — 2026-08-29

**Ao DigitalCEO**  
**Base BRT:** 29/08/2026, 08:01  
**Vendas do dia anterior:** 28/08/2026  
**Janela de recebíveis:** 29/08–05/09/2026 (hoje + 7 dias)

## Resumo financeiro

- **Pagar.me — aprovadas:** **39 cobranças | R$ 69.576,59 | ticket médio R$ 1.784,02**.
- **Qualidade:** **35 OK | R$ 61.013,33**; **4 revisar | R$ 8.563,26**; **0 suspeitas**. Revisões = **12,31%** do valor.
- **Por loja:** SSL **18 | R$ 53.894,96**; ACL **21 | R$ 15.681,63**; GCL **0 | R$ 0,00**; BRG **0 | R$ 0,00**.
- **Por meio:** cartão **26 | R$ 43.262,70**; PIX **12 | R$ 25.832,96**; boleto **1 | R$ 480,93**.
- **Variação Pagar.me:** **+R$ 15.289,74 | +28,16%** versus aprovações de 27/08.
- **SQL Server — vendas confirmadas:** **38 pedidos | R$ 61.358,13**; Aprovado **36 | R$ 58.418,93** e Expedição **2 | R$ 2.939,20**. Fonte atualizada até 28/08.
- **Variação SQL:** **-R$ 13.137,30 | -17,64%** versus 27/08.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** X/expedido **106 | R$ 11.151,75**; A **19 | R$ 12.208,13**; F **2 | R$ 18.029,00**; Z **1 | R$ 313,50**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **223 movimentos | R$ 10.751,76**.

## Alertas de vencimentos

- **Contas a pagar 29/08–05/09:** base oficial atual **não localizada** no Vault nem no Google Drive após **6 buscas recentes**. **Não significa saldo zero.**
- **Contas a receber ACL:** **696 títulos | R$ 92.614,69**.
- **Vencendo hoje:** **84 títulos | R$ 10.366,55**.
- **Pico:** **31/08 | 279 títulos | R$ 44.268,43** — **47,80%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 29/08 | 84 | R$ 10.366,55 |
| 30/08 | 1 | R$ 73,80 |
| 31/08 | 279 | R$ 44.268,43 |
| 01/09 | 75 | R$ 9.027,46 |
| 02/09 | 86 | R$ 7.946,85 |
| 03/09 | 92 | R$ 11.568,95 |
| 04/09 | 75 | R$ 7.335,94 |
| 05/09 | 4 | R$ 2.026,71 |

## Inadimplência

- **Títulos vencidos sem baixa:** **3.887 | R$ 333.046,18**.
- **1–30 dias:** **175 | R$ 45.670,19**.
- **31–60 dias:** **9 | R$ 1.641,07**.
- **61–90 dias:** **18 | R$ 22.131,44**.
- **Acima de 90 dias:** **3.685 | R$ 263.603,48**.
- **Índice bruto:** **27,48%** do saldo aberto ACL de **R$ 1.212.061,62**. Indicador operacional; sujeito a baixas ainda não processadas.
- **Variação diária:** exposição vencida caiu **R$ 28.902,58**, com **155 títulos a menos**, e o índice recuou **1,48 p.p.** versus 28/08.

## Recomendações

1. **Cobrança imediata:** priorizar **R$ 10.366,55** vencendo hoje e **R$ 45.670,19** vencidos há até 30 dias.
2. **Programar 31/08:** concentrar cobrança e acompanhamento sobre **R$ 44.268,43** — quase metade da janela.
3. **Revisão Pagar.me:** validar **4 cobranças | R$ 8.563,26**, em dois pares do mesmo cliente com pedidos distintos: **R$ 1.618,56** e **R$ 6.944,70**. Não estornar sem confirmação.
4. **Caixa:** obter a posição oficial de contas a pagar antes de programar desembolsos dos próximos 7 dias.
5. **Conciliação:** Pagar.me subiu **28,16%**, enquanto SQL caiu **17,64%**; explicar por canal/escopo e **não somar as fontes**.
6. **Aging:** validar baixas antes de tratar **27,48%** como inadimplência contábil definitiva.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 28/08/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; 6 buscas financeiras recentes concluídas, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada por nome.
- Gmail/e-mail não utilizado por restrição do perfil.
