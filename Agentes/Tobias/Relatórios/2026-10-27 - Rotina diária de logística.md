# Rotina diária de logística — 2026-10-27

## Execução
- Horário: 08:00–08:05 BRT.
- Intelipost: `status`, `delivery-methods` e rastreamento individual.
- Oracle: sessão somente leitura em `conamore`, usuário `TEST_PED`; `select 1` e `sys_context` validados.
- Colunas validadas antes das consultas: `F_PEDVENDA`, `F_SAIDAS`, `F_MOVTO`, `FI_MAG_PEDIDOS` e `I_FILA_INTELIPOST`.
- Regra aplicada: `PDV_STATUS = 'X'` significa **EXPEDIDO**; não foi interpretado como cancelamento, perda de receita ou falha de integração.

## 1. Status Intelipost
- API online.
- 9 de 15 transportadoras ativas.
- Ativas: Via Pajuçara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna/Frete Valor Fixo, Jamef, Rodonaves, Favorita e Correios Sedex.
- Fila `TEST_PED.I_FILA_INTELIPOST`: 0 registros nos últimos 7 dias e 0 nos últimos 2 dias. O silêncio foi correlacionado com shipments recentes funcionais; não foi tratado isoladamente como saúde ou falha.

## 2. Alertas reais do dia
- **1 avaria/falha de entrega aberta:** `100-0013942-2` (NF 0013942, MATRIZ, Jamef, Ilhabela-SP). Status `Delivery Failed`, 0/1 volumes entregues. Evento de 26/10 às 08:28 BRT: **“EMBALAGEM SINISTRADA (DANIFICADA)”**. O caso é objetivo e exige tratativa com a Jamef; não é apenas atraso.
- `100-0013963-2` (NF 0013963, MATRIZ, Via Pajuçara): `Shipped`, 0/2 volumes, despacho em 26/10 09:31, ETA 29/10. Sem evento de trânsito ainda, mas prazo não vencido; monitorar, sem classificar como atraso.
- `500-0002672-2` (NF 0002672, GCL, Pacífico): `Shipped`, 0/2 volumes, despacho em 26/10 15:13, ETA 16/11. Dentro do prazo.
- `300-0005689-2` (NF 0005689, ACL, Correios): shipment existente, status `CREATED_AT_LOGISTIC_PROVIDER`, rastreio `AE073724107BR`, despacho em 26/10 17:15, ETA 29/10. Sem atraso; o comando `tracking` apresentou erro técnico no formatador por `shipment_order_volume_invoice=null`, mas o payload bruto confirmou o shipment e o histórico inicial.
- `300-0005433-2` (Rápido Figueiredo): entregue em 23/10, antes do ETA de 26/10. Alerta anterior encerrado.

## 3. Oracle/DEBX complementar — 26/10/2026
- 74 NFs série 2; faturamento R$ 341.119,22; frete R$ 3.406,08.
- 4 de 5 unidades ativas.
- Transportadoras: Correios 31, Rápido Figueiredo 18, Retirada/Balcão 11, Frete Valor Fixo 5, Via Pajuçara 4, Dia e Noite 2, Jamef 1, Pacífico 1 e Favorita 1.
- Cotação Intelipost: 59/74 NFs; gasto real CIF de R$ 2.840,72, equivalente a 3,0% do faturamento CIF — dentro da meta de 5%.
- ACL nos últimos 2 dias: 17 pedidos `A` e 118 `X`. Regra canônica aplicada: `X = EXPEDIDO`.

## Recomendações
1. Abrir imediatamente tratativa com a Jamef para a NF 0013942: solicitar confirmação de avaria, fotos, preservação da embalagem, coleta/devolução ou reenvio e prazo formal de solução.
2. Acionar Comercial/atendimento do cliente da NF 0013942; não tratar como simples atraso.
3. Monitorar `100-0013963-2` e `300-0005689-2` no próximo ciclo; prazos ainda não vencidos.
4. Corrigir o formatador do script Intelipost para aceitar `shipment_order_volume_invoice=null`; o payload da API está funcional e o erro é local do script.
