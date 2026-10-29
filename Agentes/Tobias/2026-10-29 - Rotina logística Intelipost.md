---
title: Rotina logística Intelipost — 2026-10-29
tags:
  - logística
  - intelipost
  - oracle
  - rotina-diária
---

# Rotina diária — 29/10/2026 (BRT)

## Intelipost
- API online às 08:00 BRT; 9/15 transportadoras ativas.
- Ativas: Via Pajuçara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita e Correios Sedex.
- Tracking validado em 10 shipments recentes dos schemas ACL (300-), MATRIZ (100-) e GCL (500-): 6 reconhecidos e em trânsito, com eventos posteriores ao despacho e previsão futura; 4 GCL retornaram “Número do pedido desconhecido”. Nenhum atraso aberto, extravio, avaria ou falha de entrega foi confirmado.
- Amostra reconhecida: ACL `300-0005729-2` (Via Pajuçara, ETA 30/10), `300-0005730-2` (Jamef, ETA 29/10) e `300-0005727-2` (Rápido Figueiredo, ETA 11/11); MATRIZ `100-0014025-2` e `100-0014014-2` (ambos ETA 05/11); GCL `500-0002679-2` (Pacífico, ETA 09/11).
- Alerta de integração/registro: as 4 NFs GCL série 2 de 28/10 com CODTRA `89844` (0002682–0002685) retornaram “Número do pedido desconhecido” no prefixo correto `500-`. Não classificar como atraso ou extravio sem confirmação de despacho/ETA.

## Oracle/DEBX
- Sessão validada: DB/service `conamore`, usuário `TEST_PED`; consulta somente leitura.
- Colunas de `F_PEDVENDA`, `F_SAIDAS`, `F_MOVTO` nos schemas `TEST_ACL`, `TEST_MATRIZ` e `TEST_GCL` foram descobertas antes das consultas. `SAI_DATSAI` existe; veio nulo nas NFs recentes analisadas e não foi usado para inferir criticidade.
- Janela de emissão consultada: 26–28/10/2026, todos os três schemas. Totais: ACL 443 NFs / R$ 94.731,99; MATRIZ 79 / R$ 602.781,74; GCL 78 / R$ 64.251,48.
- ACL últimos 15 dias: A=47, D=4, F=1, X=1.429. Regra canônica aplicada: `PDV_STATUS='X'` = EXPEDIDO; não foi interpretado como cancelamento, perda de receita ou parada operacional.
- Os 4 D-status do ACL são antigos (19–26/10) e associados a CODTRA `29205` (frota interna) ou `A3540` (Correios SA/GCL, sem rastreio Intelipost confirmado). Portanto entram como auditoria operacional, não como extravio/atraso comprovado.
- Fila `TEST_PED.I_FILA_INTELIPOST`: 2 registros nos últimos 7 dias, ambos em 28/10 às 13:29 BRT, mensagem “Não foi possível obter a informação da cotação”. É evidência de falha de cotação, não prova de atraso de entrega.

## Leitura executiva
- Operação de transporte rastreável normal no corte de 08:00 BRT: eventos ativos e previsões não vencidas nos shipments reconhecidos.
- Novo ponto de atenção: lote GCL/CODTRA 89844 de 28/10 sem shipment order reconhecido, correlacionado temporalmente com 2 erros de cotação na fila. Impacto ainda não quantificado como atraso porque `SAI_DATSAI` está nulo e não há ETA/evento Intelipost para essas NFs.
- Não há criticidade real de entrega confirmada hoje.

## Recomendações
1. Acionar Matias para validar a cotação e a criação de shipment order do lote GCL `0002682–0002685` / CODTRA `89844`, incluindo a causa dos 2 erros de cotação da fila.
2. Não tratar `PDV_STATUS='X'` como cancelamento nem usar a ausência de shipment order isoladamente como evidência de falha logística.
3. Reconsultar os quatro shipment orders GCL após a correção/repique do job; se continuarem desconhecidos, confirmar diretamente com a operação/transportadora.
