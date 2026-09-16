# Relatório Financeiro Diário — 2026-09-16

**Ao DigitalCEO**  
**Base BRT:** 16/09/2026, 08:02  
**Vendas do dia anterior:** 15/09/2026  
**Janela financeira:** 16–23/09/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas em 15/09:** **46 pedidos | R$ 68.512,80 | ticket médio R$ 1.489,41**.
- **Pagar.me — aprovações em 15/09:** **41 cobranças | R$ 45.406,10 | ticket médio R$ 1.107,47**.
- **Qualidade Pagar.me:** **41 OK | 0 suspeitas | 0 revisar**.
- **Por loja/Pagar.me:** SSL **10 | R$ 30.303,57**; ACL **29 | R$ 12.174,29**; GCL **2 | R$ 2.928,24**; BRG **0**.
- **Por meio/Pagar.me:** cartão **28 | R$ 35.865,37**; PIX **12 | R$ 6.158,31**; boleto **1 | R$ 3.382,42**.
- **Diferença SQL x Pagar.me:** SQL **R$ 23.106,70 acima** (**+50,89%** sobre Pagar.me). **Não somar as fontes.**
- **Oracle/DEBX — PED em 15/09, separado:** status **X/expedido 98 | R$ 9.824,23**; status **A 22 | R$ 9.093,18**; status **F 1 | R$ 315,06**. Venda física `MOV_NATIND=100`: **238 movimentos | R$ 9.795,67**.

## Alertas de vencimentos

- **Contas a pagar 16–23/09:** base oficial atual **não localizada no Vault nem no Google Drive** após 6 buscas por metadados financeiros. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL — 16–23/09:** **736 títulos | R$ 107.959,72**.
- **Vencendo hoje, 16/09:** **151 títulos | R$ 17.601,12 — 16,30% da janela**.
- **Maior concentração:** **21/09 | 264 títulos | R$ 52.695,28 — 48,81% da janela**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 16/09 | 151 | R$ 17.601,12 |
| 17/09 | 98 | R$ 9.930,17 |
| 18/09 | 78 | R$ 9.122,02 |
| 19/09 | 1 | R$ 863,83 |
| 20/09 | 4 | R$ 306,54 |
| 21/09 | 264 | R$ 52.695,28 |
| 22/09 | 77 | R$ 8.577,36 |
| 23/09 | 63 | R$ 8.863,40 |

## Inadimplência

- **Títulos vencidos sem baixa:** **3.916 | R$ 322.457,25**.
- **Índice bruto:** **24,53%** do saldo aberto ACL de **R$ 1.314.615,96**.
- **1–30 dias:** **211 | R$ 36.581,96**.
- **31–60 dias:** **4 | R$ 594,11**.
- **61–90 dias:** **17 | R$ 20.989,92**.
- **Acima de 90 dias:** **3.684 | R$ 264.291,26 — 81,96% do vencido**.
- **Variação versus 15/09:** **-61 títulos | -R$ 18.901,26** no vencido.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança hoje:** atacar **R$ 36.581,96** vencidos há até 30 dias e acompanhar **R$ 17.601,12** com vencimento em 16/09.
2. **Preparar 21/09:** antecipar cobrança/baixa de **R$ 52.695,28**.
3. **Aging:** separar atraso real, baixa pendente e legado nos **R$ 264.291,26** acima de 90 dias.
4. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos da semana.
5. **Conciliação:** explicar a diferença de **R$ 23.106,70** entre SQL e Pagar.me por competência, canal e meio; não somar as bases.
6. **Pagar.me:** movimento de 15/09 limpo; manter pendente apenas a validação das **4 cobranças antigas | R$ 6.147,72** sinalizadas em 11–12/09, sem estorno automático.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 15/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 15/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Vault e Google Drive: nenhuma base oficial atual de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
