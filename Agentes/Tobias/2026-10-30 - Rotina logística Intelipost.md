---
title: Rotina logística Intelipost — 2026-10-30
tags:
  - tobias
  - logística
  - intelipost
  - debx
---

# Rotina diária — 30/10/2026 (BRT)

## 1. Status da API

- Intelipost online.
- 9/15 transportadoras ativas.
- Transportadoras ativas: Via Pajuçara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita e Correios Sedex.

## 2. Oracle/DEBX

- Sessão validada: DB `conamore`, service `conamore`, usuário `TEST_PED`.
- Descoberta de colunas executada antes das consultas operacionais para `TEST_ACL.F_PEDVENDA`, `TEST_ACL.F_SAIDAS`, `TEST_PED.FI_MAG_PEDIDOS` e `TEST_PED.I_FILA_INTELIPOST`.
- Regra aplicada: `PDV_STATUS = 'X'` é EXPEDIDO; não foi usado como evidência de cancelamento ou falha.
- Relatório de 29/10/2026: 60 NFs série 2, faturamento R$ 303.292,57, frete total R$ 2.599,90; 4 de 5 unidades ativas.
- Frete CIF: 2,5% do faturamento (abaixo da meta de 5%). 8 de 36 NFs CIF acima de 5% individualmente; tratar como alerta de custo, não como criticidade de entrega.
- Fila `I_FILA_INTELIPOST`: 2 registros em 28/10, ambos “Não foi possível obter a informação da cotação”, schema TEST_MATRIZ. Sem evidência de fila parada; monitorar recorrência.

## 3. Rastreamento validado

- `300-0005743-2` (ACL, Via Pajuçara): In Transit, 0/2, despacho 29/10 12:30, ETA 09/11; eventos de trânsito em 29 e 30/10. Normal.
- `300-0005741-2` (ACL, Jamef): In Transit, 0/1, despacho 29/10 08:36, ETA 13/11; evento de saída de transferência em 30/10. Normal.
- `500-0002687-2` (GCL, Via Pajuçara): In Transit, 0/4, despacho 29/10 12:00, ETA 06/11; eventos de trânsito em 29 e 30/10. Normal.
- `100-0014054-2` (MATRIZ, Jamef): In Transit, 0/3, ETA 30/10 23:59; chegou à filial destino às 01:20 de 30/10. Ainda dentro do prazo na consulta das 08:00 BRT; monitorar até o fim do dia.

## Conclusão

Não foi identificado atraso aberto, extravio, avaria ou falha de entrega com evidência atual nos rastreamentos validados. Único ponto operacional: acompanhar o Jamef `100-0014054-2` até o fim do ETA e investigar a repetição dos dois erros de cotação da fila se novos registros surgirem.
