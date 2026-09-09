# Relatório Financeiro Diário — 2026-09-09

**Ao DigitalCEO**  
**Base BRT:** 09/09/2026, 08:05  
**Vendas do dia anterior:** 08/09/2026  
**Janela financeira:** 09/09–16/09/2026

## Resumo financeiro

- **Pagar.me — 08/09:** **33 cobranças | R$ 59.845,78 | ticket médio R$ 1.813,51**.
- **Qualidade:** **31 OK | R$ 53.520,78**; **2 revisar | R$ 6.325,00**; **0 suspeitas**.
- **Exposição sinalizada:** **10,57%** do valor aprovado.
- **Por loja:** SSL **11 | R$ 31.100,09**; BRG **6 | R$ 17.905,95**; ACL **16 | R$ 10.839,74**; GCL **0 | R$ 0,00**.
- **Por meio:** cartão **19 | R$ 44.778,64**; PIX **13 | R$ 12.858,38**; boleto **1 | R$ 2.208,76**.
- **SQL Server — vendas confirmadas em 08/09:** **37 pedidos | R$ 95.648,16 | ticket médio R$ 2.585,09**; Aprovado **32 | R$ 73.920,51** e Expedição **5 | R$ 21.727,65**. Fonte atualizada até 08/09.
- **Diferença de escopo SQL x Pagar.me:** **R$ 35.802,38** a mais no SQL. **Não somar as fontes.**
- **Oracle/DEBX — PED, separado:** status A **18 | R$ 13.928,80**; X/expedido **116 | R$ 11.416,41**; D **1 | R$ 1.479,91**; P **1 | R$ 79,60**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **260 movimentos | R$ 10.739,70**.

## Alertas de vencimentos

- **Contas a pagar 09/09–16/09:** base oficial atual **não localizada** no Google Drive após **6 buscas** nem no Vault. **Não significa saldo zero.**
- **Contas a receber ACL:** **839 títulos | R$ 110.421,24**.
- **Vencendo hoje, 09/09:** **173 títulos | R$ 19.643,55 — 17,79%** da janela.
- **Pico:** **14/09 | 305 títulos | R$ 34.794,87**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 09/09 | 173 | R$ 19.643,55 |
| 10/09 | 103 | R$ 15.501,93 |
| 11/09 | 91 | R$ 15.654,30 |
| 12/09 | 3 | R$ 291,67 |
| 13/09 | 0 | R$ 0,00 |
| 14/09 | 305 | R$ 34.794,87 |
| 15/09 | 91 | R$ 11.913,87 |
| 16/09 | 73 | R$ 12.621,05 |

## Inadimplência

- **Títulos vencidos sem baixa:** **3.976 | R$ 348.572,02**.
- **Índice bruto:** **26,48%** do saldo aberto ACL de **R$ 1.316.330,66**.
- **1–30 dias:** **269 | R$ 61.607,58**.
- **31–60 dias:** **7 | R$ 697,74**.
- **61–90 dias:** **18 | R$ 22.604,37**.
- **Acima de 90 dias:** **3.682 | R$ 263.662,33 — 75,64%** do vencido.
- **Variação versus 07/09:** **+1 título | +R$ 24.216,94** no vencido.
- Indicador operacional sujeito a baixas ainda não processadas; não tratar como inadimplência contábil definitiva sem validação.

## Recomendações

1. **Revisão Pagar.me imediata:** validar **2 cartões de R$ 3.162,50 | total R$ 6.325,00**, mesmo cliente, pedidos distintos, aprovados com **31min52s** de intervalo. **Não estornar sem confirmar os pedidos.**
2. **Cobrança:** priorizar **R$ 61.607,58** vencidos há até 30 dias e acompanhar os **R$ 19.643,55** com vencimento hoje.
3. **Concentração:** preparar cobrança/baixa dos **R$ 34.794,87** com vencimento em 14/09.
4. **Aging:** revisar **R$ 263.662,33** acima de 90 dias, separando atraso real, baixa pendente e legado.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos dos próximos 7 dias.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 08/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Google Drive: conexão ativa; 6 buscas financeiras recentes, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
