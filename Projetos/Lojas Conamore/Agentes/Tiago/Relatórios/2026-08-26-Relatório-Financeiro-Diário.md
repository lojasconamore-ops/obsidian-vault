# Relatório Financeiro Diário — 2026-08-26

**Ao DigitalCEO**  
**Base BRT:** 26/08/2026, 08:03  
**Vendas do dia anterior:** 25/08/2026  
**Janela de vencimentos:** 26/08–02/09/2026

## Resumo financeiro

- **Pagar.me — aprovadas:** **42 cobranças | R$ 88.984,92 | ticket médio R$ 2.118,69**.
- **Qualidade:** **40 OK | R$ 83.822,62**; **2 revisar | R$ 5.162,30**; **0 suspeitas**. Revisões = **5,80%** do valor.
- **Por loja:** SSL **18 | R$ 43.448,48**; GCL **3 | R$ 29.723,16**; ACL **21 | R$ 15.813,28**; BRG **0 | R$ 0,00**.
- **Por meio:** PIX **12 | R$ 49.087,10**; cartão **30 | R$ 39.897,82**.
- **SQL Server — vendas confirmadas:** **45 pedidos | R$ 64.479,17**; Aprovado **44 | R$ 62.427,18** e Expedição **1 | R$ 2.051,99**. Fonte atualizada até 25/08.
- **Overlay bruto DEBX/SQL:** Cancelado **6 | R$ 26.409,17**; não incluído nas vendas confirmadas. Pendente/Financeiro também não incluídos.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** status X/expedido **84 | R$ 11.770,42**; status A **19 | R$ 12.998,10**; status F **2 | R$ 3.345,70**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **184 movimentos | R$ 10.976,01**.

## Alertas de vencimentos

- **Contas a pagar 26/08–02/09:** base oficial atual **não localizada** no Vault nem no Google Drive após 6 buscas recentes por metadados/conteúdo. **Não significa saldo zero.**
- **Contas a receber ACL:** **744 títulos | R$ 105.522,26**.
- **Vencendo hoje:** **126 títulos | R$ 19.169,24**.
- **Pico:** **31/08 | 280 títulos | R$ 47.596,43** — **45,11%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 26/08 | 126 | R$ 19.169,24 |
| 27/08 | 85 | R$ 8.703,06 |
| 28/08 | 89 | R$ 9.885,01 |
| 29/08 | 2 | R$ 3.120,41 |
| 30/08 | 1 | R$ 73,80 |
| 31/08 | 280 | R$ 47.596,43 |
| 01/09 | 75 | R$ 9.027,46 |
| 02/09 | 86 | R$ 7.946,85 |

## Inadimplência

- **Títulos vencidos sem baixa:** **4.351 | R$ 422.296,27**.
- **1–30 dias:** **633 | R$ 134.333,86**.
- **31–60 dias:** **15 | R$ 3.740,34**.
- **61–90 dias:** **18 | R$ 20.618,59**.
- **Acima de 90 dias:** **3.685 | R$ 263.603,48**.
- **Índice bruto:** **32,90%** do saldo aberto ACL de **R$ 1.283.683,97**. Indicador operacional; sujeito a baixas ainda não processadas.
- **Variação diária:** exposição vencida caiu **R$ 22.226,65** e o índice recuou **1,44 p.p.** versus 25/08.

## Recomendações

1. **Cobrança hoje:** priorizar **R$ 19.169,24** vencendo em 26/08 e **R$ 134.333,86** vencidos há até 30 dias.
2. **Revisão Pagar.me:** validar 2 pagamentos de Paula Fernanda Doerner Garcia, pedidos distintos, meios distintos, aprovados com 19 minutos de intervalo, total **R$ 5.162,30**; não estornar sem confirmação.
3. **Caixa:** obter a posição oficial de contas a pagar antes de programar os próximos 7 dias.
4. **Programar 31/08:** concentrar cobrança e acompanhamento sobre **R$ 47.596,43** em recebíveis.
5. **Conciliação:** explicar Pagar.me × SQL por escopo/canal; **não somar as fontes**.
6. **Aging:** validar baixas antes de tratar **32,90%** como inadimplência contábil definitiva.

## Fontes validadas

- Pagar.me v5: artefato consolidado gerado nesta execução; aprovações de 25/08/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; 6 buscas financeiras recentes concluídas, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada por nome/conteúdo.
- Gmail/e-mail não utilizado por restrição do perfil.
