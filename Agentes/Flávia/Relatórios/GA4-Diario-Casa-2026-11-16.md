# 📊 Resumo Diário de Tráfego GA4 — Loja Casa

**Conamore Casa** (lojas.conamore.com.br) · Property `394358599` (G-5709GFVVBK)
**Gerado em:** segunda-feira, 16/11/2026 · **Dados:** 13/11 (D-3) vs 12/11 (D-4) · Fuso America/Sao_Paulo

---

## Resumo executivo

- Queda generalizada em 13/11 vs 12/11: usuários ativos **−14,8%** (127 vs 149) e sessões **−17,4%** (147 vs 178) — sexta-feira mais fraca que a quinta, e o menor volume de sessões dos últimos 8 dias.
- **E-commerce zerado em 13/11** (0 transações / R$0), interrompendo sequência de 7 dias com vendas — precisa validação (queda real vs tracking).
- Qualidade de tráfego segurou: engajamento 80,3% (−1,2 p.p.) e rejeição 19,7% (+1,2 p.p.), mas tempo médio despencou **−32,5%** (6m10s → 4m09s).
- Tráfego **pago domina** (google/cpc + instagram/paid + facebook/cpc ≈ 55% dos usuários) e **mobile concentra 72%** do público.
- Ruído de **consent mode** presente: `(not set)` em landing page (6 sessões, 100% rejeição) e em newVsReturning (2 sessões) — volume baixo, assinatura conhecida.

---

## 1. Comparativo geral — 13/11 (D-3) vs 12/11 (D-4)

| Métrica | 12/11 (D-4) | 13/11 (D-3) | Δ |
|---|---:|---:|---:|
| Usuários ativos | 149 | **127** | −14,8% |
| Sessões | 178 | **147** | −17,4% |
| Usuários novos | 103 | **95** | −7,8% |
| Visualizações de página | 1.112 | **1.033** | −7,1% |
| Taxa de engajamento | 81,5% | **80,3%** | −1,2 p.p. |
| Taxa de rejeição | 18,5% | **19,7%** | +1,2 p.p. |
| Tempo médio de sessão | 6m10s | **4m09s** | −32,5% |
| Eventos | 2.663 | **2.332** | −12,4% |
| Transações | 2 | **0** | −100% |
| Receita de compras | R$ 796,70 | **R$ 0,00** | −100% |

> 🚨 **E-commerce (Magento) zerado em 13/11.** Transações/receita vêm preenchidas no restante da janela — ver item 6.

---

## 2. Novos vs Recorrentes — 13/11 (D-3)

| Segmento | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| **Novos** | 97 | 97 | 86,6% | 13,4% | 3m42s |
| **Recorrentes** | 40 | 48 | 70,8% | 29,2% | 5m16s |
| **(not set)** ⚠️ | 0 | 2 | 0% | 100% | 0s |

> `(not set)` com 2 sessões, 0 usuários, 100% rejeição e 0 engajamento — assinatura típica de **consent mode**. Volume baixo (~1,4% das sessões).

---

## 3. Canais — origem/mídia (13/11, top 15)

| Origem / Mídia | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| google / cpc | 53 | 57 | 75,4% |
| (direct) / (none) | 32 | 38 | 89,5% |
| google / organic | 12 | 12 | 66,7% |
| instagram / paid | 10 | 11 | 72,7% |
| facebook / cpc | 8 | 8 | 87,5% |
| linktr.ee / referral | 7 | 10 | 100% |
| app.octadesk.com / referral | 2 | 6 | 50,0% |
| chatgpt.com / ai-assistant | 2 | 2 | 100% |
| googlesyndication (safeframe) / referral | 1 | 1 | 100% |
| IGShopping / Social | 1 | 1 | 100% |
| rd-email / email | 1 | 1 | 100% |

> 11 origens/mídias no total. Pago (cpc/paid) soma **71 usuários (~55%)** — dominância de mídia paga no dia.

---

## 4. Páginas — top 10 landing pages (13/11)

| Landing page | Sessões | Usuários | Pageviews | Engajamento | Rejeição |
|---|---:|---:|---:|---:|---:|
| `/` | 66 | 59 | 730 | 92,4% | 7,6% |
| `/promocoes-lojas` | 9 | 9 | 69 | 88,9% | 11,1% |
| `(not set)` ⚠️ | 6 | 5 | 0 | 0% | 100% |
| `/enchimento-p-edredom-casal-2-20-x-2-50m` | 5 | 5 | 7 | 60,0% | 40,0% |
| `/lencol-casal-c-elast-140x190x30cm-percal-180-fios-...` | 4 | 4 | 8 | 75,0% | 25,0% |
| `/colcha-piquet-favo-queen-220-x-250cm-bege` | 2 | 2 | 2 | 50,0% | 50,0% |
| `/colcha-piquet-leve-queen-240-x-240cm-cinza` | 2 | 2 | 3 | 100% | 0% |
| `/colcha-solteiro-piquet-felicita-1-45-x-2-40-luiza` | 2 | 2 | 9 | 50,0% | 50,0% |
| `/hotel-em-casa` | 2 | 2 | 7 | 100% | 0% |
| `/hotel-em-casa/toalhas-de-hotel-em-sua-casa` | 2 | 2 | 7 | 100% | 0% |

> Landing page `(not set)` com 6 sessões, 0 pageviews e 100% rejeição — mesmo ruído de consent mode do item 2. 52 landing pages distintas no total.

---

## 5. Dispositivos (13/11)

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| **Mobile** | 92 | 102 | 83,3% | 16,7% |
| **Desktop** | 31 | 41 | 75,6% | 24,4% |
| **Tablet** | 4 | 4 | 50,0% | 50,0% |

> Mobile concentra **72,4% dos usuários ativos**.

---

## 6. Observações

- **E-commerce zerado em 13/11** — primeiro dia sem transação na janela 06–13/11 (todos os demais registraram de 1 a 4 transações). Recomendo validar com o time comercial se houve instabilidade no Magento ou no webhook `compra_erp` antes de tratar como queda orgânica de demanda.
- **Sexta-feira atípica** — 147 sessões é o piso dos últimos 8 dias (faixa 147–203), e o tempo médio caiu 32,5% no mesmo dia; queda de volume e de profundidade simultâneas.
- **Consent mode** — `(not set)` segue aparecendo com volume baixo (~6 sessões na landing page + 2 em newVsReturning), sem impacto material nos totais, mas confirma que o CMP não cobre 100% do tráfego (tema já escalado com Matias/Adrian).
- **Tendência da semana** — pico de engajamento em 08/11 (83,7%) e melhor receita em 10/11 (R$ 2.793,87); 13/11 fecha a semana como o dia mais fraco em volume e receita.
