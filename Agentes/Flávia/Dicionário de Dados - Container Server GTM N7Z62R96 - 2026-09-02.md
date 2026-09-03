---
tags: [gtm, sgtm, stape, inventario, dicionario-de-dados, conversao-offline]
gerado: 2026-09-02
fonte: "Google Tag Manager API"
---

# Dicionário de Dados — Container Server (GTM-N7Z62R96)

> Fluxo de VENDA mapeado tag a tag, via GTM API (service account firestore).

## Fluxo de venda (gargalo de entrada)
| Client | Path | Tipo de venda |
|---|---|---|
| Data Client — Increazy **ERP** | `/purchase_erp` | B2B/ERP |
| Data Client — Increazy **Magento** | `/purchase` | site/Magento |
| GA4 (client padrão) | `/g/collect` | navegador (cookie FPID, 2 anos) |
| Phone Normalization Client | — | normalização de telefone (p/ match ECL) |

## Tags por evento "compra" e canal

### GA4 (sgtmgaaw → measurementId G-V0KMM7L6M6)
- `compra_erp` (tag 237, ERP) e `compra_site` (tag 238, Magento)
- Campos enviados: value (ERP=`conversion.subtotal`; Magento=`value`), currency BRL, items/produtos, payment_type (method), app, status, total_value, subtotal_value, id_transacao_increazy (external_order), id_transacao_dbex (extra.incSlug), customer_email/name/cpf(document)/id/created_at + (Magento: city/uf/zip/country/phone)
- Obs: tags 140/175 `purchase (ANTIGO purchase_webhook_*)` são cópias anteriores ativas em paralelo.

### Google Ads (sgtmadsct / sgtmadsremarket)
- conversionId `AW-1041572367`
- Rótulos: `SERVER Purchase` (KkbFCKrToNoZEI_E1PAD) / `SERVER Purchase ERP` (Jyw5COuzp9sZEI_E1PAD)
- conversionValue = `ED - value` ou `[DE][CONAMORE][INCREAZY] value`; currency BRL
- Remarketing dinâmico: ecomm_prodid (id_produto), ecomm_totalvalue, ecomm_category

### Facebook CAPI (pixel 1586706054993486)
- user_data: em, ph, fn, ln, external_id, client_ip (ED ip_override), client_ua, country/st/ct/zp
- match fbp/fbc: navegador usa `ED - x-fb-ck-*`; Increazy usa `Firestore - x-fb-ck-*`

### LinkedIn CAPI
- accessToken + conversionRuleUrn → 🔴 **PREENCER** (placeholder)

## 🔴 Buracos de dados (TO-DOs)
1. **LinkedIn 100% placeholder** — Insight Token + todos os CONVERSION ID com "PREENCER". CAPI LinkedIn está montado mas NÃO dispara de fato.
2. **Facebook [INCREAZY] Purchase ERP (tag 198)** — `external_id`, `x-fb-ck-fbp`, `x-fb-ck-fbc` = "PREENCHER". O match do CAPI para venda B2B/ERP fica sem external_id e sem cookies de navegador (dependendo só de em/ph/fn/ln).
   - Contraste: tag 78 (Purchase ERP via CAPI trigger do navegador) usa `ED - x-fb-ud-external_id` e `ED - x-fb-ck-*` (valores reais).

## Conclusões
- Atribuição GA4 já é reconstruída **no server** via Firestore (transformação Incluir/Excluir x-ga; lookup utm_source/medium/campaign, ga_session_id, fbp/fbc).
- O match de Meta para venda B2B tem 3 campos "PREENCHER" (external_id + fbp + fbc) — oportunidade de melhora de match rate.
- LinkedIn é o canal mais "cru" (pendente de credencial).

## Status
- [x] Dicionário de dados de venda extraído
- [ ] Destravar LinkedIn (Insight Token + conversion rule URN) — Matias
- [ ] Corrigir "PREENCHER" na tag 198 (Facebook ERP) — avaliar com Matias
