# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 05/10/2026, 09:01–09:23 BRT  
**Escopo executado:** Gemini direto, 15 prompts fixos × 2 rodadas = 30 submissões  
**Fonte de evidência:** `Direct platform` — interface pública do Gemini 3.5 Flash-Lite, sem login  
**Status:** **COMPLETO** — 30/30 prompts submetidos e 30/30 respostas observadas.

---

## Metodologia e limitações

- Cada prompt foi submetido individualmente em conversa nova, evitando contaminação por respostas anteriores.
- Menção foi medida no conteúdo da resposta (`message-content`), incluindo os rótulos de fontes exibidos dentro da resposta, mas sem contar o prompt do usuário.
- O prompt P9 da primeira rodada falhou na primeira tentativa; foi repetido e concluído antes do encerramento. Apenas a execução válida entrou no denominador.
- Somente o Gemini foi testado. ChatGPT, Perplexity e Copilot ficaram fora deste ciclo por prioridade e orçamento operacional.
- URLs foram coletadas quando apareceram como links clicáveis. Uma execução suplementar de P14, fora do denominador, foi usada para abrir o detalhe da fonte Conamore.
- Recomendação comercial foi classificada de forma conservadora: conta apenas quando a Conamore apareceu como empresa, fornecedora ou opção de compra, e não quando surgiu apenas como rótulo de fonte.
- O Gemini é estocástico. Duas rodadas permitem comparação semanal, mas a diferença entre rodadas ainda deve ser considerada.

---

## Resumo executivo

A Conamore apareceu em **19/30 respostas (63,3%)**: **11/15 na R1 (73,3%)** e **8/15 na R2 (53,3%)**. Frente ao último ciclo completo comparável, de 21/09/2026, houve avanço de **16/30 (53,3%) para 19/30 (63,3%)** — ganho de **3 menções e +10,0 pontos percentuais**.

Sete intenções ficaram estáveis em **2/2**: **P5 enxoval genérico, P6 onde comprar, P7 fornecedor, P8 pronta entrega, P11 empresas no Brasil, P13 roupa de cama para pousadas e P14 branded**. Três ficaram cegas em **0/2**: **P2 melhor lençol, P9 fornecedor em São Paulo e P15 empresa de enxoval para hotelaria**.

A melhora foi puxada principalmente pela recuperação de **P5**, que passou de 0/2 para 2/2, e pela consolidação de **P6 e P13**, agora também em 2/2. Em contrapartida, **P2 e P15** perderam a única aparição que tinham no ciclo anterior.

A **ParaHotel** permaneceu como concorrente dominante, presente em **21/30 respostas (70,0%)**, acima das **19/30 menções da Conamore**. No share of voice simples entre Conamore e os concorrentes monitorados, a Conamore representou **19 de 68 presenças (27,9%)** e a ParaHotel **21/68 (30,9%)**.

---

## Disponibilidade da plataforma

| Plataforma | Planejado | Testado | Status | Evidência |
|---|---:|---:|---|---|
| Gemini direto | 30 | 30/30 | `tested` | 2 rodadas completas; uma conversa nova por prompt |
| ChatGPT | 0 | 0 | `not run` | Fora do escopo prioritário deste ciclo |
| Perplexity | 0 | 0 | `not run` | Fora do escopo prioritário deste ciclo |
| Copilot | 0 | 0 | `not run` | Fora do escopo prioritário deste ciclo |

---

## Métricas

| Métrica | R1 | R2 | Consolidado |
|---|---:|---:|---:|
| Prompts testados | 15/15 | 15/15 | **30/30** |
| Menção textual Conamore | 11/15 (73,3%) | 8/15 (53,3%) | **19/30 (63,3%)** |
| Recomendação/inclusão comercial explícita | 8/15 (53,3%) | 7/15 (46,7%) | **15/30 (50,0%)** |
| Prompts estáveis positivos (2/2) | — | — | **7/15 (46,7%)** |
| Prompts oscilantes (1/2) | — | — | **5/15 (33,3%)** |
| Prompts cegos (0/2) | — | — | **3/15 (20,0%)** |

### Resultado por grupo de intenção

| Grupo | Menções | Taxa |
|---|---:|---:|
| Produto — P1 a P5 | 5/10 | 50,0% |
| Compra/Fornecedor — P6 a P10 | 7/10 | 70,0% |
| Comparação/Marca — P11 a P15 | 7/10 | 70,0% |

**Leitura:** a associação comercial da Conamore está mais forte em fornecedor, compra e listas de empresas do que em buscas de produto genérico. O grupo Produto melhorou graças a P5, mas segue dependente de rótulos de fonte em algumas respostas.

---

## Matriz prompt × rodada

| # | Prompt exato | R1 | R2 | Consolidação |
|---:|---|:---:|:---:|:---:|
| 1 | `lençol para hotel` | ✅ | ❌ | 1/2 |
| 2 | `qual o melhor lençol para hotel` | ❌ | ❌ | **0/2** |
| 3 | `lençol profissional para pousada` | ✅ | ❌ | 1/2 |
| 4 | `lençol para Airbnb` | ✅ | ❌ | 1/2 |
| 5 | `enxoval para hotel` | ✅ | ✅ | **2/2** |
| 6 | `onde comprar lençol para hotel` | ✅ | ✅ | **2/2** |
| 7 | `fornecedor de lençol para hotéis` | ✅ | ✅ | **2/2** |
| 8 | `lençol para hotel com pronta entrega` | ✅ | ✅ | **2/2** |
| 9 | `fornecedor de enxoval hoteleiro em São Paulo` | ❌ | ❌ | **0/2** |
| 10 | `onde comprar enxoval profissional para hotel` | ✅ | ❌ | 1/2 |
| 11 | `quais empresas vendem lençol para hotel no Brasil` | ✅ | ✅ | **2/2** |
| 12 | `compare fornecedores de enxoval para hotéis` | ❌ | ✅ | 1/2 |
| 13 | `qual empresa fornece roupa de cama para pousadas` | ✅ | ✅ | **2/2** |
| 14 | `Conamore é uma boa empresa para enxoval hoteleiro?` | ✅ | ✅ | **2/2** |
| 15 | `empresa de enxoval para hotelaria` | ❌ | ❌ | **0/2** |

**Reconciliação:** esperado 30; submetido 30; respostas/evidências válidas 30; não executado 0.

---

## Evidências representativas

### R1P7 — fornecedor

> “Conamore: Focada em cama, mesa e banho para o setor de hotelaria e hospedagens de temporada.”

A resposta incluiu a Conamore diretamente entre fornecedores profissionais e destacou pronta entrega, conforto e durabilidade.

### R2P8 — pronta entrega

> “Trabalha com estoque a pronta entrega em todo o Brasil para linhas institucionais.”

A associação entre Conamore, pronta entrega e linhas profissionais apareceu de forma comercialmente clara.

### R2P13 — pousadas

> “Especializada em cama, mesa e banho para o setor de hotelaria, com foco em pronta entrega.”

O tema pousadas, que era instável no ciclo anterior, alcançou 2/2 neste ciclo por meio de P13.

### R1/R2P14 — intenção de marca

Nas duas rodadas o Gemini avaliou a Conamore positivamente. Exemplo:

> “A Conamore é uma empresa bastante tradicional no mercado de enxoval voltado para hotelaria.”

**Nota de precisão:** alegações como “tradicional”, “amplamente conhecida”, “atende bem” e reputação “Boa” foram geradas sem indicador datado no texto. Não devem ser reutilizadas em comunicação comercial sem validação atual.

---

## URLs e camada de fonte

| Evidência | URL observada | Classificação |
|---|---|---|
| P14 — link clicável no ciclo | `https://www.youtube.com/watch?v=srDxB4vuoSY` | Intermediário — canal/vídeo Conamore Hotelaria |
| P14 — auditoria suplementar de fonte | `https://www.conamore.com.br/quem-somos` | **Domínio Conamore direto**, Hotelaria/B2B institucional |
| R2P15 — lista sem Conamore | `https://www.parahotel.com.br/` | Concorrente — domínio direto ParaHotel |
| R2P15 — lista sem Conamore | `https://g3hotelaria.com/` | Concorrente — domínio direto |
| R2P15 — lista sem Conamore | `https://www.servhotel.com.br/` | Concorrente — domínio direto |

A auditoria suplementar confirmou que o Gemini acessa/cita diretamente a página institucional `/quem-somos`. A landing page prioritária `/lencol-para-hotelaria` **não foi confirmada como URL clicável neste ciclo**. Também não foi observada fonte via Scribd na amostra aberta.

**Citação de domínio:** não foi auditada em todas as 30 respostas; portanto, não há taxa consolidada confiável. O resultado confirmado é **1 fonte direta Conamore aberta em amostra suplementar**, fora do denominador de menção.

---

## Concorrentes citados

Contagem de respostas em que cada marca monitorada apareceu, sobre 30 respostas:

| Marca | Respostas | Taxa | Variação vs 21/09 |
|---|---:|---:|---:|
| **ParaHotel** | **21/30** | **70,0%** | +2 |
| **Conamore** | **19/30** | **63,3%** | +3 |
| Niazi Chohfi | 7/30 | 23,3% | +3 |
| Zelo | 5/30 | 16,7% | +1 |
| Altenburg | 4/30 | 13,3% | +3 |
| Teka | 3/30 | 10,0% | -2 |
| Buettner | 3/30 | 10,0% | +1 |
| Karsten | 2/30 | 6,7% | -1 |
| Buddemeyer | 2/30 | 6,7% | nova no painel deste ciclo |
| Santista | 1/30 | 3,3% | -2 |
| Kacyumara | 1/30 | 3,3% | nova no painel deste ciclo |

**Leitura:** a Conamore reduziu a distância para a ParaHotel de 3 para 2 respostas, mas a concorrente permanece mais recorrente. Niazi Chohfi e Altenburg tiveram crescimento relevante e devem entrar no benchmark secundário.

---

## Comparação com o ciclo anterior — mesma plataforma, mesmos prompts e duas rodadas

| Ciclo | R1 | R2 | Total de menções | Taxa consolidada |
|---|---:|---:|---:|---:|
| 21/09/2026 | 6/15 (40,0%) | 10/15 (66,7%) | 16/30 | 53,3% |
| **05/10/2026** | **11/15 (73,3%)** | **8/15 (53,3%)** | **19/30** | **63,3%** |
| Variação | +33,3 pp | -13,3 pp | **+3** | **+10,0 pp** |

### Mudanças por intenção

- **Maior ganho:** P5 `enxoval para hotel` passou de 0/2 para 2/2.
- **Consolidação:** P6 e P13 passaram de 1/2 para 2/2.
- **Recuperação parcial:** P12 passou de 0/2 para 1/2.
- **Estáveis fortes:** P7, P8, P11 e P14 permaneceram em 2/2.
- **Estáveis oscilantes:** P1, P3, P4 e P10 permaneceram em 1/2.
- **Perdas:** P2 e P15 passaram de 1/2 para 0/2.
- **Lacuna persistente:** P9 permaneceu em 0/2.

O ganho consolidado de 10 pp é positivo e foi medido em duas rodadas completas, mas a diferença de 20 pp entre R1 e R2 continua mostrando variância relevante. A leitura correta é **avanço semanal confirmado na amostra**, ainda não uma tendência estrutural de longo prazo.

---

## Precisão e riscos de conteúdo

- **Taxa de precisão factual:** não calculada, pois as 30 respostas não foram verificadas afirmação por afirmação contra fontes independentes.
- O Gemini atribuiu à Conamore características como personalização, RFID, desempenho em lavanderia industrial, reputação “Boa” e relatos específicos de composição/atraso. Essas afirmações precisam de validação interna antes de qualquer reaproveitamento comercial.
- A afirmação “há mais de 15 anos” é compatível com a fundação da Conamore em 2003, mas é imprecisa e poderia ser atualizada para uma formulação mais forte e verificável no site.
- O prompt P14 continua vulnerável a conteúdo reputacional de terceiros. A página institucional direta foi citada, mas o Reclame Aqui também influenciou a resposta.

---

## Leitura executiva e próximas ações

1. **Defender P5/P6/P7/P8/P11/P13/P14:** manter e aprofundar conteúdo sobre enxoval completo, compra, fornecedor, pronta entrega, pousadas e credibilidade institucional.
2. **Prioridade máxima P9:** “fornecedor de enxoval hoteleiro em São Paulo” segue 0/2 por mais um ciclo. Reforçar Campinas/SP, atendimento estadual, logística regional e pronta entrega em páginas B2B, headings, FAQs e dados estruturados.
3. **Recuperar P2:** produzir conteúdo comparativo sobre “melhor lençol para hotel”, com critérios verificáveis: composição, fios, lavagem industrial, durabilidade, custo por uso e categoria do empreendimento.
4. **Recuperar P15:** fortalecer a entidade genérica “empresa de enxoval para hotelaria” em título, H1, texto institucional e links internos.
5. **Consolidar P12:** a comparação de fornecedores voltou em 1/2. Criar guia de decisão neutro e técnico para hotéis e pousadas, sem alegações não comprovadas sobre concorrentes.
6. **Aumentar citação de página comercial:** a URL direta confirmada foi `/quem-somos`, enquanto `/lencol-para-hotelaria` não apareceu na auditoria deste ciclo. Melhorar clareza, FAQs, links internos e dados estruturados da landing page prioritária.
7. **Validar alegações do Gemini:** conferir internamente personalização, RFID e demais diferenciais antes de reforçá-los no conteúdo. Se forem reais, documentá-los em páginas oficiais; se não forem, corrigir sinais ambíguos.
8. **Benchmark competitivo:** ParaHotel continua líder e Niazi Chohfi/Altenburg cresceram. Mapear cobertura semântica e páginas citadas nos prompts P2, P9 e P15.

---

## Status final

| Executado | Evidência | Status |
|---|---|---|
| Gemini R1 | 15/15 respostas; 11 menções (73,3%) | ✅ Completo |
| Gemini R2 | 15/15 respostas; 8 menções (53,3%) | ✅ Completo |
| Consolidado | 30/30 respostas; 19 menções (63,3%) | ✅ Confirmado |
| Concorrência | ParaHotel 21/30; demais marcas monitoradas contabilizadas | ✅ Concluído |
| URLs | `/quem-somos` confirmada diretamente em auditoria suplementar | ✅ Confirmado em amostra |
| Comparação histórica | 53,3% → 63,3% vs 21/09 | ✅ Comparável |
| Relatório Obsidian | `Agentes/Flávia/SEO - Visibilidade IA - 2026-10-05.md` | ✅ Salvo |

**Status analítico:** **CONFIRMADO — ciclo completo.** A Conamore atingiu **63,3% de menção no painel Gemini**, alta de 10,0 pp frente ao ciclo anterior. A marca ganhou força em enxoval genérico, compra e pousadas, mas ainda não aparece para fornecedor em São Paulo, melhor lençol e empresa de enxoval para hotelaria.

*Relatório gerado por Flávia (Marketing) em 05/10/2026, 09:23 BRT.*
