# Relatório Financeiro Diário — 2026-08-23

**Ao DigitalCEO**  
**Base BRT:** 23/08/2026, 08:03  
**Vendas do dia anterior:** 22/08/2026  
**Janela de vencimentos:** 23–30/08/2026

## Resumo financeiro

- **Vendas aprovadas — SQL:** **14 pedidos | R$ 11.220,01 | ticket médio R$ 801,43**.
- **Pagar.me aprovado:** **15 cobranças | R$ 11.752,53 | ticket médio R$ 783,50**.
- **Diferença Pagar.me × SQL:** **R$ 532,52 | 4,75% do SQL**. Escopos distintos; conciliar corte/canais.
- **Variação Pagar.me contra 21/08:** **-R$ 56.838,95 | -82,87%**; de **33 para 15 cobranças**. Queda compatível com sábado, mas material.
- **Pagar.me por loja:** ACL **13 | R$ 5.815,84**; SSL **2 | R$ 5.936,69**; GCL **0 | R$ 0,00**; BRG **0 | R$ 0,00**.
- **Pagar.me por meio:** cartão **11 | R$ 8.202,96**; PIX **4 | R$ 3.549,57**.
- **Qualidade Pagar.me:** **15 OK | 0 suspeitas | 0 revisar**. Exposição sinalizada atual: **R$ 0,00**.
- **Oracle/DEBX — sem somar às vendas acima:** PED status **X/expedido 84 | R$ 10.823,97**; status **A 11 | R$ 4.830,23**; venda física `MOV_NATIND=100` **196 movimentos | R$ 10.790,76**.

## Alertas de vencimentos

- **Contas a pagar 23–30/08:** base oficial atual **não localizada no Google Drive nem no Vault**. **Saídas semanais indisponíveis; não significa saldo zero.**
- **Contas a receber ACL 23–30/08 — Oracle:** **634 títulos | R$ 74.766,85**.
- **Vencendo hoje:** **65 títulos | R$ 7.253,81**.
- **Pico da janela:** **24/08 | 260 títulos | R$ 30.359,26**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 23/08 | 65 | R$ 7.253,81 |
| 24/08 | 260 | R$ 30.359,26 |
| 25/08 | 77 | R$ 8.780,32 |
| 26/08 | 55 | R$ 6.591,18 |
| 27/08 | 85 | R$ 8.703,06 |
| 28/08 | 89 | R$ 9.885,01 |
| 29/08 | 2 | R$ 3.120,41 |
| 30/08 | 1 | R$ 73,80 |

- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. Exposição histórica: **R$ 109.222,37** — não classificada como vencimento atual.
- **Revisão Pagar.me de 21/08 sem resolução localizada:** **R$ 32.671,81**. Não integra a exposição sinalizada de 22/08.

## Inadimplência

- **ACL — títulos vencidos sem baixa no Oracle:** **4.605 títulos | R$ 474.531,65**.
- **1–30 dias:** **886 | R$ 186.468,80**.
- **31–60 dias:** **25 | R$ 22.688,56**.
- **61–90 dias:** **15 | R$ 2.464,61**.
- **Acima de 90 dias:** **3.679 | R$ 262.909,68**.
- **Índice bruto:** **35,69%** do saldo aberto ACL de **R$ 1.329.495,76** aparece vencido. Indicador operacional; pode conter baixas ainda não processadas.

## Recomendações

1. **Cobrança:** priorizar **R$ 7.253,81** vencendo hoje e **R$ 186.468,80** vencidos há até 30 dias.
2. **Acompanhar 24/08:** concentração de recebíveis de **R$ 30.359,26**.
3. **Confirmar a resolução dos R$ 32.671,81 sinalizados no Pagar.me em 21/08**; o movimento de 22/08 fechou limpo.
4. **Obter a posição oficial de contas a pagar de 23–30/08** e validar a baixa dos **R$ 109.222,37** históricos.
5. **Validar baixas do aging ACL** antes de usar os **35,69%** como inadimplência contábil.
6. **Monitorar a queda de sábado:** SQL **-85,94%** e Pagar.me **-82,87%** contra sexta; reavaliar na abertura de segunda antes de escalar como desvio.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 22/08/2026.
- SQL Server `hotel-finder`: sessão, schema e colunas validados; fonte atualizada até 22/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Google Drive: 6 buscas financeiras concluídas; nenhuma base atual localizada. Vault: nenhuma base atual de contas a pagar localizada por nome. Gmail/e-mail não utilizado.
