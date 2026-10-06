# Relatório Financeiro Diário — 06/10/2026

**Ao DigitalCEO**  
**Base:** 06/10/2026, BRT; vendas e aprovações de 05/10; vencimentos de 06/10 a 13/10 (hoje + 7 dias).

## Resumo financeiro
- **Vendas aprovadas, SQL Server:** 41 pedidos | **R$ 70.655,15** | ticket médio **R$ 1.723,30**. `hotel-finder.conamore.CAIXA_PERIODO_COM_ORIGEM`, status `Aprovado`; base atualizada até 05/10. Venda não equivale a recebimento.
- **Pagar.me, cobranças aprovadas (`paid_at`):** 22 | **R$ 41.168,40** | ticket médio **R$ 1.871,29**. ACL: 9 / R$ 12.217,57; SSL: 13 / R$ 28.950,83; GCL/BRG: 0. PIX: 11 / R$ 19.418,71; cartão: 9 / R$ 19.918,95; boleto: 2 / R$ 1.830,74. **20 OK; 2 REVISAR (R$ 3.350,60); 0 SUSPEITO.** As duas revisões são pedidos distintos próximos no tempo; não são duplicidade confirmada.
- **Oracle/DEBX, outra base — não somar:** PED X/expedido: 89 / R$ 8.678,13; A: 19 / R$ 25.592,81; F: 4 / R$ 4.651,59. Loja física `F_MOVTO/MOV_NATIND=100`: 196 movimentos / R$ 8.678,13. PED não é venda física.

## Vencimentos e inadimplência
- **Contas a pagar, fornecedores, 06–13/10:** posição oficial atual não localizada no Vault; Drive indisponível sem autenticação neste perfil. **Valor/vencimentos não disponíveis, não zero.** E-mail não acessado por restrição do perfil.
- **Contas a receber ACL, títulos sem data de pagamento, 06–13/10:** **790 títulos | R$ 106.123,72**. Hoje 06/10: 180 / **R$ 22.341,89**; 07/10: 67 / R$ 9.445,00; 08/10: 72 / R$ 12.113,62; 09/10: 93 / R$ 10.717,64; 10/10: 3 / R$ 572,85; 11/10: 4 / R$ 5.530,38; **12/10: 283 / R$ 33.756,84**; 13/10: 88 / R$ 11.645,50. Não é previsão de liquidação nem inclui outras lojas.
- **Vencidos ACL sem data de pagamento antes de 06/10:** **3.836 títulos | R$ 306.623,95**, **24,11%** do valor bruto aberto ACL (**R$ 1.271.780,67**). Acima de 90 dias: **3.696 | R$ 286.585,58**. Indicador operacional sujeito a baixa, abatimentos e conciliação; não é inadimplência contábil consolidada.

## Recomendações
1. Confirmar baixas/cobrança dos **R$ 22.341,89** que vencem hoje e preparar contato preventivo para os **R$ 33.756,84** de 12/10.
2. Revisar as **2 cobranças Pagar.me, R$ 3.350,60**, por cliente e pedido antes de tratá-las como duplicidade.
3. Conciliar os **R$ 286.585,58** vencidos há mais de 90 dias com pagamentos parciais e baixas reais.
4. Obter posição oficial de fornecedores de **06–13/10** antes de aprovar projeção de caixa.

## Fontes e limites
- SQL Server `hotel-finder`: sessão `hotelfinder`, colunas e atualização até 05/10 validadas; leitura agregada.
- Pagar.me v5: consolidado gerado nesta execução para `paid_at` em 05/10; XLSX relido para totais e flags.
- Oracle `conamore`: sessão `TEST_ACL` e colunas validadas; `F_TITULOS` com `TIT_NUMPAR` preenchido, `TIT_DATPGT` nulo, `TIT_VALORI` positivo; vencimentos ACL apenas. PED e movimento físico separados.
- Contas a pagar: busca por arquivos locais sem base atual; Drive não autenticado; sem acesso ao e-mail.
