# Relatório Diário de Marketing — 03/06/2026

**Gerente:** Flávia
**Período analisado:** 27/05/2026 a 02/06/2026 (7 dias completos) + 03/06 parcial
**Fonte principal:** Google Analytics 4 via Composio (RD Station MCP offline — 2º dia consecutivo)

---

## ⚠️ ALERTA — RD Station MCP Indisponível (2º dia)

**Problema mantido.** O servidor MCP do RD Station segue com:
- **401 Unauthorized** no endpoint de funil (token OAuth expirado)
- **MCP server unreachable** nos demais endpoints (assets, campanhas, workflows, segmentações)

**Impacto:** Sem dados de leads, conversões de funil, performance de email marketing e automações.

**Ação necessária (requer browser):** https://mcp.rdstationmentor.com/marketing → reconectar → atualizar config.yaml → `/reload-mcp`.

---

## CONAMORE Hotelaria OFICIAL — Visão Geral (GA4)

### Tráfego Diário

| Data | Usuários | Sessões | Pageviews | Tx Engajamento | Tx Rejeição |
|------|----------|---------|-----------|---------------|-------------|
| 27/05 (Qua) | 1.286 | 1.673 | 6.522 | 53,2% | 46,8% |
| 28/05 (Qui) | **1.508** 🏆 | **1.939** | **7.084** | **54,2%** | 45,8% |
| 29/05 (Sex) | 1.246 | 1.608 | 5.769 | 53,9% | 46,1% |
| 30/05 (Sáb) | 1.217 | 1.500 | 4.800 | 50,0% | 50,0% |
| 31/05 (Dom) | 1.255 | 1.557 | 6.838 | 51,6% | 48,4% |
| 01/06 (Seg) | 1.462 | 1.891 | 7.011 | 52,1% | 47,9% |
| 02/06 (Ter) | 1.343 | 1.770 | 6.671 | **2,6% 🔴** | **97,4%** |
| 03/06 (Qua)* | 72 | 92 | 368 | — | — |

*\*Dados parciais do dia atual*

**Totais 7 dias (27/05–02/06):** **10.317 usuários** | **11.938 sessões** | **44.695 pageviews**
**Média diária:** 1.474 usuários/dia | 1.705 sessões/dia

> 🔴 **Anomalia persiste:** 02/06 repetiu o padrão anômalo de 01/06 — engajamento em **2,6%** contra ~52% dos dias normais. Dois dias consecutivos com o mesmo comportamento: dados normais de sessões e pageviews, mas engagement rate zerado. **Problema de tracking, não de tráfego real.** Provável: falha no disparo do evento `session_engaged` ou alteração no gtag/GA4.

---

### Performance por Canal (Hotelaria)

| Canal | Usuários | Sessões | Pageviews | % Tráfego |
|-------|----------|---------|-----------|-----------|
| **Cross-network** | 2.169 | 2.656 | 9.281 | 19,5% |
| **Direct** | 1.567 | 2.065 | 5.559 | 14,1% |
| **Paid Search** | 1.322 | 1.994 | 10.648 | 11,9% |
| **Organic Search** | 1.241 | 1.712 | 6.686 | 11,2% |
| **Unassigned** ⚠️ | 1.080 | 1.357 | 3.778 | 9,7% |
| **Display** | 841 | 893 | 1.220 | 7,6% |
| **Paid Social** | 696 | 979 | 2.462 | 6,3% |
| **Email (RD Station)** | 340 | 466 | 1.686 | 3,1% |
| **Organic Social** | 222 | 249 | 1.234 | 2,0% |
| **Paid Shopping** | 207 | 226 | 881 | 1,9% |
| **Referral** | 103 | 202 | 802 | 0,9% |
| **Demais** | 95 | 170 | 826 | 0,9% |

---

### Top Campanhas Pagas

| Campanha | Usuários | Sessões | Novos |
|----------|---------|---------|-------|
| 🥇 **pmax_hotelaria_geral** | 939 | 1.221 | 730 |
| 🥈 **pmax_hotelaria_aquisicao** | 594 | 719 | 492 |
| 🥉 **display_communitas_google_hotelaria_cpc** | 451 | 464 | 453 |
| search_communitas_google_institucional_hotelaria_cpa_ampla | 424 | 487 | 321 |
| search_communitas_google_geral_cpa_hotelaria | 355 | 415 | 323 |
| display_communitas_google_hotelaria_cpc | 451 | 464 | 453 |
| dgen_communitas_google_hotelaria_purchase | 251 | 276 | 219 |
| dgen_hotelaria_airbnb | 212 | 244 | 202 |
| Meta \| Vendas \| Lojas Conamore | 186 | 252 | 121 |
| shopping_hotelaria | 140 | 142 | 129 |

**Email Marketing:**
- Boletim Maio (2805_-_boletim_maio): 278 usuários | 364 sessões
- RD Station / email: 263 usuários (source/medium) | 323 sessões

---

### Landing Pages (Top 10)

| Página | Usuários | Sessões | Tx Rejeição |
|--------|---------|---------|-------------|
| / (Home) | 2.795 | 3.518 | 41,0% ✅ |
| (empty) | 763 | 1.022 | **99,9%** 🔴 |
| /amenities-para-hotelaria | 551 | 568 | 60,2% |
| /lencol-para-hotelaria | 542 | 640 | 64,1% |
| /lencol-para-hotelaria.html | 373 | 439 | 51,7% |
| /toalhas-para-hoteis-pousadas | 347 | 393 | 54,2% |
| /enxoval-para-airbnb | 279 | 308 | 68,8% |
| /cobertor-hotelaria/linha-de-produto/microfibra | 229 | 246 | 76,4% |
| (not set) | 227 | 314 | 95,2% 🔴 |
| /enchimento-p-edredom-casal-2-20-x-2-50m | 166 | 179 | 49,2% |

---

### Top Source/Medium

| Fonte | Usuários | Sessões |
|-------|---------|---------|
| 🥇 **google / cpc** | 4.020 | 5.259 |
| 🥈 **(direct) / (none)** | 1.567 | 2.065 |
| 🥉 **google / organic** | 1.160 | 1.608 |
| (not set) | 1.034 | 1.302 |
| instagram / paid | 626 | 907 |
| RD Station / email | 263 | 323 |

---

## Alertas e Oportunidades

### 🔴 Crítico
1. **RD Station MCP offline — 2º dia consecutivo.** Sem acesso a leads, conversões e automações. Impacto direto na operação de marketing.
2. **Anomalia de tracking persiste (01 e 02/06).** Dois dias com engagement rate <3%. Dados de usuários e sessões parecem normais, mas o tracking de engajamento quebrou. **Prioridade: verificar gtag/GA4 no site.**

### 🟡 Atenção
3. **`(empty)` landing page com 763 usuários e 99,9% rejeição** — 1.022 sessões caindo em página sem URL definida. Pode ser erro de implementação, redirect quebrado ou pixel disparando sem conteúdo.
4. **`(not set)` como fonte com 1.034 usuários** — tráfego sem identificação de origem.
5. **Unassigned com 9,7% do tráfego** (1.080 usuários) — UTMs não categorizadas.

### 🟢 Oportunidades
6. **Peak day: quinta-feira (28/05)** — 1.508 usuários. Confirmando padrão: quinta é o melhor dia. Disparos estratégicos para quinta.
7. **Paid Search dominante** — google/cpc com **4.020 usuários** (36% do tráfego total). PMax hotelaria geral e aquisição puxando forte.
8. **Páginas de produto com boa performance** — amenities, lençol, toalhas convertendo entre 50-60% de bounce. Aceitável para páginas de categoria B2B.
9. **E-mail marketing do boletim maio** — 278 usuários. Campanha de email consistente.

---

## Recomendações para Hoje (03/06)

1. **[Prioridade Máxima]** Reautenticar RD Station MCP — https://mcp.rdstationmentor.com/marketing → Conectar → atualizar config.yaml → `/reload-mcp`
2. **Investigar anomalia de tracking** (01 e 02/06) — validar se gtag está carregando corretamente e se o evento `session_engaged` está sendo disparado. Verificar Google Tag Manager.
3. **Corrigir landing page `(empty)`** — 763 usuários perdidos com 99,9% de rejeição. Identificar origem desse tráfego e corrigir redirect/página.
4. **Manter campanhas PMax** — hotelaria_geral e hotelaria_aquisicao performando bem. Avaliar aumento de budget na quinta-feira (padrão de pico).
5. **Preparar próximo boletim** — boletim maio terminou, preparar edição de junho mantendo formato.

---

*Relatório gerado por Flávia — Gerente de Marketing | Lojas Conamore*
*Dados: Google Analytics 4 (Composio) → CONAMORE Hotelaria OFICIAL (G-V0KMM7L6M6)*
*RD Station MCP: OFFLINE desde 01/06*
