# Relatório Financeiro Diário — 2026-09-01

**Ao DigitalCEO**  
**Base BRT:** 01/09/2026, 08:04  
**Vendas do dia anterior:** 31/08/2026  
**Janela financeira:** 01/09–08/09/2026 (hoje + 7 dias)

## Resumo financeiro

- **Pagar.me — 31/08:** **50 cobranças | R$ 192.207,11 | ticket médio R$ 3.844,14**.
- **Qualidade:** **46 OK | R$ 97.945,23**; **2 revisar | R$ 89.308,00**; **2 suspeitas | R$ 4.953,88**.
- **Exposição total sinalizada:** **4 cobranças | R$ 94.261,88 — 49,04%** do valor aprovado.
- **Por loja:** SSL **22 | R$ 143.188,56**; ACL **27 | R$ 48.962,75**; BRG **1 | R$ 55,80**; GCL **0 | R$ 0,00**.
- **Por meio:** cartão **29 | R$ 154.631,68**; PIX **21 | R$ 37.575,43**.
- **Variação Pagar.me:** **+R$ 184.280,99 | +2.324,98%** versus domingo, 30/08. Comparação entre dias de perfis distintos; não caracteriza tendência.
- **SQL Server — vendas confirmadas:** **79 pedidos | R$ 248.690,47 | ticket médio R$ 3.147,98**; Aprovado **76 | R$ 243.780,00** e Expedição **3 | R$ 4.910,47**. Fonte atualizada até 01/09.
- **Variação SQL:** **+R$ 246.328,82 | +10.430,37%** versus domingo, 30/08. Não interpretar sem comparação com outras segundas-feiras.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** A **24 | R$ 55.235,68**; F **9 | R$ 23.828,54**; X/expedido **83 | R$ 8.205,08**; P **2 | R$ 1.818,29**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **160 movimentos | R$ 6.433,01**.

## Alertas de vencimentos

- **Contas a pagar 01/09–08/09:** base oficial atual **não localizada** no Vault nem no Google Drive após **6 buscas recentes**. **Não significa saldo zero.**
- **Contas a receber ACL:** **786 títulos | R$ 106.877,52**.
- **Vencendo hoje:** **139 títulos | R$ 23.614,07 — 22,09%** da janela.
- **Pico:** **07/09 | 285 títulos | R$ 37.724,84**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 01/09 | 139 | R$ 23.614,07 |
| 02/09 | 89 | R$ 8.342,87 |
| 03/09 | 92 | R$ 11.568,95 |
| 04/09 | 75 | R$ 7.335,94 |
| 05/09 | 4 | R$ 2.026,71 |
| 06/09 | 5 | R$ 2.147,88 |
| 07/09 | 285 | R$ 37.724,84 |
| 08/09 | 97 | R$ 14.116,26 |

## Inadimplência

- **Títulos vencidos sem baixa:** **4.000 | R$ 343.450,88**.
- **1–30 dias:** **287 | R$ 55.992,41**.
- **31–60 dias:** **8 | R$ 584,65**.
- **61–90 dias:** **19 | R$ 23.268,84**.
- **Acima de 90 dias:** **3.686 | R$ 263.604,98**.
- **Índice bruto:** **27,73%** do saldo aberto ACL de **R$ 1.238.722,94**. Indicador operacional; sujeito a baixas ainda não processadas.
- **Variação diária:** exposição vencida caiu **29 títulos | R$ 4.963,54**; índice recuou **0,72 p.p.** versus 31/08.

## Recomendações

1. **Revisão Pagar.me imediata:** validar **4 cobranças | R$ 94.261,88**. Destaques: dois cartões do mesmo cliente por **R$ 57.470,00** e **R$ 31.838,00**, aprovados com cerca de 2 minutos de intervalo; e dois cartões de **R$ 2.476,94** cada, também próximos. **Não estornar sem confirmação de pedido/cliente.**
2. **Cobrança hoje:** atuar sobre **R$ 23.614,07** vencendo em 01/09 e validar baixas dos **R$ 55.992,41** vencidos há até 30 dias.
3. **Programar 07/09:** antecipar acompanhamento de **R$ 37.724,84**, considerando o feriado.
4. **Contas a pagar:** obter a posição oficial antes de programar desembolsos; a base corrente não foi localizada.
5. **Conciliação:** diferença de escopo de **R$ 56.483,36** entre SQL confirmado (**R$ 248.690,47**) e Pagar.me (**R$ 192.207,11**); **não somar as fontes**.
6. **Tendência:** comparar 31/08 com outras segundas-feiras antes de interpretar os aumentos de **2.324,98%** no Pagar.me e **10.430,37%** no SQL.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 31/08/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e datas máximas validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; 6 buscas financeiras recentes concluídas, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada por nome ou conteúdo; somente relatórios históricos encontrados.
- Gmail/e-mail não utilizado por restrição do perfil.
