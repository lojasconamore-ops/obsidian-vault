# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 14/09/2026, 09:01–09:17 BRT  
**Escopo planejado e executado:** Gemini direto, 15 prompts fixos × 2 rodadas = 30 submissões  
**Fonte de evidência:** `Direct platform` — interface pública do Gemini 3.5 Flash-Lite, sem login  
**Status:** **COMPLETO** — 30/30 prompts submetidos e 30/30 respostas observadas.

---

## Limitações metodológicas

- O Gemini é estocástico; duas rodadas reduzem, mas não eliminam, a variância.
- Menção textual foi apurada somente no texto da resposta (`message-content`), evitando contar o prompt do usuário — especialmente importante em P14.
- As URLs de fonte não foram abertas em todas as 30 respostas. Foram feitas duas execuções suplementares, fora do denominador, para validar diretamente os detalhes das fontes de P6 e P14.
- ChatGPT, Perplexity e Copilot não foram testados neste ciclo e não entram nas métricas.

---

## Resumo executivo

A Conamore apareceu em **15/30 respostas (50,0%)**: **9/15 na R1 (60,0%)** e **6/15 na R2 (40,0%)**. Em equivalência por painel, a média foi **7,5/15 prompts**, contra **6/15 (40,0%)** no último ciclo completo comparável, em 08/08/2026: **alta de 10,0 pontos percentuais e +3 menções em 30 respostas**.

O ganho é real dentro desta amostra de duas rodadas, mas a diferença entre R1 e R2 (20 pp) confirma alta variabilidade. Cinco intenções ficaram estáveis em 2/2 execuções: **P6 onde comprar, P7 fornecedor, P8 pronta entrega, P11 empresas no Brasil e P14 branded**. Cinco ficaram cegas em 0/2: **P2 melhor lençol, P3 pousada, P5 enxoval genérico, P9 fornecedor em São Paulo e P13 roupa de cama para pousadas**.

A **ParaHotel** foi o concorrente mais recorrente, presente em **19/30 respostas (63,3%)**, acima da Conamore em presença textual. No share of voice simples entre as marcas rastreadas, a Conamore teve **15 de 55 presenças (27,3%)**; ParaHotel, **19/55 (34,5%)**.

---

## Disponibilidade da plataforma

| Plataforma | Planejado | Testado | Status | Evidência |
|---|---:|---:|---|---|
| Gemini direto | 30 | 30/30 | `tested` | 2 rodadas completas; resposta isolada em nova conversa para cada prompt |
| ChatGPT | 0 | 0 | `not run` | Fora do escopo prioritário |
| Perplexity | 0 | 0 | `not run` | Fora do escopo prioritário |
| Copilot | 0 | 0 | `not run` | Fora do escopo prioritário |

---

## Métricas

| Métrica | R1 | R2 | Consolidado |
|---|---:|---:|---:|
| Prompts testados | 15/15 | 15/15 | 30/30 |
| Menção textual Conamore | 9/15 (60,0%) | 6/15 (40,0%) | **15/30 (50,0%)** |
| Prompts estáveis (2/2) | — | — | 5/15 (33,3%) |
| Prompts oscilantes (1/2) | — | — | 5/15 (33,3%) |
| Prompts cegos (0/2) | — | — | 5/15 (33,3%) |
| Recomendação/inclusão comercial explícita | 8/15 | 5/15 | **13/30 (43,3%)** |
| Citação de domínio Conamore | não auditada em todas | não auditada em todas | amostra suplementar: 2/2 verificadas |

**Critério de recomendação/inclusão comercial:** Conamore apresentada como fornecedor/opção de compra ou avaliada positivamente. R1P4 e R2P1 foram menções/citações contextuais, não recomendações comerciais claras.

---

## Matriz prompt × rodada

| # | Prompt exato | R1 | R2 | Consolidação |
|---:|---|:---:|:---:|:---:|
| 1 | `lençol para hotel` | ❌ | ✅ | 1/2 |
| 2 | `qual o melhor lençol para hotel` | ❌ | ❌ | 0/2 |
| 3 | `lençol profissional para pousada` | ❌ | ❌ | 0/2 |
| 4 | `lençol para Airbnb` | ✅ | ❌ | 1/2 |
| 5 | `enxoval para hotel` | ❌ | ❌ | 0/2 |
| 6 | `onde comprar lençol para hotel` | ✅ | ✅ | **2/2** |
| 7 | `fornecedor de lençol para hotéis` | ✅ | ✅ | **2/2** |
| 8 | `lençol para hotel com pronta entrega` | ✅ | ✅ | **2/2** |
| 9 | `fornecedor de enxoval hoteleiro em São Paulo` | ❌ | ❌ | 0/2 |
| 10 | `onde comprar enxoval profissional para hotel` | ✅ | ❌ | 1/2 |
| 11 | `quais empresas vendem lençol para hotel no Brasil` | ✅ | ✅ | **2/2** |
| 12 | `compare fornecedores de enxoval para hotéis` | ✅ | ❌ | 1/2 |
| 13 | `qual empresa fornece roupa de cama para pousadas` | ❌ | ❌ | 0/2 |
| 14 | `Conamore é uma boa empresa para enxoval hoteleiro?` | ✅ | ✅ | **2/2** |
| 15 | `empresa de enxoval para hotelaria` | ✅ | ❌ | 1/2 |

**Reconciliação:** esperado 30; submetido 30; respostas/evidências 30; não executado 0.

---

## Evidências representativas

### R1P6 — intenção de compra

> “Conamore (Cama, Mesa e Banho para Hotelaria): Especializada no setor, oferece linhas específicas como Confort [...] e opções 100% algodão [...] com pronta entrega e envio para todo o Brasil.”

### R2P11 — lista de fornecedores

> “Conamore: Especializada em enxovais para hotelaria e Airbnb, produz lençóis com diferentes quantidades de fios [...] e opções de tamanhos variados.”

### R1/R2 P14 — intenção de marca

Nas duas rodadas o Gemini respondeu afirmativamente. Exemplo:

> “Sim, a Conamore é considerada uma empresa confiável e bem avaliada no segmento de enxoval profissional para hotelaria, pousadas, flats e locações de temporada.”

**Nota de precisão:** a avaliação reputacional foi apresentada de modo genérico; qualquer uso comercial dessa afirmação deve ser validado contra métricas e período atual do Reclame Aqui.

---

## URLs citadas — validação direta suplementar

As duas verificações abaixo repetiram os prompts exatos após as 30 submissões planejadas, exclusivamente para abrir os detalhes das fontes. Não entram nas taxas do ciclo.

| Prompt | Fonte exibida no Gemini | URL real | Segmento |
|---|---|---|---|
| P6 `onde comprar lençol para hotel` | Conamore — “Lençóis para Hotelaria e Airbnb” | https://www.conamore.com.br/lencol-para-hotelaria | Hotelaria/B2B — **landing page prioritária confirmada** |
| P14 `Conamore é uma boa empresa para enxoval hoteleiro?` | Conamore — “Prazer, somos a Conamore” | https://www.conamore.com.br/quem-somos | Hotelaria/B2B institucional |
| P14 suplementar | Reclame Aqui — “Sobre Conamore” | https://www.reclameaqui.com.br/empresa/conamore/sobre/ | Intermediário/reputação; não é domínio Conamore |

Não foi observada citação indireta via Scribd nessas duas verificações.

---

## Concorrentes citados

Contagem de respostas em que cada marca apareceu, sobre 30 respostas:

| Marca | Respostas | Taxa |
|---|---:|---:|
| **ParaHotel** | **19/30** | **63,3%** |
| **Conamore** | **15/30** | **50,0%** |
| Teka | 6/30 | 20,0% |
| Altenburg | 5/30 | 16,7% |
| Niazi Chohfi | 3/30 | 10,0% |
| Buettner | 2/30 | 6,7% |
| Karsten | 2/30 | 6,7% |
| Buddemeyer | 1/30 | 3,3% |
| Santista | 1/30 | 3,3% |
| Artex | 1/30 | 3,3% |

**Leitura:** ParaHotel mantém vantagem ampla e recorrente, inclusive em prompts sem menção da Conamore. É o principal benchmark GEO/SEO deste painel.

---

## Comparação com o último ciclo completo comparável

Os ciclos de 31/08 e 07/09 tiveram 0/30 submissões por indisponibilidade do navegador e não são comparáveis. O comparável anterior é 08/08/2026, também Gemini direto, mesmos 15 prompts e duas rodadas.

| Ciclo | R1 | R2 | Total de menções | Taxa consolidada |
|---|---:|---:|---:|---:|
| 08/08/2026 | 5/15 (33,3%) | 7/15 (46,7%) | 12/30 | 40,0% |
| **14/09/2026** | **9/15 (60,0%)** | **6/15 (40,0%)** | **15/30** | **50,0%** |
| Variação | +26,7 pp | -6,7 pp | **+3** | **+10,0 pp** |

### Mudanças por intenção

- **Ganho consistente:** P7 e P8 passaram a 2/2; no ciclo anterior eram 1/2.
- **Novas aparições oscilantes:** P4, P10, P12 e P15 apareceram em 1/2; antes eram 0/2.
- **Perda:** P13 caiu de 2/2 para 0/2.
- **Enfraquecimento:** P1 caiu de 2/2 para 1/2.
- **Estáveis positivos:** P6, P11 e P14 permaneceram 2/2.
- **Estáveis cegos:** P2, P3, P5 e P9 permaneceram 0/2.

A melhora consolidada é positiva, mas ainda não deve ser chamada de tendência sustentada sem confirmação no próximo ciclo completo.

---

## Leitura executiva e ações

1. **Defender P6/P7/P8/P11:** o Gemini associa a Conamore a compra, fornecedor e pronta entrega. Manter essas proposições claramente estruturadas na landing page `/lencol-para-hotelaria` e em FAQs.
2. **Prioridade máxima P9:** “fornecedor de enxoval hoteleiro em São Paulo” ficou 0/2, apesar da presença física/operacional em Campinas-SP. Criar/reforçar conteúdo B2B com São Paulo, Campinas, atendimento regional e entrega.
3. **Recuperar pousadas:** P3 e P13 ficaram 0/2; P13 caiu de 2/2. Reforçar páginas e FAQs específicas para pousadas, com durabilidade, pedido mínimo, pronta entrega e consultoria.
4. **Atacar P2/P5:** conteúdo comparativo sobre “melhor lençol para hotel” e guia completo de enxoval pode ampliar autoridade no topo/meio do funil.
5. **Benchmark ParaHotel:** mapear estrutura, FAQs e entidades citáveis da ParaHotel nos prompts cegos, sem copiar conteúdo.
6. **Garantir precisão reputacional:** manter página institucional atualizada e evitar reproduzir a alegação genérica de “bem avaliada” sem data/indicador verificável.

---

## Status final

| Executado | Evidência | Status |
|---|---|---|
| Gemini R1 | 15/15 respostas; 9 menções (60,0%) | ✅ Completo |
| Gemini R2 | 15/15 respostas; 6 menções (40,0%) | ✅ Completo |
| Consolidado | 30/30 respostas; 15 menções (50,0%) | ✅ Confirmado |
| URLs Conamore | 2 detalhes de fonte abertos; `/lencol-para-hotelaria` e `/quem-somos` | ✅ Confirmadas em amostra suplementar |
| Comparação histórica | Mesmo painel/plataforma vs 08/08: +10,0 pp | ✅ Comparável |
| Relatório Obsidian | `Agentes/Flávia/SEO - Visibilidade IA - 2026-09-14.md` | ✅ Salvo |

**Status analítico:** **CONFIRMADO — ciclo completo.** A Conamore alcançou 50,0% de menção no painel Gemini, acima do último ciclo completo, com força em compra/fornecedor/pronta entrega e lacunas persistentes em São Paulo, pousadas e intenção genérica de “melhor”.

*Relatório gerado por Flávia (Marketing) em 14/09/2026, 09:17 BRT.*
