# Relatório Financeiro Diário — 2026-08-17

**Ao DigitalCEO**  
**Base BRT:** 17/08/2026, 08:00  
**Vendas do dia anterior:** 16/08/2026  
**Janela Pagar.me de segunda-feira:** 14–16/08/2026  
**Janela de vencimentos:** 17–24/08/2026

## Resumo financeiro

- **Vendas aprovadas em 16/08 — Pagar.me:** **17 cobranças | R$ 14.506,27 | ticket médio R$ 853,31**.
- **Variação contra 15/08:** **+R$ 7.737,05 | +114,30%**; volume de 12 para 17 cobranças.
- **16/08 por loja:** ACL **15 | R$ 8.106,09**; SSL **2 | R$ 6.400,18**; GCL e BRG **R$ 0,00**.
- **16/08 por meio:** cartão **10 | R$ 10.471,04**; PIX **7 | R$ 4.035,23**.
- **Fim de semana 14–16/08:** **64 cobranças | R$ 63.785,71 | ticket R$ 996,65**; **64 OK | 0 suspeitas | 0 revisar**.
- **SQL Server:** fonte atualizada somente até **15/08**; o vazio de 16/08 é **defasagem**, não venda zero.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** em 16/08, status A **10 pedidos | R$ 3.880,96**; status X/expedido **0**. Venda física não interpretada como zero: `F_MOVTO` atualizada somente até **15/08**.

## Alertas de vencimentos

- **Contas a pagar 17–24/08:** base oficial atual **não localizada no Vault**; Google Drive **não autenticado neste perfil**. **Saldo semanal de saída indisponível.**
- **Contas a receber ACL 17–24/08 — Oracle:** **925 títulos | R$ 123.836,59**.
- **Pico hoje, 17/08:** **301 títulos | R$ 50.618,65**, equivalente a **40,88%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 17/08 | 301 | R$ 50.618,65 |
| 18/08 | 101 | R$ 11.137,82 |
| 19/08 | 75 | R$ 8.566,09 |
| 20/08 | 98 | R$ 11.500,59 |
| 21/08 | 88 | R$ 11.087,49 |
| 22/08 | 0 | R$ 0,00 |
| 23/08 | 2 | R$ 566,69 |
| 24/08 | 260 | R$ 30.359,26 |

- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. Exposição histórica: **R$ 109.222,37** — não classificada como vencimento atual.
- **Revisão Pagar.me anterior sem resolução localizada:** **2 cobranças | R$ 1.004,96**. A janela atual está limpa.

## Inadimplência

- **ACL — títulos vencidos sem baixa no Oracle:** **5.514 títulos | R$ 672.827,65**.
- **1–30 dias:** **1.475 | R$ 298.746,50**.
- **31–60 dias:** **341 | R$ 91.580,81**.
- **61–90 dias:** **19 | R$ 19.590,66**.
- **Acima de 90 dias:** **3.679 | R$ 262.909,68**.
- **Índice bruto:** **43,48%** do saldo aberto ACL de **R$ 1.547.392,94** aparece vencido. Indicador operacional, **não contábil definitivo**: pode incluir baixas históricas não processadas.

## Recomendações

1. **Cobrança hoje:** priorizar os **R$ 50.618,65** com vencimento em 17/08 e os **R$ 298.746,50** vencidos há até 30 dias.
2. **Validar baixas do aging ACL:** separar atraso real de baixa pendente antes de usar o índice de 43,48% como inadimplência oficial.
3. **Obter a posição oficial de contas a pagar de 17–24/08**; sem ela, o risco de caixa semanal não é mensurável.
4. **Confirmar baixa dos R$ 109.222,37 históricos** e concluir a revisão Pagar.me de **R$ 1.004,96**.

## Fontes validadas

- Pagar.me v5: artefato consolidado gerado nesta execução; aprovações de 14–16/08/2026.
- SQL Server `hotel-finder`: sessão, schema e colunas validados; atualizado até 15/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` tratados separadamente; somente leitura.
- `F_TITULOS`: contas a receber e aging somente da ACL; não consolida outros schemas.
- Vault: nenhuma base oficial atual de contas a pagar localizada.
- Google Drive: não autenticado neste perfil. Gmail/e-mail não utilizado por restrição do perfil.
