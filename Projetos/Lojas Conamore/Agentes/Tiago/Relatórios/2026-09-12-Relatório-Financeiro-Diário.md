# Relatório Financeiro Diário — 2026-09-12

**Ao DigitalCEO**  
**Base BRT:** 12/09/2026, 08:03  
**Vendas do dia anterior:** 11/09/2026  
**Janela financeira:** 12/09–19/09/2026

## Resumo financeiro

- **Pagar.me — 11/09:** **30 cobranças | R$ 44.479,00 | ticket médio R$ 1.482,63**.
- **Qualidade:** **28 OK | R$ 38.683,00**; **2 revisar | R$ 5.796,00**; **0 suspeitas**.
- **Exposição para revisão:** **13,03%** do valor aprovado.
- **Por loja:** SSL **12 | R$ 31.465,45**; GCL **4 | R$ 8.309,38**; ACL **14 | R$ 4.704,17**; BRG **0 | R$ 0,00**.
- **Por meio:** cartão **21 | R$ 35.929,51**; PIX **9 | R$ 8.549,49**.
- **SQL Server — vendas confirmadas em 11/09:** **37 pedidos aprovados | R$ 57.623,55 | ticket médio R$ 1.557,39**. Fonte atualizada até 11/09.
- **Outros status SQL, não somados às vendas aprovadas:** Expedição **1 | R$ 2.076,61**; status D **1 | R$ 154,25**.
- **Diferença de escopo SQL x Pagar.me:** **R$ 13.144,55** a mais no SQL (**29,55%** sobre Pagar.me). **Não somar as fontes.**
- **Oracle/DEBX — PED, separado:** status **X/expedido 109 | R$ 13.367,28**; status **A 16 | R$ 5.234,85**; status **P 2 | R$ 1.121,60**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **286 movimentos | R$ 13.172,08**.

## Alertas de vencimentos

- **Contas a pagar 12/09–19/09:** base oficial atual **não localizada** no Google Drive após **6 buscas** nem no Vault. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL:** **715 títulos | R$ 76.521,02**.
- **Vencendo hoje, 12/09:** **78 títulos | R$ 5.810,23**.
- **Pico:** **14/09 | 304 títulos | R$ 33.490,37 — 43,77%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 12/09 | 78 | R$ 5.810,23 |
| 13/09 | 0 | R$ 0,00 |
| 14/09 | 304 | R$ 33.490,37 |
| 15/09 | 88 | R$ 9.130,59 |
| 16/09 | 70 | R$ 8.833,54 |
| 17/09 | 96 | R$ 9.270,44 |
| 18/09 | 78 | R$ 9.122,02 |
| 19/09 | 1 | R$ 863,83 |

## Inadimplência

- **Títulos vencidos sem baixa:** **3.877 | R$ 326.261,11**.
- **Índice bruto:** **25,26%** do saldo aberto ACL de **R$ 1.291.442,73**.
- **1–30 dias:** **171 | R$ 39.393,82**.
- **31–60 dias:** **6 | R$ 662,51**.
- **61–90 dias:** **17 | R$ 21.948,75**.
- **Acima de 90 dias:** **3.683 | R$ 264.256,03 — 81,00%** do vencido.
- **Variação versus 11/09:** **-234 títulos | -R$ 54.073,92** no vencido.
- Indicador operacional sujeito a baixas ainda não processadas; não tratar como inadimplência contábil definitiva sem validação.

## Recomendações

1. **Revisão Pagar.me imediata:** validar **2 PIX do mesmo cliente**, pedidos distintos, aprovados com **1min09s** de intervalo: **R$ 2.522,98 + R$ 3.273,02 = R$ 5.796,00**. **Não estornar sem confirmar os pedidos.**
2. **Cobrança:** priorizar **R$ 39.393,82** vencidos há até 30 dias e acompanhar os **R$ 5.810,23** com vencimento hoje.
3. **Concentração:** preparar cobrança e baixa dos **R$ 33.490,37** com vencimento em 14/09.
4. **Aging:** revisar **R$ 264.256,03** acima de 90 dias, separando atraso real, baixa pendente e legado.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos dos próximos 7 dias.
6. **Conciliação:** investigar a diferença de **R$ 13.144,55** entre SQL e Pagar.me por competência, meio e canal, sem somar as bases.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 11/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Google Drive: conexão ativa; 6 buscas financeiras recentes, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
