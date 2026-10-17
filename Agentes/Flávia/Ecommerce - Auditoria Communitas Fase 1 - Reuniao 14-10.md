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
- [x] Increazy informou que implementou os ajustes em staging, não em produção.
- [x] Documento de implementação consultado: **Feedback de melhorias - Conamore**.
- [ ] Validar os 15 itens após revisão de João e aprovação da Conamore (checklist de aceite).
- [ ] Saber o que é o "Samurai" (analytics/heatmap/BI?) para avaliar integração com GA4+RD Station+sGTM.
- [ ] (Opcional) Preparar briefing de 1 página antes de terça.

## Ambientes de teste informados
- Hotelaria: https://www_conamore_com_br.lab.increazy.com/
- Casa: https://lojas_conamore_com_br.lab.increazy.com/
- Produção: **não autorizar publicação ainda**.

## Documento da Increazy — status informado
### Concluídos em ambiente de teste
- Altura do header reduzida.
- Texto de categoria movido para o final.
- Mensagem de carrinho vazio.
- Remoção de HTML de parcelamento escondido.
- Ajuste de cor de preço e botão de compra.
- Header fixo nos sites.

### Pendentes
- Altura de banner reduzida.
- Barra de benefício no Casa.
- Regra de frete.

### Dúvidas
- Item marcado como "Dúvidas" no documento compartilhado; confirmar o conteúdo/deliberação com João/Increazy antes de aprovar.

## Validação preliminar dos stagings
- Ambos os ambientes respondem e exibem catálogo/home.
- Hotelaria: H1 aparece após o bloco inicial; scripts públicos incluem GTM `GTM-MMGX8ZL` e GA4 `G-CDCKFVTR5M`/`G-V0KMM7L6M6`.
- Casa: catálogo e produtos aparecem; é necessário validar formalmente a presença/consentimento do tracking antes do aceite.
- Esta checagem não substitui QA funcional: ainda faltam testes de carrinho, frete, parcelamento, checkout, eventos GA4/RD e compra ERP.

## Validação pós-Increazy (meus guardrails)
- SEO: H1, meta tags e indexabilidade preservados (não remover, só reposicionar o bloco de 4.022 chars).
- Tracking: Consent Mode, GA4, RD Station e `compra_erp` não podem quebrar após mudanças de CSS/layout.
- Reportar em `Executado | Evidência | Status`.

