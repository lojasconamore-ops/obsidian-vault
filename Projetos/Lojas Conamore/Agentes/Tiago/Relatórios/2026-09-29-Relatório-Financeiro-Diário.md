# Relatório Financeiro Diário — 29/09/2026

**Ao DigitalCEO**  
**Base BRT:** 29/09/2026, 08:02  
**Vendas:** 28/09/2026  
**Janela de vencimentos:** 29/09–06/10/2026 (hoje + 7 dias)

## Resumo financeiro

- **SQL Server — vendas aprovadas:** 34 pedidos | **R$ 72.252,61**. Fonte: `conamore.CAIXA_PERIODO_COM_ORIGEM`, status Aprovado; atualização até 28/09 validada.
- **Pagar.me — pagamentos aprovados:** 34 cobranças | **R$ 80.593,35** | ticket médio **R$ 2.370,39**. 34 OK, 0 suspeitas, 0 revisar.
- **Diferença entre fontes:** **R$ 8.340,74** a mais no Pagar.me. Contagens coincidem, mas datas/eventos/escopo distintos; não considerar conciliado.
- **Por loja Pagar.me:** SSL 27 | R$ 32.821,98; ACL 5 | R$ 24.891,47; GCL 2 | R$ 22.879,90; BRG 0.
- **Por meio Pagar.me:** PIX 14 | R$ 51.639,71; cartão 19 | R$ 28.759,24; boleto 1 | R$ 194,40.
- **Oracle/DEBX (base separada):** PED X/expedido 102 | R$ 10.985,45; PED A 6 | R$ 26.147,97; PED F 2 | R$ 3.603,18. Venda física `MOV_NATIND=100`: 207 movimentos | R$ 10.872,85. Não somar PED à venda física.

## Alertas de vencimentos

- **Contas a pagar:** posição oficial atual não localizada nos arquivos financeiros do Vault; total confirmado indisponível, não zero. E-mail não acessado por restrição do perfil.
- **Contas a receber ACL, títulos sem baixa com vencimento de 29/09 a 06/10:** **779 | R$ 145.967,23** (somente ACL, sem consolidação das demais lojas).
- 29/09: 167 | **R$ 21.120,54**; 30/09: 72 | R$ 7.825,29; 01/10: 82 | R$ 17.438,39; 02/10: 70 | R$ 11.115,48; 03/10: 2 | R$ 12.886,65; 05/10: 267 | **R$ 57.744,03**; 06/10: 119 | R$ 17.836,85. Sem títulos nesta consulta em 04/10.
- **Pagar.me 25/09, pendência histórica sem baixa/resolução verificada nesta execução:** grupo de R$ 15.750,10 com possível duplicidade de R$ 7.875,05. Não confundir com as 34 cobranças limpas de 28/09.

## Inadimplência operacional — ACL

- **Vencidos sem baixa:** **3.935 títulos | R$ 310.093,56**, **24,08%** do saldo aberto ACL de R$ 1.287.969,51.
- 1–30 dias: 226 | R$ 22.440,19; 31–60: 6 | R$ 2.085,35; 61–90: 7 | R$ 551,92; acima de 90: 3.696 | **R$ 285.016,10**.
- Comparado à posição documentada em 27/09: **+R$ 6.026,50** no vencido; sujeito a baixas posteriores. Não equivale à inadimplência contábil definitiva.

## Recomendações

1. Conciliar pedido a pedido a diferença de **R$ 8.340,74** entre SQL e Pagar.me, sem somar fontes.
2. Cobrar/conferir baixas dos **R$ 21.120,54** de hoje e programar ação para **05/10: R$ 57.744,03** (39,56% da janela ACL).
3. Priorizar aging de 1–30 dias (**R$ 22.440,19**) e revisar o legado acima de 90 dias (**R$ 285.016,10**).
4. Obter posição oficial de contas a pagar com valores, vencimentos e baixas; não inferir disponibilidade de caixa apenas pelos recebíveis.
5. Verificar separadamente a pendência Pagar.me de 25/09 antes de concluir aquela conciliação.

## Fontes e limites

- Pagar.me v5: consolidado gerado em 29/09, filtro de `paid_at` em 28/09; XLSX da execução lido para agregações.
- SQL Server `hotel-finder`: sessão `hotelfinder`, schema, colunas e data máxima 28/09 validados; status Aprovado da caixa, somente leitura.
- Oracle `conamore`: sessão `TEST_ACL`, colunas de `F_PEDVENDA`, `F_MOVTO` e `F_TITULOS` validadas; títulos ACL sem baixa, `TIT_NUMPAR` preenchido e `TIT_VALORI` positivo; somente leitura.
- Busca local no Vault sem base atual de contas a pagar; sem acesso a e-mail. Valores de recebíveis não são contas a pagar nem previsão confirmada de liquidação.
