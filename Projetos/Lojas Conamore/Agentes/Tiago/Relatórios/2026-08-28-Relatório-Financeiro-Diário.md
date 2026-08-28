# Relatório Financeiro Diário — 2026-08-28

**Ao DigitalCEO**  
**Base BRT:** 28/08/2026, 08:00  
**Vendas do dia anterior:** 27/08/2026  
**Janela de vencimentos:** 28/08–04/09/2026

## Resumo financeiro

- **Pagar.me — aprovadas:** **38 cobranças | R$ 54.286,85 | ticket médio R$ 1.428,60**.
- **Qualidade:** **38 OK | R$ 54.286,85**; **0 revisar**; **0 suspeitas**.
- **Por loja:** SSL **15 | R$ 42.443,98**; ACL **22 | R$ 11.267,14**; GCL **1 | R$ 575,73**; BRG **0 | R$ 0,00**.
- **Por meio:** PIX **17 | R$ 32.868,46**; cartão **20 | R$ 21.039,67**; boleto **1 | R$ 378,72**.
- **Variação Pagar.me:** **-R$ 7.664,00 | -12,37%** versus aprovações de 26/08.
- **SQL Server — vendas confirmadas:** **49 pedidos | R$ 74.495,43**; Aprovado **43 | R$ 70.092,87** e Expedição **6 | R$ 4.402,56**. Fonte atualizada até 27/08.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** X/expedido **92 | R$ 17.239,37**; A **22 | R$ 15.739,53**; F **1 | R$ 2.565,74**; P **1 | R$ 519,70**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **205 movimentos | R$ 12.686,59**.

## Alertas de vencimentos

- **Contas a pagar 28/08–04/09:** base oficial atual **não localizada** no Vault nem no Google Drive após **6 buscas recentes**. **Não significa saldo zero.**
- **Contas a receber ACL:** **783 títulos | R$ 115.307,22**.
- **Vencendo hoje:** **171 títulos | R$ 24.210,23**.
- **Pico:** **31/08 | 280 títulos | R$ 47.596,43** — **41,28%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 28/08 | 171 | R$ 24.210,23 |
| 29/08 | 2 | R$ 3.120,41 |
| 30/08 | 1 | R$ 73,80 |
| 31/08 | 280 | R$ 47.596,43 |
| 01/09 | 75 | R$ 9.027,46 |
| 02/09 | 86 | R$ 7.946,85 |
| 03/09 | 93 | R$ 15.996,10 |
| 04/09 | 75 | R$ 7.335,94 |

## Inadimplência

- **Títulos vencidos sem baixa:** **4.042 | R$ 361.948,76**.
- **1–30 dias:** **328 | R$ 74.265,97**.
- **31–60 dias:** **12 | R$ 3.063,47**.
- **61–90 dias:** **17 | R$ 21.015,84**.
- **Acima de 90 dias:** **3.685 | R$ 263.603,48**.
- **Índice bruto:** **28,96%** do saldo aberto ACL de **R$ 1.249.941,33**. Indicador operacional; sujeito a baixas ainda não processadas.
- **Variação diária:** exposição vencida caiu **R$ 3.646,43** e o índice recuou **0,41 p.p.** versus 27/08.

## Recomendações

1. **Cobrança hoje:** priorizar **R$ 24.210,23** vencendo em 28/08 e **R$ 74.265,97** vencidos há até 30 dias.
2. **Programar 31/08:** concentrar cobrança e acompanhamento sobre **R$ 47.596,43**.
3. **Caixa:** obter a posição oficial de contas a pagar antes de programar desembolsos dos próximos 7 dias.
4. **Conciliação:** Pagar.me está limpo, sem flags; conciliar com SQL por escopo/canal e **não somar as fontes**.
5. **Aging:** validar baixas antes de tratar **28,96%** como inadimplência contábil definitiva.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 27/08/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; 6 buscas financeiras recentes concluídas, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada por nome.
- Gmail/e-mail não utilizado por restrição do perfil.
