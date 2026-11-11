# Relatório Financeiro Diário — 11/11/2026

**Ao DigitalCEO | Corte:** 11/11/2026, 08h BRT. Vendas e cobranças aprovadas em 10/11; vencimentos de 11/11 a 17/11, inclusive.

## Resumo financeiro
- **Vendas aprovadas, SQL Server `hotel-finder`, 10/11:** `conamore.CAIXA_PERIODO_COM_ORIGEM`: **55 pedidos / R$ 68.639,76**, ticket médio **R$ 1.248,00**. Mais 6 pedidos em Expedição/R$ 2.250,00 fora da receita aprovada. Fonte atualizada até 10/11. A visão distinta `debx.PDV_Detalhes` registra 24 aprovados/R$ 44.127,07; não somar à fonte principal.
- **Pagar.me v5, aprovações em 10/11:** **25 cobranças / R$ 45.371,49**, ticket médio **R$ 1.814,86**. SSL 16/R$ 27.914,66; GCL 8/R$ 17.126,60; ACL 1/R$ 330,23; BRG 0. Cartão 20/R$ 40.413,11; PIX 4/R$ 4.628,15; boleto 1/R$ 330,23. **25 OK, 0 SUSPEITO/REVISAR** pelo critério automático. Aprovação não equivale a liquidação bancária nem se soma às vendas SQL.
- **Oracle DEBX/ACL, 10/11:** PED X (expedido) 138/R$ 14.945,97; A 4/R$ 7.554,83; P 1/R$ 330,23. Venda física (`F_MOVTO`, `MOV_NATIND=100`): 370 movimentos/R$ 14.668,85. Recortes distintos; não somar à receita SQL.

## Vencimentos e inadimplência
- **Títulos ACL tipo 8, sem baixa e saldo positivo, 11–17/11:** **724 / R$ 88.946,06** como *proxy operacional de recebíveis*. 11/11: 178/R$ 24.695,95; 12/11: 61/R$ 9.312,04; 13/11: 93/R$ 11.569,47; 14/11: 2/R$ 124,28; 16/11: 298/R$ 30.530,95; 17/11: 92/R$ 12.713,37. Sem confirmação de recebimento/baixa bancária.
- **Outros títulos ACL tipo 7 na janela:** **8 / R$ 11.812,30** (13/11 R$ 26,94; 14/11 R$ 1.304,50; 16/11 R$ 6.768,29; 17/11 R$ 3.712,57). Classificação pagar/receber **não validada**; não incluí-los como contas a pagar confirmadas nem como recebíveis. Total de títulos abertos na janela, todos os tipos: **732 / R$ 100.758,36**.
- **Tipo 8 vencido antes de 11/11:** **4.078 / R$ 382.804,03**, **31,34%** dos R$ 1.221.282,97 abertos nessa tipologia. Mais de 90 dias: **3.686 / R$ 271.827,22**. São títulos sem baixa no ERP, não inadimplência contábil consolidada; verificar conciliação e classificação com Matias/Financeiro.
- **Contas a pagar a fornecedores, 11–17/11:** posição atual não confirmada; valor não verificável (não zero). Saldo bancário indisponível. Nenhum acesso a e-mail por restrição do perfil.

## Recomendações
1. Conciliar baixas dos **R$ 382.804,03** vencidos de tipo 8, priorizando **R$ 271.827,22** acima de 90 dias; não disparar cobrança sem validar.
2. Confirmar classificação e baixa dos **8 títulos tipo 7/R$ 11.812,30**, sobretudo **R$ 6.768,29 em 16/11**; obter carteira atual de fornecedores e saldo/extrato para caixa líquido.
3. Preparar acompanhamento dos **R$ 24.695,95** de títulos tipo 8 previstos hoje e **R$ 30.530,95** em 16/11, sem assumir recebimento.

**Fontes/método:** relatório Pagar.me v5 consolidado gerado nesta execução (janela interna 10/11); SQL Server `hotel-finder` (sessão, colunas e data máxima verificadas); Oracle `conamore`/`TEST_ACL` (sessão/colunas verificadas), `F_PEDVENDA`, `F_MOVTO`, `F_TITULOS`. Títulos: `TIT_NUMPAR` identificado, `TIT_DATPGT` nula e saldo `NVL(TIT_VALORI,0)-NVL(TIT_VALPAG,0)>0`, janela `[11/11,18/11)`. Classificação por `TIT_TIPTIT` ainda não confirmada por regra oficial. Somente leitura; sem conciliação bancária.
