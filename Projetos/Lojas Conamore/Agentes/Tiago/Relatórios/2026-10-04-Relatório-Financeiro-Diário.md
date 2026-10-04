# Relatório Financeiro Diário — 04/10/2026

**Ao DigitalCEO**  
**Base:** 04/10/2026, BRT; vendas e aprovações de 03/10; vencimentos de 04/10 a 11/10 (hoje + 7 dias).

## Resumo financeiro
- **Vendas aprovadas, SQL Server:** 8 pedidos | **R$ 5.441,46** | ticket médio **R$ 680,18**. `hotel-finder.conamore.CAIXA_PERIODO_COM_ORIGEM`, status `Aprovado`; base atualizada até 03/10. Vendas não equivalem a recebimento.
- **Pagar.me, cobranças aprovadas (`paid_at`):** 5 | **R$ 5.019,49** | ticket médio **R$ 1.003,90**. ACL: 3 / R$ 1.028,08; SSL: 2 / R$ 3.991,41; GCL/BRG: 0. PIX: 3 / R$ 1.028,08; cartão: 2 / R$ 3.991,41. **5 OK; 0 REVISAR; 0 SUSPEITO.**
- **SQL menos Pagar.me: R$ 421,97**, apenas comparação de bases com escopos distintos, **não quebra de caixa apurada**.
- **Oracle/DEBX (outra base, não somar):** PED por data do pedido — X/expedido 108 / R$ 16.670,54; A 5 / R$ 1.918,36; F 1 / R$ 640,45. Loja física `F_MOVTO/MOV_NATIND=100`: 287 movimentos / R$ 15.642,04. PED não é venda física.

## Alertas de vencimentos
- **Contas a pagar, fornecedores, 04–11/10:** base oficial corrente **não localizada** no Vault/Google Drive; valor e vencimentos **indisponíveis, não zero**. E-mail não acessado por restrição do perfil.
- **Contas a receber ACL, títulos sem data de pagamento, 04–11/10:** **700 títulos | R$ 91.951,72**. 04/10: 85 / R$ 9.939,29; **05/10: 260 / R$ 29.266,91**; 06/10: 116 / R$ 14.474,54; 07/10: 66 / R$ 9.216,16; 08/10: 72 / R$ 12.113,62; 09/10: 94 / R$ 10.837,97; 10/10: 3 / R$ 572,85; 11/10: 4 / R$ 5.530,38. Não é previsão de liquidação nem inclui outras lojas.

## Inadimplência operacional — ACL
- **Vencidos sem data de pagamento antes de 04/10:** **3.878 títulos | R$ 302.913,76**, **23,82%** do valor aberto ACL (**R$ 1.271.815,66**).
- 0–30 dias: 164 / R$ 13.488,56; 31–60: 10 / R$ 2.127,33; 61–90: 8 / R$ 712,29; **acima de 90: 3.696 / R$ 286.585,58**. Indicador operacional sujeito a conciliação de baixas; não é inadimplência contábil consolidada.

## Recomendações
1. Priorizar confirmação das baixas e cobrança preventiva de **R$ 29.266,91** com vencimento em **05/10**, após revisar os **R$ 9.939,29** de 04/10.
2. Conciliar os 8 pedidos SQL com as 5 cobranças Pagar.me por identificador, canal, prazo e competência antes de atribuir a diferença de R$ 421,97 a falha.
3. Segregar os **R$ 286.585,58** vencidos há mais de 90 dias entre saldo exigível e baixas pendentes.
4. Obter posição corrente de fornecedores de **04–11/10** antes de fechar projeção de caixa; recebíveis não substituem contas a pagar.

## Fontes e limites
- Pagar.me v5: artefato consolidado de 04/10 gerado nesta execução, janela de aprovações 03/10; XLSX relido para valores, lojas, meios e flags.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; consulta somente de leitura.
- Oracle `conamore`: sessão `TEST_PED`, schema/colunas validados; `TEST_ACL.F_TITULOS` filtrado por `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo e `TIT_VALORI` positivo, ACL apenas. Consultas de PED e movimento físico separadas.
- Google Drive e Vault: buscas de metadados/arquivos de contas, financeiro, vencer e inadimplência sem posição atual de contas a pagar; não conclui inexistência de obrigações.
