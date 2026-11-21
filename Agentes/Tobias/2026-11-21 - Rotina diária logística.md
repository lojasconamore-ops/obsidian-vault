# Rotina diária de logística — 21/11/2026 (sábado)

## Execução
- Horário: 08:00–08:12 BRT.
- Intelipost: API online (0,3 ms), 9/15 transportadoras ativas.
- Oracle/DEBX: **online** (voltou após bloqueio de rede ontem, DPY-6005). Conexão TEST_PED OK.
- Regra aplicada: `PDV_STATUS='X'` = EXPEDIDO; não usado para inferir cancelamento.

## Oracle (somente leitura)
- F_SAIDAS: janela usada **SAI_DTEMIS** (SAI_DATSAI retorna 0 para NFs recentes — ainda não populado).
- 130 NFs rastreáveis emitidas 18–19/11 (CODTRA ≠ 29205/None). Última emissão 19/11; nada em 20–21/11.
- F_PEDVENDA (TEST_ACL) D/L/G últimos 7 dias: **zero**. Zero ORA-04091.
- Fila I_FILA_INTELIPOST: 6 erros em 18/11 (4x "cotação" + 2x "consumidor final faltando"), silenciosa 19–21/11.

## Alertas do dia
### 🔴 Cluster Rápido Figueiredo "Clarify Delivery Fail" — última milha Nordeste
7 shipments (todos GCL, prefixo 500-), total R$ 15.576 / 12 volumes, todos "saída p/ entrega → averiguar falha" em 18–19/11. Sem "extravio" no evento → NÃO é extravio confirmado, mas falha de entrega ativa.
- 500-0002758-2 Fortaleza-CE (09/11, R$2.779)
- 500-0002760-2 Fortaleza-CE (09/11, R$1.386)
- 500-0002766-2 Porto Seguro-BA (09/11, R$2.465)
- 500-0002782-2 Recife-PE (10/11, R$5.000) — Pousada do Martins
- 500-0002788-2 Recife-PE (11/11, R$2.087) — Pousada do Martins
- 500-0002801-2 Recife-PE (13/11, R$1.120)
- 500-0002805-2 Porto Seguro-BA (13/11, R$739)

### 🟡 Correios Delivery Failed
- 100-0014267-2 Macaé-RJ (R$470, ECOMUM Alimentos) — ETA vencida 19/11; "averiguar falha" no dia da postagem.
- 100-0014243-2 São Paulo-SP (R$268) — ETA 25/11.

### 🟡 Pendência de coleta (etiqueta sem postagem, ETA vencida)
- 100-0014314-2 Dia e Noite, São Paulo-SP (R$2.987) — Label Created, prev 16/11 (5 dias vencida).
- 100-0014297-2 Correios Campinas-SP (R$185) — Shipped, zero postagem, prev 12/11 (9 dias vencida).

### ⚙️ Correios tracking bug (invoice=None)
131 NFs A3540 emitidas 09–15/11: 112 entregues (85%), 2 DELIVERY_FAILED, 2 SHIPPED, 2 CLARIFY_DELIVERY_FAIL, 2 PRE_SHIPMENT_LIST_FAILED (DC-e), 1 IN_TRANSIT, 10 NO_STATE (série 7). `tracking` quebra com AttributeError; fallback `shipment` (JSON) funciona.

## Recomendações
- Acionar Rápido Figueiredo para os 7 shipments Nordeste: obter motivo da falha e reagendar entrega (cluster = possível gargalo de última milha).
- Acionar Correios para 100-0014267-2 (ETA vencida) e 100-0014243-2.
- Investigar pendência de coleta 100-0014314-2 (Dia e Noite) e 100-0014297-2 (Correios).
- Corrigir bug `tracking` para `shipment_order_volume_invoice=None` (Matias/TI).
