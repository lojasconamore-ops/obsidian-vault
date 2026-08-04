---
title: "Teste de Consentimento GA4 — 02/08/2026"
date: 2026-08-04
tags: [ga4, consent-mode, diagnostico, tracking, hotelaria]
property: "properties/379729087"
---

# 🧪 Teste de Consentimento GA4 — Consolidação 02/08/2026

**Data do teste:** 04/08/2026 20:05 BRT
**Dado analisado:** 02/08/2026 (D-2, já consolidado)
**Property:** 379729087 (Hotelaria — conamore.com.br)
**Contexto:** Banner LGPD Increazy com `analytics_storage='denied'` histórico quebrando tracking (bounce 98-100%)

---

## 📊 Métricas Principais — 02/08/2026

| Métrica | Valor |
|---|---|
| Usuários ativos | 1.102 |
| Sessões | 1.327 |
| Sessões engajadas | 804 |
| Taxa de rejeição | **39,41%** |
| Duração média da sessão | 3m 17s |
| Taxa de engajamento | **60,59%** |

---

## 🔍 Diagnóstico por Origem (Top 10)

| Origem/Mídia | Sessões | Engajadas | Rejeição | Duração Média |
|---|---:|---:|---:|---|
| google / cpc | 717 | 469 | 34,59% | 3m 51s |
| (direct) / (none) | 163 | 79 | 51,53% | 2m 36s |
| google / organic | 145 | 102 | 29,66% | 3m 26s |
| instagram / paid | 93 | 57 | 38,71% | 1m 15s |
| google / dgen | 34 | 19 | 44,12% | 1m 38s |
| linkedin / paid | 30 | 4 | 86,67% | 0m 31s |
| (not set) | 28 | 9 | 67,86% | 1m 52s |
| facebook / cpc | 20 | 11 | 45,00% | 1m 21s |
| linktree / social | 13 | 8 | 38,46% | 2m 54s |
| bing / cpc | 12 | 4 | 66,67% | 2m 58s |

---

## 🚦 Status: **RESOLVIDO** ✅

### Critérios de avaliação:

| Critério | Limite | Real | Status |
|---|---|---|---|
| bounceRate < 50% | < 50% | **39,41%** | ✅ |
| engagedSessions > 30% das sessions | > 30% | **60,59%** | ✅ |

### Evidências:
- Nenhum canal principal apresenta bounce > 90% (o pior é linkedin/paid com 86,67% mas apenas 30 sessões)
- Canais de maior volume (google/cpc, direct, google/organic) todos com bounce entre 29-52%
- Média de sessão de 3m17s é compatível com tráfego real e engajado
- Dados confirmam que o consent mode está funcionando corretamente após aceite do banner LGPD

### Comparação histórica:
| Período | Bounce | Engajamento | Status |
|---|---|---|---|
| 01-02/08 (auge do problema) | 98,1% | 1,9% | ❌ Quebrado |
| **02/08 (atual)** | **39,41%** | **60,59%** | ✅ Resolvido |

---

## 📝 Notas
- Teste executado como rotina de monitoramento contínuo do consent mode
- Próximo teste agendado automaticamente para D-2 da data de execução
- Dados de (not set) com 67,86% de bounce merecem atenção, mas volume é baixo (28 sessões)
