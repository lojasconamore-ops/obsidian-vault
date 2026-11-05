# 📊 GA4 Diário — Blog Hotelaria | 05/11/2026

**Property:** `451180315` · **Measurement ID:** `G-LMY9B1F249` · **Fuso da propriedade:** America/Sao_Paulo (BRT)
**Dados: 02/11/2026 (D-3) vs 01/11/2026 (D-4).** Consultas GA4 Data API via Composio em 05/11/2026; D-1/D-0 excluídos por consolidação.

## Resumo executivo
1. Em 02/11, o blog teve **138 usuários ativos e 151 sessões**, contra 64 e 72 em 01/11 (**+115,6%** e **+109,7%**).
2. As visualizações chegaram a **161 (+87,2%)** e os eventos a **590 (+90,9%)**; novos usuários: **133 (+121,7%)**.
3. A qualidade recuou: **engajamento 49,0% (-6,5 p.p.)**, rejeição **51,0% (+6,5 p.p.)** e duração média **1m23s (-39,3%)**.
4. `rd-automacao / email` liderou com **57 usuários e 64 sessões**; as duas principais landing pages concentraram **89 sessões**.
5. Houve **5 sessões em `newVsReturning = (not set)`** (3,3% do total), com 0 usuários ativos; monitorar como possível ruído de classificação/consentimento, sem atribuir causa definitiva.

## 1. Comparativo geral

| Indicador | 02/11 (D-3) | 01/11 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 138 | 64 | +115,6% |
| Sessões | 151 | 72 | +109,7% |
| Usuários novos | 133 | 60 | +121,7% |
| Visualizações de página (`screenPageViews`) | 161 | 86 | +87,2% |
| Taxa de engajamento | 49,0% | 55,6% | -6,5 p.p. |
| Taxa de rejeição | 51,0% | 44,4% | +6,5 p.p. |
| Duração média da sessão | 1m23s | 2m17s | -39,3% |
| Eventos | 590 | 309 | +90,9% |

*Variações percentuais calculadas com valores brutos da API; taxas em pontos percentuais. Duração média arredondada para segundos na apresentação.*

## 2. Novos vs recorrentes — 02/11

| `newVsReturning` | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| new | 132 | 132 | 50,0% | 50,0% | 1m15s |
| returning | 10 | 14 | 57,1% | 42,9% | 3m12s |
| (not set) | 0 | 5 | 0,0% | 100,0% | 0s |

**Alerta de qualidade:** 5 sessões sem classificação (3,3% das sessões). A soma dos usuários por linha (142) difere do total único (138), pois usuários podem transitar entre grupos; não somar usuários de dimensões para reconstruir o total. O bucket `(not set)` é compatível com ruído de tracking/consent mode, mas este relatório não comprova a causa.

## 3. Canais — origem/mídia por usuários ativos, top 15 (02/11)

| Origem / mídia (`sessionSourceMedium`) | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| rd-automacao / email | 57 | 64 | 54,7% | 45,3% |
| (direct) / (none) | 23 | 23 | 21,7% | 78,3% |
| ig / paid | 23 | 25 | 60,0% | 40,0% |
| google / organic | 12 | 14 | 42,9% | 57,1% |
| rd-email / email | 7 | 7 | 71,4% | 28,6% |
| chatgpt.com / ai-assistant | 2 | 2 | 100,0% | 0,0% |
| instagram / paid | 2 | 3 | 0,0% | 100,0% |
| l.instagram.com / referral | 2 | 2 | 50,0% | 50,0% |
| related.inspiredtoday.net / referral | 2 | 2 | 50,0% | 50,0% |
| bing / organic | 1 | 1 | 0,0% | 100,0% |
| bit.ly / referral | 1 | 1 | 100,0% | 0,0% |
| fb / paid | 1 | 1 | 0,0% | 100,0% |
| google / cpc | 1 | 1 | 100,0% | 0,0% |
| linktree / social | 1 | 1 | 100,0% | 0,0% |
| qa-claude / (not set) | 1 | 1 | 100,0% | 0,0% |

*15 de 18 origens/mídias retornadas, conforme limite top 15. O percentual de engajamento em amostras mínimas não indica tendência.*

## 4. Landing pages — top 10 por usuários ativos (02/11)

| Landing page | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| `/calculadora-roupa-de-cama-de-hotel` | 58 | 63 | 57,1% | 42,9% |
| `/checklist-para-quartos-pousada` | 24 | 26 | 57,7% | 42,3% |
| `/` | 5 | 6 | 16,7% | 83,3% |
| `/category/dicas-de-sustentabilidade-para-hoteis-e-pousadas` | 3 | 3 | 0,0% | 100,0% |
| `/como-melhorar-praticas-e-estrategias-para-tornar-a-gestao-do-seu-hotel-mais-eficiente-e-lucrativa/como-melhorar-praticas-e-estrategias-para-tornar-a-gestao` | 3 | 3 | 33,3% | 66,7% |
| `/enxoval-airbnb-pousada-quanto-comprar` | 3 | 3 | 100,0% | 0,0% |
| `/lencol-hotelaria-densidade-fios` | 3 | 3 | 66,7% | 33,3% |
| `/mais-cidades-e-regioes-estao-no-mapa-turismo-brasileiro` | 3 | 3 | 66,7% | 33,3% |
| `(not set)` | 2 | 3 | 0,0% | 100,0% |
| `/7-atributos-que-os-hospedes-mais-levam-em-conta-na-hora-de-fazer-uma-reserva` | 2 | 2 | 100,0% | 0,0% |

*10 de 40 landing pages retornadas, conforme limite top 10.*

## 5. Dispositivos — 02/11

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| mobile | 99 | 107 | 49,5% | 50,5% | 1m14s |
| desktop | 38 | 43 | 46,5% | 53,5% | 1m48s |
| tablet | 1 | 1 | 100,0% | 0,0% | 0m10s |

## 6. Observações e alertas

- **Volume vs qualidade:** salto de sessões na segunda-feira (02/11) frente ao domingo (01/11), concomitante com redução do engajamento e tempo médio. A diferença entre dias da semana impede atribuir a variação apenas a campanhas.
- **Composição dos canais:** `rd-automacao / email` respondeu por 64 de 151 sessões (42,4%); `ig / paid`, 25. Verificar desempenho e segmentação do envio de e-mail, sem inferir causalidade do aumento sem comparação por canal no D-4.
- **Atenção ao direto:** 23 sessões com 21,7% de engajamento e 78,3% de rejeição. Dois UTMs para Instagram pago (`ig / paid` e `instagram / paid`) fragmentam a análise; padronização recomendada.
- **Conteúdo:** calculadora e checklist somaram 89 de 151 sessões (58,9%); priorizar experiência e próximos passos nessas páginas. `landingPage = (not set)` teve 3 sessões e 100% de rejeição; observar o ruído de mensuração.
- **Dispositivos:** mobile concentrou 99 de 138 usuários (71,7%). Tablet: base de apenas 1 usuário.
- **Nota técnica:** propriedade informou fuso `America/Sao_Paulo`. Métricas de comércio eletrônico não se aplicam ao blog. Fontes: cinco respostas `GOOGLE_ANALYTICS_RUN_REPORT` da property `properties/451180315`, período exato 01–02/11/2026.

**Status:** concluído — dados consultados na GA4 Data API.
