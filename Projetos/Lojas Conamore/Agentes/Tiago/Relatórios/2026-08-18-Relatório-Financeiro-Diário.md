# Relatório Financeiro Diário — 2026-08-18

**Ao DigitalCEO**  
**Base BRT:** 18/08/2026, 08:00  
**Vendas do dia anterior:** 17/08/2026  
**Janela de vencimentos:** 18–25/08/2026

## Resumo financeiro

- **Vendas aprovadas — SQL:** **41 pedidos | R$ 129.302,07 | ticket médio R$ 3.153,71**.
- **Pagar.me aprovado:** **32 cobranças | R$ 97.295,88 | ticket médio R$ 3.040,50**.
- **Diferença SQL × Pagar.me:** **R$ 32.006,19** (**24,75%** do SQL). Fontes têm escopos distintos; diferença requer conciliação, não é perda presumida.
- **Variação Pagar.me contra 16/08:** **+R$ 82.789,61 | +570,72%**; de 17 para 32 cobranças.
- **Pagar.me por loja:** SSL **10 | R$ 62.717,74**; GCL **14 | R$ 31.523,90**; ACL **8 | R$ 3.054,24**; BRG **R$ 0,00**.
- **Pagar.me por meio:** cartão **20 | R$ 66.278,45**; PIX **12 | R$ 31.017,43**.
- **Qualidade Pagar.me:** **28 OK | R$ 93.931,98**; **2 suspeitas | R$ 2.029,00**; **2 revisar | R$ 1.334,90**. Exposição sob análise: **R$ 3.363,90**.
- **Oracle/DEBX — sem somar às vendas acima:** PED status X/expedido **99 | R$ 10.537,27**; status A **13 | R$ 6.965,03**; venda física `MOV_NATIND=100` **234 movimentos | R$ 9.953,12**.

## Alertas de vencimentos

- **Contas a pagar 18–25/08:** base oficial atual **não localizada no Vault**. **Saldo semanal de saída indisponível; não significa saldo zero.**
- **Contas a receber ACL 18–25/08 — Oracle:** **766 títulos | R$ 85.940,04**.
- **Pico da janela:** 24/08 — **260 títulos | R$ 30.359,26**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 18/08 | 167 | R$ 16.927,41 |
| 19/08 | 75 | R$ 8.566,09 |
| 20/08 | 98 | R$ 11.309,98 |
| 21/08 | 87 | R$ 9.430,29 |
| 22/08 | 0 | R$ 0,00 |
| 23/08 | 2 | R$ 566,69 |
| 24/08 | 260 | R$ 30.359,26 |
| 25/08 | 77 | R$ 8.780,32 |

- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. Exposição histórica: **R$ 109.222,37** — não classificada como vencimento atual.

## Inadimplência

- **ACL — títulos vencidos sem baixa no Oracle:** **5.154 títulos | R$ 617.761,93**.
- **1–30 dias:** **1.432 | R$ 311.096,93**.
- **31–60 dias:** **23 | R$ 23.997,81**.
- **61–90 dias:** **20 | R$ 19.757,51**.
- **Acima de 90 dias:** **3.679 | R$ 262.909,68**.
- **Índice bruto:** **42,40%** do saldo aberto ACL de **R$ 1.456.817,27** aparece vencido. Indicador operacional, não contábil definitivo; pode conter baixas não processadas.

## Recomendações

1. **Revisar hoje os R$ 3.363,90 do Pagar.me**, principalmente as 2 cobranças suspeitas de mesmo cliente e mesmo valor (**R$ 2.029,00**).
2. **Cobrança:** priorizar **R$ 16.927,41** com vencimento hoje e **R$ 311.096,93** vencidos há até 30 dias.
3. **Preparar caixa para 24/08:** concentração de recebíveis de **R$ 30.359,26**; acompanhar realização e baixas.
4. **Obter a posição oficial de contas a pagar de 18–25/08**; sem ela, o risco de caixa semanal não é mensurável.
5. **Validar baixas do aging ACL** antes de usar os **42,40%** como inadimplência oficial e confirmar os **R$ 109.222,37** históricos.

## Fontes validadas

- Pagar.me v5: artefato consolidado gerado nesta execução; aprovações de 17/08/2026.
- SQL Server `hotel-finder`: sessão, schema e colunas validados; fonte atualizada até 17/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: recebíveis e aging somente da ACL; não consolida outros schemas.
- Vault: nenhuma base oficial atual de contas a pagar localizada. Gmail/e-mail não utilizado por restrição do perfil.
