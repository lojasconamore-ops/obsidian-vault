# Relatório Financeiro Diário — 2026-09-13

**Ao DigitalCEO**  
**Base BRT:** 13/09/2026, 08:00  
**Vendas do dia anterior:** 12/09/2026  
**Janela financeira:** 13/09–20/09/2026

## Resumo financeiro

- **Pagar.me — 12/09:** **27 cobranças | R$ 21.710,36 | ticket médio R$ 804,09**.
- **Qualidade:** **25 OK | R$ 21.358,64**; **2 revisar | R$ 351,72**; **0 suspeitas**.
- **Exposição para revisão:** **1,62%** do valor aprovado.
- **Por loja:** ACL **23 | R$ 12.742,59**; SSL **3 | R$ 8.424,77**; GCL **1 | R$ 543,00**; BRG **0 | R$ 0,00**.
- **Por meio:** cartão **19 | R$ 19.199,39**; PIX **8 | R$ 2.510,97**.
- **SQL Server:** fonte atualizada somente até **11/09**; resultado vazio em 12/09 é **defasagem, não venda zero**.
- **Oracle/DEBX — PED, separado:** status **X/expedido 32 | R$ 12.018,48**; status **A 5 | R$ 1.281,65**.
- **Venda física Oracle, separada da PED:** `MOV_NATIND=100` **96 movimentos | R$ 9.050,72**.
- **Diferença Pagar.me x PED X:** **R$ 9.691,88** a mais no Pagar.me (**80,64%** sobre PED X). **Não somar as fontes.**

## Alertas de vencimentos

- **Contas a pagar 13/09–20/09:** base oficial atual **não localizada** após **6 buscas no Google Drive** nem no Vault. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL:** **669 títulos | R$ 74.764,70**.
- **Vencendo hoje, 13/09:** **28 títulos | R$ 3.747,37**.
- **Pico:** **14/09 | 304 títulos | R$ 33.490,37 — 44,79%** da janela.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 13/09 | 28 | R$ 3.747,37 |
| 14/09 | 304 | R$ 33.490,37 |
| 15/09 | 88 | R$ 9.130,59 |
| 16/09 | 70 | R$ 8.833,54 |
| 17/09 | 96 | R$ 9.270,44 |
| 18/09 | 78 | R$ 9.122,02 |
| 19/09 | 1 | R$ 863,83 |
| 20/09 | 4 | R$ 306,54 |

## Inadimplência

- **Títulos vencidos sem baixa:** **3.955 | R$ 332.071,34**.
- **Índice bruto:** **25,52%** do saldo aberto ACL de **R$ 1.301.170,88**.
- **1–30 dias:** **249 | R$ 45.204,05**.
- **31–60 dias:** **6 | R$ 662,51**.
- **61–90 dias:** **17 | R$ 21.948,75**.
- **Acima de 90 dias:** **3.683 | R$ 264.256,03 — 79,58%** do vencido.
- **Variação versus 12/09:** **+78 títulos | +R$ 5.810,23** no vencido.
- Indicador operacional sujeito a baixas ainda não processadas; não tratar como inadimplência contábil definitiva sem validação.

## Recomendações

1. **Cobrança imediata:** priorizar **R$ 45.204,05** vencidos há até 30 dias e os **R$ 3.747,37** vencendo hoje.
2. **Concentração:** preparar cobrança/baixa de **R$ 33.490,37** com vencimento em 14/09.
3. **Revisão Pagar.me:** validar **2 cobranças no cartão do mesmo cliente**, pedidos e valores distintos, total **R$ 351,72**; **não estornar sem confirmar os pedidos**.
4. **Aging:** revisar **R$ 264.256,03** acima de 90 dias, separando atraso real, baixa pendente e legado.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos dos próximos 7 dias.
6. **Conciliação:** investigar a diferença de **R$ 9.691,88** entre Pagar.me e PED X por competência, meio e canal, sem somar as bases.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; aprovações de 12/09/2026.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: títulos individuais (`TIT_NUMPAR IS NOT NULL`) da ACL; não consolida outros schemas.
- Google Drive: conexão ativa; 6 buscas financeiras recentes, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
