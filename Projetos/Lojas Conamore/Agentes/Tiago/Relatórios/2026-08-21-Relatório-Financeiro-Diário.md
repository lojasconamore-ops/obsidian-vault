# Relatório Financeiro Diário — 2026-08-21

**Ao DigitalCEO**  
**Base BRT:** 21/08/2026, 08:04  
**Vendas do dia anterior:** 20/08/2026  
**Janela de vencimentos:** 21–28/08/2026

## Resumo financeiro

- **Vendas aprovadas — SQL:** **53 pedidos | R$ 174.132,67 | ticket médio R$ 3.285,52**.
- **Pagar.me aprovado:** **50 cobranças | R$ 101.874,29 | ticket médio R$ 2.037,49**.
- **Diferença SQL × Pagar.me:** **R$ 72.258,38** (**41,50%** do SQL). Escopos distintos; conciliar canais, boleto e corte de aprovação.
- **Variação Pagar.me contra 19/08:** **+R$ 33.773,51 | +49,59%**; de **47 para 50 cobranças**.
- **Pagar.me por loja:** SSL **14 | R$ 52.379,56**; GCL **14 | R$ 36.700,25**; ACL **22 | R$ 12.794,48**; BRG **0 | R$ 0,00**.
- **Pagar.me por meio:** cartão **30 | R$ 72.632,95**; PIX **20 | R$ 29.241,34**.
- **Qualidade Pagar.me:** **50 OK | 0 suspeitas | 0 revisar**. Exposição sinalizada atual: **R$ 0,00**.
- **Oracle/DEBX — sem somar às vendas acima:** PED status X/expedido **90 | R$ 9.606,11**; status A **19 | R$ 12.518,76**; venda física `MOV_NATIND=100` **151 movimentos | R$ 7.591,27**.

## Alertas de vencimentos

- **Contas a pagar 21–28/08:** base oficial atual **não localizada no Google Drive nem no Vault**. **Saídas semanais indisponíveis; não significa saldo zero.**
- **Contas a receber ACL 21–28/08 — Oracle:** **735 títulos | R$ 86.599,90**.
- **Vencendo hoje:** **163 títulos | R$ 19.385,03**.
- **Pico da janela:** 24/08 — **261 títulos | R$ 30.622,16**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 21/08 | 163 | R$ 19.385,03 |
| 22/08 | 0 | R$ 0,00 |
| 23/08 | 2 | R$ 566,69 |
| 24/08 | 261 | R$ 30.622,16 |
| 25/08 | 77 | R$ 8.780,32 |
| 26/08 | 55 | R$ 6.591,18 |
| 27/08 | 86 | R$ 9.436,06 |
| 28/08 | 91 | R$ 11.218,46 |

- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. Exposição histórica: **R$ 109.222,37** — não classificada como vencimento atual.

## Inadimplência

- **ACL — títulos vencidos sem baixa no Oracle:** **4.759 títulos | R$ 524.528,77**.
- **1–30 dias:** **1.039 | R$ 219.649,23**.
- **31–60 dias:** **22 | R$ 22.304,25**.
- **61–90 dias:** **19 | R$ 19.665,61**.
- **Acima de 90 dias:** **3.679 | R$ 262.909,68**.
- **Índice bruto:** **38,03%** do saldo aberto ACL de **R$ 1.379.268,74** aparece vencido. Indicador operacional; pode conter baixas ainda não processadas.

## Recomendações

1. **Cobrança hoje:** priorizar **R$ 19.385,03** com vencimento em 21/08 e **R$ 219.649,23** vencidos há até 30 dias.
2. **Acompanhar 24/08:** concentração de recebíveis de **R$ 30.622,16**.
3. **Conciliar os R$ 72.258,38 de diferença SQL × Pagar.me**, separando Increazy, MAG/GER, boleto e corte de aprovação.
4. **Obter a posição oficial de contas a pagar de 21–28/08**; sem ela, o risco de caixa semanal não é mensurável.
5. **Validar baixas do aging ACL e dos R$ 109.222,37 históricos** antes de usar o índice de **38,03%** como inadimplência contábil.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 20/08/2026.
- SQL Server `hotel-finder`: sessão, schema e colunas validados; fonte atualizada até 20/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Google Drive: 6 buscas financeiras concluídas; nenhuma base atual de contas a pagar localizada. Gmail/e-mail não utilizado.
