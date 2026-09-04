---
title: Passo a passo — reativar Firestore de pagamentos (increazy-erp / increazy-site)
tags: [firestore, gtm, sgtm, stape, compra_erp, atribuicao, passo-a-passo]
gerado: 2026-09-03
status: proposta-para-aprovacao
---

# Reativar gravação de pagamentos no Firestore (espelho do init_checkout_web)

> Objetivo: fazer o Firestore voltar a guardar **pagamento ↔ client_id ↔ e-mail** (collections `increazy-erp` e `increazy-site`), espelhando a tag `init_checkout_web` que já funciona. Hoje essas collections estão **congeladas desde 12/02/2025** porque o container server-side **não tem** tag Firestore Writer para os eventos de compra.

## Onde mexer
GTM server-side → conta "Conamore Hotelaria" (`6100042948`) → container "CONAMORE Hotelaria (Server)" (`196967926` / `GTM-N7Z62R96`) → workspace `30` "Default Workspace".

## Peças existentes (reaproveitar, não criar)
| Peça | ID | O que é |
|---|---|---|
| Template | `135` | **Firestore Writer** (Stape, `github.com/stape-io/firestore-writer-tag`) — já instalado |
| Tag referência | `151` | `⚫3.1 [FIRESTORE] init_checkout_web` — o espelho a copiar |
| Trigger ERP | `153` | `[CONAMORE][WEBHOOK] Increazy ERP Purchase - purchase` |
| Trigger Magento | `154` | `[CONAMORE][WEBHOOK] Increazy Magento Purchase - purchase` |

## Parâmetros do template (validados no templateData)
`firebasePath` (path do doc/collection) · `addEventData` (grava todo event data) · `firebaseMerge` (merge vs sobrescreve) · `firebaseProjectIdOverride` + `firebaseProjectId` (projeto) · `addTimestamp` + `timestampFieldName` · `skipNilValues` · `customDataListGroup` (campos custom) · `logsGroup`.

> `firebaseProjectIdOverride=false` → usa `GOOGLE_CLOUD_PROJECT` do ambiente = service account do container = `agile-kite-392211`.

## Passo a passo (2 tags novas)

### Tag A — `⚫3.2 [FIRESTORE] increazy_erp`
1. Tags → Nova → "Firestore Writer" (template 135).
2. Parâmetros:
   - `firebasePath` = `increazy-erp`
   - `addEventData` = ✅
   - `addTimestamp` = ✅ · `timestampFieldName` = `timestamp`
   - `skipNilValues` = ✅
   - `firebaseMerge` = ❌
   - `firebaseProjectIdOverride` = ❌
   - Logs = `debug`
3. Trigger de disparo = `[CONAMORE][WEBHOOK] Increazy ERP Purchase - purchase` (153).

### Tag B — `⚫3.3 [FIRESTORE] increazy_site`
Igual, mudando:
- `firebasePath` = `increazy-site`
- Trigger = `[CONAMORE][WEBHOOK] Increazy Magento Purchase - purchase` (154).

## Ponto de decisão — dedup / document id
O template cria **document ID aleatório** quando o `firebasePath` aponta para uma collection. Como o webhook Increazy pode reenviar eventos, há risco de duplicata. Duas opções:
1. **(Recomendada)** `firebasePath` dinâmico apontando para um document específico: `increazy-erp/{{unique_event_id}}` — o payload Increazy já traz `unique_event_id` (ex.: `1738867744317_552786601`), virando idempotência natural. Validar se a variável `unique_event_id` está disponível no escopo do Data Client.
2. Manter `firebasePath = increazy-erp` (collection) e aceitar docs duplicados em reenvio (o `unique_event_id` fica gravado como campo, permitindo dedup depois).

## Validação
1. Preview/Debug do sGTM → disparar um pagamento real (ERP e/ou Magento).
2. Conferir no Firestore (`GET .../documents/increazy-erp?orderBy=timestamp desc`) se aparecem docs com data de hoje.
3. Monitorar 7 dias.

## Riscos / alinhamentos
- **LGPD**: volta a gravar PII (e-mail, CPF, telefone, endereço) no Firestore → validar com **Adrian**.
- **Quota**: volume baixo (~336 pagamentos/mês) — sem risco de estourar o free tier.
- **Atribuição não fecha só com isso**: o `gdid`/`campaign` no payload ainda vem placeholder (ver diagnóstico Firestore). Este passo reativa o HISTÓRICO de pagamento; a atribuição correta ao clique Ads é o passo seguinte.

## Dono
Execução no GTM = **Matias (TI)** · aprovação de escopo = **DigitalCEO/Sérgio**.
