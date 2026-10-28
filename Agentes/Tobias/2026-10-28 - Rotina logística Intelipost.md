---
title: Rotina logística Intelipost — 2026-10-28
tags:
  - logística
  - intelipost
  - oracle
  - rotina-diária
---

# Rotina diária — 28/10/2026 (BRT)

## Intelipost
- API online; 9/15 transportadoras ativas.
- Transportadoras ativas: Via Pajuçara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita e Correios Sedex.
- Tracking validado em 17 shipment orders da emissão de 27/10, cobrindo ACL (300-), MATRIZ (100-) e GCL (500-).
- Todos os shipments rastreados estão dentro da previsão; nenhum atraso aberto, extravio, avaria ou falha de entrega identificado.
- Dois shipments da MATRIZ, `100-0013996-2` e `100-0013997-2`, retornaram “Número do pedido desconhecido”. O mesmo prefixo/schema funciona em outras NFs do dia; tratar como gap pontual de integração/registro, não como criticidade de entrega.

## Oracle/DEBX
- Sessão validada: DB/service `conamore`, usuário `TEST_PED`.
- Janela operacional: 27/10/2026, série 2.
- Relatório: 83 NFs, faturamento R$ 259.086,52, frete total R$ 2.547,80, 4/5 unidades ativas.
- Status ACL do dia: A=16, X=104. Regra canônica aplicada: `PDV_STATUS='X'` = EXPEDIDO; não foi interpretado como cancelamento.
- Criticidade direta D/L/G/SEM STATUS no ACL: zero registros no dia.
- Fila `TEST_PED.I_FILA_INTELIPOST` desde 27/10: zero registros.
- `SAI_DATSAI` veio nulo nas NFs consultadas; portanto a ausência de data de saída não foi usada para inferir atraso.

## Leitura executiva
- Operação normal no corte das 08:00 BRT.
- Pendência de acompanhamento: validar os dois shipment orders desconhecidos (NFs 0013996 e 0013997) no ERP/fila, sem classificar como atraso até existir previsão vencida ou evidência de falha.
