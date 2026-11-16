# Rotina Diária — 16/11/2026 (seg, 08:00 BRT)

## API Intelipost
- ✅ Online (0.3ms). 9/15 transportadoras ativas.

## Oracle DEBX
- Sessão TEST_PED válida (conamore).
- Últimos 5 dias (12–16/11): 155 NFs · R$ 914.889,09 · frete gasto CIF 3,2% (meta <5%).
- Ontem (dom 15/11): 0 NFs (normal).

## Criticidade
- **Zero atraso aberto** — nenhuma NF em trânsito com ETA vencida (<16/11).
- **Zero extravio/avaria** — nenhum CLARIFY_DELIVERY_FAIL em transportadoras de rede (Via Pajucara, Jamef, Rápido Figueiredo, Pacífico).
- **2 falhas de entrega Correios Sedex (falha de contato, NÃO extravio):**
  - NF 0005999 (WLADYA ALCÂNTARA, Guaratinguetá-SP, R$21,54) — "carteiro não atendido" / DESTINATÁRIO AUSENTE (13/11).
  - NF 0005997 (JOSÉ MARCOS ALVES DE LIMA, SP, R$12,97) — "aguardando retirada" (13/11).
- D-status residual: 0129128 (07/11, R$821,81) — Magento MPD_STATUS='C' (cancelado), sem ORA-04091, sem NF. Antigo, sem ação nova.
- L-status: 129941A (12/11, R$43,90) — B2B, sem match Magento. Baixo valor.

## Fila Intelipost
- 0 erros nos últimos 5 dias → integração ERP→Intelipost SAUDÁVEL (shipment orders recentes existem e tracking flui).

## Observações
- Correios Sedex: `shipment_order_volume_invoice = null` em todas as NFs, mas `electronic_content_declaration` presente e DC-e autorizada → gap de normalização do payload, NÃO é a falha de emissão DC-e (PROCESSING_FAILED) documentada em 11/11. O comando `tracking` quebra com AttributeError nesses casos; usar `shipment`.
- Série 7 Correios (NFs 0705341–0705350, cliente 16041, 10 NFs R$22–27 cada, 12/11): sem shipment order e SAI_DATSAI=None (não expedidas). Baixo valor, provável fluxo fiscal/manual — não tratado como falha de integração.

## Ação
- Comercial: contato com os 2 clientes Correios (reagendar entrega / orientar retirada).
