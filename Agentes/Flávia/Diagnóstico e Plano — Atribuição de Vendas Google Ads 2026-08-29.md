# Diagnóstico + Plano de Correção — Atribuição de Vendas no Google Ads

**Data:** 29/08/2026 · Flávia (Marketing)
**Objetivo:** fazer o Google Ads medir corretamente as vendas da Conamore.

## Escopo decidido (Sérgio)

| Fonte de venda | Entra na conversão? |
|---|---|
| Link de pagamento Increazy (ERP/B2B + site) | ✅ SIM (agora) |
| Venda física de loja (`F_MOVTO`) | ❌ NÃO |
| Boleto / faturamento | ⏳ DEPOIS (futuro) |

## Como funciona hoje (arquitetura real)

```
CLIENTE clica no anúncio → vira lead (RD Station)
        ↓
Venda fecha OFFLINE → pagamento via LINK DA INCREAZY
        ↓
Increazy envia webhook pro server-side (Stape):
   ├─ path /purchase_erp  → "compra_erp"  (B2B/ERP)
   └─ path /purchase      → "compra_site" (site/Magento)
        ↓
sGTM na Stape (GTM-N7Z62R96) dispara:
   GA4 (compra_erp/compra_site) + Google Ads + Facebook CAPI + LinkedIn
```

Dois fluxos em paralelo: (1) evento GA4 no navegador, (2) webhook da Increazy.

## Os 3 buracos encontrados

1. **Checkout órfão `i1764011093`** — 458 pagamentos aprovados na `I_PEDINCREAZY` que não são cobertos na origem. O server-side roteia por **path** (não por código de checkout), então quem decide o caminho é a Increazy.
2. **Lookup table do client-side desatualizada** — o GTM client-side (`GTM-MMGX8ZL`) tem uma lista fixa de checkouts (236/284/387/388 → `compra_erp`; 209-211/186-188 → `compra_site`) que não inclui o `i1764011093`.
3. **GCLID não é persistido** — capturado no clique (cookie) mas não guardado no RD Station, limitando re-atribuição posterior.

## Impacto

`compra_erp` registra ~R$ 530 mil/30 dias, contra ~R$ 2,2–3,1M de vendas reais no mesmo período (dependendo da referência). Smart Bidding otimiza com fração do faturamento.

## Plano de correção

| # | Ação | Dono | Prioridade |
|---|---|---|---|
| 1 | Mapear **todos** os checkouts → path correto (`/purchase_erp` = B2B, `/purchase` = site), incluindo `i1764011093` | Increazy | 🔴 Imediato |
| 2 | Atualizar a lookup table do client-side com todos os códigos de checkout | Increazy | 🔴 Imediato |
| 3 | Persistir o GCLID no lead (campo no form + RD Station) | Increazy/Matias | 🟡 Depois |
| 4 | Criar webhook/evento para boleto e faturamento (quando entrarem no escopo) | Increazy | ⏳ Futuro |
| 5 | Monitorar `compra_erp` vs faturamento real + alarme | Flávia | 🟢 Contínuo |

## IDs de referência

- Google Ads: `AW-1041572367` (customer `2335779078`)
- Ação de conversão primária: `WEB Conamore Offline ERP (compra_erp)` → `conversionActions/6886109455`
- Rótulos: `SERVER Purchase` (`KkbFCKrToNoZEI_E1PAD`) · `SERVER Purchase ERP` (`Jyw5COuzp9sZEI_E1PAD`)
- GTM client-side: `GTM-MMGX8ZL` · sGTM (Stape): `GTM-N7Z62R96` (`https://vtutlczq.san.stape.io`)
- GA4: `G-V0KMM7L6M6` (property `379729087`)
