# 📊 GA4 Diário — Loja Casa (varejo)

**Property:** 394358599 · `G-5709GFVVBK` · lojas.conamore.com.br
**Data de geração:** sábado, 21/11/2026 (BRT)
**Dados:** 18/11 (D-3) vs 17/11 (D-4)

---

## Resumo executivo

- Tráfego levemente positivo em volume: +1,9% usuários ativos (155→158) e +5,6% sessões (178→188), mas qualidade da sessão caiu (engajamento 82,6%→74,5%, rejeição 17,4%→25,5%).
- E-commerce em queda forte: 2 transações e R$ 213,41 de receita vs 5 transações / R$ 3.362,78 no D-4 (−93,7%) — volume absoluto baixo, leitura estatística limitada.
- `google/cpc` disparou para 60 usuários (maior fonte) mas com engajamento fraco (59,4%); `facebook/cpc` surgiu com 22 usuários (canal novo, provável campanha).
- Instagram pago caiu pela metade (22→11 usuários: `ig/paid` 7 + `instagram/paid` 4).
- Ruído de consent mode presente em landing page: `(not set)` com 9 sessões (4,8%), 0% engajamento — maior volume dos últimos dias; ausente em novos vs recorrentes.

---

## 1. Comparativo geral — 18/11 (D-3) vs 17/11 (D-4)

| Métrica | 17/11 (D-4) | 18/11 (D-3) | Δ |
|---|---:|---:|---:|
| Usuários ativos | 155 | 158 | **+1,9%** |
| Sessões | 178 | 188 | **+5,6%** |
| Novos usuários | 109 | 112 | +2,8% |
| Visualizações de página | 1.291 | 1.242 | −3,8% |
| Taxa de engajamento | 82,6% | 74,5% | −8,1 p.p. |
| Taxa de rejeição | 17,4% | 25,5% | +8,1 p.p. |
| Tempo médio de sessão | 5m39s | 4m22s | −1m16s |
| Eventos | 2.807 | 2.667 | −5,0% |
| **Transações** | 5 | 2 | **−3** |
| **Receita de compras** | R$ 3.362,78 | R$ 213,41 | **−93,7%** |

> E-commerce (Magento) ativo e com dados — não veio zerado, mas recuou fortemente em um dia de menor ticket.

---

## 2. Novos vs Recorrentes — 18/11 (D-3)

| Segmento | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| new | 116 | 116 | 81,9% | 18,1% | 4m50s |
| returning | 55 | 72 | 62,5% | 37,5% | 3m38s |

✅ `(not set)` **ausente** em novos vs recorrentes neste dia — sem ruído de consent mode nessa dimensão (diferente de dias anteriores). Nota: a soma new+returning (171) excede os 158 usuários ativos por sobreposição normal do GA4 (mesmo usuário com sessão "new" e "returning" no mesmo dia).

---

## 3. Canais (origem/mídia) — top 15 por usuários ativos (18/11)

| Origem / Mídia | Usuários | Sessões | Engaj. | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| google / cpc | 60 | 69 | 59,4% | 40,6% | 1m47s |
| (direct) / (none) | 31 | 36 | 77,8% | 22,2% | 6m19s |
| facebook / cpc | 22 | 23 | 82,6% | 17,4% | 6m02s |
| google / organic | 18 | 21 | 76,2% | 23,8% | 1m34s |
| linktr.ee / referral | 13 | 13 | 100% | 0% | 8m52s |
| ig / paid | 7 | 7 | 100% | 0% | 4m44s |
| instagram / paid | 4 | 4 | 75,0% | 25,0% | 3m25s |
| app.octadesk.com / referral | 3 | 5 | 80,0% | 20,0% | 10m18s |
| (data not available) | 2 | 2 | 100% | 0% | 8m35s |
| chatgpt.com / ai-assistant | 2 | 2 | 100% | 0% | 2m09s |
| safeframe.googlesyndication.com / referral | 1 | 5 | 80,0% | 20,0% | 12m48s |
| instagram.com / referral | 1 | 1 | 100% | 0% | 1m20s |

> **`facebook/cpc` é canal novo** (22 usuários, 82,6% engajamento) — provável campanha nova no Meta, sem registro no dia anterior. `google/cpc` saltou 49→60 usuários, mas com a pior qualidade do topo (59,4% engajamento, 40,6% rejeição, 1m47s). Instagram pago somou 11 usuários (`ig/paid` + `instagram/paid`), metade dos 22 do D-4. `(direct)` segue sólido (77,8% engajamento, 6m19s).

---

## 4. Landing pages — top 10 por sessões (18/11)

| Página | Sessões | Usuários | Engaj. | Rejeição |
|---|---:|---:|---:|---:|
| / | 55 | 54 | 96,4% | 3,6% |
| /lencois/linha-de-produto.html/serena | 16 | 16 | 87,5% | 12,5% |
| /lencois/linha-de-produto/avulsos.html | 13 | 13 | 84,6% | 15,4% |
| /lencol-casal-c-elast-140x190x30cm-percal-180-fios-50-algod-o-e-50-poliester | 13 | 13 | 92,3% | 7,7% |
| (not set) | 9 | 9 | 0,0% | 100% |
| /edredom-king-2-50x2-80 | 5 | 5 | 80,0% | 20,0% |
| /hotel-em-casa | 4 | 4 | 25,0% | 75,0% |
| /hotel-em-casa/toalhas-de-hotel-em-sua-casa | 4 | 4 | 50,0% | 50,0% |
| /lencois | 4 | 4 | 75,0% | 25,0% |
| /colcha-piquet-leve-queen-240-x-240cm-azul-1 | 3 | 3 | 100% | 0% |

> `(not set)` com 9 sessões (4,8% do total), 100% rejeição e zero engajamento — assinatura de ruído de consent mode. Volume em alta (5→6→9 sessões nos últimos 3 relatórios): vale escalar Matias (GTM/CMP) se persistir. `/lencois/linha-de-produto.html/serena` (16 sessões) é página nova no topo — provável alvo de campanha em andamento.

---

## 5. Dispositivos — 18/11 (D-3)

| Dispositivo | Usuários | Sessões | Engaj. | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| mobile | 122 | 134 | 77,6% | 22,4% | 3m36s |
| desktop | 36 | 54 | 66,7% | 33,3% | 6m18s |
| tablet | 0 | 0 | — | — | — |

> Mobile domina com folga (77,2% dos usuários), mas sessões mais curtas (3m36s) que desktop (6m18s) — consistente com navegação de vitrine B2C. Nenhum tablet no dia.

---

## 6. Observações

- **E-commerce caiu forte** (5→2 transações, receita R$ 3.362,78→R$ 213,41), mas o volume absoluto é baixo demais para leitura de tendência — acompanhar nos próximos dias antes de qualquer alarme.
- **Qualidade da sessão piorou** no D-3 (engajamento −8,1 p.p., rejeição +8,1 p.p., tempo médio −1m16s) apesar do leve crescimento de volume — sinal de tráfego pago de topo de funil diluindo a qualidade.
- **`google/cpc` cresceu mas com baixa qualidade** (59,4% engajamento vs 77,8% do direto) — vale auditar segmentação/anúncios para evitar compra de cliques frios.
- **`facebook/cpc` novo** com boa qualidade (82,6%) — verificar com Natália/Comercial se há campanha nova no Meta e garantir UTMs padronizadas.
- **Instagram pago com tags divergentes** (`ig/paid` vs `instagram/paid`) segue sem padronização — dificulta leitura limpa de ROAS por campanha.
- **Consent mode**: `(not set)` em landing page subiu para 9 sessões (maior dos últimos dias); ausente em novos vs recorrentes — monitorar e escalar Matias se continuar subindo.
