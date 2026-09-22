# Relatório Financeiro Diário — 2026-09-22

**Ao DigitalCEO**  
**Base BRT:** 22/09/2026, 08:01  
**Vendas do dia anterior:** 21/09/2026  
**Janela de vencimentos:** 22–28/09/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas em 21/09:** **47 pedidos | R$ 83.010,57 | ticket médio R$ 1.766,18**.
- **Outros status no SQL:** Expedição **2 | R$ 3.674,77**; status D **1 | R$ 2.602,50**. Não somados às vendas aprovadas.
- **Pagar.me — aprovações em 21/09:** **39 cobranças | R$ 59.751,90 | ticket médio R$ 1.532,10**.
- **Qualidade Pagar.me:** **37 OK | R$ 55.356,70**; **0 suspeitas**; **2 revisar | R$ 4.395,20** (**7,36%** do valor aprovado).
- **Por loja:** SSL **15 | R$ 43.030,96**; GCL **6 | R$ 10.705,02**; ACL **18 | R$ 6.015,92**; BRG **0**.
- **Por meio:** cartão **24 | R$ 41.361,07**; PIX **15 | R$ 18.390,83**.
- **SQL x Pagar.me:** diferença de escopo de **R$ 23.258,67**; fontes **não conciliadas** nesta execução. SQL inclui vendas aprovadas fora do consolidado Pagar.me.
- **Oracle/DEBX — PED em 21/09, separado:** status X/expedido **104 | R$ 9.764,39**; status A **15 | R$ 5.671,81**. Venda física `MOV_NATIND=100`: **230 movimentos | R$ 9.592,92**. PED não representa venda física.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual **não localizada no Vault nem no Google Drive**. Total confirmado indisponível; **não significa saldo zero**.
- **Contas a receber ACL — 22–28/09:** **637 títulos | R$ 81.654,81**.
- **Vencendo hoje, 22/09:** **161 títulos | R$ 16.211,56** — **19,85%** da janela semanal.
- Demais: 23/09 **63 | R$ 8.924,58**; 24/09 **67 | R$ 7.164,10**; 25/09 **69 | R$ 9.333,24**; 26/09 **3 | R$ 221,58**; 27/09 **3 | R$ 1.065,93**; 28/09 **271 | R$ 38.733,82**.
- **Maior concentração:** 28/09, **R$ 38.733,82** — **47,44%** da janela.
- **Pagar.me/GCL:** 2 PIX do mesmo cliente, pedidos e valores diferentes, aprovados com 10 minutos de intervalo; exposição **R$ 4.395,20**. Classificação: **REVISAR**, sem duplicidade confirmada.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.842 | R$ 301.966,99**.
- **Índice bruto:** **23,59%** do saldo aberto ACL de **R$ 1.280.127,16**.
- **1–30 dias:** **136 | R$ 16.091,66**.
- **31–60 dias:** **4 | R$ 427,25**.
- **61–90 dias:** **17 | R$ 20.989,97**.
- **Acima de 90 dias:** **3.685 | R$ 264.458,11** — **87,58%** do vencido.
- **Vencidos em 21/09 ainda sem baixa:** **104 títulos | R$ 11.866,19**.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança imediata:** priorizar os **R$ 11.866,19** vencidos em 21/09 e os **R$ 16.091,66** da faixa de 1–30 dias.
2. **Preparar 28/09:** confirmar cobrança e capacidade de caixa para a concentração de **R$ 38.733,82** em recebíveis.
3. **Revisar Pagar.me/GCL:** validar os 2 PIX, total **R$ 4.395,20**, antes do fechamento da conciliação.
4. **Conciliar canais:** explicar a diferença SQL x Pagar.me de **R$ 23.258,67** por origem/forma de pagamento.
5. **Aging:** separar atraso real, baixa pendente e legado nos **R$ 264.458,11** acima de 90 dias.
6. **Contas a pagar:** obter a posição oficial antes de autorizar desembolsos; a base atual não foi localizada.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 21/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 21/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: recebíveis e aging somente da ACL; não consolida outros schemas.
- Vault e Google Drive: seis buscas financeiras atuais, sem base oficial de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
