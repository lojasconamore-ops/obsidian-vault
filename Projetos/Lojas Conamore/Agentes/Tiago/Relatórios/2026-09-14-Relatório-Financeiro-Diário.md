# Relatório Financeiro Diário — 2026-09-14

**Ao DigitalCEO**  
**Base BRT:** 14/09/2026, 08:01  
**Vendas do dia anterior:** 13/09/2026  
**Janela Pagar.me de segunda-feira:** 11–13/09/2026  
**Janela financeira:** 14–21/09/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas em 13/09:** **55 pedidos | R$ 42.490,70 | ticket médio R$ 772,56**. Origem: **MAG**.
- **Pagar.me — 13/09:** **30 cobranças | R$ 24.157,25 | ticket médio R$ 805,24**.
- **Pagar.me — fim de semana 11–13/09:** **87 cobranças | R$ 90.346,61 | ticket médio R$ 1.038,47**.
- **Qualidade no fim de semana:** **83 OK | R$ 84.198,89**; **4 revisar | R$ 6.147,72**; **0 suspeitas**. Exposição em revisão: **6,80%**.
- **Por loja/fim de semana:** SSL **19 | R$ 49.612,42**; ACL **63 | R$ 31.881,81**; GCL **5 | R$ 8.852,38**; BRG **0**.
- **Por meio/fim de semana:** cartão **59 | R$ 74.268,94**; PIX **28 | R$ 16.077,67**.
- **13/09 sem flags:** **30 OK | R$ 24.157,25**. As **4 revisões** são de 11–12/09 e seguem pendentes de validação.
- **Diferença SQL x Pagar.me em 13/09:** SQL **R$ 17.288,04 acima** (**68,60%** sobre Pagar.me). **Não somar as fontes.**
- **Oracle/DEBX — PED em 13/09, separado:** status **A 24 | R$ 14.580,36**; status **X/expedido 0**. Venda física `MOV_NATIND=100`: **0 movimentos**.

## Alertas de vencimentos

- **Contas a pagar 14–21/09:** base oficial atual **não localizada no Vault**; Google Drive **sem autenticação disponível nesta execução**. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL — 14–21/09:** **917 títulos | R$ 128.826,44**.
- **Vencendo hoje, 14/09:** **314 títulos | R$ 38.341,31** — **29,76%** da janela.
- **Maior vencimento:** **21/09 | 265 títulos | R$ 52.792,13**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 14/09 | 314 | R$ 38.341,31 |
| 15/09 | 89 | R$ 9.296,63 |
| 16/09 | 70 | R$ 8.833,54 |
| 17/09 | 96 | R$ 9.270,44 |
| 18/09 | 78 | R$ 9.122,02 |
| 19/09 | 1 | R$ 863,83 |
| 20/09 | 4 | R$ 306,54 |
| 21/09 | 265 | R$ 52.792,13 |

## Inadimplência

- **Títulos vencidos sem baixa:** **3.991 | R$ 338.329,70**.
- **Índice bruto:** **25,48%** do saldo aberto ACL de **R$ 1.327.864,61**.
- **1–30 dias:** **285 | R$ 51.462,41**.
- **31–60 dias:** **5 | R$ 654,01**.
- **61–90 dias:** **17 | R$ 21.922,02**.
- **Acima de 90 dias:** **3.684 | R$ 264.291,26 — 78,12%** do vencido.
- **Variação versus 13/09:** **+36 títulos | +R$ 6.258,36** no vencido.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança hoje:** atacar **R$ 51.462,41** vencidos há até 30 dias e acompanhar **R$ 38.341,31** com vencimento em 14/09.
2. **Preparar 21/09:** antecipar cobrança/baixa de **R$ 52.792,13**.
3. **Revisão Pagar.me:** validar **4 cobranças antigas**, total **R$ 6.147,72**; não estornar sem confirmar os pedidos. O movimento de 13/09 está limpo.
4. **Aging:** separar atraso real, baixa pendente e legado nos **R$ 264.291,26** acima de 90 dias.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos da semana.
6. **Conciliação:** explicar os **R$ 17.288,04** de diferença SQL x Pagar.me por competência, canal e meio; não somar as bases.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 11–13/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 13/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Vault: nenhuma base oficial atual de contas a pagar localizada.
- Google Drive: autenticação indisponível nesta execução.
- Gmail/e-mail não utilizado por restrição do perfil.
