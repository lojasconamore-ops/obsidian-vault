# Relatório Financeiro Diário — 2026-08-27

**Ao DigitalCEO**  
**Base BRT:** 27/08/2026, 08:00  
**Vendas do dia anterior:** 26/08/2026  
**Janela de vencimentos:** 27/08–03/09/2026

## Resumo financeiro

- **Pagar.me — aprovadas:** **44 cobranças | R$ 61.950,85 | ticket médio R$ 1.407,97**.
- **Qualidade:** **42 OK | R$ 52.992,64**; **2 revisar | R$ 8.958,21**; **0 suspeitas**. Revisões = **14,46%** do valor.
- **Por loja:** ACL **32 | R$ 35.635,07**; SSL **10 | R$ 24.441,81**; GCL **2 | R$ 1.873,97**; BRG **0 | R$ 0,00**.
- **Por meio:** cartão **27 | R$ 33.091,34**; PIX **14 | R$ 22.603,94**; boleto **3 | R$ 6.255,57**.
- **SQL Server — vendas confirmadas:** **51 pedidos | R$ 139.699,96**; Aprovado **44 | R$ 120.674,89** e Expedição **7 | R$ 19.025,07**. Fonte atualizada até 26/08.
- **Overlay bruto DEBX/SQL:** Cancelado **10 | R$ 38.875,19**; não incluído nas vendas confirmadas. Orçamento/Pendente/Financeiro também não incluídos.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** X/expedido **90 | R$ 7.307,82**; A **33 | R$ 33.295,80**; F **1 | R$ 2.022,40**; P **1 | R$ 367,30**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **164 movimentos | R$ 7.241,69**.

## Alertas de vencimentos

- **Contas a pagar 27/08–03/09:** base oficial atual **não localizada** no Vault nem no Google Drive após 6 buscas recentes. **Não significa saldo zero.**
- **Contas a receber ACL:** **798 títulos | R$ 118.633,54**.
- **Vencendo hoje:** **172 títulos | R$ 25.094,75**.
- **Pico:** **31/08 | 280 títulos | R$ 47.596,43** — **40,12%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 27/08 | 172 | R$ 25.094,75 |
| 28/08 | 89 | R$ 9.777,74 |
| 29/08 | 2 | R$ 3.120,41 |
| 30/08 | 1 | R$ 73,80 |
| 31/08 | 280 | R$ 47.596,43 |
| 01/09 | 75 | R$ 9.027,46 |
| 02/09 | 86 | R$ 7.946,85 |
| 03/09 | 93 | R$ 15.996,10 |

## Inadimplência

- **Títulos vencidos sem baixa:** **4.089 | R$ 365.595,19**.
- **1–30 dias:** **370 | R$ 77.512,84**.
- **31–60 dias:** **16 | R$ 3.860,28**.
- **61–90 dias:** **18 | R$ 20.618,59**.
- **Acima de 90 dias:** **3.685 | R$ 263.603,48**.
- **Índice bruto:** **29,37%** do saldo aberto ACL de **R$ 1.244.676,14**. Indicador operacional; sujeito a baixas ainda não processadas.
- **Variação diária:** exposição vencida caiu **R$ 56.701,08** e o índice recuou **3,53 p.p.** versus 26/08.

## Recomendações

1. **Cobrança hoje:** priorizar **R$ 25.094,75** vencendo em 27/08 e **R$ 77.512,84** vencidos há até 30 dias.
2. **Revisão Pagar.me:** validar 2 PIX do mesmo cliente, pedidos distintos, aprovados com **1min31s** de intervalo, total **R$ 8.958,21**; não estornar sem confirmação.
3. **Caixa:** obter a posição oficial de contas a pagar antes de programar os próximos 7 dias.
4. **Programar 31/08:** concentrar cobrança e acompanhamento sobre **R$ 47.596,43** em recebíveis.
5. **Conciliação:** explicar Pagar.me × SQL por escopo/canal; **não somar as fontes**.
6. **Aging:** validar baixas antes de tratar **29,37%** como inadimplência contábil definitiva.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 26/08/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; 6 buscas financeiras recentes concluídas, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada por nome.
- Gmail/e-mail não utilizado por restrição do perfil.
