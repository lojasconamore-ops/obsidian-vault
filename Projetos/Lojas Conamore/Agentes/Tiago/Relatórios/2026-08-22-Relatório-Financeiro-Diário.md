# Relatório Financeiro Diário — 2026-08-22

**Ao DigitalCEO**  
**Base BRT:** 22/08/2026, 08:00  
**Vendas do dia anterior:** 21/08/2026  
**Janela de vencimentos:** 22–29/08/2026

## Resumo financeiro

- **Vendas aprovadas — SQL:** **40 pedidos | R$ 79.824,69 | ticket médio R$ 1.995,62**.
- **Em expedição — SQL, separado:** **2 pedidos | R$ 1.169,80**.
- **Pagar.me aprovado:** **33 cobranças | R$ 68.591,48 | ticket médio R$ 2.078,53**.
- **Diferença SQL × Pagar.me:** **R$ 11.233,21 | 14,07% do SQL**. Escopos distintos; conciliar boleto, MAG/GER e corte de aprovação.
- **Variação Pagar.me contra 20/08:** **-R$ 33.282,81 | -32,67%**; de **50 para 33 cobranças**.
- **Pagar.me por loja:** SSL **9 | R$ 44.024,68**; GCL **13 | R$ 20.643,92**; ACL **11 | R$ 3.922,88**; BRG **0 | R$ 0,00**.
- **Pagar.me por meio:** PIX **18 | R$ 43.055,64**; cartão **15 | R$ 25.535,84**.
- **Qualidade Pagar.me:** **28 OK | R$ 35.919,67**; **5 revisar | R$ 32.671,81**; **0 suspeitas**. A revisão representa **47,63%** do valor aprovado.
- **Oracle/DEBX — sem somar às vendas acima:** PED status **X/expedido 101 | R$ 8.570,06**; status **A 17 | R$ 5.727,06**; venda física `MOV_NATIND=100` **175 movimentos | R$ 8.045,82**.

## Alertas de vencimentos

- **Contas a pagar 22–29/08:** base oficial atual **não localizada no Vault**. **Saídas semanais indisponíveis; não significa saldo zero.**
- **Contas a receber ACL 22–29/08 — Oracle:** **654 títulos | R$ 76.732,15**.
- **Vencendo hoje:** **84 títulos | R$ 8.726,22**.
- **Pico da janela:** **24/08 | 260 títulos | R$ 30.359,26**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 22/08 | 84 | R$ 8.726,22 |
| 23/08 | 2 | R$ 566,69 |
| 24/08 | 260 | R$ 30.359,26 |
| 25/08 | 77 | R$ 8.780,32 |
| 26/08 | 55 | R$ 6.591,18 |
| 27/08 | 85 | R$ 8.703,06 |
| 28/08 | 89 | R$ 9.885,01 |
| 29/08 | 2 | R$ 3.120,41 |

- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. Exposição histórica: **R$ 109.222,37** — não classificada como vencimento atual.

## Inadimplência

- **ACL — títulos vencidos sem baixa no Oracle:** **4.521 títulos | R$ 465.805,43**.
- **1–30 dias:** **803 | R$ 177.977,38**.
- **31–60 dias:** **24 | R$ 22.453,76**.
- **61–90 dias:** **15 | R$ 2.464,61**.
- **Acima de 90 dias:** **3.679 | R$ 262.909,68**.
- **Índice bruto:** **35,47%** do saldo aberto ACL de **R$ 1.313.332,53** aparece vencido. Indicador operacional; pode conter baixas ainda não processadas.

## Recomendações

1. **Revisar hoje os R$ 32.671,81 sinalizados no Pagar.me**, principalmente 3 PIX simultâneos de um mesmo cliente (**R$ 29.890,86**) e 2 PIX próximos de outro cliente (**R$ 2.780,95**); confirmar pedidos distintos antes de qualquer ação.
2. **Cobrança:** priorizar **R$ 8.726,22** vencendo hoje e **R$ 177.977,38** vencidos há até 30 dias.
3. **Acompanhar 24/08:** concentração de recebíveis de **R$ 30.359,26**.
4. **Conciliar R$ 11.233,21 de diferença SQL × Pagar.me**, separando boleto, MAG/GER e corte de aprovação.
5. **Obter a posição oficial de contas a pagar de 22–29/08** e validar a baixa dos **R$ 109.222,37** históricos.
6. **Validar baixas do aging ACL** antes de usar os **35,47%** como inadimplência contábil.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 21/08/2026.
- SQL Server `hotel-finder`: sessão, schema e colunas validados; fonte atualizada até 21/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Vault: nenhuma base atual de contas a pagar localizada por nome. Gmail/e-mail não utilizado.
