# Ecommerce — Auditoria Communitas Fase 1 + Reunião 14/10

**Data:** 09/10/2026
**Fonte:** https://communitascom.github.io/conamore-fase1/ (Junior Communitas — Marketing)
**Reunião:** quarta 14/10 às 9:00 — ecommerce (ajustes sugeridos pelo Junior), com João e "Samurai" nas análises.

## Contexto
Sérgio falou com João e combinou avançar com ajustes de ecommerce sugeridos pelo Junior (Communitas). Também vão "colocar o Samurai" para as análises. Reunião 14/10 9h.

## O que é a auditoria
- UX/UI dos 2 e-commerces (Hotelaria B2B + Casa B2C).
- 11 achados medidos em pixels; 15 ajustes de Fase 1 (CSS/config, sem reestruturação). Fase 2 = estrutura (produtos duplicados, filtros, taxonomia).

## Achados críticos (consenso meu)
1. #3 PDP com foto de OUTRO produto (Fronha Harmony mostra lençol Quality + fronha Confort 180) — mesmo problema de higiene de dados do Mercado Livre.
2. #13 Frete grátis piso B2B (R$1.500) aplicado à Casa — "faltam R$1.456" em carrinho de R$43,90.
3. #5 Carrinho "vazio" + Subtotal/Total sobrepostos (14px).
4. #7 Parcelamento escondido por CSS (1x / até 4x / hidden).
5. #1/#2 Produto não aparece sem rolagem (mobile 2,5–3 telas).

## Meus alertas
- #8 (SEO text antes dos produtos): mover para baixo OK, mas preservar H1/meta/indexabilidade (impacta SEO/GEO).
- #10 (27 domínios 3º / 187KB JS): inclui GTM/Consent/RD — testar tracking após qualquer mudança de layout.

## Pendências
- [x] Sérgio solicitou os 15 ajustes da Fase 1 à Increazy (09/10).
- [ ] Validar os 15 itens após deploy da Increazy (checklist de aceite).
- [ ] Saber o que é o "Samurai" (analytics/heatmap/BI?) para avaliar integração com GA4+RD Station+sGTM.
- [ ] (Opcional) Preparar briefing de 1 página antes de terça.

## Validação pós-Increazy (meus guardrails)
- #8 SEO: H1, meta tags e indexabilidade preservados (não remover, só reposicionar o bloco de 4.022 chars).
- #10 + layout: Consent Mode, GA4, RD Station e `compra_erp` não podem quebrar após mudanças de CSS/layout.
- Reportar em `Executado | Evidência | Status`.
