# Relatório Financeiro Diário — 11/08/2026

**Ao DigitalCEO | Base:** 10/08/2026 | **Emissão:** 11/08/2026 08:06 BRT

## Resumo financeiro
- **Vendas aprovadas — SQL Server:** 41 pedidos | **R$ 98.251,50** | ticket médio **R$ 2.396,38**.
- **Pedidos em expedição — SQL Server:** 3 | **R$ 6.962,97**. Não somados às vendas aprovadas.
- **Pagar.me aprovado:** 34 cobranças | **R$ 45.165,89** | ticket médio **R$ 1.328,41**.
- **Pagar.me por loja:** SSL 7 | R$ 27.421,90 (60,71%); GCL 7 | R$ 9.970,21 (22,07%); ACL 20 | R$ 7.773,78 (17,21%); BRG 0 | R$ 0,00.
- **Pagar.me por meio:** cartão 22 | R$ 38.920,66 (86,17%); PIX 12 | R$ 6.245,23 (13,83%).
- **Conciliação Pagar.me:** 34 OK | **R$ 45.165,89**; 0 SUSPEITO; 0 REVISAR.
- **Oracle/DEBX — PED, separado da venda física:** status X 125 | **R$ 14.497,25**; status A 24 | **R$ 10.584,58**.
- **Venda física Oracle — F_MOVTO/MOV_NATIND=100:** 281 movimentos | **R$ 13.442,71**.

## Alertas de vencimentos
- **Contas a pagar 11–18/08:** base atual não localizada no Google Drive; **total confirmado indisponível**.
- **Pendências antigas para confirmação de baixa, posição de 05/08:** Grupo GPS R$ 73.820,00 + aluguel R$ 34.000,00 + Jamef R$ 1.402,37 = **R$ 109.222,37**. Não tratadas como saldo atual confirmado.
- **Contas a receber ACL 11–18/08 — Oracle F_TITULOS:** 894 títulos | **R$ 122.720,95**.

| Vencimento | Títulos | Valor |
|---|---:|---:|
| 11/08 | 218 | R$ 31.775,75 |
| 12/08 | 82 | R$ 15.233,73 |
| 13/08 | 116 | R$ 14.416,17 |
| 14/08 | 90 | R$ 10.272,92 |
| 15/08 | 1 | R$ 745,53 |
| 16/08 | 2 | R$ 2.699,53 |
| 17/08 | 294 | **R$ 47.906,83** |
| 18/08 | 101 | R$ 11.137,82 |

## Inadimplência e risco
- **ACL — títulos vencidos sem baixa no Oracle:** 5.861 títulos | **R$ 742.503,63**.
- **Atraso de 1–30 dias:** 1.422 títulos | **R$ 288.897,47**.
- **Atraso de 31–60 dias:** 756 títulos | **R$ 191.796,14**.
- **Atraso de 61–90 dias:** 14 títulos | **R$ 1.146,63**.
- **Atraso acima de 90 dias:** 3.669 títulos | **R$ 260.663,39**.
- **Índice sobre títulos abertos ACL:** 51,27% do saldo aberto aparece vencido. **Alto risco de base com baixas históricas não processadas; validar antes de usar como inadimplência contábil definitiva.**
- **Pagar.me 10/08:** 0 cobranças suspeitas ou para revisão.
- **Pendência carregada de 03/08:** 2 PIX de R$ 752,80; exposição potencial de duplicidade **R$ 752,80**, sem evidência de resolução localizada.

## Recomendações
1. **Prioridade máxima:** validar as baixas do aging ACL; começar pelos **R$ 288.897,47 vencidos há até 30 dias** e separar atraso real de baixa pendente.
2. Cobrar/monitorar os **R$ 122.720,95** com vencimento até 18/08; pico em 17/08: **R$ 47.906,83** (39,04% da janela).
3. Confirmar hoje a situação dos **R$ 109.222,37** de fornecedores carregados da posição de 05/08.
4. Disponibilizar base corrente de contas a pagar; sem ela, preservar caixa e evitar compromissos discricionários.
5. Encerrar a revisão dos 2 PIX de 03/08 e documentar a conclusão.

## Fontes e limites
- SQL Server `hotel-finder`: sessão e colunas validadas; fonte atualizada até 10/08/2026.
- Pagar.me v5: aprovações de 10/08/2026; artefato do dia gerado e conferido.
- Oracle/DEBX: sessão `TEST_ACL` validada; PED e venda física reportadas separadamente.
- Aging e próximos vencimentos: `TEST_ACL.F_TITULOS`, somente contas a receber ACL; não consolida os demais schemas.
- Google Drive: pesquisa por contas, vencer, títulos, financeiro, inadimplência e pagar; nenhum arquivo financeiro atual localizado.
- Gmail/e-mail não utilizado por restrição do perfil.
