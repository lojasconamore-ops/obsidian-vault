---
tags: [google-ads, api, data-manager, ecl, conversao-offline, migracao, obsolescencia]
gerado: 2026-09-02
fonte: "Google Ads Developer Blog (15/mai/2026) + docs deprecations"
---

# Migração Google Ads API → Data Manager (jun/2026) — impacto Conamore

## A mudança
- Deadlines progressivos restringindo a Google Ads API em favor da **Data Manager API**:
  - **02/fev/2026** — `session attributes` + `IP address` em imports (novos adotantes bloqueados).
  - **15/jun/2026** — offline conversion imports + Enhanced Conversions for Leads: `UploadClickConversions`/`OfflineConversionFeedService` bloqueados p/ novos adotantes → erro `CUSTOMER_NOT_ALLOWLISTED_FOR_THIS_FEATURE`.
  - abr–jun/2026 — Enhanced Conversions web+leads unificados num único toggle.
- **Data Manager API** passa a ser o método primário p/ importar conversões offline.

## Allowlist (o gatilho)
- Quem NÃO importou offline conversions via Ads API **entre dez/2025 e mai/2026** fica FORA da allowlist → `UploadClickConversions` falha.
- Quem já importou, pode continuar via Ads API enquanto migra pro Data Manager.

## Impacto na Conamore
1. **`compra_erp` atual (via sGTM tag `sgtmadsct`)** — NÃO afetado. É conversion tracking via tag (GCLID+value+label), não `UploadClickConversions`.
2. **Plano ECL (29/08)** — AFETADO. Usava `ConversionUploadService`/`UploadEnhancedConversionsForLeads` + `user_ip_address` (IP já bloqueado desde fev/2026). Precisa migrar p/ **Data Manager API**.
3. **GCLID crítico** — fluxo de tag server-side depende de GCLID/FPID; nosso `cf_gclid` está vazio (bug Nexopath/consent).

## Ações
- [ ] Migrar plano ECL de `UploadClickConversions` → Data Manager API (ou Data Manager no Ads UI).
- [ ] Verificar se o developer token Conamore está allowlisted (histórico de import dez/2025–mai/2026).
- [ ] Confirmar modelo unificado de Enhanced Conversions na conta Ads.
- [ ] Reforçar captura de GCLID (cf_gclid) — pré-requisito do fluxo server-side.

## Referência
- https://ads-developers.googleblog.com/2026/05/changes-to-offline-click-conversion.html
- https://developers.google.com/google-ads/api/docs/deprecations
- https://support.google.com/google-ads/answer/2998031
