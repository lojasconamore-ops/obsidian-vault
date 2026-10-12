# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 12/10/2026, 09:01–09:31 BRT
**Escopo executado:** Gemini direto, 15 prompts fixos × 2 rodadas = 30 submissões
**Fonte de evidência:** `Direct platform` — interface pública do Gemini (Flash-Lite), sem login
**Status:** **COMPLETO** — 30/30 prompts submetidos e 30/30 respostas observadas (0 erros).

---

## Metodologia e limitações

- Cada prompt foi submetido individualmente em conversa nova (reset via botão "New chat"), evitando contaminação.
- Menção foi medida no trecho da resposta (após o marcador "Gemini said"), **excluindo o eco do prompt do usuário** e com detecção case-insensitive de `conamore`. Inclui rótulos de fonte exibidos dentro da resposta (mesma metodologia do ciclo anterior).
- Distinção entre **menção textual/inclusão comercial** (Conamore descrita como empresa/fornecedora/opção) e **menção apenas como fonte citada** (chip "Hotelaria BLOG CONAMORE" sem prosa sobre a marca).
- Recomendação comercial classificada de forma conservadora: conta só quando a Conamore aparece como empresa, fornecedora ou opção de compra, não quando surge só como rótulo de fonte.
- Somente o Gemini foi testado. ChatGPT, Perplexity e Copilot ficaram fora deste ciclo por prioridade e orçamento operacional.
- O Gemini é estocástico: duas rodadas permitem comparação semanal, mas a diferença entre rodadas continua alta (20 pp neste ciclo).

---

## Resumo executivo

A Conamore apareceu em **17/30 respostas (56,7%)**: **7/15 na R1 (46,7%)** e **10/15 na R2 (66,7%)**. Frente ao último ciclo completo comparável (05/10/2026), houve recuo de **19/30 (63,3%) para 17/30 (56,7%)** — **−2 menções e −6,6 pontos percentuais**.

Sete intenções ficaram estáveis em **2/2**: **P5 enxoval genérico, P6 onde comprar, P7 fornecedor, P8 pronta entrega, P10 enxoval profissional, P12 comparação e P14 branded**. Cinco ficaram cegas em **0/2**: **P1 lençol para hotel, P3 pousada profissional, P4 Airbnb, P9 fornecedor em São Paulo e P13 roupa de cama para pousadas**.

A queda concentrou-se no **grupo Produto (P1, P3, P4, que saíram de 1/2 para 0/2)** e em **P13 (pousadas), que despencou de 2/2 para 0/2** — a perda mais relevante do ciclo. Em compensação, **P2 (melhor lençol) e P15 (empresa de enxoval para hotelaria)** recuperaram menção (0→1) e **P10 e P12** consolidaram em 2/2.

---

## Disponibilidade da plataforma

| Plataforma | Planejado | Testado | Status | Evidência |
|---|---:|---:|---|---|
| Gemini direto | 30 | 30/30 | `tested` | 2 rodadas completas; conversa nova por prompt; respostas geradas sem login |
| ChatGPT | 0 | 0 | `not run` | Fora do escopo prioritário deste ciclo |
| Perplexity | 0 | 0 | `not run` | Fora do escopo prioritário deste ciclo |
| Copilot | 0 | 0 | `not run` | Fora do escopo prioritário deste ciclo |

> **Nota de acessibilidade:** o Gemini voltou a responder **sem login** neste ciclo (Flash-Lite gera resposta completa), contradizendo a matriz de acessibilidade datada de 17/08 (que registrava "login required"). A matriz foi atualizada.

---

## Métricas

| Métrica | R1 | R2 | Consolidado |
|---|---:|---:|---:|
| Prompts testados | 15/15 | 15/15 | **30/30** |
| Menção total (texto + fonte) | 7/15 (46,7%) | 10/15 (66,7%) | **17/30 (56,7%)** |
| Inclusão comercial explícita | 6/15 (40,0%) | 8/15 (53,3%) | **14/30 (46,7%)** |
| Menção apenas como fonte citada | 1/15 | 2/15 | **3/30 (10,0%)** |
| Citação de fonte Conamore | 2/15 (13,3%) | 4/15 (26,7%) | **6/30 (20,0%)** |
| Prompts estáveis positivos (2/2) | — | — | **7/15 (46,7%)** |
| Prompts oscilantes (1/2) | — | — | **3/15 (20,0%)** |
| Prompts cegos (0/2) | — | — | **5/15 (33,3%)** |

### Resultado por grupo de intenção

| Grupo | Menções | Taxa |
|---|---:|---:|
| Produto — P1 a P5 | 3/10 | 30,0% |
| Compra/Fornecedor — P6 a P10 | 8/10 | 80,0% |
| Comparação/Marca — P11 a P15 | 6/10 | 60,0% |

**Leitura:** a associação comercial da Conamore continua mais forte em compra/fornecedor (80%) e comparação/marca (60%). O grupo Produto caiu para 30% — a marca quase não é associada a buscas de produto genérico, exceto enxoval (P5).

---

## Matriz prompt × rodada

| # | Prompt exato | R1 | R2 | Consolidação |
|---:|---|:---:|:---:|:---:|
| 1 | `lençol para hotel` | ❌ | ❌ | **0/2** |
| 2 | `qual o melhor lençol para hotel` | ❌ | ✅ | 1/2 |
| 3 | `lençol profissional para pousada` | ❌ | ❌ | **0/2** |
| 4 | `lençol para Airbnb` | ❌ | ❌ | **0/2** |
| 5 | `enxoval para hotel` | ✅ | ✅ | **2/2** |
| 6 | `onde comprar lençol para hotel` | ✅ | ✅ | **2/2** |
| 7 | `fornecedor de lençol para hotéis` | ✅ | ✅ | **2/2** |
| 8 | `lençol para hotel com pronta entrega` | ✅ | ✅ | **2/2** |
| 9 | `fornecedor de enxoval hoteleiro em São Paulo` | ❌ | ❌ | **0/2** |
| 10 | `onde comprar enxoval profissional para hotel` | ✅ | ✅ | **2/2** |
| 11 | `quais empresas vendem lençol para hotel no Brasil` | ❌ | ✅ | 1/2 |
| 12 | `compare fornecedores de enxoval para hotéis` | ✅ | ✅ | **2/2** |
| 13 | `qual empresa fornece roupa de cama para pousadas` | ❌ | ❌ | **0/2** |
| 14 | `Conamore é uma boa empresa para enxoval hoteleiro?` | ✅ | ✅ | **2/2** |
| 15 | `empresa de enxoval para hotelaria` | ❌ | ✅ | 1/2 |

**Reconciliação:** esperado 30; submetido 30; respostas/evidências válidas 30; não executado 0.

---

## Evidências representativas

### R1P6 — onde comprar

> “Conamore Hotelaria: Especializada em moda de cama e banho para hotéis, pousadas e Airbnb. Vende tanto em grandes volumes quanto em pequenas quantidades à pronta-entrega.”

### R1P7 — fornecedor

> “🏢 Principais Fornecedores e Fabricantes — Conamore Enxovais: Especialidade: Linha completa de cama, mesa e banho para hotelaria, pousadas e Airbnb. Destaque: Pronta entrega e var…”.

### R2P8 — pronta entrega

> “Conamore Cama, Mesa e Banho: Especializada em hotelaria e Airbnb, oferece enxovais brancos para os tamanhos Solteiro, Casal, Queen e King à pronta entrega e sem exigência de pedido mínimo alto.”

### R1/R2P14 — intenção de marca

Nas duas rodadas o Gemini avaliou a Conamore positivamente. Exemplo (R2):

> “Sim, a Conamore é considerada uma boa empresa e uma opção bastante consolidada para enxoval hoteleiro. Ela atende hotéis, pousadas, imóveis de temporada (Airbnb) e redes hospitalares há vários anos.”

A resposta cita o **Reclame Aqui** (“Reputação Boa, nota média em torno de 7,8/10”, “mais de 15 anos”) e o vídeo institucional **Conamore Hotelaria | Da produção à entrega** (YouTube, ~35K views) como fontes.

**Nota de precisão:** alegações como “consolidada”, “há vários anos”, “reputação boa (7,8/10)” e “mais de 15 anos” foram geradas sem indicador datado no texto. Não devem ser reutilizadas em comunicação comercial sem validação atual.

---

## URLs e camada de fonte

| Evidência | Fonte observada | Classificação |
|---|---|---|
| P14 (rodadas 1 e 2) | `Hotelaria BLOG CONAMORE` (chip de fonte) | Intermediário — blog `hotelaria.conamore.com.br` |
| P14 (rodadas 1 e 2) | `Reclame AQUI` | Terceiro — reputacional |
| P14 (rodada suplementar) | YouTube — vídeo institucional "Da produção à entrega" | Intermediário — canal Conamore |
| R1P6/P7, R2P6/P8/P10 | chips `Conamore Hotelaria` / `Conamore Cama, Mesa e Banho` | Fonte Conamore (não auditada por URL clicável) |

**Citação de domínio:** não foi aberta URL clicável do domínio principal `www.conamore.com.br` neste ciclo. A fonte Conamore observada em P14 foi o **blog** (`hotelaria.conamore.com.br`), reforçando o padrão de **indexação indireta via blog/conteúdo** — não a landing page comercial `/lencol-para-hotelaria`, que segue **não confirmada** como fonte citada.

---

## Concorrentes citados

Contagem de respostas em que cada marca monitorada apareceu, sobre 30 respostas:

| Marca | Respostas | Taxa | Observação |
|---|---:|---:|---|
| **Profitel (Blog - Profitel)** | **24/30** | **80,0%** | **Novo líder** — não estava no painel do ciclo anterior |
| **ParaHotel** | **17/30** | **56,7%** | −4 vs 05/10 (era 21/30 = 70%) |
| **Conamore** | **17/30** | **56,7%** | −2 vs 05/10 (era 19/30 = 63,3%) |
| Servhotel | 14/30 | 46,7% | não monitorado antes |
| Teka | 12/30 | 40,0% | +9 vs 05/10 |
| Altenburg | 9/30 | 30,0% | +5 |
| Proficione | 9/30 | 30,0% | novo no painel |
| Buddemeyer | 7/30 | 23,3% | +5 |
| Niazi Chohfi | 4/30 | 13,3% | −3 |
| Sabanalia | 2/30 | 6,7% | novo |
| Karsten | 2/30 | 6,7% | = |
| Santista | 2/30 | 6,7% | +1 |
| Trussardi / Dohler / Zelo | 1/30 cada | 3,3% | marginais |

**Leitura crítica:** o **Blog Profitel (Profitel)** tornou-se a fonte mais citada pelo Gemini em hotelaria (80%), ultrapassando todos os fabricantes/distribuidores. Isso indica que o Gemini passou a priorizar **conteúdo editorial/de blog** como fonte de autoridade tópica — exatamente o tipo de conteúdo que a Conamore precisa competir (o próprio blog da Conamore é citado como fonte, mas com frequência baixa: 6/30).

---

## Comparação com o ciclo anterior — mesma plataforma, mesmos prompts e duas rodadas

| Ciclo | R1 | R2 | Total de menções | Taxa consolidada |
|---|---:|---:|---:|---:|
| 05/10/2026 | 11/15 (73,3%) | 8/15 (53,3%) | 19/30 | 63,3% |
| **12/10/2026** | **7/15 (46,7%)** | **10/15 (66,7%)** | **17/30** | **56,7%** |
| Variação | −26,7 pp | +13,3 pp | **−2** | **−6,6 pp** |

### Mudanças por intenção

- **Perda mais relevante:** P13 `roupa de cama para pousadas` caiu de 2/2 para 0/2.
- **Perdas no grupo Produto:** P1, P3 e P4 caíram de 1/2 para 0/2.
- **Perda parcial:** P11 caiu de 2/2 para 1/2.
- **Recuperações:** P2 e P15 saíram de 0/2 para 1/2; P10 e P12 consolidaram de 1/2 para 2/2.
- **Estáveis fortes:** P5, P6, P7, P8 e P14 permaneceram em 2/2.
- **Lacuna persistente:** P9 permaneceu em 0/2 pelo quarto ciclo consecutivo.

O recuo de −6,6 pp foi medido em duas rodadas completas, mas a variância entre R1 (46,7%) e R2 (66,7%) continua de 20 pp. A leitura correta é **oscilação semanal dentro da faixa de variância esperada**, não uma tendência estrutural de queda. P13 e o grupo Produto merecem atenção específica no próximo ciclo.

---

## Precisão e riscos de conteúdo

- **Taxa de precisão factual:** não calculada (as 30 respostas não foram verificadas afirmação por afirmação).
- O Gemini atribuiu à Conamore características como "linha completa cama/mesa/banho", "pronta entrega sem pedido mínimo alto", "vendas corporativas/atacado" e reputação "Boa (7,8/10)". Devem ser validadas internamente antes de qualquer reaproveitamento comercial.
- O prompt P14 continua fortemente influenciado pelo **Reclame Aqui** (reputacional) e pelo vídeo institucional no YouTube — não por páginas comerciais próprias.
- A landing page prioritária `/lencol-para-hotelaria` segue **sem citação confirmada** como fonte.

---

## Leitura executiva e próximas ações

1. **Investigar queda de P13 (pousadas):** passou de 2/2 para 0/2. Reforçar conteúdo B2B para pousadas em títulos, headings, FAQs e dados estruturados; verificar se a concorrência (ParaHotel/Servhotel) publicou conteúdo novo sobre pousadas.
2. **Recuperar grupo Produto (P1, P3, P4):** criar páginas/FAQ específicas de produto (lençol para hotel, pousada, Airbnb) com especificações verificáveis, já que a associação de produto genérico praticamente sumiu (30%).
3. **Prioridade máxima P9:** "fornecedor de enxoval hoteleiro em São Paulo" segue 0/2 (4º ciclo). Reforçar Campinas/SP, atendimento estadual, logística regional e pronta entrega.
4. **Defender P5/P6/P7/P8/P10/P12/P14:** manter e aprofundar conteúdo de enxoval completo, compra, fornecedor, pronta entrega, comparação e credibilidade institucional.
5. **Ameaça competitiva — Blog Profitel:** o Gemini agora cita o Blog Profitel em 80% das respostas (autoridade de conteúdo editorial). Mapear a cobertura semântica do Profitel e intensificar a produção de conteúdo próprio no blog `hotelaria.conamore.com.br` para competir nessa camada de fonte.
6. **Converter citação indireta em citação de domínio:** a Conamore é citada via blog e Reclame Aqui, não via `www.conamore.com.br`. Melhorar clareza, FAQs, links internos e dados estruturados da landing page prioritária para atrair citação direta do domínio.
7. **Validar alegações do Gemini:** conferir internamente "pronta entrega sem pedido mínimo alto", "atacado/vendas corporativas" e reputação antes de reforçá-los no conteúdo.

---

## Status final

| Executado | Evidência | Status |
|---|---|---|
| Gemini R1 | 15/15 respostas; 7 menções (46,7%) | ✅ Completo |
| Gemini R2 | 15/15 respostas; 10 menções (66,7%) | ✅ Completo |
| Consolidado | 30/30 respostas; 17 menções (56,7%) | ✅ Confirmado |
| Inclusão comercial | 14/30 (46,7%) | ✅ Classificado |
| Citação de fonte Conamore | 6/30 (20%), via blog | ✅ Observado |
| Concorrência | Profitel 80% (novo líder); ParaHotel 56,7% | ✅ Concluído |
| Comparação histórica | 63,3% → 56,7% vs 05/10 | ✅ Comparável |
| Relatório Obsidian | `Agentes/Flávia/SEO - Visibilidade IA - 2026-10-12.md` | ✅ Salvo |

**Status analítico:** **CONFIRMADO — ciclo completo.** A Conamore atingiu **56,7% de menção no painel Gemini** (−6,6 pp vs 05/10), dentro da faixa de variância semanal. A marca manteve força em compra/fornecedor e branded, mas perdeu associação em pousadas (P13) e no grupo Produto. Alerta competitivo: o **Blog Profitel tornou-se a fonte mais citada pelo Gemini (80%)**.

*Relatório gerado por Flávia (Marketing) em 12/10/2026, 09:31 BRT.*
