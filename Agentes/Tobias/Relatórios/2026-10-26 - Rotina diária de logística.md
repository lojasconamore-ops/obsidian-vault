# Rotina diária de logística — 2026-10-26

## Execução
- Horário: 08:05 BRT.
- Fonte Intelipost: `status`, `delivery-methods` e tracking individual.
- Fonte Oracle: sessão somente leitura em `conamore`, usuário `TEST_PED`; sessão validada com `select 1` e `sys_context`.
- Colunas validadas antes das consultas: `F_SAIDAS`, `F_PEDVENDA`, `F_MOVTO`, `FI_MAG_PEDIDOS` e `I_FILA_INTELIPOST`.

## 1. Status Intelipost
- API online; 9 de 15 transportadoras ativas.
- Ativas: Via Pajuçara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna/Frete Valor Fixo, Jamef, Rodonaves, Favorita e Correios Sedex.
- Fila Oracle `TEST_PED.I_FILA_INTELIPOST`: 0 registros nos últimos 7 dias e 0 nos últimos 2 dias. Não foi interpretado isoladamente como saúde/falha: há shipments recentes funcionando.

## 2. Alertas reais do dia
- Nenhum atraso aberto, extravio ou avaria confirmado nos pedidos amostrados.
- `300-0005433-2` (NF 0005433, ACL, Rápido Figueiredo): status `To Be Delivered`, saiu para entrega em 23/10, ETA 26/10/2026. É acompanhamento do dia; ainda não é atraso.
- `100-0013942-2` (NF 0013942, MATRIZ, Jamef): `In Transit`, chegada na filial destino em 26/10 03:00, ETA 04/11. Dentro do prazo.
- `500-0002662-2`, `500-0002663-2` e `500-0002664-2` (GCL): em trânsito, ETAs de 09/11, 10/11 e 12/11; sem criticidade.
- `100-0013956-2` (Correios): entregue em 24/10, apesar de ETA 26/10; encerrado, não alerta aberto.
- `100-0013710-2`, `100-0013711-2`, `100-0013717-2`, `300-0005435-2`: entregues; atrasos históricos não identificados como abertos.
- `300-0005432-2`: “Número do pedido desconhecido” no tracking. Sem conclusão de falha: tratar como ausência de shipment order/gap a investigar com schema, `SAI_DATSAI`, CODTRA e fila; não é evidência de extravio.

## 3. Oracle/DEBX complementar
- Relatório de ontem (25/10/2026): 0 NFs série 2; domingo, sem operação de expedição registrada.
- Janela de 15 dias (12–26/10): 552 NFs, faturamento R$ 1.660.607,31, frete contratado R$ 48.866,45, gasto real R$ 34.213,52, 4,0% do faturamento CIF — dentro da meta de 5%.
- Distribuição de transportadoras: Correios 228, Retirada/Balcão 85, Via Pajuçara 72, Rápido Figueiredo 54, Jamef 47, Frota Interna 23, Dia e Noite 23, Pacífico 8, Rodonaves 7 e Favorita 5.
- ACL nos últimos 2 dias: 18 pedidos `A` e 62 `X`. Regra aplicada: `PDV_STATUS = 'X'` significa EXPEDIDO; não foi usado como cancelamento ou justificativa de ausência de shipment order.

## Recomendações
1. Confirmar encerramento de `300-0005433-2` ao final do dia; se permanecer sem entrega após o ETA, abrir tratativa com a Rápido Figueiredo.
2. Não abrir sinistro para nenhum pedido desta execução.
3. Investigar separadamente o gap `300-0005432-2` no próximo ciclo, validando prefixo/schema ACL (`300-`), `SAI_DATSAI`, CODTRA e integração; não inferir criticidade pelo status X.
4. Manter revisão dos 208 casos de frete CIF acima de 5% apontados pelo relatório de 15 dias; o agregado permanece saudável (4,0%), mas há indício de distorção por frete contratado em pedidos de baixo valor.
