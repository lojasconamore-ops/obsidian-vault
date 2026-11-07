# 📊 GA4 Diário — Blog Hotelaria | 07/11/2026

**Property:** `451180315` · **Measurement ID informado:** `G-LMY9B1F249` · **Fuso GA4:** America/Sao_Paulo (BRT)
**Dados: 04/11/2026 (D-3) vs 03/11/2026 (D-4).** Consulta à GA4 Data API via Composio em 07/11/2026; D-1/D-0 excluídos por consolidação.

## Resumo executivo
1. Em 04/11, **455 usuários ativos e 468 sessões**, contra 102 e 121 em 03/11 (**+346,1%** e **+286,8%**).
2. O ganho de volume não veio com qualidade: engajamento **11,5% (-42,2 p.p.)**, rejeição **88,5% (+42,2 p.p.)**, duração média **25s** (ante 2m21s).
3. `(direct) / (none)` respondeu por **405 sessões (86,5%)**, com **4,0% de engajamento**; desktop concentrou **422 sessões (90,2%)**.
4. As **420 linhas de landing page** para 468 sessões e o salto de tráfego direto com baixa interação sugerem tráfego automatizado ou problema de atribuição — **hipótese, não diagnóstico confirmado**.
5. `newVsReturning = (not set)` teve **7 sessões (1,5%)**, 0 usuários ativos; monitorar ruído de classificação/consentimento. O recorte por hostname confirmou **100% das 468 sessões em `hotelaria.conamore.com.br`**.

## 1. Comparativo geral

| Indicador | 04/11 (D-3) | 03/11 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 455 | 102 | +346,1% |
| Sessões | 468 | 121 | +286,8% |
| Usuários novos | 441 | 89 | +395,5% |
| Visualizações de página (`screenPageViews`) | 481 | 141 | +241,1% |
| Taxa de engajamento | 11,5% | 53,7% | -42,2 p.p. |
| Taxa de rejeição | 88,5% | 46,3% | +42,2 p.p. |
| Duração média da sessão | 25s | 2m21s | -82,2% |
| Eventos | 1.559 | 478 | +226,2% |

*Variações calculadas dos valores brutos da API (taxas em pontos percentuais); tempo arredondado só para exibição.*

## 2. Novos vs recorrentes — 04/11

| `newVsReturning` | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| new | 442 | 443 | 8,6% | 91,4% | 14s |
| returning | 13 | 18 | 83,3% | 16,7% | 5m07s |
| (not set) | 0 | 7 | 14,3% | 85,7% | <1s |

**Alerta:** 7 sessões não classificadas (1,5%), ante 8 (6,6%) no D-4 conforme [[GA4-Diario-Blog-2026-11-06]]. Compatível com ruído de consent mode/tracking, mas sem causalidade comprovada. Os usuários ativos por dimensão não devem ser somados indiscriminadamente para reconstruir usuários únicos.

## 3. Canais — origem/mídia, top 15 por usuários ativos (04/11)

| Origem / mídia (`sessionSourceMedium`) | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| (direct) / (none) | 401 | 405 | 4,0% | 96,0% |
| google / organic | 13 | 16 | 81,3% | 18,8% |
| ig / paid | 11 | 11 | 54,5% | 45,5% |
| rd-automacao / email | 7 | 11 | 54,5% | 45,5% |
| bing / organic | 3 | 3 | 33,3% | 66,7% |
| linktree / social | 3 | 3 | 66,7% | 33,3% |
| chatgpt.com / ai-assistant | 2 | 2 | 100,0% | 0,0% |
| instagram / paid | 2 | 2 | 100,0% | 0,0% |
| l.instagram.com / referral | 2 | 2 | 50,0% | 50,0% |
| outlook.live.com / referral | 2 | 2 | 50,0% | 50,0% |
| rd-email / email | 2 | 2 | 50,0% | 50,0% |
| (not set) | 1 | 1 | 0,0% | 100,0% |
| blog / (not set) | 1 | 3 | 33,3% | 66,7% |
| fb / paid | 1 | 1 | 0,0% | 100,0% |
| k6li72b606.preview-beefreecontent.com / referral | 1 | 1 | 100,0% | 0,0% |

*Top 15 de 18 origens/mídias na API. Usuários ativos entre origens podem não ser aditivos; percentuais de amostras pequenas não indicam tendência.*

## 4. Landing pages — top 10 por usuários ativos (04/11)

| Landing page | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| `/checklist-para-quartos-pousada` | 14 | 14 | 50,0% |
| `/calculadora-roupa-de-cama-de-hotel` | 11 | 14 | 57,1% |
| `(not set)` | 3 | 6 | 0,0% |
| `/` | 3 | 3 | 66,7% |
| `/11-dicas-de-livros-que-todo-hoteleiro-deveria-ler` | 3 | 3 | 100,0% |
| `/como-melhorar-praticas-e-estrategias-para-tornar-a-gestao-do-seu-hotel-mais-eficiente-e-lucrativa/como-melhorar-praticas-e-estrategias-para-tornar-a-gestao` | 3 | 5 | 20,0% |
| `/ebook-receba-bem-kit-basico-aluguel-temporada` | 3 | 3 | 100,0% |
| `/conheca-a-conamore-enxoval-profissional-para-hotelaria` | 2 | 2 | 100,0% |
| `/enxoval-airbnb-pousada-quanto-comprar` | 2 | 2 | 50,0% |
| `/hotelaria-hospitalar-conforto-acolhimento-servicos-saude` | 2 | 2 | 100,0% |

*Top 10 de 420 linhas de landing page na API; `(not set)` não é URL. O número 420 inclui variações de caminhos e a linha `(not set)`; não corresponde necessariamente a 420 artigos distintos.*

## 5. Dispositivos — 04/11

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| desktop | 413 | 422 | 7,6% | 92,4% | 21s |
| mobile | 42 | 45 | 48,9% | 51,1% | 1m06s |
| tablet | 0 | 1 | 0,0% | 100,0% | 0s |

## 6. Observações e alertas

- **Anomalia dominante:** direto passou de 21 sessões em 03/11 (relatório anterior) para 405 em 04/11; a rejeição nesse canal chegou a 96,0%. Não atribuir crescimento a demanda humana sem validar logs de servidor/CDN, user-agents/IPs, integridade do consentimento e padrão de `session_start`/`page_view` no GTM/GA4.
- **Conteúdo:** checklist e calculadora tiveram 14 sessões cada; 420 linhas de landing page para 468 sessões, contra 36 linhas no dia anterior (relatório anterior). Propor investigação de varredura automatizada e parâmetros/URLs duplicadas.
- **Classificação:** `(not set)` de novos/recorrentes teve 7 sessões, enquanto `(not set)` de landing page teve 6; são dimensões distintas, sem equivalência necessária.
- **Escopo:** consulta adicional `hostName` retornou somente `hotelaria.conamore.com.br` (455 usuários, 468 sessões, 481 pageviews) em 04/11; portanto o recorte do D-3 é do blog apesar do nome administrativo “LPS | Conamore Hotelaria” observado anteriormente. O D-4 foi consultado sem filtro de hostname, como no relatório anterior.
- **Fonte:** seis respostas bem-sucedidas de `GOOGLE_ANALYTICS_RUN_REPORT` na property `properties/451180315`; fuso `America/Sao_Paulo` confirmado no metadata. Nenhuma métrica de e-commerce usada.

**Status:** concluído; alerta de qualidade do tráfego e possível automação pendente de investigação.
