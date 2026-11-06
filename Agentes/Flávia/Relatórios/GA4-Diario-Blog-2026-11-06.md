# 📊 GA4 Diário — Blog Hotelaria | 06/11/2026

**Property:** `451180315` · **Measurement ID informado:** `G-LMY9B1F249` · **Fuso da propriedade:** America/Sao_Paulo (BRT)
**Dados: 03/11/2026 (D-3) vs 02/11/2026 (D-4).** Consulta à GA4 Data API via Composio em 06/11/2026; D-1/D-0 excluídos por consolidação.

## Resumo executivo
1. Em 03/11, houve **102 usuários ativos e 121 sessões**, ante 138 e 151 em 02/11 (**-26,1%** e **-19,9%**).
2. Os **89 usuários novos (-33,1%)**, **141 visualizações (-12,4%)** e **478 eventos (-19,0%)** acompanharam a queda de volume.
3. A qualidade melhorou: **engajamento 53,7% (+4,7 p.p.)**, rejeição **46,3% (-4,7 p.p.)** e duração média **2m21s (+70,4%)**.
4. `rd-automacao / email` liderou com **40 usuários e 45 sessões**; a calculadora de roupa de cama recebeu **50 sessões**.
5. **Alerta de classificação:** `newVsReturning = (not set)` registrou **8 sessões (6,6%)**, 0 usuários ativos e 100% de rejeição; compatível com ruído de tracking/consentimento, sem causa confirmada.

## 1. Comparativo geral

| Indicador | 03/11 (D-3) | 02/11 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 102 | 138 | -26,1% |
| Sessões | 121 | 151 | -19,9% |
| Usuários novos | 89 | 133 | -33,1% |
| Visualizações de página (`screenPageViews`) | 141 | 161 | -12,4% |
| Taxa de engajamento | 53,7% | 49,0% | +4,7 p.p. |
| Taxa de rejeição | 46,3% | 51,0% | -4,7 p.p. |
| Duração média da sessão | 2m21s | 1m23s | +70,4% |
| Eventos | 478 | 590 | -19,0% |

*Variações calculadas com valores brutos da API; taxas em pontos percentuais. Tempo arredondado para segundos somente na exibição.*

## 2. Novos vs recorrentes — 03/11

| `newVsReturning` | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio |
|---|---:|---:|---:|---:|---:|
| new | 91 | 91 | 57,1% | 42,9% | 2m16s |
| returning | 20 | 22 | 59,1% | 40,9% | 3m33s |
| (not set) | 0 | 8 | 0,0% | 100,0% | 0s |

**Alerta:** 8 sessões sem classificação (6,6% de 121), acima das 5 sessões (3,3%) observadas no D-4 no relatório anterior. Esse padrão é compatível com ruído de consent mode/tracking, mas não demonstra causa. Usuários ativos podem aparecer em mais de um grupo; não somar 91 e 20 para reconstruir 102 usuários únicos.

## 3. Canais — origem/mídia por usuários ativos, top 15 (03/11)

| Origem / mídia (`sessionSourceMedium`) | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| rd-automacao / email | 40 | 45 | 62,2% | 37,8% |
| google / organic | 19 | 23 | 56,5% | 43,5% |
| (direct) / (none) | 18 | 21 | 52,4% | 47,6% |
| ig / paid | 11 | 13 | 46,2% | 53,8% |
| rd-email / email | 3 | 4 | 50,0% | 50,0% |
| (not set) | 2 | 2 | 0,0% | 100,0% |
| linktree / social | 2 | 2 | 0,0% | 100,0% |
| bing / organic | 1 | 2 | 50,0% | 50,0% |
| blog / artigo | 1 | 1 | 100,0% | 0,0% |
| br.search.yahoo.com / referral | 1 | 1 | 100,0% | 0,0% |
| fb / paid | 1 | 1 | 0,0% | 100,0% |
| fourfourtwo.com / referral | 1 | 1 | 0,0% | 100,0% |
| k6li72b606.preview-beefreecontent.com / referral | 1 | 1 | 100,0% | 0,0% |
| th / paid | 1 | 1 | 100,0% | 0,0% |
| RD Station / email | 0 | 1 | 0,0% | 100,0% |

*15 de 17 origens/mídias retornadas pela API. Percentuais em amostras muito pequenas não indicam tendência.*

## 4. Landing pages — top 10 por usuários ativos (03/11)

| Landing page | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| `/calculadora-roupa-de-cama-de-hotel` | 46 | 50 | 66,0% |
| `/checklist-para-quartos-pousada` | 13 | 15 | 46,7% |
| `(not set)` | 6 | 7 | 0,0% |
| `/ebook-diferenciais-para-anfitrioes-do-airbnb-saiba-como-se-destacar-dos-demais` | 4 | 4 | 75,0% |
| `/` | 3 | 4 | 50,0% |
| `/como-divulgar-pousada-trivago` | 2 | 2 | 50,0% |
| `/como-preparar-regras-hospedes-hoteis-pousadas` | 2 | 3 | 33,3% |
| `/conheca-a-conamore-enxoval-profissional-para-hotelaria` | 2 | 2 | 0,0% |
| `/conheca-a-conamore-hotelaria-enxoval-profissional-para-voce` | 2 | 3 | 33,3% |
| `/enxoval-airbnb-pousada-quanto-comprar` | 2 | 2 | 100,0% |

*10 de 36 landing pages retornadas pela API; `(not set)` não é URL.*

## 5. Dispositivos — 03/11

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| desktop | 52 | 64 | 59,4% | 40,6% |
| mobile | 50 | 57 | 47,4% | 52,6% |
| tablet | 0 | 0 | — | — |

*Tablet não apresentou linha no retorno da API; zeros indicam ausência de registros retornados, não medição separada.*

## 6. Observações e alertas

- **Volume caiu, qualidade subiu:** a comparação é de terça-feira (03/11) com segunda-feira (02/11); não atribuir causalidade sem comparar mix de campanhas e dias equivalentes.
- **E-mail ainda lidera:** `rd-automacao / email` passou de 64 sessões no D-4 para 45 no D-3; `ig / paid` passou de 25 para 13. Esses recortes do D-4 vêm do relatório [[GA4-Diario-Blog-2026-11-05]], não de nova consulta de canais.
- **Conteúdo:** a calculadora teve 50 de 121 sessões (41,3%) e 66,0% de engajamento; o checklist, 15 sessões. `landingPage = (not set)` teve 7 sessões (5,8%), todas não engajadas.
- **Classificação:** o bucket `(not set)` de novos/recorrentes subiu de 5 para 8 sessões; monitorar consentimento e eventos `session_start`/`page_view`. Não confundir 8 sessões sem classificação de usuários com as 7 sessões de landing page ausente; são dimensões distintas e não necessariamente as mesmas sessões.
- **Nome da propriedade:** a Admin API identifica `properties/451180315` como **“LPS | Conamore Hotelaria”**. A property solicitada foi usada corretamente, mas o nome sugere escopo possivelmente mais amplo que apenas o blog; validar stream/hostname antes de interpretar esses números como tráfego exclusivamente de `hotelaria.conamore.com.br`. Nenhum filtro de hostname foi aplicado nesta rotina.
- **Fonte:** cinco respostas bem-sucedidas de `GOOGLE_ANALYTICS_RUN_REPORT`, property `properties/451180315`; fuso confirmado pela Admin API como `America/Sao_Paulo`. Não foram usadas métricas de e-commerce.

**Status:** concluído com ressalva de escopo da propriedade e ruído de classificação.
