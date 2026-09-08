# Relatório Financeiro Diário — 08/09/2026

**Ao DigitalCEO | Base:** 07/09/2026 | **Emissão:** 08/09/2026 08:02 BRT

## Resumo financeiro
- **Pagar.me aprovado:** 22 cobranças | **R$ 16.042,82** | ticket médio **R$ 729,22**.
- **SQL Server aprovado:** 21 pedidos | **R$ 14.921,14**.
- **Conciliação SQL × Pagar.me:** Pagar.me acima em **1 cobrança e R$ 1.121,68**; validar integração/competência.
- **Pagar.me por loja:** ACL 20 | **R$ 9.743,92** (60,74%); SSL 2 | **R$ 6.298,90** (39,26%); GCL/BRG 0.
- **Pagar.me por meio:** PIX 9 | **R$ 9.727,80** (60,64%); cartão 13 | **R$ 6.315,02** (39,36%).
- **Conciliação Pagar.me:** 22 OK | 0 SUSPEITO | 0 REVISAR.
- **Oracle/DEBX — PED, separado da venda física:** status A 18 pedidos | **R$ 6.745,21**. Nenhum status X na data.
- **Venda física Oracle — F_MOVTO/MOV_NATIND=100:** 0 movimentos em 07/09. Data foi feriado nacional; não inferir paralisação operacional apenas pelo zero.

## Alertas de vencimentos
- **Contas a pagar 08–15/09:** base atual não localizada no Google Drive; **total confirmado indisponível**.
- **Contas a receber ACL 08–15/09 — Oracle F_TITULOS:** 785 títulos | **R$ 104.914,69**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 08/09 | 105 | R$ 16.556,27 |
| 09/09 | 87 | R$ 10.201,78 |
| 10/09 | 103 | R$ 15.501,93 |
| 11/09 | 91 | R$ 15.654,30 |
| 12/09 | 3 | R$ 291,67 |
| 13/09 | 0 | R$ 0,00 |
| 14/09 | 305 | **R$ 34.794,87** |
| 15/09 | 91 | R$ 11.913,87 |

## Inadimplência e risco
- **ACL — títulos vencidos sem baixa:** 4.265 títulos | **R$ 361.742,48**.
- **1–30 dias:** 558 títulos | **R$ 74.778,04**.
- **31–60 dias:** 7 títulos | **R$ 697,74**.
- **61–90 dias:** 18 títulos | **R$ 22.604,37**.
- **Acima de 90 dias:** 3.682 títulos | **R$ 263.662,33**.
- **Saldo aberto ACL:** 10.175 títulos | **R$ 1.322.536,62**.
- **Índice vencido/saldo aberto:** **27,35%**. Validar baixas antes de tratar como inadimplência contábil definitiva.

## Recomendações
1. **Conciliação hoje:** localizar a cobrança de **R$ 1.121,68** de diferença entre Pagar.me e SQL/competência.
2. **Cobrança:** priorizar os **R$ 74.778,04** vencidos há até 30 dias, após validar baixas.
3. **Caixa em 14/09:** preparar cobrança preventiva sobre **R$ 34.794,87** (33,16% da janela).
4. **Base histórica:** sanear os **R$ 263.662,33** acima de 90 dias.
5. **Saídas:** não assumir novos compromissos discricionários sem a posição corrente de contas a pagar.

## Fontes e limites
- Pagar.me v5: aprovações de 07/09/2026; artefato atual gerado e conferido.
- SQL Server `hotel-finder`: sessão/colunas validadas; fonte atualizada até 07/09/2026.
- Oracle/DEBX: sessão `TEST_ACL`, schema e colunas validados; PED e venda física separados.
- Vencimentos/aging: `TEST_ACL.F_TITULOS`, somente contas a receber ACL.
- Google Drive: buscas por contas, vencer, título, financeiro, inadimplência e pagar; nenhuma base financeira atual localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
