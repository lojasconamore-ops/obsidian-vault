# Relatório Financeiro Diário — 2026-08-31

**Ao DigitalCEO**  
**Base BRT:** 31/08/2026, 08:02  
**Vendas do dia anterior:** 30/08/2026  
**Janela financeira:** 31/08–07/09/2026 (hoje + 7 dias)

## Resumo financeiro

- **Pagar.me — 30/08:** **17 cobranças | R$ 7.926,12 | ticket médio R$ 466,24**.
- **Qualidade em 30/08:** **17 OK | R$ 7.926,12**; **0 revisar**; **0 suspeitas**.
- **Por loja em 30/08:** ACL **16 | R$ 5.764,89**; SSL **1 | R$ 2.161,23**; GCL **0 | R$ 0,00**; BRG **0 | R$ 0,00**.
- **Por meio em 30/08:** cartão **10 | R$ 5.593,24**; PIX **7 | R$ 2.332,88**.
- **Variação Pagar.me:** **-R$ 14.382,74 | -64,47%** versus 29/08.
- **Janela Pagar.me de segunda-feira, 28–30/08:** **75 cobranças | R$ 99.330,64**; **71 OK | R$ 90.767,38**; **4 revisar | R$ 8.563,26**; **0 suspeitas**.
- **Por dia na janela:** 28/08 **38 | R$ 69.095,66**; 29/08 **20 | R$ 22.308,86**; 30/08 **17 | R$ 7.926,12**.
- **SQL Server — vendas confirmadas em 30/08:** **6 pedidos | R$ 2.361,65 | ticket médio R$ 393,61**; todos com status **Aprovado**. Fonte atualizada até 30/08.
- **Variação SQL:** **-R$ 3.714,73 | -61,13%** versus 29/08.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** status A **5 pedidos | R$ 1.685,41** em 30/08.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **0 movimentos | R$ 0,00** em 30/08.

## Alertas de vencimentos

- **Contas a pagar 31/08–07/09:** base oficial atual **não localizada** no Vault nem no Google Drive após **6 buscas recentes**. **Não significa saldo zero.**
- **Contas a receber ACL:** **903 títulos | R$ 122.760,50**.
- **Vencendo hoje:** **279 títulos | R$ 44.268,43** — **36,06%** da janela.
- **Segundo pico:** **07/09 | 285 títulos | R$ 37.724,84**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 31/08 | 279 | R$ 44.268,43 |
| 01/09 | 77 | R$ 9.740,90 |
| 02/09 | 86 | R$ 7.946,85 |
| 03/09 | 92 | R$ 11.568,95 |
| 04/09 | 75 | R$ 7.335,94 |
| 05/09 | 4 | R$ 2.026,71 |
| 06/09 | 5 | R$ 2.147,88 |
| 07/09 | 285 | R$ 37.724,84 |

## Inadimplência

- **Títulos vencidos sem baixa:** **4.029 | R$ 348.414,42**.
- **1–30 dias:** **317 | R$ 61.038,43**.
- **31–60 dias:** **8 | R$ 649,07**.
- **61–90 dias:** **19 | R$ 23.123,44**.
- **Acima de 90 dias:** **3.685 | R$ 263.603,48**.
- **Índice bruto:** **28,45%** do saldo aberto ACL de **R$ 1.224.745,70**. Indicador operacional; sujeito a baixas ainda não processadas.
- **Variação diária:** exposição vencida aumentou **57 títulos | R$ 4.858,89**; índice subiu **0,34 p.p.** versus 30/08.

## Recomendações

1. **Cobrança hoje:** priorizar **R$ 44.268,43** vencendo em 31/08 e validar baixas dos **R$ 61.038,43** vencidos há até 30 dias.
2. **Programar 07/09:** antecipar acompanhamento de **R$ 37.724,84**, considerando o feriado.
3. **Revisão Pagar.me:** validar **4 cobranças | R$ 8.563,26** de 28/08; exposição equivale a **8,62%** da janela de fim de semana. Não estornar sem confirmação.
4. **Contas a pagar:** obter a posição oficial antes de programar desembolsos; a base corrente não foi localizada.
5. **Conciliação:** diferença de escopo de **R$ 5.564,47** entre Pagar.me de 30/08 (**R$ 7.926,12**) e SQL confirmado (**R$ 2.361,65**); **não somar as fontes**.
6. **Aging:** tratar **28,45%** como indicador operacional, não inadimplência contábil definitiva, até confirmar baixas.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; janela 28–30/08/2026 e fatia de 30/08 separada.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; 6 buscas financeiras recentes concluídas, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada por nome ou conteúdo; somente relatórios históricos encontrados.
- Gmail/e-mail não utilizado por restrição do perfil.
