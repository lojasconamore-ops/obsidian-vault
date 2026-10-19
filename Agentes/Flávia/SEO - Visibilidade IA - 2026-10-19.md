# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 19/10/2026, 09:17–09:31 BRT
**Escopo executado:** Gemini direto, 15 prompts fixos × 2 rodadas = 30 submissões
**Fonte de evidência:** `Direct platform` — interface pública do Gemini (Flash-Lite), sem login
**Status:** **COMPLETO** — 30/30 prompts submetidos e 30/30 respostas observadas (0 erros, 0 timeouts).

---

## Metodologia e limitações

- Cada prompt foi submetido individualmente em conversa nova (via botão "New chat", com confirmação do diálogo "Clear current chat"), evitando contaminação entre respostas.
- Menção foi medida no trecho da resposta após o marcador `Gemini said`, **excluindo o eco do prompt do usuário**, com detecção case-insensitive de `conamore`. Inclui rótulos/chips de fonte exibidos dentro da resposta (mesma metodologia do ciclo de 12/10).
- Respostas foram lidas somente após estabilização do texto (dois reads consecutivos idênticos), evitando captura de stream parcial.
- Recomendação comercial classificada de forma conservadora: conta quando a Conamore aparece como empresa/fornecedora/opção, não apenas como rótulo de fonte.
- Somente o Gemini foi testado. ChatGPT, Perplexity e Copilot ficaram fora deste ciclo por prioridade e orçamento operacional.
- O Gemini é estocástico; duas rodadas reduzem, mas não eliminam, a variância. Neste ciclo a variância entre rodadas foi **baixa (6,7 pp)**, o que aumenta a confiança no nível medido.

---

## Resumo executivo

A Conamore apareceu em **11/30 respostas (36,7%)**: **5/15 na R1 (33,3%)** e **6/15 na R2 (40,0%)**. Frente ao ciclo completo imediatamente anterior (12/10/2026), houve queda de **17/30 (56,7%) para 11/30 (36,7%)** — **−6 menções e −20,0 pontos percentuais**, sustentada nas duas rodadas.

**A queda concentrou-se inteiramente no grupo Compra/Fornecedor (P6–P10), que zerou: de 8/10 (80%) em 12/10 para 0/10 (0%) agora.** Os territórios historicamente mais fortes da Conamore — **P7 "fornecedor de lençol para hotéis"**, **P8 "pronta entrega"**, **P6 "onde comprar"** e **P10 "onde comprar enxoval profissional"** — todos saíram de 2/2 estáveis para **0/2**.

Em compensação, o grupo **Comparação/Marca (P11–P15)** permaneceu sólido em **9/10 (90%)**, com **P11, P12, P13 e P14 estáveis em 2/2** e **P15 em 1/2**. **P1 ("lençol para hotel")** recuperou para 2/2, mas via chip **"Hotelaria BLOG CONAMORE"** — indexação indireta pelo blog, não pelo domínio comercial.

A queda não é exclusiva da Conamore: **Profitel caiu de 24/30 para 11/30** e **ParaHotel de 17/30 para 6/30**. O modelo migrou de citar *especialistas em hotelaria* (Conamore, ParaHotel, Profitel, ServHotel) para citar *marcas têxteis tradicionais* (Karsten +6, Santista +5, Altenburg, Buddemeyer) em consultas de produto/compra.

---

## Disponibilidade da plataforma

| Plataforma | Planejado | Testado | Status | Evidência |
|---|---:|---:|---|---|
| Gemini direto | 30 | 30/30 | `tested` | 2 rodadas completas; conversa nova por prompt; respostas geradas sem login (Flash-Lite) |
| ChatGPT | 0 | 0 | `not run` | Fora do escopo prioritário deste ciclo |
| Perplexity | 0 | 0 | `not run` | Fora do escopo prioritário deste ciclo |
| Copilot | 0 | 0 | `not run` | Fora do escopo prioritário deste ciclo |

> **Nota de acessibilidade:** o Gemini respondeu **sem login** neste ciclo (Flash-Lite gera resposta completa), consistente com a matriz de acessibilidade atualizada. Observou-se, porém, **busca na web intermitente** — algumas respostas declararam "não posso realizar buscas na internet no momento" (ex.: P8 na R1), retornando conteúdo genérico sem citações.

---

## Métricas

| Métrica | R1 | R2 | Consolidado |
|---|---:|---:|---:|
| Prompts testados | 15/15 | 15/15 | **30/30** |
| Menção textual Conamore | 5/15 (33,3%) | 6/15 (40,0%) | **11/30 (36,7%)** |
| Prompts estáveis positivos (2/2) | — | — | **5/15 (33,3%)** |
| Prompts oscilantes (1/2) | — | — | **1/15 (6,7%)** |
| Prompts cegos (0/2) | — | — | **9/15 (60,0%)** |
| URL clicável do domínio `www.conamore.com.br` | 0/15 | 0/15 | **0/30 (0%)** |

### Resultado por grupo de intenção

| Grupo | Menções | Taxa | Variação vs 12/10 |
|---|---:|---:|---:|
| Produto — P1 a P5 | 2/10 | 20,0% | −10,0 pp (era 30%) |
| Compra/Fornecedor — P6 a P10 | 0/10 | **0,0%** | **−80,0 pp (era 80%)** |
| Comparação/Marca — P11 a P15 | 9/10 | 90,0% | +30,0 pp (era 60%) |

**Leitura:** a associação comercial da Conamore praticamente desapareceu em compra/fornecedor e consolidou-se em listas/comparação/intenção de marca. É a primeira vez, em todo o histórico monitorado, que o grupo de compra zera.

---

## Matriz prompt × rodada

| # | Prompt exato | R1 | R2 | Consolidação |
|---:|---|:---:|:---:|:---:|
| 1 | `lençol para hotel` | ✅ | ✅ | **2/2** |
| 2 | `qual o melhor lençol para hotel` | ❌ | ❌ | 0/2 |
| 3 | `lençol profissional para pousada` | ❌ | ❌ | 0/2 |
| 4 | `lençol para Airbnb` | ❌ | ❌ | 0/2 |
| 5 | `enxoval para hotel` | ❌ | ❌ | 0/2 |
| 6 | `onde comprar lençol para hotel` | ❌ | ❌ | **0/2** |
| 7 | `fornecedor de lençol para hotéis` | ❌ | ❌ | **0/2** |
| 8 | `lençol para hotel com pronta entrega` | ❌ | ❌ | **0/2** |
| 9 | `fornecedor de enxoval hoteleiro em São Paulo` | ❌ | ❌ | 0/2 |
| 10 | `onde comprar enxoval profissional para hotel` | ❌ | ❌ | **0/2** |
| 11 | `quais empresas vendem lençol para hotel no Brasil` | ✅ | ✅ | **2/2** |
| 12 | `compare fornecedores de enxoval para hotéis` | ✅ | ✅ | **2/2** |
| 13 | `qual empresa fornece roupa de cama para pousadas` | ✅ | ✅ | **2/2** |
| 14 | `Conamore é uma boa empresa para enxoval hoteleiro?` | ✅ | ✅ | **2/2** |
| 15 | `empresa de enxoval para hotelaria` | ❌ | ✅ | 1/2 |

**Reconciliação:** esperado 30; submetido 30; respostas/evidências válidas 30; não executado 0.

---

## Evidências representativas

### R1P11 — lista de empresas (menção)

> "Conamore: Empresa muito conhecida no s[egmento]…"

### R2P11 — lista de empresas (menção)

> "Conamore: Focada em enxovais para [hotelaria, pousadas e Airbnbs]…"

### R1/R2P14 — intenção de marca (menção, nas duas rodadas)

> "A Conamore (registrada como Conamore Cama, Mesa e Banho) é uma empresa bastante conhecida no mercado brasileiro e especializada no fornecimento de enxoval profissional para hotelaria, pousadas, motéis e anfitriões de Airbnb." (R1)

> "Sim, a Conamore é considerada uma boa empresa e uma opção confiável no mercado de enxovais, com forte atuação voltada tanto para o consumidor final quanto para o segmento profissional… Boa avaliação no Re[clame Aqui]." (R2)

### Contraste — P7 fornecedor (R2, SEM menção à Conamore)

> "1. Fabricantes e Especialistas em Hotelaria (Venda Direta / Atacado) — Proficione Enxovais… Fábrica tradicional de enxovais profissionais para hot[éis]…"

### Contraste — P8 pronta entrega (R1, busca web desligada)

> "Como não posso realizar buscas na internet no momento, recomendo que você entre em contato direto com fornecedores especializados em enxoval hoteleiro (hotelaria) que possuem estoque nacional."

**Nota de precisão:** expressões reputacionais em P14 ("bastante conhecida", "opção confiável", "Boa avaliação no Reclame Aqui") foram geradas sem indicador quantitativo datado. Não devem ser reproduzidas em comunicação comercial sem validação atual.

---

## URLs e camada de fonte

Nenhuma URL clicável do domínio `www.conamore.com.br` foi capturada em nenhuma das 30 respostas. A presença da Conamore neste ciclo deu-se por:

| Evidência | Fonte observada | Classificação |
|---|---|---|
| P1 (R1) | chip `Hotelaria BLOG CONAMORE` | Indireta — blog `hotelaria.conamore.com.br` |
| P14 (R1/R2) | chip `Reclame AQUI` | Terceiro — reputacional |
| P11/P12/P13/P15 | menção em prosa (lista/comparação) | Texto gerado, sem URL exposta |

A landing page prioritária **`/lencol-para-hotelaria` segue sem citação confirmada** como fonte em qualquer rodada.

---

## Concorrentes citados

Contagem de respostas em que cada marca monitorada apareceu, sobre 30 respostas:

| Marca | Respostas | Taxa | Variação vs 12/10 |
|---|---:|---:|---:|
| **Profitel** | 11/30 | 36,7% | **−13** (era 24/30 = 80%) |
| **Altenburg** | 11/30 | 36,7% | +2 |
| **Conamore** | 11/30 | 36,7% | **−6** (era 17/30 = 56,7%) |
| Proficione | 10/30 | 33,3% | +1 |
| Teka | 10/30 | 33,3% | −2 |
| ServHotel | 9/30 | 30,0% | −5 |
| Buddemeyer | 9/30 | 30,0% | +2 |
| Karsten | 8/30 | 26,7% | **+6** |
| Santista | 7/30 | 23,3% | **+5** |
| ParaHotel | 6/30 | 20,0% | **−11** (era 17/30) |
| Artex | 5/30 | 16,7% | novo no painel |
| Zelo | 4/30 | 13,3% | +3 |
| Buettner | 2/30 | 6,7% | — |
| OnixProtel | 2/30 | 6,7% | — |
| Niazi Chohfi | 2/30 | 6,7% | −2 |
| Sabanalia / MMartan / Lepine | 1/30 cada | 3,3% | marginais |

**Leitura crítica:** a queda da Conamore é parte de um movimento mais amplo — o Gemini deixou de priorizar os *especialistas em hotelaria* (Profitel blog, ParaHotel, Conamore, ServHotel) e passou a citar *marcas têxteis tradicionais* (Karsten, Santista, Altenburg, Buddemeyer) em consultas de produto/compra. Conamore, ParaHotel e Profitel caíram juntos; a marca ainda resiste apenas em listas/comparação/branded.

---

## Comparação com o ciclo anterior — mesma plataforma, mesmos prompts, duas rodadas

| Ciclo | R1 | R2 | Total de menções | Taxa consolidada |
|---|---:|---:|---:|---:|
| 12/10/2026 | 7/15 (46,7%) | 10/15 (66,7%) | 17/30 | 56,7% |
| **19/10/2026** | **5/15 (33,3%)** | **6/15 (40,0%)** | **11/30** | **36,7%** |
| Variação | −13,3 pp | −26,7 pp | **−6** | **−20,0 pp** |

### Mudanças por intenção

- **Perda crítica — grupo Compra/Fornecedor zerou:** P6, P7, P8 e P10 saíram de 2/2 para 0/2. P7 (fornecedor) e P8 (pronta entrega) eram estáveis 2/2 desde o início do monitoramento.
- **Perda no grupo Produto:** P5 ("enxoval para hotel") caiu de 2/2 para 0/2.
- **Recuperações:** P1 ("lençol para hotel") subiu de 0/2 para 2/2 (via blog, indireto); P13 ("pousadas") recuperou de 0/2 para 2/2.
- **Estáveis fortes:** P11, P12, P13 e P14 permaneceram em 2/2; P15 em 1/2.
- **Lacuna persistente:** P9 ("fornecedor em São Paulo") segue 0/2 (5º ciclo).

A queda de −20,0 pp foi medida em **duas rodadas completas e consistentes** (R1 33,3% e R2 40,0%, ambas bem abaixo do ciclo anterior), com variância entre rodadas de apenas 6,7 pp. **Não é ruído de rodada única** — merece investigação.

---

## Precisão e riscos de conteúdo

- O Gemini atribuiu à Conamore características como "especializada em hotelaria/pousadas/Airbnb", "enxovais para cama/banho", "pronta entrega" e reputação "boa/confiável". Devem ser validadas internamente antes de reaproveitamento comercial.
- O prompt P14 continua fortemente influenciado por **Reclame Aqui** (reputacional) — não por páginas comerciais próprias.
- **Busca web intermitente no Flash-Lite:** parte da queda no grupo de compra decorre de respostas sem busca web (sem citação de marca). Não confundir ausência de citação com queda de indexação do domínio — os dois fatores coexistem neste ciclo.
- A landing page prioritária `/lencol-para-hotelaria` segue **sem citação confirmada**.

---

## Leitura executiva e próximas ações

1. **Prioridade crítica — recuperar grupo Compra/Fornecedor (P6–P10):** zerou após ser o território mais forte (80% em 12/10). Reforçar a associação da Conamore a atributos de compra — **fornecedor, pronta entrega, onde comprar, pedido mínimo** — em títulos, headings, FAQs, dados estruturados e no blog.
2. **Defender "pronta entrega" (P8):** era o diferencial mais citado da Conamore e sumiu (R1 inclusive sem busca web). Tornar "pronta entrega" atributo inequívoco e verificável em toda página comercial.
3. **Mapear Proficione e ServHotel:** passaram a ocupar o espaço de "fornecedor/fabricante" que antes era da Conamore/ParaHotel. Auditar cobertura semântica e páginas citadas.
4. **Concorrer com marcas têxteis tradicionais:** Karsten (+6) e Santista (+5) cresceram. Garantir que o conteúdo da Conamore explicite *por que* um fornecedor especialista em hotelaria supera o varejo tradicional (durabilidade industrial, pronta entrega, atendimento B2B).
5. **Manter grupo Comparação/Marca (P11–P15):** 90%, estável — é hoje o pilar de visibilidade. Aprofundar conteúdo comparativo e de listas.
6. **Converter indexação indireta em citação de domínio:** P1 voltou via chip "Hotelaria BLOG CONAMORE". Direcionar autoridade do blog para `www.conamore.com.br` e a landing `/lencol-para-hotelaria`, que segue sem citação.
7. **Monitorar próxima rodada:** confirmar se o colapso do grupo de compra persiste (2ª medição) ou reverte. Uma queda estrutural em compra/fornecedor exige ação imediata de conteúdo.

---

## Status final

| Executado | Evidência | Status |
|---|---|---|
| Gemini R1 | 15/15 respostas; 5 menções (33,3%) | ✅ Completo |
| Gemini R2 | 15/15 respostas; 6 menções (40,0%) | ✅ Completo |
| Consolidado | 30/30 respostas; 11 menções (36,7%) | ✅ Confirmado |
| Concorrência | Profitel/Altenburg/Conamore 36,7%; Karsten/Santista em alta | ✅ Concluído |
| URLs | Nenhuma URL clicável do domínio principal capturada | ✅ Observado |
| Comparação histórica | 56,7% → 36,7% vs 12/10 (−20,0 pp) | ✅ Comparável (2 rodadas) |
| Relatório Obsidian | `Agentes/Flávia/SEO - Visibilidade IA - 2026-10-19.md` | ✅ Salvo |

**Status analítico:** **CONFIRMADO — ciclo completo.** A Conamore atingiu **36,7% de menção no painel Gemini** (−20,0 pp vs 12/10), a maior queda já registrada no monitoramento, sustentada nas duas rodadas. A marca zerou no grupo Compra/Fornecedor (P6–P10) — incluindo os antes estáveis "fornecedor" e "pronta entrega" — mas manteve 90% em listas/comparação/branded. A queda é parte de um giro do modelo em direção a marcas têxteis tradicionais, somado a busca web intermitente no Flash-Lite.

*Relatório gerado por Flávia (Marketing) em 19/10/2026, 09:32 BRT.*
