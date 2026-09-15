# Relatório Financeiro Diário — 2026-09-15

**Ao DigitalCEO**  
**Base BRT:** 15/09/2026, 08:00  
**Vendas do dia anterior:** 14/09/2026  
**Janela financeira:** 15–22/09/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas em 14/09:** **43 pedidos | R$ 44.612,80 | ticket médio R$ 1.037,51**.
- **Pagar.me — aprovações em 14/09:** **39 cobranças | R$ 45.560,86 | ticket médio R$ 1.168,23**.
- **Qualidade Pagar.me:** **39 OK | 0 suspeitas | 0 revisar**.
- **Por loja/Pagar.me:** SSL **15 | R$ 27.615,33**; ACL **19 | R$ 11.843,63**; GCL **5 | R$ 6.101,90**; BRG **0**.
- **Por meio/Pagar.me:** cartão **29 | R$ 38.918,17**; PIX **10 | R$ 6.642,69**.
- **Diferença SQL x Pagar.me:** SQL **R$ 948,06 abaixo** (**-2,08%** sobre Pagar.me). **Não somar as fontes.**
- **Oracle/DEBX — PED em 14/09, separado:** status **X/expedido 87 | R$ 10.247,21**; status **A 24 | R$ 14.114,23**. Venda física `MOV_NATIND=100`: **218 movimentos | R$ 10.275,15**.

## Alertas de vencimentos

- **Contas a pagar 15–22/09:** base oficial atual **não localizada no Vault**; Google Drive **sem autenticação disponível nesta execução**. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL — 15–22/09:** **739 títulos | R$ 105.993,98**.
- **Vencendo hoje, 15/09:** **148 títulos | R$ 16.228,12**.
- **Maior concentração:** **21/09 | 265 títulos | R$ 52.792,13 — 49,81% da janela**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 15/09 | 148 | R$ 16.228,12 |
| 16/09 | 70 | R$ 8.833,54 |
| 17/09 | 96 | R$ 9.270,44 |
| 18/09 | 78 | R$ 9.122,02 |
| 19/09 | 1 | R$ 863,83 |
| 20/09 | 4 | R$ 306,54 |
| 21/09 | 265 | R$ 52.792,13 |
| 22/09 | 77 | R$ 8.577,36 |

## Inadimplência

- **Títulos vencidos sem baixa:** **3.977 | R$ 341.358,51**.
- **Índice bruto:** **25,71%** do saldo aberto ACL de **R$ 1.327.638,87**.
- **1–30 dias:** **272 | R$ 55.483,22**.
- **31–60 dias:** **4 | R$ 594,11**.
- **61–90 dias:** **17 | R$ 20.989,92**.
- **Acima de 90 dias:** **3.684 | R$ 264.291,26 — 77,42% do vencido**.
- **Variação versus 14/09:** **-14 títulos | +R$ 3.028,81** no vencido.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança hoje:** atacar **R$ 55.483,22** vencidos há até 30 dias e acompanhar **R$ 16.228,12** com vencimento em 15/09.
2. **Preparar 21/09:** antecipar cobrança/baixa de **R$ 52.792,13**.
3. **Aging:** separar atraso real, baixa pendente e legado nos **R$ 264.291,26** acima de 90 dias.
4. **Revisão Pagar.me:** movimento de 14/09 está limpo; confirmar a resolução das **4 cobranças antigas | R$ 6.147,72** sinalizadas em 11–12/09 antes de qualquer estorno.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos da semana.
6. **Conciliação:** explicar a diferença de **R$ 948,06** entre SQL e Pagar.me por competência, canal e meio; não somar as bases.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 14/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 14/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Vault: nenhuma base oficial atual de contas a pagar localizada.
- Google Drive: autenticação indisponível nesta execução.
- Gmail/e-mail não utilizado por restrição do perfil.
