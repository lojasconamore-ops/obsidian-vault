# Cruzamento pagamentos liberados ML × pedidos DEBX

**Data:** 18/11/2026 BRT  
**Conta ML:** CONAMORE_HOTELARIA  
**Período dos pagamentos liberados:** 28/10/2026 a 17/11/2026

## Fonte e método

- Mercado Livre/Mercado Pago: planilha `Pagamentos_Liberados_por_Venda.xlsx`, agrupada por `pack_id`/número da venda.
- DEBX: consulta de leitura no espelho SQL `debx.PDV_Detalhes`, filtrando `Tipo_Pagamento`/`Codigo_Forma_Pgto` como Mercado Pago (`MERCADO PAGO`/`MP`) e aprovações entre 20/10/2026 e 19/11/2026.
- O Oracle `TEST_PED` foi tentado antes da consulta, mas retornou `ORA-01033` (inicialização ou encerramento em andamento). Portanto, o cruzamento abaixo usa o espelho SQL como fallback e deve ser revalidado no Oracle quando ele voltar.
- Critérios: número da venda ML quando disponível; CPF/CNPJ; valor bruto da venda; nome/razão social; data de aprovação como corroborador. Não foi forçada relação um-para-um por valor isolado.
- `PED` foi tratado como pedido do ERP, não automaticamente como venda física.

## Resultado

- 19 vendas agrupadas no ML, 29 sub-pedidos, bruto ML de R$ 4.854,40 e líquido liberado de R$ 3.566,26.
- 9 conciliações fortes por CPF/CNPJ + valor: R$ 2.063,20 bruto.
- 1 conciliação com ressalva nominal: Ítalo Irapuã → PED 0127952, R$ 503,20; CPF/CNPJ e valor coincidem, mas o nome/razão do DEBX diverge.
- 1 divergência de identidade: Elizabete Pessoa de Santana → o CPF/CNPJ aponta para Adriana Pessoa Gomes no DEBX, apesar de valor igual; não associar automaticamente.
- 1 divergência de valor: Maria José, venda ML de R$ 151,60; o mesmo CPF/CNPJ aparece no PED 0126879 de R$ 56,80 e no PED 0126830 de R$ 208,40. O caso precisa de conferência operacional, sem classificar como duplicidade automaticamente.
- 7 vendas não localizadas em PED Mercado Pago no período consultado: Authentic Mds (2), Paulo José Pimenta, Thayssa Estefani Brustelo, Thais Mozer, Jessica Montibeller Baumann e José Alfredo Gantuss. Alguns CPFs/CNPJs foram localizados no cadastro, mas não havia PED correspondente no recorte.

## Arquivo

`/home/sergio-ladeira/workspace/meli-integration/data/Cruzamento_Pagamentos_Liberados_ML_x_DEBX.xlsx`

A planilha contém a aba detalhada com número da venda ML, cliente, CPF/CNPJ, valor ML, status do cruzamento, ID DEBX, número PED, data/valor do PED, forma de pagamento, representante e observações; e uma aba de resumo por status.
