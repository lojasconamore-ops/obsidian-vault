# Mercado Livre — Auditoria de Anúncio: Kit 2 Lençóis Casal (SKU 17689)

**Data:** 09/10/2026
**Item ID:** MLB7771709766
**Catálogo:** p/MLB80277389
**Tipo de anúncio:** Clássico
**Preço:** R$ 133,80 (2 × R$ 66,90 — preço público unitário)

## Dados extraídos do anúncio

- Título: "Kit 2 Lençóis Casal Hotelaria Profissiona 180 Fios Sem Elástico 220x250 - Conamore Branco"
- Frete: grátis acima de R$ 19 (frete grátis 1ª compra) + retirada em agência grátis
- Estoque no anúncio: 5 kits disponíveis
- Vendido por: **CB20261006210217684** (nome automático — não é "Conamore")

## Ficha técnica (o que está correto)

- Marca: Conamore ✓
- Linha: Confort ✓
- Apresentação: Lençol plano ✓
- Cor: Branco ✓
- Composição: 50% algodão, 50% poliéster ✓
- Fios: 180 ✓
- Formato de venda: Kit, 2 peças ✓

## Problemas críticos (corrigir antes de divulgar mais)

1. **Nome do vendedor** = "CB20261006210217684" em vez de "Conamore". Mata a confiança e a marca.
2. **Dimensões erradas na ficha:**
   - "Comprimento do lençol plano: 180 cm" → deveria ser **250 cm**.
   - "Largura do lençol plano: 140 cm" → deveria ser **220 cm**.
   - Campos "lençol com elástico" (140×190) preenchidos → produto é **sem elástico**; remover/esvaziar.
   - Conflito com o título (220x250) → risco de devolução.
3. **"Hipoalergênico: Sim"** → não consta no descritivo oficial da Conamore. Remover ou comprovar.
4. **"Material principal: Algodão"** → composição é mista 50/50. Ajustar.

## Ajustes médios

- Título longo e com "Profissiona" (deve ser "Profissional"); ML corta a ~60 chars.
- "É adequado para branqueador: Sim" → revisar (poliéster + alvejante).
- "Altura máxima do colchão 40 cm" → sem sentido para lençol plano.

## Observações

- Divergência interna Conamore já conhecida: público diz 220×250, atributo interno `lencois_medidas_casal` diz 220×245. No ML, usar **220×250** (consistente com título e página pública).
- Parcelamento 12x R$ 13,22 = R$ 158,64 (com juros, coerente com Clássico).
- Frete grátis obrigatório (preço > R$ 79) cai sobre o vendedor — incluir no cálculo de margem.

## Margem ilustrativa (antes do frete)

| Comissão | Líquido |
|---|---|
| 10% | R$ 120,42 |
| 12% | R$ 117,74 |
| 14% | R$ 115,07 |
| 19% (Premium) | R$ 108,38 |

Confirmar % exata da categoria "Cama, Mesa e Banho" na seção de tarifas do anúncio.

## Ações recomendadas (ordem)

1. Renomear o vendedor/loja para "Conamore" (ou "Conamore Hotelaria").
2. Corrigir dimensões da ficha (plano 220×250; esvaziar campos de "com elástico").
3. Remover "hipoalergênico" ou obter comprovação.
4. Ajustar "material principal" e campos de lavagem.
5. Revisar título (≤ 60 chars, "Profissional" correto).
6. Validar sincronização de estoque com Oracle.
7. Fechar DRE (comissão + frete + embalagem + impostos + margem).
