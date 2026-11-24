# Rotina diária de logística — 24/11/2026 (terça)

## Execução
- Horário: 08:00–08:20 BRT.
- Intelipost: API online (0,3 ms), 9/15 transportadoras ativas.
- Oracle/DEBX: online. Conexão TEST_PED OK.
- Regra aplicada: `PDV_STATUS='X'` = EXPEDIDO; não usado para inferir cancelamento.

## Oracle (somente leitura)
- Consolidação 23/11 (`daily-order-check.sh --yesterday`): **61 NFs, R$ 325.073,29**, frete R$ 2.434,50 (CIF 0,3%), ticket médio R$ 5.329,07, 4/5 unidades ativas.
- F_PEDVENDA (TEST_ACL) D/L/G últimos 15 dias: 4 D-status CODTRA 29205 (frota interna, 12–17/11) + 1 L-status None (retirada, 12/11). Sem registro no Magento (FI_MAG_PEDIDOS) → sem ORA-04091 confirmável; investigação operacional/física, não via API. Nenhuma criticidade nova.
- Fila I_FILA_INTELIPOST: **0 erros em 5 dias** (19–23/11). Consistente com integração saudável (shipment orders sendo geradas em todos os schemas).

## Descoberta: prefixo BRG = 700-
- Confirmado via `TEST_BRG.I_COTACAO_INTELIPOST.ICI_ORDNUM` (24 NFs de 23/11 com prefixo `700-`).
- **Prefixo `400-` NÃO é o TEST_BRG atual**: retorna shipment orders de 2025 (transportadoras inativas "Camilo dos Santos"/"Generoso"). A numeração de NF do BRG reiniciou e coincidiu com NFs 2025 de outro schema.
- Mapa de prefixos agora: MATRIZ=100-, ACL=300-, GCL=500-, BRG=700-. TEST_FILIAL/TEST_CHC ainda não confirmados.

## Criticidade (tracking Intelipost)
### 🔴 Pendência de coleta persistente (etiqueta sem postagem)
- `100-0014314-2` — Dia e Noite (05976), São Paulo-SP, **R$ 2.987,01**, 3 volumes, Label Created, prev 16/11 (**8 dias vencido**), etiqueta nunca coletada.
- `100-0014297-2` — Correios (A3540), Campinas-SP, **R$ 185,00**, Shipped zero postagem, prev 12/11 (**12 dias vencido**).

### 🟡 Devoluções concluídas (retornadas ao CD)
- `100-0014267-2` — Correios, Macaé-RJ, R$ 469,78: "devolvido por solicitação do contratante/remetente" → entregue ao remetente 16/11.
- `100-0014243-2` — Correios, São Paulo-SP, R$ 268,03: "cliente desconhecido no local" → entregue ao remetente 13/11.

### ✅ Resolvido
- Cluster Rápido Figueiredo Nordeste (7 shipments GCL de 21/11): todos entregues (Delivered).

## Bug tracking Correios Sedex (invoice=None)
- `tracking` quebra com `AttributeError` em TODOS os Correios Sedex (A3540) com `shipment_order_volume_invoice=None`, mesmo com estado SHIPPED + "Emissão de DC-e realizada com sucesso". **Não é falha logística** — é bug do script. Fallback: `shipment` (JSON). Afeta 300-0006068-2, 700-0000921-2, 700-0000913-2 etc.

## Recomendações
- Acionar Dia e Noite (100-0014314-2, R$ 2.987) e Correios (100-0014297-2): carga não coletada há 8–12 dias — verificar coleta/retificar.
- Processar devoluções 4267 e 4243 (retorno ao CD): reemitir NF ou dar baixa no faturamento.
- Corrigir bug `tracking` para `shipment_order_volume_invoice=None` (Matias/TI).
