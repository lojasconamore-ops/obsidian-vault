# 📊 GA4 Diário — Loja Casa

**Property:** 394358599 · `G-5709GFVVBK` · lojas.conamore.com.br (Magento varejo)
**Dados:** 11/11 (D-3, quarta) vs 10/11 (D-4, terça)
**Gerado em:** 14/11/2026 (sábado)

---

## Resumo executivo

- Queda generalizada de volume em D-3: usuários **-11,4%** (156 vs 176), sessões -13,3% e pageviews **-23,8%**.
- Qualidade de sessão recuou: tempo médio caiu de **5m23s para 4m17s** (-20,4%); engajamento segue estável (~78%).
- E-commerce caiu pela metade: **2 transações e R$ 1.237,30** (vs 4 / R$ 2.793,87) — dados Magento **não zerados**.
- Mobile domina (73% dos usuários); top canal segue **google / cpc** (62 usuários, 71,4% engajamento).
- Ruído de consent mode persiste: landing page "(not set)" com **9 usuários e 0 pageviews** (3ª maior porta de entrada).

---

## 1. Comparativo geral — D-3 vs D-4

| Métrica | D-3 (11/11) | D-4 (10/11) | Δ |
|---|---:|---:|---:|
| Usuários ativos | 156 | 176 | **-11,4%** |
| Sessões | 176 | 203 | -13,3% |
| Usuários novos | 119 | 130 | -8,5% |
| Visualizações de página | 1.101 | 1.444 | **-23,8%** |
| Taxa de engajamento | 77,8% | 78,3% | -0,5 p.p. |
| Taxa de rejeição | 22,2% | 21,7% | +0,5 p.p. |
| Tempo médio de sessão | 4m 17s | 5m 23s | **-20,4%** |
| Eventos | 2.475 | 3.207 | **-22,8%** |
| Transações | 2 | 4 | -50,0% |
| Receita de compras | R$ 1.237,30 | R$ 2.793,87 | **-55,7%** |

> ✅ E-commerce **não zerado** — dados reais de conversão Magento chegando corretamente ao GA4.

---

## 2. Novos vs Recorrentes — D-3 (11/11)

| Segmento | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| New (novos) | 127 | 127 | 85,0% | 15,0% | 4m 34s |
| Returning (recorrentes) | 37 | 47 | 61,7% | 38,3% | 3m 41s |
| (not set) | 0 | 2 | 0% | 100% | 0s |

- Novos respondem por ~77% dos usuários, com engajamento bem superior (85,0% vs 61,7%).
- **(not set): apenas 2 sessões, 0 usuários** — volume irrelevante, sem impacto no total (ruído de consent mode).

---

## 3. Canais — origem/mídia (D-3, top 15)

| Origem / Mídia | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| google / cpc | 62 | 70 | 71,4% |
| (direct) / (none) | 30 | 34 | 76,5% |
| google / organic | 21 | 23 | 82,6% |
| facebook / cpc | 16 | 16 | 81,3% |
| linktr.ee / referral | 10 | 10 | 100% |
| instagram / paid | 6 | 7 | 100% |
| chatgpt.com / ai-assistant | 3 | 3 | 100% |
| (not set) | 2 | 2 | 0% |
| IGShopping / Social | 2 | 2 | 100% |
| app.octadesk.com / referral | 2 | 5 | 80,0% |
| (data not available) | 1 | 1 | 100% |
| br.search.yahoo.com / referral | 1 | 1 | 100% |
| facebook-SiteLink / cpc | 1 | 1 | 0% |
| instagram.com / referral | 1 | 1 | 100% |

- **Google Ads (cpc) é o principal motor** de aquisição paga — 62 usuários (40% do total); Google (cpc + orgânico) soma 83 usuários.
- Meta (facebook cpc + instagram paid + SiteLink + IGShopping + instagram referral) soma 26 usuários em mídia paga/orgânica.
- **chatgpt.com / ai-assistant** aparece com 3 usuários e 100% engajamento — tráfego de IA presente.

---

## 4. Páginas — top 10 landing pages (D-3)

| Landing page | Usuários ativos | Sessões | Pageviews | Engajamento |
|---|---:|---:|---:|---:|
| / | 50 | 53 | 459 | 98,1% |
| /promocoes-lojas | 17 | 17 | 88 | 82,4% |
| **(not set)** | 9 | 11 | 0 | 0% |
| /edredom-queen-2-50x2-60 | 5 | 5 | 19 | 60,0% |
| /hotel-em-casa | 5 | 5 | 7 | 60,0% |
| /lencol-casal-c-elast-140x190x30cm-percal-180-fios-50-algod-o-e-50-poliester | 5 | 5 | 33 | 80,0% |
| /hotel-em-casa/toalhas-de-hotel-em-sua-casa | 4 | 4 | 24 | 75,0% |
| /capa-para-edredom-queen-250x260 | 3 | 3 | 13 | 100% |
| /edredom-king-2-50x2-80 | 3 | 3 | 4 | 33,3% |
| /enchimento-p-edredom-queen-2-50-x-2-60m | 3 | 3 | 3 | 66,7% |

- Home concentra tráfego (50 usuários); **/promocoes-lojas** é a 2ª porta de entrada — página de ofertas performando bem.
- **"(not set)" na 3ª posição com 9 usuários, 0 pageviews e 0% engajamento** = ruído de consent mode (mesma assinatura conhecida). Escalar Matias (GTM/CMP) + Adrian (LGPD).

---

## 5. Dispositivos (D-3)

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| Mobile | 114 | 118 | 82,2% | 17,8% | 4m 7s |
| Desktop | 42 | 58 | 69,0% | 31,0% | 4m 38s |
| Tablet | 0 | 0 | — | — | — |

- **Mobile domina com 73% dos usuários** — essencial manter experiência mobile otimizada.
- Desktop com engajamento menor (69%) e rejeição maior (31%) — jornada de comparação de produto.

---

## 6. Observações & Alertas

- 🔻 **Queda de volume e conversão em D-3:** usuários, pageviews, eventos e receita todos em retração vs D-4 (que foi o pico da semana). Parte esperada de oscilação diária; acompanhar se vira tendência.
- ⚠️ **Consent mode:** "(not set)" aparece como 3ª landing page (9 usuários, 0 pageviews) e na tabela de canais (2 usuários). Distorce leitura de páginas/canais. Correção de CMP pendente com Matias/Adrian.
- 📉 **Tempo médio em queda:** de 5m23s para 4m17s (-20,4%) — alinhado à redução de pageviews por sessão (6,3 vs 7,1).
- 🤖 **Tráfego de IA:** chatgpt.com/ai-assistant presente com engajamento 100% — sinal de visibilidade em buscas assistidas.
- 💰 **Google Ads (cpc) segue dominante** — 62 usuários, muito à frente do direto (30). Vale validar ROAS nos próximos relatórios de Ads.

---

*Relatório gerado automaticamente pela Flávia (Marketing) · Dados GA4 via Composio · Fuso America/Sao_Paulo*
