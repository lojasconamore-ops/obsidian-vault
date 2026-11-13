# Relatório Financeiro Diário — 13/11/2026

**Ao DigitalCEO | Corte:** 13/11/2026, 08h BRT. Vendas de 12/11; títulos com vencimento de 13/11 a 19/11, inclusive.

## Resumo financeiro
- **Vendas aprovadas — SQL Server `hotel-finder`, 12/11:** `conamore.CAIXA_PERIODO_COM_ORIGEM`: **47 pedidos / R$ 75.543,24**, ticket médio **R$ 1.607,30**. Fonte atualizada até 12/11. Mais 3 pedidos em Expedição/R$ 224.667,55 fora do aprovado; não tratar como receita aprovada.
- **DEBX/ACL, 12/11:** PED status X (*expedido*) 117/R$ 13.535,06; A 4/R$ 14.374,86; F 4/R$ 14.992,18; L 1/R$ 43,90; P 2/R$ 299,68. Venda física (`F_MOVTO`, `MOV_NATIND=100`): 253 movimentos/R$ 11.651,31. Recortes distintos; não somar à receita SQL.
- **Visão SQL distinta `debx.PDV_Detalhes`, 12/11:** Aprovado 16/R$ 48.160,78; Cancelado 2/R$ 2.297,00; Expedição 2/R$ 225.723,75; Financeiro 23/R$ 68.940,63; Pendente 3/R$ 2.086,08. Não somar nem deduzir da fonte principal sem conciliar pedidos.

## Vencimentos e inadimplência
- **Títulos ACL tipo 8, sem baixa e saldo positivo, 13–19/11:** **735 / R$ 93.806,97** — *proxy operacional de recebíveis*, classificação sem validação oficial. 13/11: 176/R$ 32.748,68; 14/11: 2/R$ 124,28; 16/11: 298/R$ 30.530,95; 17/11: 92/R$ 12.713,37; 18/11: 71/R$ 7.193,23; 19/11: 96/R$ 10.496,46. Não são entradas de caixa confirmadas.
- **Títulos ACL tipo 7, 13–19/11:** **12 / R$ 19.074,00**; 13/11 R$ 26,94; 14/11 R$ 1.304,50; 15/11 R$ 80,00; 16/11 R$ 6.768,29; 17/11 R$ 3.712,57; 19/11 R$ 7.181,70. Classificação pagar/receber não validada: **não** tratar como contas a pagar confirmadas. Todos os tipos na janela: **747 / R$ 112.880,97**.
- **Tipo 8 vencido antes de 13/11:** **3.913 / R$ 372.021,41**, **30,84%** dos R$ 1.206.398,76 abertos dessa tipologia; acima de 90 dias **3.686 / R$ 271.827,22**. Atraso no ERP, não inadimplência contábil consolidada nem prova de ausência de baixa bancária.
- **Contas a pagar a fornecedores:** carteira com vencimentos 13–19/11 não validada; valor **indisponível, não zero**. Saldo bancário indisponível; sem acesso a e-mail por restrição de perfil.

## Recomendações
1. Conciliar baixas do tipo 8 vencido (**R$ 372.021,41**), priorizando os **R$ 271.827,22** acima de 90 dias; validar classificação antes de cobrança.
2. Confirmar a carteira real de fornecedores e classificar os **12 títulos tipo 7/R$ 19.074,00** com Matias/Financeiro; programar acompanhamento de **R$ 32.748,68** previstos hoje e **R$ 30.530,95** em 16/11, sem presumir recebimento.
3. Conciliar os 3 pedidos em Expedição/R$ 224.667,55 na visão principal e o status da visão `debx.PDV_Detalhes` antes de qualquer projeção de caixa/receita.

**Fontes/método:** SQL Server `hotel-finder` (sessão `hotel-finder`/`hotelfinder`, colunas e frescor validados); Oracle `conamore`/`TEST_ACL` (sessão `TEST_PED`, `select 1`, contexto e colunas validados). `F_TITULOS`: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nula, saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`; janela `[13/11,20/11)`. Consultas somente leitura; sem conciliação bancária nem comprovantes de pagamento.
