# Relatório Financeiro Diário — 2026-09-26

**Ao DigitalCEO**  
**Base BRT:** 26/09/2026, 08:07  
**Vendas analisadas:** 25/09/2026  
**Janela de vencimentos:** 26/09–02/10/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas em 25/09:** **53 pedidos | R$ 238.905,50 | ticket médio R$ 4.507,65**.
- Outros status, não somados: Expedição **1 | R$ 2.866,68**; Financeiro **1 | R$ 1.709,41**.
- **Pagar.me — aprovações em 25/09:** **44 cobranças | R$ 73.938,98 | ticket médio R$ 1.680,43**.
- **Variação diária Pagar.me:** **+R$ 18.231,40 | +32,73%** contra 24/09.
- **Qualidade Pagar.me:** **42 OK | R$ 66.063,93**; **0 suspeitas**; **2 revisar | R$ 7.875,05** (**10,65%**).
- **Por loja:** SSL **33 | R$ 42.410,38**; ACL **11 | R$ 31.528,60**; GCL **0**; BRG **0**.
- **Por meio:** cartão **29 | R$ 49.036,61**; PIX **13 | R$ 18.844,01**; boleto **2 | R$ 6.058,36**.
- **SQL x Pagar.me:** diferença de escopo de **R$ 164.966,52**; fontes não conciliadas nesta execução.
- **Oracle/DEBX — separado:** PED status X/expedido **106 | R$ 25.764,23**; status A **12 | R$ 32.400,16**; status F **1 | R$ 630,87**. Venda física `MOV_NATIND=100`: **210 movimentos | R$ 16.451,63**. PED não representa venda física.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual não localizada no Vault. Google Drive sem autenticação disponível; e-mail não utilizado por restrição do perfil. Total confirmado indisponível — não significa saldo zero.
- **Contas a receber ACL — 26/09 a 02/10:** **638 títulos | R$ 90.205,81**.
- 26/09: **70 | R$ 8.787,15**.
- 27/09: **4 | R$ 1.937,49**.
- 28/09: **259 | R$ 35.111,70** — **38,92%** da janela.
- 29/09: **83 | R$ 8.316,15**.
- 30/09: **70 | R$ 7.499,45**.
- 01/10: **82 | R$ 17.438,39**.
- 02/10: **70 | R$ 11.115,48**.
- **Pagar.me/ACL — revisão prioritária:** mesma cliente teve uma cobrança de **R$ 7.875,05** e, depois, duas cobranças de **R$ 2.899,60 + R$ 4.975,45**, cuja soma repete exatamente **R$ 7.875,05**. Exposição total do conjunto: **R$ 15.750,10**. Duplicidade não confirmada.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.803 | R$ 295.104,11**.
- **Índice bruto:** **23,39%** do saldo aberto ACL de **R$ 1.261.661,99**.
- **1–30 dias:** **94 | R$ 7.450,74**.
- **31–60 dias:** **6 | R$ 2.085,35**.
- **61–90 dias:** **9 | R$ 2.294,52**.
- **Acima de 90 dias:** **3.694 | R$ 283.273,50** — **95,99%** do vencido.
- **Vencidos em 25/09 ainda sem baixa:** **49 | R$ 2.983,85**.
- **Variação contra 24/09:** **+23 títulos | +R$ 1.688,31** no vencido; índice bruto **+0,84 p.p.**
- Indicador operacional sujeito a baixas posteriores; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Bloquear conclusão da conciliação** das 3 cobranças da mesma cliente até validar se houve substituição/fracionamento ou duplicidade; possível exposição duplicada: **R$ 7.875,05**.
2. **Cobrança imediata:** atuar nos **R$ 2.983,85** vencidos em 25/09 e nos **R$ 7.450,74** da faixa de 1–30 dias.
3. **Preparar 28/09:** antecipar cobrança dos **R$ 35.111,70**; segunda concentração em 01/10, **R$ 17.438,39**.
4. **Conciliar SQL x Pagar.me:** investigar a diferença de **R$ 164.966,52** por canal, origem e condição de pagamento; não tratar as fontes como equivalentes.
5. **Aging:** separar legado, atraso real e baixa pendente nos **R$ 283.273,50** acima de 90 dias.
6. **Contas a pagar:** obter a posição oficial antes de autorizar desembolsos; nenhuma base corrente foi localizada.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 25/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e atualização até 26/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_PED`: sessão e colunas validadas; PED, venda física e `TEST_ACL.F_TITULOS` separados; somente leitura.
- `F_TITULOS`: recebíveis e aging somente da ACL; não consolida outros schemas.
- Vault: busca atual sem base oficial de contas a pagar localizada. Google Drive não autenticado nesta execução.
