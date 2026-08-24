# Relatório Financeiro Diário — 2026-08-24

**Ao DigitalCEO**  
**Base BRT:** 24/08/2026, 08:01  
**Vendas do dia anterior:** 23/08/2026  
**Janela Pagar.me de segunda-feira:** 21–23/08/2026  
**Janela de vencimentos:** 24–31/08/2026

## Resumo financeiro

- **Pagar.me — 23/08:** **16 cobranças | R$ 9.806,79 | ticket médio R$ 612,92**; **16 OK | R$ 9.806,79**.
- **Pagar.me — fim de semana:** **64 cobranças | R$ 90.150,80 | ticket médio R$ 1.408,61**.
- **Por dia:** 21/08 **33 | R$ 68.591,48**; 22/08 **15 | R$ 11.752,53**; 23/08 **16 | R$ 9.806,79**.
- **Por loja, fim de semana:** SSL **12 | R$ 51.586,37**; GCL **13 | R$ 20.643,92**; ACL **39 | R$ 17.920,51**; BRG **0 | R$ 0,00**.
- **Por meio, fim de semana:** PIX **28 | R$ 49.195,25**; cartão **36 | R$ 40.955,55**.
- **Qualidade Pagar.me:** **59 OK | R$ 57.478,99**; **5 revisar | R$ 32.671,81**; **0 suspeitas**. As 5 revisões são de 21/08 e representam **36,24%** do total do fim de semana.
- **Revisões:** José Wilson Silveira **3 PIX | R$ 29.890,86**; Douglas Rautemberg Fortaleza **2 PIX | R$ 2.780,95**.
- **SQL Server:** fonte atualizada até **22/08**, portanto não há fechamento confiável de 23/08. Última posição: **14 pedidos aprovados | R$ 11.220,01** em 22/08.
- **Oracle/DEBX — 23/08, sem somar ao Pagar.me:** PED status A **13 | R$ 7.467,21**; status X/expedido **0**; venda física `MOV_NATIND=100` **0 movimentos**.

## Alertas de vencimentos

- **Contas a pagar 24–31/08:** base oficial atual **não localizada no Vault**; Google Workspace local sem autenticação. **Saídas confirmadas indisponíveis; não significa saldo zero.**
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. Exposição histórica: **R$ 109.222,37** — não classificada como saldo atual.
- **Contas a receber ACL 24–31/08 — Oracle:** **855 títulos | R$ 117.699,26**.
- **Vencendo hoje:** **265 títulos | R$ 32.828,12**.
- **Pico da janela:** **31/08 | 280 títulos | R$ 47.596,43**, equivalente a **40,44%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 24/08 | 265 | R$ 32.828,12 |
| 25/08 | 78 | R$ 8.901,25 |
| 26/08 | 55 | R$ 6.591,18 |
| 27/08 | 85 | R$ 8.703,06 |
| 28/08 | 89 | R$ 9.885,01 |
| 29/08 | 2 | R$ 3.120,41 |
| 30/08 | 1 | R$ 73,80 |
| 31/08 | 280 | R$ 47.596,43 |

## Inadimplência

- **ACL — títulos vencidos sem baixa no Oracle:** **4.670 títulos | R$ 481.785,46**.
- **1–30 dias:** **950 | R$ 193.650,61**.
- **31–60 dias:** **21 | R$ 12.511,90**.
- **61–90 dias:** **19 | R$ 12.549,87**.
- **Acima de 90 dias:** **3.680 | R$ 263.073,08**.
- **Índice bruto:** **36,02%** do saldo aberto ACL de **R$ 1.337.677,30** aparece vencido. Indicador operacional; pode conter baixas ainda não processadas.

## Recomendações

1. **Cobrança hoje:** atuar sobre **R$ 32.828,12** vencendo em 24/08 e **R$ 193.650,61** vencidos há até 30 dias.
2. **Revisão Pagar.me:** confirmar os 5 PIX de **R$ 32.671,81** como pedidos distintos antes de qualquer estorno ou ajuste.
3. **Caixa:** obter a posição oficial de contas a pagar de 24–31/08 e validar a baixa dos **R$ 109.222,37** históricos.
4. **Programar 31/08:** reservar acompanhamento para **R$ 47.596,43** em recebíveis concentrados.
5. **Conciliação:** aguardar atualização do SQL de 23/08; não tratar ausência de linhas como venda zero.
6. **Aging:** validar baixas antes de usar os **36,02%** como inadimplência contábil definitiva.

## Fontes validadas

- Pagar.me v5: artefato consolidado gerado nesta execução; janela 21–23/08/2026.
- SQL Server `hotel-finder`: sessão, schema e colunas validados; fonte atualizada até 22/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Gmail/e-mail não utilizado por restrição do perfil.
