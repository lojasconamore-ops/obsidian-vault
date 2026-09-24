# Relatório Financeiro Diário — 2026-09-24

**Ao DigitalCEO**  
**Base BRT:** 24/09/2026, 08:04  
**Vendas do dia anterior:** 23/09/2026  
**Janela de vencimentos:** 24–30/09/2026

## Resumo financeiro

- **Pagar.me — aprovações em 23/09:** **34 cobranças | R$ 41.789,57 | ticket médio R$ 1.229,11**.
- **Variação diária Pagar.me:** **-R$ 34.873,96 | -45,49%** contra 22/09.
- **Qualidade Pagar.me:** **32 OK | R$ 39.086,22**; **0 suspeitas**; **2 revisar | R$ 2.703,35** (**6,47%** do valor aprovado).
- **Por loja:** SSL **23 | R$ 33.934,49**; ACL **8 | R$ 3.992,28**; GCL **3 | R$ 3.862,80**; BRG **0**.
- **Por meio:** cartão **20 | R$ 20.740,53**; PIX **12 | R$ 17.402,82**; boleto **2 | R$ 3.646,22**.
- **SQL Server:** fonte atualizada somente até **22/09/2026**. Vendas aprovadas de 23/09 **indisponíveis por defasagem da fonte**, não interpretadas como zero.
- **Oracle/DEBX — PED em 23/09, separado:** status X/expedido **84 | R$ 10.702,37**; status A **8 | R$ 4.364,20**. Venda física `MOV_NATIND=100`: **190 movimentos | R$ 9.923,38**. PED não representa venda física.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual **não localizada no Vault nem no Google Drive**, após **6 buscas atuais**. Total confirmado indisponível; **não significa saldo zero**.
- **Contas a receber ACL — 24–30/09:** **632 títulos | R$ 139.504,51**.
- **Vencendo hoje, 24/09:** **129 títulos | R$ 13.765,69** — **9,87%** da janela semanal.
- Demais: 25/09 **69 | R$ 9.333,24**; 26/09 **3 | R$ 221,58**; 27/09 **3 | R$ 1.065,93**; 28/09 **271 | R$ 38.733,82**; 29/09 **83 | R$ 8.316,15**; 30/09 **74 | R$ 68.068,10**.
- **Maior concentração:** 30/09, **R$ 68.068,10** — **48,79%** da janela.
- **Pagar.me/SSL:** 2 cobranças do mesmo cliente em 28 minutos, pedidos e valores diferentes, total **R$ 2.703,35**. Classificação: **REVISAR**, sem duplicidade confirmada.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.780 | R$ 293.415,80**.
- **Índice bruto:** **22,55%** do saldo aberto ACL de **R$ 1.301.294,19**.
- **1–30 dias:** **72 | R$ 5.882,37**.
- **31–60 dias:** **6 | R$ 2.085,35**.
- **61–90 dias:** **8 | R$ 2.174,58**.
- **Acima de 90 dias:** **3.694 | R$ 283.273,50** — **96,54%** do vencido.
- **Vencidos em 23/09 ainda sem baixa:** **28 títulos | R$ 3.149,50**.
- **Variação contra o relatório anterior:** **-8 títulos | -R$ 397,07** no vencido; saldo aberto **+R$ 309,57**.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança imediata:** priorizar os **R$ 3.149,50** vencidos em 23/09 e os **R$ 5.882,37** da faixa de 1–30 dias.
2. **Preparar 30/09:** antecipar cobrança da concentração de **R$ 68.068,10**; segunda concentração em 28/09, **R$ 38.733,82**.
3. **Revisar Pagar.me/SSL:** validar as 2 cobranças, total **R$ 2.703,35**, antes do fechamento da conciliação.
4. **Restabelecer conciliação:** cobrar atualização do SQL Server para 23/09; hoje não há comparação confiável SQL x Pagar.me.
5. **Aging:** separar legado, atraso real e baixa pendente nos **R$ 283.273,50** acima de 90 dias.
6. **Contas a pagar:** obter a posição oficial antes de autorizar desembolsos; a base corrente não foi localizada.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 23/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 22/09 validados; somente leitura.
- Oracle `conamore`: sessão e colunas validadas; PED, venda física e `TEST_ACL.F_TITULOS` separados; somente leitura.
- `F_TITULOS`: recebíveis e aging somente da ACL; não consolida outros schemas.
- Vault e Google Drive: buscas atuais sem base oficial de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
