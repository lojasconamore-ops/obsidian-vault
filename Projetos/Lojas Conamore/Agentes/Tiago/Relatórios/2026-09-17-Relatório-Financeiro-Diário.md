# Relatório Financeiro Diário — 2026-09-17

**Ao DigitalCEO**  
**Base BRT:** 17/09/2026, 08:01  
**Vendas do dia anterior:** 16/09/2026  
**Janela de recebíveis:** 17–24/09/2026

## Resumo financeiro

- **SQL Server — vendas confirmadas em 16/09:** **59 pedidos | R$ 94.944,51 | ticket médio R$ 1.609,23**. Status: Aprovado **58 | R$ 94.541,51**; Expedição **1 | R$ 403,00**.
- **Pagar.me — aprovações em 16/09:** **62 cobranças | R$ 99.835,63 | ticket médio R$ 1.610,25**.
- **Qualidade Pagar.me:** **62 OK | 0 suspeitas | 0 revisar**.
- **Por loja/Pagar.me:** SSL **20 | R$ 59.185,89**; GCL **9 | R$ 24.724,86**; ACL **33 | R$ 15.924,88**; BRG **0**.
- **Por meio/Pagar.me:** cartão **40 | R$ 74.649,23**; PIX **22 | R$ 25.186,40**.
- **Diferença SQL x Pagar.me:** Pagar.me **R$ 4.891,12 acima** (**+5,15%** sobre SQL). **Não somar as fontes**: possuem escopos/status distintos.
- **Oracle/DEBX — PED em 16/09, separado:** status **A 31 | R$ 15.350,72**; status **X/expedido 126 | R$ 11.324,78**. Venda física `MOV_NATIND=100`: **272 movimentos | R$ 10.542,27**.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual **não localizada** no Vault/Drive. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL — 17–24/09:** **754 títulos | R$ 110.293,30**.
- **Vencendo hoje, 17/09:** **197 títulos | R$ 22.277,84**.
- **Maior concentração:** **21/09 | 263 títulos | R$ 29.973,54**.
- Demais: 18/09 **82 | R$ 32.266,69**; 19/09 **1 | R$ 863,83**; 20/09 **4 | R$ 306,54**; 22/09 **77 | R$ 8.577,36**; 23/09 **63 | R$ 8.863,40**; 24/09 **67 | R$ 7.164,10**.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.830 | R$ 303.332,38**.
- **Índice bruto:** **23,23%** do saldo aberto ACL de **R$ 1.305.738,26**.
- **1–30 dias:** **125 | R$ 17.457,09**.
- **31–60 dias:** **4 | R$ 594,11**.
- **61–90 dias:** **16 | R$ 20.823,07**.
- **Acima de 90 dias:** **3.685 | R$ 264.458,11 — 87,19% do vencido**.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança hoje:** atuar sobre **R$ 17.457,09** vencidos até 30 dias e acompanhar **R$ 22.277,84** com vencimento em 17/09.
2. **Preparar 21/09:** priorizar cobrança/baixa de **R$ 29.973,54**.
3. **Aging:** separar atraso real, baixa pendente e legado nos **R$ 264.458,11** acima de 90 dias.
4. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos da semana.
5. **Conciliação:** explicar a diferença de **R$ 4.891,12** entre SQL e Pagar.me por competência, canal e status; não somar bases.
6. **Pagar.me:** movimento de 16/09 sem flags; manter conciliação diária por loja e método.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 16/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 16/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: buscas atuais por contas/vencer/títulos/inadimplência/pagar não localizaram base financeira; resultados com “Financeiro” eram imagens de 2025.
- Gmail/e-mail não utilizado por restrição do perfil.
