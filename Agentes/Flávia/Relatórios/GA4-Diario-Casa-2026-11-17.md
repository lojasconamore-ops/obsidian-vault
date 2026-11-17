# 📊 Resumo Diário de Tráfego GA4 — Loja Casa

**Conamore Casa** (lojas.conamore.com.br) · Property `394358599` (G-5709GFVVBK)
**Gerado em:** terça-feira, 17/11/2026 · **Dados:** 14/11 (D-3) vs 13/11 (D-4) · Fuso America/Sao_Paulo

---

## Resumo executivo

- Sábado 14/11 em forte recuperação vs sexta 13/11: usuários ativos **+28,3%** (163 vs 127) e sessões **+23,1%** (181 vs 147) — comportamento típico de varejo (sábado mais forte que sexta).
- Qualidade de tráfego em alta: engajamento **81,8%** (+1,5 p.p.), rejeição **18,2%** (−1,5 p.p.) e tempo médio **4m30s** (+21s).
- 🚨 **E-commerce zerado pelo 2º dia consecutivo** (0 transações / R$0 em 13/11 e 14/11) — reforça suspeita de falha no webhook `compra_erp`, não queda de demanda.
- Tráfego **pago domina** (google/cpc + ig/paid + instagram/paid + facebook/cpc = 94 usuários, ~58%) e **mobile concentra 84,7%** do público.
- Ruído de consent mode baixo (1 sessão em newVsReturning + 4 landing `(not set)`); Instagram aparece **fragmentado** (ig/paid 26 + instagram/paid 7).

---

## 1. Comparativo geral — 14/11 (D-3) vs 13/11 (D-4)

| Métrica | 13/11 (D-4) | 14/11 (D-3) | Δ |
|---|---:|---:|---:|
| Usuários ativos | 127 | **163** | +28,3% |
| Sessões | 147 | **181** | +23,1% |
| Usuários novos | 95 | **130** | +36,8% |
| Visualizações de página | 1.033 | **1.406** | +36,1% |
| Taxa de engajamento | 80,3% | **81,8%** | +1,5 p.p. |
| Taxa de rejeição | 19,7% | **18,2%** | −1,5 p.p. |
| Tempo médio de sessão | 4m09s | **4m30s** | +21s |
| Eventos | 2.332 | **3.032** | +30,0% |
| Transações | 0 | **0** | — |
| Receita de compras | R$ 0,00 | **R$ 0,00** | — |

> 🚨 **E-commerce (Magento) zerado em 14/11** — segundo dia seguido sem transações/receita (13/11 também zerado). Ver item 6.

---

## 2. Novos vs Recorrentes — 14/11 (D-3)

| Segmento | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| **Novos** | 134 | 134 | 85,8% | 14,2% | 3m49s |
| **Recorrentes** | 39 | 46 | 71,7% | 28,3% | 6m35s |
| **(not set)** ⚠️ | 0 | 1 | 0% | 100% | 5s |

> `(not set)` com apenas 1 sessão (0,6% do total), 0 usuários, 100% rejeição — assinatura de **consent mode**, volume irrelevante. Nota: soma de novos (134) + recorrentes (39) = 173 > 163 usuários ativos; usuários que mudam de classificação dentro do dia são contados em ambos — sem impacto na leitura.

---

## 3. Canais — origem/mídia (14/11, top 15)

| Origem / Mídia | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| google / cpc | 56 | 63 | 66,7% | 33,3% |
| (direct) / (none) | 37 | 40 | 97,5% | 2,5% |
| ig / paid | 26 | 26 | 84,6% | 15,4% |
| google / organic | 18 | 21 | 90,5% | 9,5% |
| linktr.ee / referral | 11 | 11 | 100% | 0% |
| instagram / paid | 7 | 7 | 100% | 0% |
| facebook / cpc | 5 | 5 | 60,0% | 40,0% |
| chatgpt.com / ai-assistant | 3 | 4 | 50,0% | 50,0% |
| (data not available) | 1 | 1 | 100% | 0% |
| googlesyndication (safeframe) / referral | 1 | 3 | 66,7% | 33,3% |

> 10 origens/mídias no total. Pago (cpc/paid) soma **94 usuários (~57,7%)** — dominância de mídia paga no dia. Instagram fragmentado: `ig/paid` (26) + `instagram/paid` (7) = **33 usuários** se unificados.

---

## 4. Páginas — top 10 landing pages (14/11)

| Landing page | Sessões | Usuários | Pageviews | Engajamento | Rejeição |
|---|---:|---:|---:|---:|---:|
| `/` | 60 | 55 | 530 | 93,3% | 6,7% |
| `/lencois/linha-de-produto/avulsos.html` | 25 | 25 | 256 | 84,0% | 16,0% |
| `/lencol-casal-c-elast-140x190x30cm-percal-180-fios-...` | 8 | 8 | 51 | 100% | 0% |
| `/colcha-piquet-leve-queen-240-x-240cm-azul-1` | 6 | 6 | 25 | 50,0% | 50,0% |
| `/promocoes-lojas` | 6 | 6 | 17 | 83,3% | 16,7% |
| `(not set)` ⚠️ | 4 | 4 | 0 | 25,0% | 75,0% |
| `/toalha-de-maquiagem-makeup-preta-para-hotelaria-conamore` | 4 | 3 | 4 | 50,0% | 50,0% |
| `/colcha-king-piquet-felicita-2-80-x-2-40-floral-blue` | 3 | 3 | 15 | 100% | 0% |
| `/edredom-queen-2-50x2-60` | 3 | 3 | 3 | 0% | 100% |
| `/lencol-super-king-sem-elast-280x300cm-percal-180-fios-...` | 3 | 2 | 3 | 66,7% | 33,3% |

> Landing `(not set)` com 4 sessões, 0 pageviews e 75% rejeição — mesmo ruído de consent mode (em queda: 6 sessões em 13/11 → 4 em 14/11). 63 landing pages distintas no total. `/lencois/linha-de-produto/avulsos.html` disparou para #2 (25 sessões, 256 pageviews) — provável empurrão de campanha.

---

## 5. Dispositivos (14/11)

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| **Mobile** | 138 | 148 | 83,1% | 16,9% |
| **Desktop** | 23 | 31 | 74,2% | 25,8% |
| **Tablet** | 2 | 2 | 100% | 0% |

> Mobile concentra **84,7% dos usuários ativos** (138 de 163).

---

## 6. Observações

- **🚨 E-commerce zerado por 2 dias seguidos (13/11 e 14/11)** — o relatório de 16/11 já havia sinalizado 13/11 como o primeiro zero após 7 dias com vendas (faixa de 1 a 4 transações/dia). Dois zeros consecutivos reforçam fortemente a hipótese de **falha no webhook `compra_erp`** (GA4+Ads+CAPI+LinkedIn) ou instabilidade no Magento, em vez de queda orgânica de demanda. Recomendo escalar Matias (TI) para validar o pipeline de compras com urgência.
- **Sábado 14/11 saudável em volume e qualidade** — recuperação de +28,3% em usuários e +30% em eventos sobre a sexta 13/11, com engajamento subindo para 81,8%. Padrão esperado de varejo (sábado > sexta).
- **`/lencois/linha-de-produto/avulsos.html` em disparada** — saltou para a 2ª landing page (25 sessões, 256 pageviews, 84% engajamento). Investigar se há campanha ativa apontando para essa categoria ou se é tráfego orgânico novo; 256 pageviews em 25 sessões sugere navegação profunda de catálogo.
- **Instagram fragmentado** — `ig/paid` (26 usuários) e `instagram/paid` (7 usuários) são o mesmo canal com UTMs inconsistentes. Unificar a nomenclatura de mídia nas campanhas para consolidar a leitura (33 usuários no total).
- **Google/cpc com rejeição acima da média** — 33,3% vs média geral de 18,2%, e engajamento de 66,7% (abaixo dos 81,8% gerais). Monitorar qualidade do tráfego pago de busca, embora siga sendo o maior canal em volume (56 usuários).
- **Direto excepcionalmente qualificado** — 97,5% de engajamento e 2,5% de rejeição (37 usuários), o melhor patamar recente; comportamento de usuários retornantes com intenção de compra.
- **Consent mode sob controle** — `(not set)` em queda (newVsReturning: 1 sessão; landing: 4 sessões), sem impacto material nos totais. Tema segue sob acompanhamento com Matias/Adrian.
