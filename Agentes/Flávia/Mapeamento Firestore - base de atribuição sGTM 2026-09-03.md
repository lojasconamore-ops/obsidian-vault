---
title: Mapeamento do Firestore (base de atribuição do sGTM)
tags: [firestore, gcp, sgtm, stape, atribuicao, tagueamento]
gerado: 2026-09-03
fonte: "Firestore REST API (service account via Stape power-up serviceAccount)"
---

# Firestore — base de atribuição do server-side (mapeada)

**Local:** Google Cloud Firestore, projeto `agile-kite-392211`. Acesso via service account `conamore-hotelaria-firestore@agile-kite-392211.iam.gserviceaccount.com` (recuperada do power-up `serviceAccount` da Stape, container `vtutlczq`).

## Collections (4)

| Collection | Docs | Última escrita | Papel |
|---|---:|---|---|
| `increazy-erp` | 242 | **12/02/2025** ❄️ | pagamentos B2B/ERP (webhook `/purchase_erp`) |
| `increazy-site` | 514 | **12/02/2025** ❄️ | pagamentos site/Magento (webhook `/purchase`) |
| `increazy_site` | 2 | **11/02/2025** ❄️ | eventos de navegação do site (add_shipping_info…) |
| `init_checkout_web` | 20.088 | **hoje (03/09/2026)** ✅ | begin_checkout / atribuição de campanha |

## Estrutura (documento `increazy-erp`)
Campos de topo: `order` (or_…), `app` (checkout 284/388…), `status` (success/canceled/waiting), `substatus` (complete/failed/pending), `method` (pix/creditcard/billet), `gateway` (pagarme5), `total`, `client_id` (dcid…), `unique_event_id`, `timestamp`, `sgtm_timestamp`.

- **`conversion`** (map): `id`, `application_id`, `external_quote`, `external_order` (id Increazy), `subtotal`, `freight`, `discount`, `tax`, `finished`, `gateway`, `method`, **`client`** (map: `id`, `name`, `email`, `document`, `created_at`), `products` (array), `created_at`, `updated_at`, `order_id` (nº pedido DEBX), `origin`, `source`, `custom_inputs`, `metadata` (ex.: `{"already_rdstation": true}`).
- **`extra`** (map): `methods`, `is_unique`, `has_coupon`, `expires_days`, `has_delivery`, `freight_label`, `freight_price`, `set_installment`, **`incSlug`** (= id_transacao_dbex), `options`.
- **`details`** (map): `bin`, `nsu`, `tid`, `card`, `brand`, `last4`, **`phone`**, **`holder`**, `address` (map 11 campos: uf/city/street/number/postcode…), `charges`, **`document`** (CPF), `installments`.
- **`history`** (array): mudanças de status (id, order_id, status, created_at, prev_total…).

## Estrutura (`init_checkout_web`)
Atribuição de campanha + topo de funil: `event_name` (begin_checkout/init_checkout_event), `campaign`/`campaign_source`/`campaign_medium`/`campaign_term`/`campaign_content`, `source`/`medium`/`term`/`content`, `utm_source/medium/campaign`, **`x-ga-gdid`** (Google Ads ID), `x-ga-gclid`?, `x-ga-gcs` (G111), `ga_session_id`, `client_id`, `x-ga-measurement_id` (G-V0KMM7L6M6), `x-ga-*` (ecid, pscdl/consent, gcd, dma…), `x-fb-ck-fbp`, `x-fb-ud-external_id`, `user_data` (map), `items`, `id_produto`, `id_cart`, `value`, `currency`, `page_location`, `page_title`.

## Achados-chave
1. **Firestore tem first-party data rico**: `email`, `document` (CPF), `phone`, `holder`/`name` — mas **só nos pagamentos congelados de 2025**.
2. **Collections de pagamento CONGELADAS desde 12/02/2025** (`increazy-erp` e `increazy-site`). Só o `init_checkout_web` segue ativo (20k docs, escrita até hoje). O Firestore Writer atual do sGTM só grava `init_checkout_web`.
3. **`x-ga-gdid` tem valor FIXO** (`dY2E1Nz.dNzQzZD`) em docs de 2025 E 2026 → placeholder/estático, NÃO é o gclid real de cada clique. Reforça o problema de captura de gclid (cf_gclid vazio / consent mode quebrado).
4. **`campaign = {campaignname}`** literal em alguns docs → template não resolvido; nome real da campanha Ads não está chegando.
5. `conversion.subtotal` (não `total`) é o valor da conversão — confirma que o compra_erp usa subtotal; a diferença é só o frete (~1,6% no agregado).

## Conexão com o gap
- A base que guardava **pagamento ↔ client_id ↔ email** (`increazy-erp`) parou em fev/2025 → o histórico de atribuição de venda por cliente está congelado.
- A atribuição viva hoje vem só do `init_checkout_web` (topo de funil), e mesmo ali o `gdid` está placeholder e a `campaign` não resolve.

## Artefatos
- Service account: `.hermes/profiles/marketing/tmp/gcp_service_account.json`
- Container Stape (JSON): `.hermes/profiles/marketing/tmp/stape_container.json`
- Collections: `.hermes/profiles/marketing/tmp/firestore_collections.json`
