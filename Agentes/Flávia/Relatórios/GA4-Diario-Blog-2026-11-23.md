# 📊 Resumo Diário de Tráfego GA4 — Blog

**Blog Conamore** (hotelaria.conamore.com.br) · Property `451180315` (G-LMY9B1F249)
**Dados:** sexta 20/11 (D-3) vs quinta 19/11 (D-4) · Fuso America/Sao_Paulo

---

## Resumo executivo

Volume em alta (usuários +12,6%, sessões +6,7%, novos +19,1%), mas **qualidade caiu forte**: engajamento despencou de 46,2% → 34,2% e tempo médio de 2m33s → 47s, com rejeição subindo a 65,8%. Tráfego de baixa qualidade (direto com engajamento de 16,7%, mobile/desktop) puxou a queda. A landing `/calculadora-roupa-de-cama-de-hotel` concentra 32% dos usuários mas com engajamento fraco — sinal de tráfego de baixa intenção ou bot. Reforço: acompanhar conversão e qualidade das visitas à calculadora.

---

## 1. Comparativo geral — 20/11 vs 19/11

| Métrica | 19/11 (D-4) | **20/11 (D-3)** | Δ |
|---|---:|---:|---:|
| Usuários ativos | 95 | **107** | +12,6% |
| Sessões | 104 | **111** | +6,7% |
| Usuários novos | 89 | **106** | +19,1% |
| Visualizações de página | 118 | **123** | +4,2% |
| Taxa de engajamento | 46,2% | **34,2%** | −12,0 p.p. |
| Taxa de rejeição | 53,8% | **65,8%** | +11,9 p.p. |
| Tempo médio | 2m 33s | **0m 47s** | −1m 46s |
| Eventos | 393 | **399** | +1,5% |

---

## 2. Novos vs Recorrentes — 20/11 (D-3)

| Segmento | Usuários | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| new | 104 | 104 | 32,7% | 67,3% | 0m 42s |
| returning | 4 | 4 | 75,0% | 25,0% | 3m 24s |
| (not set) | 0 | 3 | 33,3% | 66,7% | 0m 12s |

⚠️ **"(not set)"** com 3 sessões e 0 usuários — assinatura de ruído de **consent mode** (3 sessões sem usuário atribuível). Volume baixo, mas presente.

---

## 3. Canais — top por usuários ativos (20/11)

| Origem / Mídia | Usuários | Sessões | Engaj. | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| (direct) / (none) | 46 | 48 | 16,7% | 83,3% | 0m 03s |
| facebook / cpc | 33 | 34 | 41,2% | 58,8% | 1m 25s |
| google / organic | 12 | 12 | 50,0% | 50,0% | 1m 53s |
| ig / paid | 3 | 4 | 50,0% | 50,0% | 1m 48s |
| linktree / social | 3 | 3 | 66,7% | 33,3% | 0m 06s |
| poki.com / referral | 3 | 3 | 0,0% | 100,0% | 0m 00s |
| bing / organic | 2 | 2 | 50,0% | 50,0% | 0m 54s |
| chatgpt.com / ai-assistant | 2 | 2 | 100,0% | 0,0% | 0m 30s |
| blog / artigo | 1 | 1 | 100,0% | 0,0% | 0m 15s |
| br.search.yahoo.com / referral | 1 | 1 | 100,0% | 0,0% | 0m 35s |
| rd-automacao / email | 1 | 1 | 100,0% | 0,0% | 3m 39s |

---

## 4. Top 10 landing pages (20/11)

| Landing page | Usuários | Sessões | Páginas | Engaj. | Rejeição |
|---|---:|---:|---:|---:|---:|
| /calculadora-roupa-de-cama-de-hotel | 35 | 36 | 37 | 41,7% | 58,3% |
| /como-melhorar-praticas-e-estrategias-para-tornar-a-gestao-do-seu-hotel-mais-eficiente-e-lucrativa | 6 | 7 | 8 | 14,3% | 85,7% |
| /checklist-para-quartos-pousada | 4 | 5 | 7 | 60,0% | 40,0% |
| /conheca-a-conamore-enxoval-profissional-para-hotelaria | 4 | 4 | 5 | 75,0% | 25,0% |
| / | 3 | 3 | 4 | 66,7% | 33,3% |
| /protetor-de-colchao-saiba-como-usar-e-como-escolher-o-melhor-para-o-seu-hotel | 3 | 3 | 3 | 0,0% | 100,0% |
| /como-arrumar-cama-hotel | 2 | 3 | 3 | 33,3% | 66,7% |
| /category/dicas-de-sustentabilidade-para-hoteis-e-pousadas | 2 | 2 | 2 | 0,0% | 100,0% |
| /qual-a-diferenca-entre-hotel-pousada-e-hostel | 2 | 2 | 2 | 0,0% | 100,0% |
| /travesseiros-tudo-que-voce-precisa-saber-e-como-escolher-o-melhor-para-o-seu-hotel | 2 | 2 | 2 | 100,0% | 0,0% |

---

## 5. Dispositivos (20/11)

| Dispositivo | Usuários | Sessões | Engaj. | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| mobile | 60 | 63 | 46,0% | 54,0% | 0m 58s |
| desktop | 48 | 49 | 22,4% | 77,6% | 0m 32s |
| tablet | 1 | 1 | 0,0% | 100,0% | 0m 00s |

---

## 6. Observações e alertas

- 🚨 **Queda de qualidade generalizada:** engajamento −12 p.p. e tempo médio de 2m33s → 47s, apesar do volume em alta. Motor da queda é o tráfego **direto** (46 usuários, engajamento 16,7%, tempo 3s) e o **desktop** (rejeição 77,6%, tempo 32s).
- 🤖 **Sinal de bot/spam:** `poki.com / referral` — 3 sessões, 0% engajamento, 0s de duração. Tráfego não humano. A `/calculadora-roupa-de-cama-de-hotel` (35 usuários, engaj. 41,7%) concentra tráfego de baixa intenção — investigar possível bot ou campanha segmentada.
- ⚠️ **Consent mode:** "(not set)" em newVsReturning com 3 sessões / 0 usuários — ruído esperado do consent mode, volume baixo.
- 📈 **Positivo:** facebook/cpc e google/organic entregam engajamento saudável (41,2% e 50,0%). chatgpt.com/ai-assistant aparece com engajamento 100% (2 usuários) — consistente com o monitoramento de visibilidade em IA.
- 🧭 **Recomendação:** validar com o time de mídia se o tráfego direto e o da calculadora refletem campanhas (ex.: UTM ausente) ou bot; se for bot, avaliar filtro de IP/referrer no GA4.
