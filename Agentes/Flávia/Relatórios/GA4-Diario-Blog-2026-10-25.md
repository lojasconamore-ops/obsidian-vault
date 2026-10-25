# 📊 GA4 Diário — Blog Conamore | 25/10/2026

**Property:** `451180315` · **Measurement ID:** `G-LMY9B1F249` · **Fuso:** America/Sao_Paulo (BRT)  
**Dados:** 22/10/2026 (D-3) vs 21/10/2026 (D-4). Recortes de canais, páginas, perfil e dispositivos: 22/10/2026.

## Resumo executivo
1. Sessões subiram de 61 para 74 (+21,3%); usuários ativos foram de 57 para 60 (+5,3%).
2. Visualizações de página cresceram de 84 para 93 (+10,7%) e eventos de 272 para 321 (+18,0%).
3. Engajamento avançou de 52,5% para 58,1% (+5,6 p.p.); rejeição recuou de 47,5% para 41,9% (−5,6 p.p.).
4. Google orgânico e acesso direto empataram na liderança por usuários (19 cada); orgânico teve 26 sessões e 65,4% de engajamento.
5. Alerta de qualidade: `newVsReturning = (not set)` concentrou 6 sessões (8,1% do total), com 83,3% de rejeição; investigar instrumentação/consentimento sem atribuir causa definitiva.

## 1. Comparativo geral

| Indicador | 22/10 (D-3) | 21/10 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 60 | 57 | +5,3% |
| Sessões | 74 | 61 | +21,3% |
| Usuários novos | 57 | 55 | +3,6% |
| Visualizações de página | 93 | 84 | +10,7% |
| Taxa de engajamento | 58,1% | 52,5% | +5,6 p.p. |
| Taxa de rejeição | 41,9% | 47,5% | −5,6 p.p. |
| Tempo médio da sessão | 2m18s (137,5s) | 1m50s (109,9s) | +27,6s (+25,1%) |
| Eventos | 321 | 272 | +18,0% |

## 2. Novos vs Recorrentes — 22/10

| Perfil (`newVsReturning`) | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio da sessão |
|---|---:|---:|---:|---:|---:|
| new | 56 | 56 | 58,9% | 41,1% | 1m32s |
| returning | 6 | 12 | 75,0% | 25,0% | 6m53s |
| (not set) | 0 | 6 | 16,7% | 83,3% | 0m07s |

**Alerta:** `(not set)` responde por 6 de 74 sessões (8,1%), apesar de 0 usuários ativos atribuídos nessa linha. É um sinal de ruído de atribuição/consent mode a investigar, não diagnóstico causal. Usuários ativos por perfil não devem ser somados como únicos do dia (uma pessoa pode transitar entre perfis).

## 3. Canais — origem/mídia, 22/10

| Origem / mídia | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| (direct) / (none) | 19 | 20 | 45,0% | 55,0% |
| google / organic | 19 | 26 | 65,4% | 34,6% |
| ig / paid | 6 | 7 | 42,9% | 57,1% |
| linktree / social | 4 | 4 | 100,0% | 0,0% |
| bing / organic | 3 | 3 | 100,0% | 0,0% |
| instagram / paid | 3 | 5 | 60,0% | 40,0% |
| chatgpt.com / ai-assistant | 2 | 2 | 50,0% | 50,0% |
| an / paid | 1 | 1 | 0,0% | 100,0% |
| fb / paid | 1 | 1 | 100,0% | 0,0% |
| rd-station / email | 1 | 3 | 66,7% | 33,3% |
| th / paid | 1 | 1 | 0,0% | 100,0% |
| yahoo / organic | 0 | 1 | 0,0% | 100,0% |

São as 12 origens/mídias retornadas pela API (limite solicitado: 15). Métricas de usuários por origem não são necessariamente aditivas. `ig / paid` e `instagram / paid` aparecem separados: revisar padronização de UTMs; `an / paid` e `th / paid` precisam de identificação antes de interpretação.

## 4. Top 10 landing pages — 22/10

| Landing page | Usuários ativos | Sessões | Engajamento | Rejeição |
|---|---:|---:|---:|---:|
| `/checklist-para-quartos-pousada` | 9 | 10 | 40,0% | 60,0% |
| `/conheca-a-conamore-enxoval-profissional-para-hotelaria` | 4 | 4 | 75,0% | 25,0% |
| `/qual-a-diferenca-entre-hotel-pousada-e-hostel` | 4 | 4 | 50,0% | 50,0% |
| `/ebook-receba-bem-kit-basico-aluguel-temporada` | 3 | 5 | 60,0% | 40,0% |
| `/` | 2 | 3 | 66,7% | 33,3% |
| `/11-dicas-de-livros-que-todo-hoteleiro-deveria-ler` | 2 | 2 | 50,0% | 50,0% |
| `/3-perguntas-basicas-que-todo-anfitriao-precisa-saber-como-responder` | 2 | 2 | 100,0% | 0,0% |
| `/como-melhorar-praticas-e-estrategias-para-tornar-a-gestao-do-seu-hotel-mais-eficiente-e-lucrativa/como-melhorar-praticas-e-estrategias-para-tornar-a-gestao` | 2 | 3 | 33,3% | 66,7% |
| `/como-preparar-regras-hospedes-hoteis-pousadas` | 2 | 2 | 100,0% | 0,0% |
| `/gestao-de-hotelaria-7-indicadores-para-acompanhar-de-perto` | 2 | 2 | 0,0% | 100,0% |

Top 10 de 44 landing pages distintas informadas pela API; a URL longa é o valor retornado pelo GA4, sem validação de URL/canonical.

## 5. Dispositivos — 22/10

| Dispositivo | Usuários ativos | Sessões | Engajamento | Rejeição | Tempo médio da sessão |
|---|---:|---:|---:|---:|---:|
| mobile | 38 | 45 | 55,6% | 44,4% | 1m52s |
| desktop | 22 | 29 | 62,1% | 37,9% | 2m58s |
| tablet | 0* | 0* | — | — | — |

\* Sem linha de tablet na resposta da API; os dois dispositivos informados totalizam as 74 sessões do dia.

## 6. Observações e próximos cuidados

- O crescimento de sessões (+21,3%) superou o de usuários ativos (+5,3%): mais visitas por usuário no comparativo, sem concluir tendência por apenas dois dias.
- Página líder `/checklist-para-quartos-pousada` tem 10 sessões e 60% de rejeição; vale acompanhar o engajamento antes de propor ajuste editorial.
- O bloco `(not set)` de 6 sessões e 83,3% de rejeição pode contaminar leituras por perfil; conferir consent mode/GTM com TI, sem inferir causa apenas deste relatório.
- Origem paga fragmentada (`ig`/`instagram`, `an`, `th`) pede auditoria das convenções de UTM; amostras individuais são pequenas.
- Fonte: Google Analytics Data API via Composio, `GOOGLE_ANALYTICS_RUN_REPORT`, property `properties/451180315`; timezone devolvido pela API: `America/Sao_Paulo`. D-1 e D-0 foram excluídos por consolidação incompleta.

**Status:** Concluído.
