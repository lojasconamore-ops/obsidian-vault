# 📊 GA4 Diário — Blog | 28/10/2026

**Blog:** hotelaria.conamore.com.br · Property `451180315` · G-LMY9B1F249  
**Dados:** 25/10/2026 (D-3) vs 24/10/2026 (D-4) · fuso America/Sao_Paulo (BRT).  
**Fonte:** GA4 Data API via Composio, consultas `GOOGLE_ANALYTICS_RUN_REPORT` (data, newVsReturning, sessionSourceMedium, landingPage, deviceCategory).

## Resumo executivo
- Sessões: **60 vs 64** (−6,2%); usuários ativos: **57 vs 58** (−1,7%).
- Visualizações: **66 vs 74** (−10,8%); novos usuários: **58 vs 57** (+1,8%).
- Engajamento caiu de **51,6% para 36,7%** (−14,9 p.p.); rejeição subiu de **48,4% para 63,3%** (+14,9 p.p.).
- `ig / paid` liderou com **16 sessões**; `google / organic` teve **13**. Mobile concentrou **51/60 sessões (85%)**.
- Atenção a `poki.com / referral` (**6 sessões, 0% engajamento**); `(not set)` em novos/recorrentes teve **2 sessões**, possível ruído de mensuração.

## 1. 📈 Comparativo geral

| Indicador | 25/10 (D-3) | 24/10 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 57 | 58 | −1,7% |
| Sessões | 60 | 64 | −6,2% |
| Usuários novos | 58 | 57 | +1,8% |
| Visualizações de página | 66 | 74 | −10,8% |
| Taxa de engajamento | 36,7% | 51,6% | −14,9 p.p. |
| Taxa de rejeição | 63,3% | 48,4% | +14,9 p.p. |
| Duração média da sessão | 0m53s | 1m00s | −12,6% |
| Eventos | 227 | 258 | −12,0% |

## 2. 🔎 Novos vs recorrentes — 25/10

| Categoria GA4 (`newVsReturning`) | Usuários ativos | Sessões | Engajamento | Rejeição | Duração média |
|---|---:|---:|---:|---:|---:|
| new | 57 | 57 | 36,8% | 63,2% | 0m54s |
| returning | 1 | 1 | 100,0% | 0,0% | 1m45s |
| (not set) | 0 | 2 | 0,0% | 100,0% | 0m00s |

**Nota:** `(not set)` representa 2/60 sessões (3,3%), apesar de zero usuários ativos; compatível com ruído de consent mode, sem comprovação causal por este relatório. Usuários por categoria não são somáveis diretamente ao total diário (58 na soma das categorias vs 57 no total); métricas de usuário são distintas por dimensão e podem se sobrepor. `newUsers` (58) também não é intercambiável com `newVsReturning=new` (57 usuários ativos).

## 3. 📣 Canais — origem/mídia, 25/10 (top 15 disponíveis)

| Origem / mídia (`sessionSourceMedium`) | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| ig / paid | 14 | 16 | 37,5% | 62,5% |
| google / organic | 13 | 13 | 30,8% | 69,2% |
| (direct) / (none) | 10 | 10 | 50,0% | 50,0% |
| poki.com / referral | 6 | 6 | 0,0% | 100,0% |
| linktree / social | 4 | 4 | 100,0% | 0,0% |
| chatgpt.com / ai-assistant | 2 | 2 | 0,0% | 100,0% |
| google / cpc | 2 | 2 | 100,0% | 0,0% |
| instagram / paid | 2 | 2 | 0,0% | 100,0% |
| 7a6d8e9b87bb958cdb1aed0a7a275c90.safeframe.googlesyndication.com / referral | 1 | 1 | 100,0% | 0,0% |
| cnnbrasil.com.br / referral | 1 | 1 | 0,0% | 100,0% |
| lm.facebook.com / referral | 1 | 1 | 0,0% | 100,0% |
| m.facebook.com / referral | 1 | 1 | 0,0% | 100,0% |
| notebookcheck.net / referral | 1 | 1 | 0,0% | 100,0% |

**Cobertura:** API retornou 13 origens/mídias (`rowCount=13`), todas exibidas; usuários ativos por origem podem se repetir entre origens. A nomenclatura `ig / paid` e `instagram / paid` aparece separada no GA4.

## 4. 📄 Landing pages — 25/10 (top 10 por usuários ativos)

| Landing page (`landingPage`) | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| `/checklist-para-quartos-pousada` | 15 | 17 | 35,3% |
| `/hotelaria-hospitalar-como-realizar-a-gestao-do-enxoval/enxoval-hotelaria-hospitalar-clinica` | 7 | 7 | 0,0% |
| `/toalhas-e-lencois-para-clinicas-saloes-de-beleza-e-academias-como-acertar-na-escolha` | 7 | 7 | 28,6% |
| `/conheca-a-conamore-enxoval-profissional-para-hotelaria` | 4 | 4 | 100,0% |
| `/enxoval-para-hotelaria-tire-todas-as-duvidas-sobre-os-produtos-e-forma-de-comprar-na-conamore` | 4 | 4 | 0,0% |
| `/` | 2 | 2 | 50,0% |
| `/11-dicas-de-livros-que-todo-hoteleiro-deveria-ler` | 2 | 2 | 0,0% |
| `/como-melhorar-praticas-e-estrategias-para-tornar-a-gestao-do-seu-hotel-mais-eficiente-e-lucrativa/como-melhorar-praticas-e-estrategias-para-tornar-a-gestao` | 2 | 2 | 0,0% |
| `/ebook-receba-bem-kit-basico-aluguel-temporada` | 2 | 2 | 0,0% |
| `/lencol-hotelaria-densidade-fios` | 2 | 2 | 0,0% |

**Cobertura:** 10 de 21 landing pages reportadas pelo GA4, ordenadas por usuários ativos.

## 5. 📱 Dispositivos — 25/10

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição | Duração média |
|---|---:|---:|---:|---:|---:|
| mobile | 48 | 51 | 35,3% | 64,7% | 1m01s |
| desktop | 9 | 9 | 44,4% | 55,6% | 0m05s |
| tablet | 0 | 0 | — | — | — |

**Nota:** tablet não retornou linha na API (não foi observado tráfego nesse recorte); não é uma linha numérica da resposta GA4.

## 6. 🚨 Observações e alertas

- A deterioração de qualidade é mais expressiva que a queda de volume: engajamento −14,9 p.p., rejeição +14,9 p.p. e visualizações −10,8%. Comparação diária limitada, sem inferência de tendência longa.
- `poki.com / referral`: 6 sessões, 10% do total diário, todas rejeitadas; investigar origem/referral spam e páginas de destino antes de concluir invalidade do tráfego.
- `ig / paid` e `instagram / paid` separados sugerem padronização de UTM para melhorar a leitura de campanhas (não somar usuários distintos como pessoas únicas).
- `(not set)` em novos vs recorrentes: 2 sessões, 0 usuários, 0% engajamento; monitorar possível ruído de consent mode.
- `google / organic` apresentou 13 sessões e 30,8% de engajamento; a landing page de checklist liderou com 17 sessões e 35,3% de engajamento.
- Nenhuma métrica de e-commerce usada, pois esta propriedade mede o blog de conteúdo.

**Status:** concluído; 5/5 consultas GA4 retornaram dados, com timezone `America/Sao_Paulo` confirmado na resposta.
