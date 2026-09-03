---
tags: [gtm, sgtm, stape, inventario, firestore, conversao-offline]
gerado: 2026-09-02
fonte: "Google Tag Manager API (service account conamore-hotelaria-firestore)"
---

# Inventário do Container Server-side (GTM-N7Z62R96) — COMPLETO

> Acesso via GTM API. Service account: `conamore-hotelaria-firestore@agile-kite-392211.iam.gserviceaccount.com`.

## IDs
| Item | Valor |
|---|---|
| Conta GTM | `6100042948` — "Conamore Hotelaria" |
| Container | `196967926` — `GTM-N7Z62R96` "CONAMORE Hotelaria (Server)" |
| Workspace | `30` — "Default Workspace" |

## Contagem
- Clients: **4** | Tags: **44** | Triggers: **27** | Variáveis: **113** | Transformações: **2** | Modelos: **6**

## Clients
1. `GA4` (gaaw_client) — client padrão GA4
2. `Data Client Stape - Increazy Magento Purchase`
3. `Data Client Stape - Increazy ERP Purchase`
4. `Phone Normalization Client`

## Templates (modelos customizados)
- Data Client · Firestore Writer · Phone Normalization Client · Array Builder · Facebook Conversion API · LinkedIn Conversion API

## Tags (por destino)
- **Google Ads**: sgtmadsct (Conversão Otimizada) + sgtmadsremarket (Remarketing Dinâmico) + sgtmadscl (Vinculador de conversões) — Purchase, ERP, AddToCart, Search, ViewItem, Begin Checkout, AddPaymentInfo
- **GA4 (sgtmgaaw)**: compra_erp, compra_site, purchase (antigo webhook_erp/web)
- **Facebook CAPI**: Purchase, ERP, PageView, ViewContent, AddToCart, InitiateCheckout, AddPaymentInfo, Search, Contact, Envio Form WhatsApp
- **LinkedIn CAPI**: Purchase, ERP, AddToCart, Begin Checkout, Ligação, Formulário News, Contato WhatsApp
- **Firestore Writer**: init_checkout_web

## Triggers (27)
- Webhooks **Increazy ERP/Magento** (purchase, add_shipping_info) + variantes "NULL ID Transação DEBX/Magento"
- CAPI triggers (always): PageView, view_item, add_to_cart, begin_checkout, add_payment_info, search, purchase_website, purchase_erp, contact, contato_whatsapp, call, form_news
- Event triggers (customEvent): purchase, add_to_cart, search, view_item, add_payment_info, begin_checkout, purchase_erp
- Firestore: init_checkout_event

## Variáveis (113) — destaques
- **Firestore (fs)**: utm_source/medium/campaign, ga_session_id, ga_session_number, user_data, products, page_*, x-ga-* (measurement_id, ecid, session, pscdl/consent, dma, gclid), x-fb-ck-fbp/fbc, x-fb-ud-external_id
- **Event data (ed)**: [DE][CONAMORE][INCREAZY] — items, total, value, conversion.*, client.*, user_data.*, details.address.*
- **Constantes (c)**: IDs de conversão Ads, rótulos SERVER *, pixel Meta (1586706054993486), tokens, LinkedIn IDs
- **Transformações**: Incluir Parâmetros x-ga (Atribuição no GA4) · Excluir Parâmetros x-ga

## Achados relevantes
1. **Firestore como base de atribuição JÁ implementado** — confirma arquitetura da Live 109 (guardar UTM/sessão/user_data e reatribuir no GA4 via transformação x-ga).
2. **compra_erp:** Increazy → Data Client ERP → tag GA4 compra_erp + Ads + CAPI + LinkedIn.
3. **🔴 LinkedIn CAPI com credenciais placeholder "PREENCER"** — montado mas tokens/IDs não preenchidos (não dispara).
4. **Phone Normalization Client** presente — base p/ ECL (hash de telefone).
5. **Eventos de lead/contato já mapeados** (Facebook Contact, Envio WhatsApp, LinkedIn Ligação/News) — base para qualify_lead/working_lead no futuro.

## Status
- [x] Inventário real do container mapeado (via GTM API)
- [ ] Corrigir nota anterior que dizia "container vazio" (erro de parsing — chave plural vs singular)
- [ ] Avaliar LinkedIn CAPI (credenciais pending) — acionar Matias se for prioridade
