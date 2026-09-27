# Relatório Financeiro Diário — 2026-09-27

**Ao DigitalCEO**  
**Base BRT:** 27/09/2026, 08:01  
**Vendas analisadas:** 26/09/2026  
**Janela de vencimentos:** 27/09–03/10/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas em 26/09:** **19 pedidos | R$ 10.804,86 | ticket médio R$ 568,68**.
- **Pagar.me — aprovações em 26/09:** **19 cobranças | R$ 10.804,84 | ticket médio R$ 568,68**.
- **Conciliação SQL x Pagar.me:** diferença de **R$ 0,02**; volume e quantidade conciliados.
- **Variação diária Pagar.me:** **-R$ 63.134,14 | -85,39%** contra 25/09. Movimento de sábado; validar retomada na segunda-feira antes de classificar como desvio.
- **Qualidade Pagar.me:** **19 OK | R$ 10.804,84**; **0 suspeitas**; **0 revisar**.
- **Por loja:** SSL **18 | R$ 9.933,28**; ACL **1 | R$ 871,56**; GCL **0**; BRG **0**.
- **Por meio:** cartão **13 | R$ 9.071,37**; PIX **6 | R$ 1.733,47**; boleto **0**.
- **Oracle/DEBX — separado:** PED status **X/expedido 76 | R$ 9.822,11**. Venda física `MOV_NATIND=100`: **193 movimentos | R$ 9.679,15**. PED não representa venda física.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual não localizada no Vault. E-mail não utilizado por restrição do perfil. Total confirmado indisponível — não significa saldo zero.
- **Contas a receber ACL — 27/09 a 03/10:** **624 títulos | R$ 99.033,36**.
- 27/09: **58 | R$ 6.665,54**.
- 28/09: **259 | R$ 35.111,70** — **35,45%** da janela.
- 29/09: **83 | R$ 8.316,15**.
- 30/09: **70 | R$ 7.499,45**.
- 01/10: **82 | R$ 17.438,39**.
- 02/10: **70 | R$ 11.115,48**.
- 03/10: **2 | R$ 12.886,65**.
- **Pendência Pagar.me de 25/09:** conjunto de **R$ 15.750,10**, com possível duplicidade de **R$ 7.875,05**, segue sem resolução localizada. O movimento de 26/09 fechou limpo.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.874 | R$ 304.067,06**.
- **Índice bruto:** **23,91%** do saldo aberto ACL de **R$ 1.271.730,93**.
- **1–30 dias:** **164 | R$ 16.331,99**.
- **31–60 dias:** **7 | R$ 2.167,05**.
- **61–90 dias:** **8 | R$ 1.667,52**.
- **Acima de 90 dias:** **3.695 | R$ 283.900,50** — **93,37%** do vencido.
- **Vencidos em 26/09 ainda sem baixa:** **71 | R$ 8.962,95**.
- **Variação contra 26/09:** **+71 títulos | +R$ 8.962,95** no vencido; índice bruto **+0,52 p.p.**
- Indicador operacional sujeito a baixas posteriores; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança imediata:** atuar nos **R$ 8.962,95** vencidos em 26/09 e nos **R$ 16.331,99** da faixa de 1–30 dias.
2. **Preparar 28/09:** antecipar cobrança e conferência de baixas dos **R$ 35.111,70**; segunda concentração em 01/10, **R$ 17.438,39**.
3. **Pagar.me:** manter bloqueada a conclusão da conciliação do conjunto de 25/09 até validar a possível duplicidade de **R$ 7.875,05**.
4. **Aging:** separar legado, atraso real e baixa pendente nos **R$ 283.900,50** acima de 90 dias.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos da semana.
6. **Segunda-feira:** confirmar retomada de vendas; a queda de **85,39%** ocorreu no sábado e não deve ser escalada isoladamente.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 26/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e atualização até 26/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_PED`: sessão e colunas validadas; PED, venda física e `TEST_ACL.F_TITULOS` separados; somente leitura.
- `F_TITULOS`: recebíveis e aging somente da ACL; não consolida outros schemas.
- Vault: busca atual sem base oficial de contas a pagar localizada. Gmail/e-mail não utilizado.
