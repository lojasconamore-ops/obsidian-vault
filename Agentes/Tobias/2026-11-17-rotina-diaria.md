# Rotina Diária — 17/11/2026 (ter, 08:00 BRT)

## API Intelipost
- ✅ Online (0.3ms). 9/15 transportadoras ativas (Via Pajucara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita, Correios Sedex).

## Oracle DEBX
- Sessão TEST_PED válida (conamore).
- Seg 16/11: 32 NFs com CODTRA · R$ 102.781,92 (retomada pós-feriado; sáb 14 e dom/feriado 15 = 0 NFs, normal).
- Criticidade 15 dias: X=1701 (R$312k), A=30, F=3, D=1, L=1. Zero G, zero SEM STATUS.

## Criticidade
- **Zero atraso aberto** — nenhum shipment em trânsito com ETA vencida.
- **Zero extravio/avaria.**
- D-status residual: 0129128 (07/11, R$821,81) — Magento cancelado, sem ORA-04091, sem NF. Antigo, sem ação nova (idem 16/11).
- L-status: 129941A (12/11, R$43,90) — B2B retirada/balcão, baixo valor. Sem ação nova.
- ⚠️ Watch (não crítico): 300-0005854-2 (Jamef, Santa Maria-RS) — chegou filial destino 11/11, ETA 18/11 (amanhã), 6 dias sem evento de entrega. Dentro do SLA; reavaliar amanhã.

## Fila Intelipost
- 0 erros em 15 dias → integração ERP→Intelipost SAUDÁVEL. Contraprova: NFs de 16/11 (100-/300-) têm shipment order e tracking fluindo (In Transit/Shipped, ETA futuro).

## Observações
- Correios `tracking` segue quebrando com AttributeError em `shipment_order_volume_invoice=null`; usar `shipment` (JSON). Ex 300-0006024-2 está DELIVERED (16/11), não PROCESSING_FAILED.
- SAI_DATSAI null em todas as NFs — campo não populado no fluxo; não interpretar como "não expedido" (regra X=expedido).
