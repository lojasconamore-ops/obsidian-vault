# Relatório Diário de Logística — 13/11/2026 (sex)

## Status
- Intelipost: ✅ online (0.4ms), 9 transportadoras ativas.
- Oracle DEBX: ✅ online (sessão TEST_PED ok).
- Integração ERP→Intelipost: ✅ saudável — NFs recentes geram shipment orders (300-0006010-2, 100-0014314-2, 500-0002800-2 confirmados).
- Fila I_FILA_INTELIPOST: zerada 5 dias (sem erro = saudável, pois shipment orders recentes existem).
- Correios DC-e (falha 03-04/11 documentada): ✅ resolvida — Correios antigos (05-08/11) todos DELIVERED.

## Resumo Oracle (ontem, 12/11, série 2)
- 66 NFs · R$ 473.441,60 · frete R$ 2.134,23 · ticket R$ 7.173,36.
- 4 de 5 unidades ativas.

## Alertas do dia (Via Pajucara — última milha RJ)
1. ⚠️ **300-0005790-2** — SAAM TOWAGE BRASIL S.A., Itaguaí-RJ, R$ 11.529 (7 vol, 143 kg, frete R$ 544,15). Parado em São João de Meriti desde 06/11, ETA 11/11 vencida, 0/7 entregues. 7 dias sem movimentação. Atraso/ausência de progresso.
2. ⚠️ **100-0014137-2** — 93 Comercio de Alimentos, Rio-RJ, R$ 1.836,67 (frete R$ 96,23). "Averiguar falha na entrega" 11/11: "LOCAL DE DIFICIL ACESSO, CARRO PEQUENO, AGENDAR A ENTREGA". NÃO é extravio — falha de acesso; aguarda reagendamento.

## Baixa prioridade
- 1 devolução D-status (0129128, Correios Sedex, 07/11, R$ 821,81) sem ORA-04091 = devolução genuína, sem shipment order.
- 1 L-status (129941A, 12/11, R$ 43,90, retirada/balcão).

## Recomendações
- Acionar Via Pajucara para os 2 casos RJ (última milha). Não abrir sinistro (nenhum extravio confirmado).
- Monitorar Via Pajucara last-mile RJ (2 casos na mesma região/carrier).

## Pitfall Oracle registrado
- `SAI_CODTRA <> ''` e `NOT IN ('', ...)` retornam 0 silenciosamente: Oracle trata `''` como NULL, fazendo `X <> NULL` = NULL (nunca TRUE). Usar apenas `SAI_CODTRA IS NOT NULL` + exclusão explícita de valores não-nulos.
