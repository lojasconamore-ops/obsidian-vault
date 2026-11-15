# Relatório Financeiro Diário — 15/11/2026

**Ao DigitalCEO | Corte:** 15/11/2026, 08h02 BRT. Vendas/aprovações de 14/11; vencimentos de 15/11 a 21/11, inclusive.

## Resumo financeiro
- **Vendas aprovadas — SQL Server `hotel-finder`, 14/11:** `conamore.CAIXA_PERIODO_COM_ORIGEM`: **21 pedidos / R$ 17.955,40**, ticket médio **R$ 855,02**. Fonte atualizada até 14/11; status Aprovado.
- **Pagar.me v5 — cobranças aprovadas em 14/11:** **6 / R$ 4.965,00**, ticket médio **R$ 827,50**; todas SSL/cartão, 6 OK, 0 SUSPEITO/REVISAR. Aprovação não equivale a liquidação bancária; não somar à venda SQL.
- **DEBX/ACL, 14/11:** PED status X (*expedido*) **108 / R$ 14.050,97**. Venda física `F_MOVTO`, `MOV_NATIND=100`: **257 movimentos / R$ 13.746,67**. São recortes distintos; não somar à receita SQL.

## Vencimentos e inadimplência
- **Títulos ACL tipo 8, sem baixa e saldo positivo, 15–21/11:** **714 / R$ 83.112,96** — proxy operacional de recebíveis, classificação não validada oficialmente. Por data: 15/11 77/R$ 8.507,35; 16/11 286/R$ 28.343,47; 17/11 92/R$ 12.713,37; 18/11 71/R$ 7.193,23; 19/11 96/R$ 10.496,46; 20/11 92/R$ 15.859,08. Não são entradas de caixa confirmadas.
- **Títulos tipo 7:** **3 / R$ 1.460,68** (17/11 R$ 45,48; 19/11 R$ 15,73; 21/11 R$ 1.399,47). **Tipo 17:** 1/R$ 29,18 (20/11). Sem validação da natureza pagar/receber; não contabilizar como contas a pagar confirmadas.
- **Tipo 8 vencido antes de 15/11:** **4.018 / R$ 413.663,21**, **33,46%** de R$ 1.236.152,03 abertos nessa tipologia; acima de 90 dias **3.686 / R$ 271.827,22**. É atraso registrado no ERP, não inadimplência contábil consolidada ou comprovação de não pagamento.
- **Contas a pagar a fornecedores:** carteira validada com vencimentos até 21/11 **não localizada; valor indisponível, não zero**. Saldo bancário não consultado; Gmail restrito a Elias.

## Recomendações
1. Conciliar baixas dos R$ 413.663,21 vencidos do tipo 8, priorizando R$ 271.827,22 acima de 90 dias; validar natureza antes de cobrança.
2. Confirmar a carteira real de fornecedores e classificar os 3 títulos tipo 7/R$ 1.460,68 e 1 título tipo 17/R$ 29,18 com Financeiro/Matias. Priorizar a programação operacional de 16/11 (R$ 28.343,47 em tipo 8), sem pressupor caixa recebido.
3. Manter aprovações Pagar.me, venda SQL, PED e movimento físico em visões separadas até conciliação.

**Fontes/método:** relatório consolidado Pagar.me desta execução (janela interna 14/11; XLSX relido), SQL Server `hotel-finder` (sessão, colunas, frescor e status validados), Oracle `conamore`/`TEST_ACL` (sessão e colunas validadas). `F_TITULOS`: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nula e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`; janela `[15/11,22/11)`. Consultas somente leitura; sem conciliação bancária ou confirmação de contas a pagar.
