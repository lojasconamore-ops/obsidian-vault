# Rotina diária de logística — 11/11/2026

## Status da API
- Intelipost online às 08:00 BRT (0.3 ms).
- 9/15 transportadoras ativas: Via Pajucara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita, Correios Sedex.
- Fila `TEST_PED.I_FILA_INTELIPOST`: 0 registros de 01/11 a 11/11 (silenciosa). Shipments recentes existem para todos os carriers, então a integração ERP→Intelipost NÃO está parada — mas a falha de DC-e abaixo NÃO gera entrada na fila (falha silenciosa).

## 🚨 Alerta crítico do dia — falha de emissão DC-e Correios (37 NFs)
- **37 NFs Correios Sedex (CODTRA A3540) em `PROCESSING_FAILED`**, provider_message: "Correios reportou erro ao emitir DC-e".
- Janela da falha: **11-03 (33 NFs, 0005753 a 0005785) + 11-04 (4 NFs: 0005792, 0005793, 0005806, 0005809)**.
- Valor total: **R$ 1.253,08** (37 pedidos e-commerce de baixo ticket, ~R$11–155 cada).
- Estado: volume marcado `SHIPPED` (pré-lista enviada) → `PROCESSING_FAILED` na emissão do DC-e. `shipment_order_volume_invoice` = null (NF não vinculada ao volume).
- Confirmação de escopo: 11-03 NFs 0005750–0005752 entregues; 11-05 em diante TODAS entregues/em trânsito (falha resolvida no provider, mas os 37 ficaram presos).
- **Fila silenciosa mascara o problema:** 0 erros na `I_FILA_INTELIPOST` — a falha é no trecho Intelipost→Correios (pós envio do ERP), que não retroalimenta a fila.

## Demais leituras (sem criticidade)
- Oracle ACL: 1 `PDV_STATUS='D'` recente (0129128, 11-07, A3540, R$ 821,81) = cancelamento antes de NF (`MPD_STATUS='C'`, sem `F_MOVTO`) — não é devolução logística nem extravio. Nenhum L/G.
- Demais carriers normais: Jamef 0005804 (11-04) entregue; Dia e Noite 0005794 entregue; Pajucara 0005844/0005790 em trânsito ETA 17/11; Pacífico 0005814 em trânsito ETA 26/11; Rápido Figueiredo 0005801 em trânsito.
- Shipments recentes 11-09/11-10: Correios/Pajucara/Jamef/Pacífico/Rápido Figueiredo em estado normal (CREATED_AT_LOGISTIC_PROVIDER / SHIPPED).

## Aprendizado novo (registrar na skill)
1. **A3540 (Correios) em TEST_ACL AGORA gera shipment order via Intelipost (carrier 2 = Correios Sedex).** A nota antiga "A3540 ❌ sem shipment order" era específica do TEST_GCL e está desatualizada para ACL.
2. **Nova falha: `PROCESSING_FAILED` + "Correios reportou erro ao emitir DC-e"** — falha de emissão de DC-e no trecho Intelipost→Correios, que NÃO aparece na fila `I_FILA_INTELIPOST`. Detectar via `shipment` (estado do volume), não via fila.
3. **Bug no script `intelipost-track.py`:** o comando `tracking` quebra com `AttributeError` quando `shipment_order_volume_invoice` é None (caso de PROCESSING_FAILED). Usar `shipment` para enxergar o estado real desses pedidos.

## Recomendações
1. Acionar Matias (TI) + Intelipost + Correios para re-emitir o DC-e das 37 NFs e liberar a postagem.
2. Confirmar posição física dos 37 volumes (origin Valinhos): presos no CD ou já seguiram sem rastreio?
3. Acionar comercial para comunicar os 37 clientes (pedidos 03–04/11, Correios Sedex ETA 6 dias úteis já vencido).
4. Corrigir o script `intelipost-track.py` para não quebrar quando `shipment_order_volume_invoice` é None (é isso que mascara PROCESSING_FAILED na rotina diária).
5. Reconsultar os 37 shipments no próximo ciclo para confirmar re-processamento.
