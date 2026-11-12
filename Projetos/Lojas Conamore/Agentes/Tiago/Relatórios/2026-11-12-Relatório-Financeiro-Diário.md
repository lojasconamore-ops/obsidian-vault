# Relatório Financeiro Diário — 12/11/2026

**Ao DigitalCEO | Corte:** 12/11/2026, 08h03 BRT. Vendas/aprovações de 11/11; vencimentos de 12/11 a 18/11, inclusive.

## Resumo financeiro
- **Vendas aprovadas — SQL Server `hotel-finder`, 11/11:** `conamore.CAIXA_PERIODO_COM_ORIGEM`: **43 pedidos / R$ 176.864,63**, ticket médio **R$ 4.113,13**. Mais 10 pedidos em Expedição/R$ 17.789,50 fora do total aprovado. Fonte atualizada até 11/11.
- **Pagar.me v5 — aprovações em 11/11:** **20 cobranças / R$ 64.077,59**, ticket médio **R$ 3.203,88**. SSL 15/R$ 38.671,24; GCL 5/R$ 25.406,35; ACL 0; BRG 0. Cartão 13/R$ 43.133,36; PIX 7/R$ 20.944,23. **20 OK; 0 SUSPEITO/REVISAR** na regra automática. Aprovação não é liquidação bancária nem se soma à venda SQL.
- **DEBX/ACL, 11/11:** PED status X (*expedido*) 134/R$ 17.378,15; A 4/R$ 6.987,24; F 4/R$ 14.403,37. Venda física (`F_MOVTO`, `MOV_NATIND=100`) 295 movimentos/R$ 13.618,36. PED e venda física são recortes distintos; não somar à receita SQL.
- **Alerta de status, visão SQL distinta `debx.PDV_Detalhes`:** 20 pedidos com status Cancelado/R$ 279.007,52 e 17 Aprovado/R$ 138.201,44 em 11/11. Não somar nem deduzir da receita aprovada principal sem conciliar pedidos e sem verificar semântica/status com Matias.

## Vencimentos e inadimplência
- **Títulos ACL tipo 8, sem baixa e com saldo positivo, 12–18/11:** **722 / R$ 87.130,03**, *proxy operacional de recebíveis*, classificação ainda não validada oficialmente. 12/11: 166/R$ 24.998,73; 13/11: 93/R$ 11.569,47; 14/11: 2/R$ 124,28; 16/11: 298/R$ 30.530,95; 17/11: 92/R$ 12.713,37; 18/11: 71/R$ 7.193,23. Não é recebimento confirmado.
- **Títulos ACL tipo 7 na mesma janela:** **8 / R$ 11.812,30** (13/11 R$ 26,94; 14/11 R$ 1.304,50; 16/11 R$ 6.768,29; 17/11 R$ 3.712,57). Classificação pagar/receber não validada; não tratar como contas a pagar confirmadas. Todos os tipos na janela: **730 / R$ 98.942,33**.
- **Tipo 8 vencido antes de 12/11:** **4.012 / R$ 380.917,47**, **31,35%** dos R$ 1.215.097,98 abertos nessa tipologia; acima de 90 dias **3.686 / R$ 271.827,22**. *Atraso no ERP*, não inadimplência contábil consolidada nem confirmação de ausência de baixa bancária.
- **Contas a pagar a fornecedores (12–18/11):** carteira atual não localizada/validada; valor **indisponível, não zero**. Busca local e metadados do Drive sem base atual; sem acesso a e-mail por restrição de perfil. Saldo bancário indisponível.

## Recomendações
1. Conciliar **R$ 380.917,47** do tipo 8 vencido, começando pelos **R$ 271.827,22** acima de 90 dias; validar classificação e baixas antes de cobrança.
2. Confirmar a carteira de fornecedores e classificar **8 títulos tipo 7/R$ 11.812,30** com o Financeiro/Matias; preparar **R$ 24.998,73** (12/11) e **R$ 30.530,95** (16/11) de recebíveis operacionais previstos, sem assumir entrada em caixa.
3. Investigar os **20 cancelados/R$ 279.007,52** na visão `debx.PDV_Detalhes` contra os pedidos da visão principal antes de interpretar impacto financeiro.

**Fontes/método:** relatório Pagar.me v5 consolidado gerado nesta execução (janela interna 11/11), SQL Server `hotel-finder` (sessão/colunas/frescor verificados) e Oracle `conamore`/`TEST_ACL` (sessão/colunas verificadas). `F_TITULOS`: `TIT_NUMPAR` preenchido, `TIT_DATPGT` nula, saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`; vencimentos `[12/11,19/11)`. Busca Drive por contas/financeiro/titulos/pagar sem carteira atual. Consultas somente leitura; sem conciliação bancária.
