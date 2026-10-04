# 📊 Resumo Diário de Tráfego GA4 — Loja Casa

**Conamore Casa** · `lojas.conamore.com.br` · Property `394358599`  
**Gerado em:** domingo, 04/10/2026 (BRT)  
**Dados consolidados:** 01/10/2026 (D-3) vs 30/09/2026 (D-4)

## Resumo executivo

- O tráfego avançou em 01/10: **128 usuários ativos (+8,5%)** e **153 sessões (+15,0%)**.
- A qualidade também melhorou: **76,5% de engajamento (+2,8 p.p.)**, rejeição de **23,5% (-2,8 p.p.)** e duração média de **7m 22s (+56,4%)**.
- O consumo cresceu acima do tráfego: **1.011 visualizações (+32,5%)** e **2.231 eventos (+26,9%)**.
- O e-commerce registrou **5 transações e R$ 3.207,04 em receita**; em 30/09 ambos estavam zerados, com ticket médio indicado de **R$ 641,41**.
- Alerta de mensuração: a landing page **`(not set)` concentrou 12 usuários (9,4%)**, 91,7% de rejeição e tempo praticamente zero, assinatura típica de ruído de Consent Mode.

---

## 1. Comparativo geral

**Dados: 01/10/2026 vs 30/09/2026.**

| Indicador | 30/09 (D-4) | 01/10 (D-3) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 118 | **128** | **+8,5%** |
| Sessões | 133 | **153** | **+15,0%** |
| Novos usuários | 95 | **91** | **-4,2%** |
| Visualizações de página/tela | 763 | **1.011** | **+32,5%** |
| Taxa de engajamento | 73,7% | **76,5%** | **+2,8 p.p.** |
| Taxa de rejeição | 26,3% | **23,5%** | **-2,8 p.p.** |
| Duração média da sessão | 4m 43s | **7m 22s** | **+56,4%** |
| Eventos | 1.758 | **2.231** | **+26,9%** |
| Transações | 0 | **5** | Base anterior zerada |
| Receita de compras | R$ 0,00 | **R$ 3.207,04** | Base anterior zerada |

> **E-commerce:** as métricas não vieram zeradas em 01/10. O salto deve ser interpretado com cautela porque a base de 30/09 foi zero; recomenda-se acompanhar a consistência do evento `purchase` nos próximos dias consolidados.

---

## 2. Novos vs Recorrentes

**Data: 01/10/2026 (D-3).**

| Perfil | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| New | 100 | 100 | **84,0%** | 16,0% | 7m 38s |
| Returning | 37 | 53 | 62,3% | **37,7%** | 6m 51s |

- Não houve linha **`(not set)`** na dimensão `newVsReturning` neste dia.
- Usuários ativos por perfil não devem ser somados para reconciliar o total geral, pois a métrica de usuários não é aditiva entre dimensões.
- Novos usuários exibiram qualidade superior aos recorrentes: maior engajamento e rejeição 21,7 p.p. menor.

---

## 3. Canais — origem/mídia

**Data: 01/10/2026 (D-3) · ordenado por usuários ativos.** A API retornou 12 origens/mídias no total.

| # | Origem / mídia | Usuários | Sessões | Engajamento | Rejeição | Tempo médio |
|---:|---|---:|---:|---:|---:|---:|
| 1 | google / cpc | **42** | 44 | 68,2% | 31,8% | 5m 58s |
| 2 | (direct) / (none) | **36** | 49 | 77,6% | 22,4% | 8m 29s |
| 3 | google / organic | **19** | 20 | 75,0% | 25,0% | 7m 17s |
| 4 | rd-email / email | **15** | 17 | 82,4% | 17,6% | 7m 07s |
| 5 | instagram / paid | **4** | 6 | 83,3% | 16,7% | 4m 48s |
| 6 | app.octadesk.com / referral | **3** | 8 | 75,0% | 25,0% | 15m 48s |
| 7 | linktr.ee / referral | **3** | 3 | 100,0% | 0,0% | 1m 33s |
| 8 | chatgpt.com / ai-assistant | **2** | 2 | 100,0% | 0,0% | 8m 42s |
| 9 | (data not available) | **1** | 1 | 100,0% | 0,0% | 3m 38s |
| 10 | duckduckgo / organic | **1** | 1 | 100,0% | 0,0% | 0m 48s |
| 11 | ig / social | **1** | 1 | 100,0% | 0,0% | 0m 13s |
| 12 | k6li72b606.preview-beefreecontent.com / referral | **1** | 1 | 100,0% | 0,0% | 0m 10s |

**Leituras:**
- `google / cpc` liderou em usuários, com 42 (**32,8% do total geral**), mas teve qualidade inferior a direto, orgânico e e-mail.
- Direto liderou em sessões, com 49 (**32,0% do total**), e apresentou duração média forte de 8m 29s.
- `rd-email / email` trouxe 15 usuários com **82,4% de engajamento**, desempenho qualitativo positivo.
- `app.octadesk.com / referral` deve ser tratado como possível autorreferência/retorno operacional; foram 8 sessões e tempo elevado.

---

## 4. Top 10 landing pages

**Data: 01/10/2026 (D-3) · ordenado por usuários ativos.**

| # | Landing page | Usuários | Sessões | Engajamento | Rejeição | Tempo médio |
|---:|---|---:|---:|---:|---:|---:|
| 1 | `/` | **41** | 46 | **95,7%** | 4,3% | 10m 46s |
| 2 | `/promocoes-lojas` | **19** | 19 | **89,5%** | 10,5% | 6m 41s |
| 3 | `(not set)` | **12** | 12 | **8,3%** | **91,7%** | 0m 00s |
| 4 | `/lencol-casal-sem-elast-220-x-250cm-percal-180-fios-50-algod-o-e-50-poliester` | **8** | 8 | 37,5% | 62,5% | 0m 58s |
| 5 | `/lencol-casal-c-elast-140x190x30cm-percal-180-fios-50-algod-o-e-50-poliester` | **7** | 7 | 85,7% | 14,3% | 4m 16s |
| 6 | `/destaques-lojas` | **6** | 6 | 66,7% | 33,3% | 3m 39s |
| 7 | `/lencol-super-king-sem-elast-280x300cm-percal-180-fios-50-algod-o-e-50-poliester` | **6** | 6 | 83,3% | 16,7% | 7m 39s |
| 8 | `/lencol-queen-c-elast-160x200x25cm-percal-180-fios-50-algod-o-e-50-poliester` | **5** | 5 | 80,0% | 20,0% | 11m 15s |
| 9 | `/amenities-para-hotel-500-sabonetes-10g-capim-limao-conamore` | **2** | 2 | 50,0% | 50,0% | 14m 43s |
| 10 | `/fronha-branca-3-abas-180-fios-hotelaria` | **2** | 2 | 50,0% | 50,0% | 5m 51s |

> **Alerta Consent Mode:** `(not set)` representa 12 usuários, equivalentes a **9,4% do total geral**, com 91,7% de rejeição e duração média de aproximadamente 0 segundo. É a assinatura de tráfego sem atribuição adequada de landing page e deve permanecer sob monitoramento.

---

## 5. Dispositivos

**Data: 01/10/2026 (D-3).**

| Dispositivo | Usuários | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| Mobile | **83** | 88 | 75,0% | 25,0% | 4m 20s |
| Desktop | **44** | 64 | **78,1%** | **21,9%** | **11m 38s** |
| Tablet | **1** | 1 | 100,0% | 0,0% | 0m 33s |

- Mobile concentrou **64,8% dos usuários** e 57,5% das sessões.
- Desktop teve apenas 34,4% dos usuários, mas 41,8% das sessões e duração média **2,7 vezes maior** que mobile, sugerindo navegação mais profunda.
- Tablet teve volume insuficiente para conclusão.

---

## 6. Observações e alertas

1. **Crescimento consistente de volume e profundidade:** sessões, pageviews, eventos, engajamento e duração avançaram juntos em 01/10.
2. **E-commerce voltou a registrar receita:** 5 transações e R$ 3.207,04 após um dia zerado. Monitorar se o registro se mantém nos próximos dados consolidados para diferenciar retomada comercial de oscilação de tracking.
3. **Ruído relevante em landing page:** `(not set)` atingiu 9,4% dos usuários, com comportamento extremo de baixa qualidade; provável efeito de Consent Mode/atribuição.
4. **Recorrentes merecem atenção:** rejeição de 37,7%, contra 16,0% nos novos, apesar de tempo médio ainda alto.
5. **Possível autorreferência:** `app.octadesk.com / referral` gerou 8 sessões; avaliar exclusão de referência/fluxo entre domínios se esse tráfego não representar aquisição real.
6. **CPC lidera volume, não qualidade:** Google Ads respondeu pelo maior número de usuários, porém ficou abaixo de direto, orgânico e RD e-mail em engajamento.

---

## Status

**Executado:** relatório diário GA4 da Loja Casa gerado com dados consolidados de D-3 e D-4.  
**Evidência:** 5 consultas `GOOGLE_ANALYTICS_RUN_REPORT` concluídas com sucesso; timezone retornado pela API: `America/Sao_Paulo`; moeda: `BRL`.  
**Status:** **Concluído**.
