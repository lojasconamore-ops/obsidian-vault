---
title: Rotina logística Intelipost — 2026-11-15
tags:
  - tobias
  - logística
  - intelipost
  - rotina-diária
---

# Rotina logística — 15/11/2026 08:01 BRT

## Fontes e validações
- Intelipost: `status`, `delivery-methods`, tracking/shipment dos pedidos recentes.
- Oracle DEBX: sessão validada em `conamore`, usuário `TEST_PED`; consultas somente leitura.
- Colunas validadas antes da consulta: `TEST_ACL.F_PEDVENDA`, `TEST_ACL.F_SAIDAS`, `TEST_PED.I_FILA_INTELIPOST`.
- Regra aplicada: `PDV_STATUS = 'X'` = expedido; não foi interpretado como cancelamento.
- Janela Oracle: últimos 15 dias; rotina diária de 14/11 retornou zero NFs, coerente com sábado sem expedição série 2.

## Resultado
- API Intelipost online; 9/15 transportadoras ativas.
- Oracle: sessão normal. ACL nos últimos 15 dias: 1.682 pedidos X (expedidos), sem usar X como evidência de cancelamento.
- Fila `I_FILA_INTELIPOST`: zero registros nos últimos 15 dias; último registro em 28/10/2026, erro de cotação em TEST_MATRIZ. Não há erro novo na fila, mas o silêncio prolongado deve ser acompanhado.
- NFs ACL série 2 recentes possuem shipment orders `300-...-2` válidos.
- Tracking recente: NF 0006025/CORREIOS entregue em 14/11; NF 0006011/CORREIOS em trânsito com ETA 17/11; NF 0006027/Jamef em trânsito com ETA 18/11; NF 0006030/Via Pajucara despachada, ETA 19/11.
- Ponto de monitoramento: NF 0006029/Pacífico, despachada em 13/11, permanece `Shipped`, sem ETA e sem evento de trânsito após o despacho. Sem evidência suficiente para classificar como atraso/extravio neste domingo; acompanhar na próxima execução.

## Conclusão
Nenhuma criticidade logística real nova confirmada nesta execução. Não há atraso aberto por ETA vencida, extravio, avaria ou falha de entrega nos pedidos verificados.
