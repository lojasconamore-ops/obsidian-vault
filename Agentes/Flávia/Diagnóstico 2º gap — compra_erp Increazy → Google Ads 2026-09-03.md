---
title: 2º gap — compra_erp Increazy → Google Ads (fragmentação + DDA)
tags: [google-ads, compra_erp, increazy, dda, atribuicao, conversao]
gerado: 2026-09-03
fonte: "Google Ads API (GAQL, customers/2335779078) + Oracle DEBX"
---

# Diagnóstico do 2º gap: Increazy → Google Ads

**Pergunta (Sérgio):** por que o `compra_erp` no Ads (~R$ 454K / 126 conv.) fica muito abaixo dos **336 pagamentos confirmados = R$ 1.034.176,04** que a Increazy de fato processou (Oracle, 30d)?

## Janela comparada
08/04/2026 → 09/03/2026 (mesma janela nos dois lados).

## O que é o "126,23 conversões / R$ 454K"
É a ação **`WEB Conamore Offline ERP (compra_erp)`** (WEBPAGE, PURCHASE, `primary_for_goal=true`, atribuição **DATA_DRIVEN**). No GAQL dos 30d:
- `conversions` = **127,29** · `conversions_value` = **R$ 455.928,74**
- `all_conversions` = 129,29 · `all_conversions_value` = R$ 458.393,40

## A venda ERP está FRAGMENTADA em 4+ ações (duplicadas)
| Ação | primary | conv | valor | obs |
|---|---|---:|---:|---|
| WEB Conamore Offline ERP (compra_erp) | ✅ | 127,29 | R$ 455.928,74 | a que o Sérgio vê |
| 01092024 Compra Otimizada (Web) | ✅ | 295,57 | R$ 229.349,26 | legado, ativa |
| [SERVERSIDE] Conv. Otimiz - Purchase | ❌ | 268,84* | R$ 233.009,80 | server-side |
| CONAMORE Hotelaria - GA4 purchase | ❌ | 99,19* | R$ 88.324,12 | Magento (compra_site) |
| SERVER SIDE Compra ERP | ❌ | 0 | 0 | não dispara no período |

\* = `all_conversions` (ações non-primary não entram em `conversions`).

O dicionário do sGTM já apontava: **tags 140/175 `purchase (ANTIGO purchase_webhook_*)` ativas em paralelo** com as novas server-side.

## Por que o número do Sérgio "some"
1. **Fragmentação** — a mesma venda ERP cai em várias ações ao mesmo tempo (webhook antigo + server-side novo + GA4). Nenhuma ação isolada soma os 336 pedidos.
2. **Atribuição DDA** — os "127,29" são crédito fracionário (data-driven), não 127 vendas. O mesmo vale para o valor (R$ 456K é o crédito atribuído, não o total).
3. **`primary_for_goal` errado** — as ações server-side reais (`[SERVERSIDE] Conv. Otimiz - Purchase`, `SERVER SIDE Compra ERP`) estão `primary=false`, então ficam fora da métrica "conversões".

## O que NÃO explica (descartado)
- **Frete/subtotal**: frete = R$ 16.555 (1,6% de R$ 1.034.176). Subtotal vs total é irrisório. O valor do compra_erp usa `conversion.subtotal`, mas a diferença é ~1,6%, não os ~56% do gap.

## Conclusão
O R$ 1,03M de pagamentos confirmados **não está "perdido"** — está **espalhado** por ações duplicadas e **fracionado** pela atribuição DDA. O "126,23 / R$ 454K" é um fragmento (uma ação) sob a lente da DDA.

## Correções (proposta p/ Sérgio/DigitalCEO)
1. **Consolidar** as ações de compra ERP numa única (`WEB Conamore Offline ERP (compra_erp)`), desativando as duplicadas (`01092024 Compra Otimizada`, `[SERVERSIDE] Conv. Otimiz - Purchase`, `SERVER SIDE Compra ERP`).
2. **Desativar as tags legadas** 140/175 (`purchase_webhook_*`) no sGTM.
3. **Definir `primary_for_goal` correto** e decidir atribuição (DDA mantém decimais; last-click → inteiro).
4. (Menor) alinhar `conversion.subtotal` × total, se quiser casar valor exato com o PED.

> Mudanças de conta (primary_for_goal, desativar ações/tags) = aprovação do Sérgio/DigitalCEO.
