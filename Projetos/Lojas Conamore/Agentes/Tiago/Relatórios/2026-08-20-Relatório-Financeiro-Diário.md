# Relatório Financeiro Diário — 2026-08-20

**Ao DigitalCEO**  
**Base BRT:** 20/08/2026, 08:01  
**Vendas do dia anterior:** 19/08/2026  
**Janela de vencimentos:** 20–27/08/2026

## Resumo financeiro

- **Vendas aprovadas — SQL:** **51 pedidos | R$ 73.199,04 | ticket médio R$ 1.435,28**.
- **Pagar.me aprovado:** **47 cobranças | R$ 68.100,78 | ticket médio R$ 1.448,95**.
- **Diferença SQL × Pagar.me:** **R$ 5.098,26** (**6,96%** do SQL). Fontes têm escopos distintos; diferença requer conciliação, não é perda presumida.
- **Pagar.me por loja:** GCL **13 | R$ 31.820,62**; SSL **12 | R$ 26.863,21**; ACL **22 | R$ 9.416,95**; BRG **R$ 0,00**.
- **Pagar.me por meio:** cartão **28 | R$ 46.107,82**; PIX **19 | R$ 21.992,96**.
- **Qualidade Pagar.me:** **44 OK | R$ 63.414,66**; **2 suspeitas | R$ 3.152,30**; **1 revisar | R$ 1.533,82**. Exposição sob análise: **R$ 4.686,12** (**6,88%** do aprovado).
- **Oracle/DEBX — sem somar às vendas acima:** PED status X/expedido **99 | R$ 8.446,48**; status A **19 | R$ 7.372,08**; venda física `MOV_NATIND=100` **194 movimentos | R$ 7.722,15**.

## Alertas de vencimentos

- **Contas a pagar 20–27/08:** base oficial atual **não localizada no Google Drive nem no Vault**. **Saldo semanal de saída indisponível; não significa saldo zero.**
- **Contas a receber ACL 20–27/08 — Oracle:** **756 títulos | R$ 85.435,43**.
- **Vencendo hoje:** **187 títulos | R$ 19.543,75**.
- **Pico da janela:** 24/08 — **261 títulos | R$ 30.622,16**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 20/08 | 187 | R$ 19.543,75 |
| 21/08 | 88 | R$ 9.895,27 |
| 22/08 | 0 | R$ 0,00 |
| 23/08 | 2 | R$ 566,69 |
| 24/08 | 261 | R$ 30.622,16 |
| 25/08 | 77 | R$ 8.780,32 |
| 26/08 | 55 | R$ 6.591,18 |
| 27/08 | 86 | R$ 9.436,06 |

- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. Exposição histórica: **R$ 109.222,37** — não classificada como vencimento atual.

## Inadimplência

- **ACL — títulos vencidos sem baixa no Oracle:** **5.065 títulos | R$ 584.797,90**.
- **1–30 dias:** **1.344 | R$ 278.704,25**.
- **31–60 dias:** **22 | R$ 23.426,46**.
- **61–90 dias:** **20 | R$ 19.757,51**.
- **Acima de 90 dias:** **3.679 | R$ 262.909,68**.
- **Índice bruto:** **40,70%** do saldo aberto ACL de **R$ 1.436.799,70** aparece vencido. Indicador operacional, não contábil definitivo; pode conter baixas não processadas.

## Recomendações

1. **Revisar hoje os R$ 4.686,12 sinalizados no Pagar.me**, com prioridade para 2 cobranças suspeitas do mesmo cliente e mesmo valor (**R$ 3.152,30**).
2. **Cobrança:** priorizar **R$ 19.543,75** vencendo hoje e **R$ 278.704,25** vencidos há até 30 dias.
3. **Preparar acompanhamento para 24/08:** concentração de recebíveis de **R$ 30.622,16**.
4. **Conciliar os R$ 5.098,26 de diferença SQL × Pagar.me**, separando canais, boleto e corte de aprovação.
5. **Obter a posição oficial de contas a pagar de 20–27/08** e validar as baixas do aging e dos **R$ 109.222,37** históricos.

## Fontes validadas

- Pagar.me v5: artefato consolidado gerado nesta execução; aprovações de 19/08/2026.
- SQL Server `hotel-finder`: sessão, schema e colunas validados; fonte atualizada até 19/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Google Drive: 6 buscas financeiras concluídas; nenhuma base atual de contas a pagar localizada. Gmail/e-mail não utilizado por restrição do perfil.
