# Relatório Financeiro Diário — 2026-08-25

**Ao DigitalCEO**  
**Base BRT:** 25/08/2026, 08:01  
**Vendas do dia anterior:** 24/08/2026  
**Janela de vencimentos:** 25/08–01/09/2026

## Resumo financeiro

- **Pagar.me — aprovadas:** **37 cobranças | R$ 92.493,66 | ticket médio R$ 2.499,83**.
- **Qualidade:** **35 OK | R$ 91.828,36**; **2 revisar | R$ 665,30**; **0 suspeitas**.
- **Por loja:** SSL **17 | R$ 75.317,81**; GCL **7 | R$ 10.213,74**; ACL **13 | R$ 6.962,11**; BRG **0 | R$ 0,00**.
- **Por meio:** cartão **21 | R$ 66.835,12**; PIX **12 | R$ 18.596,53**; boleto **4 | R$ 7.062,01**.
- **SQL Server — vendas confirmadas:** **43 pedidos | R$ 118.748,35**; sendo Aprovado **38 | R$ 90.160,36** e Expedição **5 | R$ 28.587,99**. Fonte atualizada até 24/08.
- **Overlay bruto DEBX/SQL:** Cancelado **13 | R$ 98.025,55**; não incluído nas vendas confirmadas.
- **Oracle/DEBX — PED, sem somar ao Pagar.me:** status X/expedido **80 | R$ 9.164,79**; status A **16 | R$ 8.723,83**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **152 movimentos | R$ 8.230,73**.

## Alertas de vencimentos

- **Contas a pagar 25/08–01/09:** base oficial atual **não localizada** no Vault nem no Google Drive por buscas de metadados; **não significa saldo zero**.
- **Contas a receber ACL:** **731 títulos | R$ 101.067,20**.
- **Vencendo hoje:** **141 títulos | R$ 13.822,97**.
- **Pico:** **31/08 | 280 títulos | R$ 47.596,43** — **47,09%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 25/08 | 141 | R$ 13.822,97 |
| 26/08 | 56 | R$ 7.375,13 |
| 27/08 | 87 | R$ 10.165,99 |
| 28/08 | 89 | R$ 9.885,01 |
| 29/08 | 2 | R$ 3.120,41 |
| 30/08 | 1 | R$ 73,80 |
| 31/08 | 280 | R$ 47.596,43 |
| 01/09 | 75 | R$ 9.027,46 |

## Inadimplência

- **Títulos vencidos sem baixa:** **4.461 | R$ 444.522,92**.
- **1–30 dias:** **743 | R$ 156.560,51**.
- **31–60 dias:** **16 | R$ 3.860,29**.
- **61–90 dias:** **19 | R$ 20.682,14**.
- **Acima de 90 dias:** **3.683 | R$ 263.419,98**.
- **Índice bruto:** **34,34%** do saldo aberto ACL de **R$ 1.294.644,90**. Indicador operacional; sujeito a baixas ainda não processadas.

## Recomendações

1. **Cobrança hoje:** priorizar **R$ 13.822,97** vencendo em 25/08 e **R$ 156.560,51** vencidos há até 30 dias.
2. **Revisão Pagar.me:** validar 2 cartões do cliente Otavio Santos Viotto, pedidos distintos, aprovados com 4 minutos de intervalo, total **R$ 665,30**; não estornar sem confirmação.
3. **Caixa:** localizar a base oficial de contas a pagar antes de autorizar a programação dos próximos 7 dias.
4. **Programar 31/08:** acompanhar a concentração de **R$ 47.596,43** em recebíveis.
5. **Conciliação:** explicar a diferença Pagar.me × SQL por escopo/canal; não somar as fontes.
6. **Aging:** validar baixas antes de tratar **34,34%** como inadimplência contábil definitiva.

## Fontes validadas

- Pagar.me v5: artefato consolidado gerado nesta execução; aprovação em 24/08/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; seis buscas recentes por metadados financeiros, sem arquivo candidato.
- Gmail/e-mail não utilizado por restrição do perfil.
