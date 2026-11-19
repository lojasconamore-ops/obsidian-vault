# Rotina logística — 19/11/2026

## Execução
- Horário: 08:00–08:10 BRT.
- Intelipost: API online, 0,9 ms, 9/15 transportadoras ativas.
- Transportadoras ativas: Via Pajuçara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita e Correios Sedex.
- Oracle: sessão validada em `conamore`, usuário `TEST_PED`; consultas somente leitura.
- DEBX/Oracle: validação de colunas executada para `F_SAIDAS`, `F_PEDVENDA`, `F_MOVTO`, `FI_MAG_PEDIDOS` e `I_FILA_INTELIPOST`.

## Resumo de 18/11/2026
- 72 NFs série 2; faturamento R$ 106.712,47; frete R$ 2.175,63.
- 4 de 5 unidades ativas.
- 64/72 NFs com cotação Intelipost; CIF 58 e FOB 6.
- Gasto real com frete CIF: R$ 3.302,40, equivalente a 4,1% do faturamento CIF — dentro da meta de 5%.

## Rastreio atual
- Amostragem completa dos shipments das séries recentes de TEST_MATRIZ (prefixo `100-`), TEST_ACL (`300-`) e TEST_GCL (`500-`).
- Nenhum atraso aberto, extravio ou avaria confirmado.
- NFs 0014437 e 0014438: Correios, em trânsito, ETA 19/11/2026 23:59; eventos recentes em São Paulo, sem atraso às 08:00 BRT.
- NF 0014428: Correios, `SHIPPED`, ETA 24/11/2026; sem evento de trânsito ainda, mas prazo não vencido.
- Demais shipments rastreáveis estão dentro da ETA ou em estado operacional compatível.

## Alerta novo
- `I_FILA_INTELIPOST`: 6 registros em 18/11, todos `TEST_MATRIZ`:
  - 4x “Não foi possível obter a informação da cotação”;
  - 2x “Número de envio para o consumidor final está faltando”.
- Shipments sem reconhecimento no lote recente: `100-0014429-2` e `100-0014448-2` (CODTRA A3540), `100-0014443-2` (CODTRA 29205/frota interna) e `100-0014446-2`/`100-0014447-2` (CODTRA nulo). Não classificar como atraso: não há ETA/evento; requer correlação da fila e validação de expedição.
- Regra canônica aplicada: `PDV_STATUS='X'` foi tratado como EXPEDIDO, nunca como cancelado.

## Conclusão
- Operação normal do ponto de vista de criticidade de entrega.
- Alerta operacional de integração/cotação restrito a 6 ocorrências na TEST_MATRIZ; acompanhar reprocessamento e confirmação de shipment order.
