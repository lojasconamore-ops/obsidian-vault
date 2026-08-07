# Ads — Conamore — Análise Completa de Canibalização (Tráfego Pago vs Orgânico)

**Data:** 07 de Agosto de 2026 (consolidado das análises de 04/08/2026)  
**Responsável:** Flávia — Gerente de Marketing  
**Fontes:** Google Ads (search_term_view + keyword_view) via Composio, Google Search Console  
**Customer ID:** 2335779078  
**Período:** Janeiro/2025 a Agosto/2026  
**Status:** ⛔ ANÚNCIO PREJUDICIAL — recomendar pausa imediata

---

## 1. Resumo Executivo

> **Veredicto: Em 2026, o anúncio pago no termo "conamore" está DANDO PREJUÍZO.** A canibalização do tráfego orgânico supera os cliques incrementais trazidos pelo anúncio. Em 2025 o cenário era favorável (CPC baixo, muito tráfego incremental), mas a reativação em junho/2026 mudou completamente a equação: CPC 3-5× maior, CTR 5-10× menor, e o tráfego total COM anúncio ficou ABAIXO do orgânico puro sem anúncio.

**Recomendação:** ⛔ **DESATIVAR** o anúncio de marca "conamore" imediatamente. Se quiser proteção de marca, usar budget mínimo (R$50-100/mês) com segmentação restrita (Search Network apenas, sem partners).

---

## 2. Contexto: O Experimento Natural

Em **julho/2025**, Sérgio removeu a palavra-chave "conamore" do Google Ads. Em **junho/2026**, a palavra foi reativada. Isso criou um experimento natural com 3 períodos distintos:

| Período | Anúncio | Duração | CTR Orgânico | Cliques Orgânicos/mês |
|---|---|---|---|---|
| mar–jun/2025 | 🔴 ATIVO | 4 meses | ~14–16% | ~2.022 |
| **jul/2025 – mai/2026** | 🟢 **REMOVIDO** | **11 meses** | **60–77%** | **~4.749** |
| jun–jul/2026 | 🔴 REATIVADO | 2 meses | 22–28% | ~1.160 |

**A posição orgânica sempre esteve entre 1,0 e 1,5.** A variação de CTR é inteiramente explicada pela presença/ausência do anúncio pago — um dos casos mais limpos de causa e efeito que já documentei.

---

## 3. Evidência do Search Console: O Efeito no CTR

### Termo principal: "conamore" (61.398 cliques no período)

| Mês | Cliques | Impr. | CTR | Pos |
|-----|---------|-------|------|-----|
| mar/25* | 836 | 6.148 | 13,60% | 1,07 |
| abr/25 | 3.777 | 23.637 | 15,98% | 1,08 |
| mai/25 | 2.265 | 14.871 | 15,23% | 1,24 |
| jun/25 | 1.209 | 8.869 | 13,63% | 1,32 |
| **jul/25** | **5.445** | 9.027 | **60,32%** | 1,28 |
| ago/25 | 5.027 | 6.842 | **73,47%** | 1,50 |
| set/25 | 4.119 | 5.478 | **75,19%** | 1,29 |
| out/25 | 4.489 | 5.997 | 74,85% | 1,38 |
| nov/25 | 5.447 | 7.317 | 74,44% | 1,35 |
| dez/25 | 4.020 | 5.503 | 73,05% | 1,40 |
| jan/26 | 6.039 | 7.822 | 77,21% | 1,36 |
| fev/26 | 4.443 | 5.732 | 77,51% | 1,45 |
| mar/26 | 4.729 | 6.552 | 72,18% | 1,26 |
| abr/26 | 3.735 | 5.728 | 65,21% | 1,26 |
| mai/26 | 3.450 | 5.642 | 61,15% | 1,24 |
| **jun/26** | **1.007** | 4.594 | **21,92%** | 1,16 |
| **jul/26** | **1.313** | 4.681 | **28,05%** | 1,03 |
| ago/26* | 48 | 111 | 43,24% | 1,00 |

> *Meses parciais: mar/25 a partir do dia 22; ago/26 apenas dia 01.

**Observação crucial:** as impressões caíram menos que os cliques. De ~5.600/mês para ~4.600/mês (queda de 18%), enquanto os cliques caíram de ~4.700 para ~1.160 (queda de 75%). Ou seja, o anúncio não reduziu a visibilidade — apenas disputou (e ganhou) o clique.

---

## 4. Evidência dos Typos: Padrão Replicado em 5 Variações

Além do termo exato "conamore", **4 variações de typo confirmam exatamente o mesmo padrão de canibalização:**

| Termo (#) | Total Cliques | CTR Total | Com Anúncio (CTR) | Sem Anúncio (CTR) | Efeito |
|---|---|---|---|---|---|
| **conamore** (#1) | 61.398 | 45,63% | 13–22% | 60–77% | Confirmado |
| **canamore** (#6) | 555 | 18,60% | ~10% | ~70% | Confirmado |
| **comamore** (#9) | 419 | 44,29% | ~15% | ~70% | Confirmado |
| **consmore** (#10) | 396 | 39,72% | ~15% | ~70% | Confirmado |
| **conamorr** (#18) | 275 | 40,20% | 9–12% | 39–77% | Confirmado |

**Total dos 5 termos:** ~63.043 cliques no período. Todos exibem o mesmo comportamento: CTR explode quando o anúncio sai (~10-15% → ~70%) e desaba quando volta (~70% → ~20%).

**Termo de controle:** "conamore hotelaria" (#2, 4.782 cliques) NÃO exibe esse padrão — seu CTR se manteve entre 6-17% independentemente do período, sugerindo que não estava sendo impactado pelo mesmo anúncio (ou o anúncio não aparecia para essa query composta).

---

## 5. Dados do Google Ads: A Verdade Financeira

### Tabela comparativa: Orgânico vs Pago (search term "conamore")

| Mês | Status | Orgânico (GSC) | Pago (Ads) | Total | Custo (BRL) | CPC | CTR Pago |
|---|---|---|---|---|---|---|---|
| 2025-01 | 🔴 COM | 0 | 10.398 | 10.398 | R$5.392,20 | R$0,52 | 69,4% |
| 2025-02 | 🔴 COM | 0 | 5.732 | 5.732 | R$2.510,21 | R$0,44 | 53,2% |
| 2025-03 | 🔴 COM | 836 | 9.797 | 10.633 | R$1.079,99 | R$0,11 | 46,9% |
| 2025-04 | 🔴 COM | 3.777 | 17.036 | 20.813 | R$1.292,74 | R$0,08 | 50,0% |
| 2025-05 | 🔴 COM | 2.265 | 10.923 | 13.188 | R$1.192,97 | R$0,11 | 38,8% |
| 2025-06 | 🔴 COM | 1.209 | 5.829 | 7.038 | R$1.028,18 | R$0,18 | 37,2% |
| 2025-07 | 🟡 RESIDUAL | 5.445 | 443 | 5.888 | R$54,06 | R$0,12 | 49,6% |
| 2025-08 a 2026-04 | 🟢 SEM | **~4.749/mês** | 0 | ~4.749/mês | R$0,00 | — | — |
| 2026-05 | 🟡 RESIDUAL | 3.450 | 428 | 3.878 | R$123,54 | R$0,29 | 12,0% |
| 2026-06 | 🔴 COM 2.0 | 1.007 | 3.355 | 4.362 | R$1.235,57 | R$0,37 | 10,0% |
| 2026-07 | 🔴 COM 2.0 | 1.313 | 3.180 | 4.493 | R$1.312,11 | R$0,41 | 6,2% |
| 2026-08 | 🟡 RESIDUAL | 48 | 54 | 102 | R$15,83 | R$0,29 | 6,1% |

---

## 6. Métricas Agregadas por Período

### Período 1: COM anúncio (mar-jun/2025)
| Métrica | Valor |
|---|---|
| Cliques pagos | 43.585 |
| Cliques orgânicos | 8.087 |
| **Total** | **51.672** |
| Custo total | R$4.593,88 |
| CPC médio | R$0,11 |
| Orgânico médio/mês | 2.022 |

### Período 2: SEM anúncio (jul/2025-abr/2026, 10 meses)
| Métrica | Valor |
|---|---|
| Cliques pagos residuais | 443 |
| Cliques orgânicos | 47.493 |
| **Orgânico médio/mês** | **4.749** |
| Custo | R$0,00 |

### Período 3: COM anúncio reativado (jun-jul/2026)
| Métrica | Valor |
|---|---|
| Cliques pagos | 6.535 |
| Cliques orgânicos | 2.320 |
| **Total** | **8.855** |
| Custo total | R$2.547,68 |
| CPC médio | R$0,39 |
| Orgânico médio/mês | 1.160 |

---

## 7. Cálculo de Canibalização

> **Baseline:** 4.749 cliques orgânicos/mês (média dos 10 meses sem anúncio: jul/2025–abr/2026)

### 🟡 2025 (mar-jun, 4 meses)

| Indicador | Valor |
|---|---|
| Orgânico esperado (sem anúncio) | 18.997 |
| Orgânico real (com anúncio) | 8.087 |
| **Canibalizados** | **10.910** (25,0% dos pagos) |
| **Incrementais reais** | **+32.675** |
| CPC incremental | **R$0,14** |
| Custo total | R$4.593,88 |

### 🔴 2026 (jun-jul, 2 meses)

| Indicador | Valor |
|---|---|
| Orgânico esperado (sem anúncio) | 9.499 |
| Orgânico real (com anúncio) | 2.320 |
| **Canibalizados** | **7.179** (109,8% dos pagos) |
| **Incrementais reais** | **−644** ⚠️ |
| CPC incremental | ∞ (negativo — cada "clique extra" custa infinito pois não há incrementais) |
| Custo total | R$2.547,68 |

---

## 8. O Dado Mais Chocante

```
Tráfego MÉDIO MENSAL no termo "conamore":

 SEM anúncio (orgânico puro):  4.749 cliques/mês  ← GRÁTIS
 COM anúncio 2026 (pago+org):  4.428 cliques/mês  ← PAGANDO R$1.274/mês

 Resultado: pior que não fazer nada.
```

**Em 2026, o tráfego total COM anúncio (4.428) ficou ABAIXO do tráfego orgânico puro sem anúncio (4.749).** O anúncio está ativamente PIORANDO o resultado.

---

## 9. Diagnóstico: O Que Mudou de 2025 para 2026?

| Métrica | 2025 (mar-jun) | 2026 (jun-jul) | Variação |
|---|---|---|---|
| CTR do anúncio | 37–69% | 6–10% | ↓ 5–10× |
| CPC médio | R$0,08–0,18 | R$0,37–0,41 | ↑ 3–5× |
| Canibalização | 25% dos pagos | 110% dos pagos | ↑ 4,4× |
| Incrementais/mês | +8.169 | −322 | Inverteu sinal |
| Custo/mês | ~R$1.148 | ~R$1.274 | ↑ 11% |

**Causas prováveis da piora em 2026:**
1. **Mudança no algoritmo de leilão do Google** — CPCs de marca subiram globalmente
2. **Concorrência no leilão de marca** — alguém pode estar dando bid em "conamore"
3. **Qualidade do anúncio caiu** — CTR de 6% é muito baixo para termo de marca (esperado >30%)
4. **Search partners ou Display Network** podem estar inflando impressões sem conversão (CTR 6% sugere tráfego de baixa qualidade)
5. **Mudança na campanha** — a reativação em 2026 pode ter usado configurações diferentes (bidding, segmentação)

---

## 10. Keywords Associadas (keyword_view)

Todas as keywords contendo "conamore" no período jan/2025–ago/2026:

| Keyword | Cliques | Custo (BRL) | Match Type |
|---|---|---|---|
| **conamore** | 91.970 | R$58.437,88 | BROAD |
| **conamore hotelaria** | 14.097 | R$8.776,96 | BROAD |
| conamore casa | 807 | R$575,05 | BROAD |
| cupom conamore | 296 | R$2.611,15 | BROAD |
| conamore toalhas | 149 | R$194,73 | BROAD |

> ⚠️ As variações "conamore hotelaria" e "conamore casa" têm lógicas de canibalização diferentes (CTR orgânico não foi afetado pela remoção do anúncio). Recomenda-se análise separada.

---

## 11. Conclusão e Recomendações

### 2025: ✅ Valeu a pena
- CPC irrisório (R$0,08–0,18), muito volume incremental (32.675 cliques em 4 meses)
- Custo total de apenas R$4.593,88 para 43.585 cliques pagos
- Canibalização de 25% era aceitável dado o CPC baixíssimo
- Tráfego total COM anúncio (12.918/mês) era 2,7× maior que sem (4.749/mês)

### 2026: ⛔ Prejuízo
- O anúncio canibaliza mais tráfego do que traz (109,8% de canibalização)
- Tráfego total COM anúncio (4.428/mês) é MENOR que orgânico sem anúncio (4.749/mês)
- Gasta-se R$1.274/mês para PIORAR o resultado em 322 cliques/mês
- CPC 3–5× maior que em 2025, CTR 5–10× menor

### Recomendações

1. **⛔ Pausar imediatamente** o anúncio de marca "conamore" em todas as campanhas
2. **🔍 Investigar** por que o CTR caiu tanto — verificar search partners, configurações de segmentação, e qualidade do anúncio
3. **📊 Reavaliar em 30 dias** — se o orgânico voltar ao patamar de ~4.700/mês, confirma-se que o anúncio era prejudicial
4. **🛡️ Proteção de marca (se desejado):** anúncio com budget mínimo (R$50/mês), segmentação restrita (Google Search apenas, sem partners) — mas o cenário atual não justifica
5. **📈 Redirecionar verba:** ~R$1.274/mês para campanhas de termos genéricos (não-marca) com tráfego verdadeiramente incremental
6. **🧪 Analisar separadamente:** "conamore hotelaria" e "conamore casa" — que não exibiram o mesmo padrão de canibalização e podem ter justificativa diferente

---

## 12. Metodologia

- **Fonte paga:** Google Ads API via Composio (`GOOGLEADS_SEARCH_STREAM_GAQL`), customer_id 2335779078
- **Fonte orgânica:** Google Search Console, propriedade `sc-domain:conamore.com.br`
- **Query GAQL (search_term_view):** filtro exato `search_term = 'conamore'`, período 2025-01-01 a 2026-08-01
- **Query GAQL (keyword_view):** filtro `LIKE '%conamore%'`, mesmo período
- **Query GSC:** top 10 queries + dados diários por query, dimensão `date`, filtro exato por query
- **Cálculo de canibalização:** baseline = média de cliques orgânicos nos 10 meses sem anúncio (jul/2025–abr/2026). Canibalizados = orgânico esperado − orgânico real. Incrementais = cliques pagos − canibalizados.
- **Custo:** cost_micros / 1.000.000 = BRL
- **CPC:** custo ÷ cliques pagos

---

## 13. Arquivos Relacionados no Obsidian

- `Agentes/Flávia/SEO - Conamore - Canibalização Paga vs Orgânica - 04 Ago 2026.md` — Descoberta inicial do efeito
- `Agentes/Flávia/Ads - Conamore - Análise Canibalização - 04 Ago 2026.md` — Análise completa com Google Ads (versão anterior)
- `Agentes/Flávia/Ads - Conamore - Análise Completa de Canibalização - 07 Ago 2026.md` — **Este documento (versão consolidada final)**

---

*Análise consolidada por Flávia (Marketing) em 07/08/2026, baseada nos dados extraídos em 04/08/2026.*
