# Rotina diária de logística — 01/11/2026

## Status da API
- Intelipost online às 08:00 BRT.
- 9/15 transportadoras ativas.
- Transportadoras listadas: Via Pajucara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita e Correios Sedex.
- Fila `TEST_PED.I_FILA_INTELIPOST`: 0 registros nos últimos 3 dias; há shipments recentes válidos, portanto não há evidência de integração parada.

## Alertas reais do dia
- **1 atraso aberto:** `300-0005747-2`, NF 0005747 série 2, Jamef, São Paulo-SP. ETA 30/10/2026 23:59; status `In Transit`, 0/1 entregue. Último evento: chegada na filial destino em 31/10 às 05:20. Requer confirmação de entrega/coleta local com a Jamef.
- Sem extravio ou avaria confirmados nos rastreios amostrados.
- `300-0005743-2` (Via Pajucara, 2 volumes) em trânsito, ETA 09/11; sem atraso.
- `100-0014065-2` (Rápido Figueiredo, 2 volumes) em trânsito, ETA 30/11; sem atraso.
- `500-0002695-2` (Pacífico, 1 volume) em trânsito, ETA 12/11; sem atraso.
- Oracle ACL: 3 registros `PDV_STATUS='D'` nos últimos 15 dias, todos `CODTRA=29205` (Frota Interna). Não foram tratados como extravio nem como atraso Intelipost. `MPD_MSGERR` sem erro nos registros consultados; o status X foi preservado como EXPEDIDO.

## Base Oracle validada
- Sessão confirmada: DB/service `conamore`, usuário `TEST_PED`.
- Colunas validadas antes das consultas em `F_PEDVENDA`, `F_MOVTO`, `F_SAIDAS`, `FI_MAG_PEDIDOS` e `I_FILA_INTELIPOST`.
- Janela de criticidade: últimos 15 dias; janela de NFs: últimos 3 dias; filtro de série e datas mantido conforme rotina.
- Relatório de 31/10 (sábado): 0 NFs de série 2 no resumo consolidado. A leitura por schema mostrou atividade em 29-30/10 e normalidade de shipments rastreáveis.

## Recomendações
1. Acionar Jamef hoje para NF 0005747 e exigir atualização de entrega após chegada na filial destino.
2. Reconsultar o shipment `300-0005747-2` no próximo ciclo; escalar se continuar sem evento de entrega.
3. Não abrir incidente para os demais pedidos amostrados: estão dentro da ETA.
4. Manter monitoramento dos pedidos com `CODTRA=29205` por operação física, fora da Intelipost.
