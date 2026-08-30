# Relatório Financeiro Diário — 2026-08-30

**Ao DigitalCEO**  
**Base BRT:** 30/08/2026, 08:00  
**Vendas do dia anterior:** 29/08/2026  
**Janela financeira:** 30/08–06/09/2026 (hoje + 7 dias)

## Resumo financeiro

- **Pagar.me — aprovadas:** **20 cobranças | R$ 22.308,86 | ticket médio R$ 1.115,44**.
- **Qualidade:** **20 OK | R$ 22.308,86**; **0 revisar**; **0 suspeitas**.
- **Por loja:** SSL **6 | R$ 16.630,58**; ACL **14 | R$ 5.678,28**; GCL **0 | R$ 0,00**; BRG **0 | R$ 0,00**.
- **Por meio:** cartão **11 | R$ 14.195,34**; PIX **9 | R$ 8.113,52**.
- **Variação Pagar.me:** **-R$ 47.267,73 | -67,94%** versus aprovações de 28/08.
- **SQL Server — vendas confirmadas:** **11 pedidos | R$ 6.076,38 | ticket médio R$ 552,40**; todos com status **Aprovado**. Fonte atualizada até 29/08.
- **Variação SQL:** **-R$ 55.281,75 | -90,10%** versus 28/08.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** X/expedido **80 | R$ 8.270,23**; A **7 | R$ 2.529,43**; P **1 | R$ 1.803,00**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **177 movimentos | R$ 7.844,30**.

## Alertas de vencimentos

- **Contas a pagar 30/08–06/09:** base oficial atual **não localizada** no Vault nem no Google Drive após **6 buscas recentes**. **Não significa saldo zero.**
- **Contas a receber ACL:** **673 títulos | R$ 89.181,11**; redução diária de **23 títulos | R$ 3.433,58** na janela móvel.
- **Vencendo hoje:** **57 títulos | R$ 4.858,89**.
- **Pico:** **31/08 | 279 títulos | R$ 44.268,43** — **49,64%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 30/08 | 57 | R$ 4.858,89 |
| 31/08 | 279 | R$ 44.268,43 |
| 01/09 | 75 | R$ 9.027,46 |
| 02/09 | 86 | R$ 7.946,85 |
| 03/09 | 92 | R$ 11.568,95 |
| 04/09 | 75 | R$ 7.335,94 |
| 05/09 | 4 | R$ 2.026,71 |
| 06/09 | 5 | R$ 2.147,88 |

## Inadimplência

- **Títulos vencidos sem baixa:** **3.972 | R$ 343.555,53**.
- **1–30 dias:** **260 | R$ 56.179,54**.
- **31–60 dias:** **9 | R$ 1.641,07**.
- **61–90 dias:** **18 | R$ 22.131,44**.
- **Acima de 90 dias:** **3.685 | R$ 263.603,48**.
- **Índice bruto:** **28,11%** do saldo aberto ACL de **R$ 1.222.384,05**. Indicador operacional; sujeito a baixas ainda não processadas.
- **Variação diária:** exposição vencida aumentou **R$ 10.509,35**, com **85 títulos a mais**, e o índice subiu **0,63 p.p.** versus 29/08.

## Recomendações

1. **31/08:** mobilizar cobrança sobre **R$ 44.268,43**, quase metade dos recebíveis da janela.
2. **Inadimplência curta:** priorizar **R$ 56.179,54** vencidos há até 30 dias; validar baixas antes da cobrança.
3. **Contas a pagar:** obter a posição oficial antes de programar desembolsos; a base corrente não foi localizada.
4. **Conciliação:** investigar a diferença de escopo de **R$ 16.232,48** entre Pagar.me (**R$ 22.308,86**) e SQL confirmado (**R$ 6.076,38**); **não somar as fontes**.
5. **Operação de fim de semana:** quedas de **67,94%** no Pagar.me e **90,10%** no SQL exigem comparação com sábados anteriores antes de concluir perda de desempenho.
6. **Aging:** tratar **28,11%** como indicador operacional, não inadimplência contábil definitiva, até confirmar baixas.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 29/08/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; 6 buscas financeiras recentes concluídas, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada por nome/conteúdo.
- Gmail/e-mail não utilizado por restrição do perfil.
