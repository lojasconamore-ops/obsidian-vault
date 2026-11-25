# Rotina diária de logística — 25/11/2026 (quarta)

## Execução
- Horário: 08:00–08:20 BRT.
- Intelipost: API online (0,3 ms), 9/15 transportadoras ativas.
- Oracle/DEBX: online. Conexão TEST_PED OK.
- Regra aplicada: `PDV_STATUS='X'` = EXPEDIDO; não usado para inferir cancelamento.

## Oracle (somente leitura)
- NFs com CODTRA (7d, 18–24/11, por SAI_DTEMIS): **338** = 235 rastreáveis + 103 frota interna (29205).
- Valor rastreável: **R$ 373.245,14**.
- CODTRA 7d: A3540=113, 98693=47, 89844=34, 29227=26, 05976=10, 29232=3, 00599=2 (rastreáveis) + 29205=103.
- D/L/G (TEST_ACL, 7d): 1 registro — PDV 0131602, status D, CODTRA 29205 (frota interna), R$ 63,00, MPD_MSGERR vazio (sem ORA-04091). Sem criticidade logística.
- Fila I_FILA_INTELIPOST (7d): 6 erros em 18/11 (4 "cotação" + 2 "consumidor final faltando"); silenciosa 19–24/11. Integração saudável.

## Tracking Intelipost (235 NFs rastreáveis)
- Reconhecidas: 223/235 (95%). NÃO é zombie API.
- Classes: 159 em andamento, 51 entregues (20 no prazo + 31 atraso histórico), 13 com ETA vencido, 12 SEM_SO.
- Os 13 "ETA vencido" são FALSOS: `estimated_delivery_date_lp_iso`=24/11 desatualizado vs CT-e real (previsão 25/11). Todos em trânsito ativo (Via Pajucara/Jamef chegando na unidade destino; Correios em transferência 23–24/11). Zero atraso real.

## SEM shipment order (12 NFs)
- 6 de 24/11 (ontem) → lag de integração, devem gerar SO hoje.
- 6 antigas (18–23/11): 100-0014429/14448 (A3540), 100-0014469/14475 (29227), 100-0014494/14495 (29227). Padrão gapado conhecido, ~5%, não crítico.

## Criticidade REAL (persistem os 2 de ontem)
- 🔴 `100-0014314-2` — Dia e Noite (05976), São Paulo-SP, R$ 2.987,01, 3 volumes, **Label Created** desde 12/11, prev 16/11 → **9 dias vencido**. Carga nunca coletada.
- 🔴 `100-0014297-2` — Correios Sedex (A3540), Campinas-SP, R$ 185,00, **Shipped** (11/11) zero postagem, prev 12/11 → **13 dias vencido**. Etiqueta sem postagem.

## Recomendações
- Escalar Dia e Noite (14314): coleta não realizada há 9 dias — retificar coleta/reprocessar.
- Escalar Correios (14297): etiqueta sem postagem há 13 dias — confirmar coleta.
- Acompanhar 6 NFs de 24/11 sem SO no próximo ciclo.
