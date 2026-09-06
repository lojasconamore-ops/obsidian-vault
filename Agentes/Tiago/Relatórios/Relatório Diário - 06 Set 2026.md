# Relatório Financeiro Diário — 06/09/2026

**Ao DigitalCEO | Base:** 05/09/2026 | **Emissão:** 06/09/2026 08:01 BRT

## Resumo financeiro
- **Vendas aprovadas — SQL Server:** 19 pedidos | **R$ 13.728,82** | ticket médio **R$ 722,57**.
- **Pagar.me aprovado:** 19 cobranças | **R$ 13.728,79** | ticket médio **R$ 722,57**.
- **Conciliação SQL × Pagar.me:** diferença de **R$ 0,03**; quantidade conciliada em 19.
- **Pagar.me por loja:** ACL 16 | **R$ 7.036,37** (51,25%); BRG 1 | **R$ 3.864,08** (28,15%); SSL 2 | **R$ 2.828,34** (20,60%); GCL 0 | **R$ 0,00**.
- **Pagar.me por meio:** cartão 13 | **R$ 7.495,00** (54,59%); PIX 6 | **R$ 6.233,79** (45,41%).
- **Conciliação Pagar.me:** 19 OK | **R$ 13.728,79**; 0 SUSPEITO; 0 REVISAR.
- **Oracle/DEBX — PED, separado da venda física:** status X (expedido) 87 pedidos | **R$ 18.416,32**; status A 17 pedidos | **R$ 8.616,00**.
- **Venda física Oracle — F_MOVTO/MOV_NATIND=100:** 218 movimentos | **R$ 13.391,72**.

## Alertas de vencimentos
- **Contas a pagar 06–13/09:** base atual não localizada no Google Drive; **total confirmado indisponível**.
- **Contas a receber ACL 06–13/09 — Oracle F_TITULOS:** 730 títulos | **R$ 97.144,00**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 06/09 | 66 | R$ 8.053,54 |
| 07/09 | 284 | **R$ 34.804,43** |
| 08/09 | 97 | R$ 14.116,26 |
| 09/09 | 86 | R$ 8.721,87 |
| 10/09 | 103 | R$ 15.501,93 |
| 11/09 | 91 | R$ 15.654,30 |
| 12/09 | 3 | R$ 291,67 |
| 13/09 | 0 | R$ 0,00 |

## Inadimplência e risco
- **ACL — títulos vencidos sem baixa no Oracle:** 3.909 títulos | **R$ 316.301,54**.
- **Atraso de 1–30 dias:** 202 títulos | **R$ 29.337,10**.
- **Atraso de 31–60 dias:** 8 títulos | **R$ 712,29**.
- **Atraso de 61–90 dias:** 17 títulos | **R$ 22.589,82**.
- **Atraso acima de 90 dias:** 3.682 títulos | **R$ 263.662,33**.
- **Saldo aberto ACL:** 10.095 títulos | **R$ 1.304.368,43**.
- **Índice vencido sobre saldo aberto:** **24,25%**. Há forte concentração histórica acima de 90 dias; validar baixas antes de tratar como inadimplência contábil definitiva.

## Recomendações
1. **Cobrança imediata:** priorizar os **R$ 29.337,10** vencidos há até 30 dias, após validar baixas.
2. **Monitorar 07/09:** **R$ 34.804,43** a vencer, equivalente a 35,83% da janela.
3. **Saneamento de base:** revisar os **R$ 263.662,33** acima de 90 dias para separar inadimplência real de baixas não processadas.
4. **Caixa:** evitar novos compromissos discricionários até disponibilizar a base corrente de contas a pagar.
5. **Conciliação:** registrar a diferença residual de **R$ 0,03** entre SQL Server e Pagar.me como arredondamento a validar, sem impacto material.

## Fontes e limites
- SQL Server `hotel-finder`: sessão e colunas validadas; fonte de vendas atualizada até 05/09/2026.
- Pagar.me v5: aprovações de 05/09/2026; artefato do dia gerado e conferido.
- Oracle/DEBX: sessão `TEST_ACL` validada; PED e venda física reportadas separadamente.
- Próximos vencimentos e aging: `TEST_ACL.F_TITULOS`, somente contas a receber ACL; não consolida outros schemas.
- Google Drive: pesquisas por contas, vencer, título, financeiro, inadimplência e pagar; nenhuma base financeira atual localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
