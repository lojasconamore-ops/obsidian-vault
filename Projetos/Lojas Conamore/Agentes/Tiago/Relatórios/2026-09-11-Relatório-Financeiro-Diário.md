# Relatório Financeiro Diário — 2026-09-11

**Ao DigitalCEO**  
**Base BRT:** 11/09/2026, 08:01  
**Vendas do dia anterior:** 10/09/2026  
**Janela financeira:** 11/09–18/09/2026

## Resumo financeiro

- **Pagar.me — 10/09:** **41 cobranças | R$ 116.233,82 | ticket médio R$ 2.834,97**.
- **Qualidade:** **39 OK | R$ 64.376,15**; **2 revisar | R$ 51.857,67**; **0 suspeitas**.
- **Exposição para revisão:** **44,61%** do valor aprovado.
- **Por loja:** GCL **10 | R$ 61.345,46**; SSL **12 | R$ 41.025,28**; ACL **16 | R$ 7.680,82**; BRG **3 | R$ 6.182,26**.
- **Por meio:** cartão **24 | R$ 60.194,24**; PIX **16 | R$ 55.549,72**; boleto **1 | R$ 489,86**.
- **SQL Server — vendas confirmadas em 10/09:** **48 pedidos | R$ 152.867,52 | ticket médio R$ 3.184,74**; todos em status **Aprovado**. Fonte atualizada até 10/09.
- **Diferença de escopo SQL x Pagar.me:** **R$ 36.633,70** a mais no SQL (**31,52%** sobre Pagar.me). **Não somar as fontes.**
- **Oracle/DEBX — PED, separado:** status **X/expedido 81 | R$ 11.348,83**; status **A 13 | R$ 5.797,78**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **183 movimentos | R$ 9.853,95**.

## Alertas de vencimentos

- **Contas a pagar 11/09–18/09:** base oficial atual **não localizada** no Google Drive após **6 buscas** nem no Vault. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL:** **812 títulos | R$ 104.397,88**.
- **Vencendo hoje, 11/09:** **162 títulos | R$ 24.543,98**.
- **Pico:** **14/09 | 305 títulos | R$ 34.794,87 — 33,33%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 11/09 | 162 | R$ 24.543,98 |
| 12/09 | 4 | R$ 513,36 |
| 13/09 | 0 | R$ 0,00 |
| 14/09 | 305 | R$ 34.794,87 |
| 15/09 | 91 | R$ 11.913,87 |
| 16/09 | 73 | R$ 12.621,05 |
| 17/09 | 97 | R$ 10.640,27 |
| 18/09 | 80 | R$ 9.370,48 |

## Inadimplência

- **Títulos vencidos sem baixa:** **4.111 | R$ 380.335,03**.
- **Índice bruto:** **28,45%** do saldo aberto ACL de **R$ 1.336.752,30**.
- **1–30 dias:** **404 | R$ 93.370,59**.
- **31–60 dias:** **7 | R$ 697,74**.
- **61–90 dias:** **17 | R$ 22.010,67**.
- **Acima de 90 dias:** **3.683 | R$ 264.256,03 — 69,48%** do vencido.
- **Variação versus 09/09:** **+135 títulos | +R$ 31.763,01** no vencido.
- Indicador operacional sujeito a baixas ainda não processadas; não tratar como inadimplência contábil definitiva sem validação.

## Recomendações

1. **Revisão imediata GCL:** validar **2 aprovações do mesmo cliente em 2min55s**, pedidos e meios distintos, de **R$ 30.688,55** e **R$ 21.169,12**; exposição total **R$ 51.857,67**. **Não estornar sem confirmar os pedidos.**
2. **Cobrança:** priorizar **R$ 93.370,59** vencidos há até 30 dias e acompanhar os **R$ 24.543,98** com vencimento hoje.
3. **Concentração:** preparar cobrança/baixa dos **R$ 34.794,87** com vencimento em 14/09.
4. **Aging:** revisar **R$ 264.256,03** acima de 90 dias, separando atraso real, baixa pendente e legado.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos dos próximos 7 dias.
6. **Conciliação:** investigar a diferença de **R$ 36.633,70** entre SQL e Pagar.me por competência, forma de pagamento e canal, sem somar as bases.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 10/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Google Drive: conexão ativa; 6 buscas financeiras recentes, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
