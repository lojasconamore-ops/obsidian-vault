# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 23/11/2026, 09:00–09:26 BRT
**Escopo executado:** Gemini direto, 15 prompts fixos × 2 rodadas = 30 submissões
**Fonte de evidência:** `Direct platform` — interface pública do Gemini (Flash-Lite), sem login, via navegador headless (Chrome for Testing 156)
**Status:** **COMPLETO** — 30/30 prompts submetidos e 30/30 respostas observadas (0 erros, 0 timeouts).

---

## Metodologia e limitações

- Cada prompt foi submetido individualmente em conversa nova (`goto_url` para `/app` + gate de frescor: `contenteditable` presente **e** `model-response === 0` antes de digitar), evitando contaminação entre respostas.
- Menção medida **no container da resposta** (`message-content`), excluindo o eco do prompt do usuário, com detecção case-insensitive de `conamore`. Chips de fonte e menção textual foram registrados separadamente.
- Respostas lidas somente após estabilização do texto (2 amostras idênticas + presença de controle de ação/`Redo`).
- Somente o Gemini foi testado (per prioridade e orçamento operacional). ChatGPT/Perplexity (Cloudflare) e Copilot (região) seguem fora de alcance.

### ⚠️ Limitação metodológica crítica deste ciclo

**Busca na web essencialmente inativa.** Em 28 das 30 respostas não foi observado **nenhum chip de citação/fonte** — apenas sugestões de follow-up ("Para aprofundar…"). As únicas exceções foram P14 (chip `Reclame AQUI`, nas duas rodadas) e R2P4 (chip `Blog - Profitel`). Ou seja: as respostas foram majoritariamente geradas a partir do **conhecimento de treinamento** do modelo, não de uma busca web ao vivo.

Isso confunde a medição: quando a busca web está desligada, o Gemini só consegue citar marcas têxteis tradicionais presentes no corpus de treino (Teka, Karsten, Altenburg, Santista, Buddemeyer) e **não** um player B2B regional como a Conamore — cuja presença histórica sempre veio de citação web (blog, Scribd, catálogos). **Os números abaixo devem ser lidos com essa ressalva; não são uma medida limpa de indexação do domínio.**

---

## Resumo executivo

A Conamore apareceu em **2/30 respostas (6,7%)**: **1/15 na R1 (6,7%)** e **1/15 na R2 (6,7%)** — variância entre rodadas **zero**. Frente ao ciclo completo imediatamente anterior (19/10/2026), houve queda de **11/30 (36,7%) para 2/30 (6,7%)** — **−9 menções e −30,0 pontos percentuais**.

**As duas únicas menções foram no prompt de marca P14 ("Conamore é uma boa empresa…")** — o único intrinsecamente *branded* do painel. **Nenhum dos 28 prompts não-marca mencionou a Conamore.** Os grupos Produto (P1–P5) e Compra/Fornecedor (P6–P10) **zeraram em ambas as rodadas (0/10 cada)**.

**Nenhuma URL/domínio da Conamore foi citada em nenhuma das 30 respostas** (0/30) — nem `www.conamore.com.br`, nem `hotelaria.conamore.com.br`, nem `lojas.conamore.com.br`. A presença residual em P14 é reputacional, via chip `Reclame AQUI`.

**Não é possível distinguir, com os dados deste ciclo, uma queda estrutural real de um artefato de medição** (busca web desligada). A queda é sustentada nas duas rodadas (critério do protocolo para "investigar"), mas o colapso simultâneo dos *especialistas em hotelaria* (Conamore, Profitel, ParaHotel, ServHotel) **e** a ascensão uniforme das marcas têxteis tradicionais é a assinatura clássica de resposta sem busca web — não necessariamente de perda de autoridade de domínio.

---

## Disponibilidade da plataforma

| Plataforma | Planejado | Testado | Status | Evidência |
|---|---:|---:|---|---|
| Gemini direto | 30 | 30/30 | `tested` | 2 rodadas completas; conversa nova por prompt; respostas geradas sem login (Flash-Lite) |
| ChatGPT | 0 | 0 | `not run` | Cloudflare — fora de alcance para automação |
| Perplexity | 0 | 0 | `not run` | Cloudflare — fora de alcance para automação |
| Copilot | 0 | 0 | `not run` | Restrição regional |

> **Nota de acessibilidade:** o Gemini respondeu **sem login** (consistente com a matriz). Porém, diferentemente de ciclos anteriores, **a busca na web não foi acionada na maioria das respostas** — ver limitação metodológica acima.

---

## Métricas

| Métrica | R1 | R2 | Consolidado |
|---|---:|---:|---:|
| Prompts testados | 15/15 | 15/15 | **30/30** |
| Menção textual Conamore | 1/15 (6,7%) | 1/15 (6,7%) | **2/30 (6,7%)** |
| Prompts estáveis positivos (2/2) | — | — | **1/15 (6,7%)** — apenas P14 |
| Prompts cegos (0/2) | — | — | **14/15 (93,3%)** |
| URL clicável do domínio `www.conamore.com.br` | 0/15 | 0/15 | **0/30 (0%)** |

### Resultado por grupo de intenção

| Grupo | Menções | Taxa | Variação vs 19/10 |
|---|---:|---:|---:|
| Produto — P1 a P5 | 0/10 | **0,0%** | −20,0 pp (era 20%) |
| Compra/Fornecedor — P6 a P10 | 0/10 | **0,0%** | 0,0 pp (já estava 0%) |
| Comparação/Marca — P11 a P15 | 2/10 | 20,0% | −70,0 pp (era 90%) |

**Leitura:** a Conamore desapareceu de *todos* os territórios não-marca. O único resíduo é o prompt que a cita no enunciado (P14). Em 19/10 o grupo Comparação/Marca sustentava 90% (P11–P15); agora caiu para 20% (apenas P14). É a menor taxa de todo o histórico monitorado.

---

## Matriz prompt × rodada

| # | Prompt exato | R1 | R2 | Consolidação |
|---:|---|:---:|:---:|:---:|
| 1 | `lençol para hotel` | ❌ | ❌ | 0/2 |
| 2 | `qual o melhor lençol para hotel` | ❌ | ❌ | 0/2 |
| 3 | `lençol profissional para pousada` | ❌ | ❌ | 0/2 |
| 4 | `lençol para Airbnb` | ❌ | ❌ | 0/2 |
| 5 | `enxoval para hotel` | ❌ | ❌ | 0/2 |
| 6 | `onde comprar lençol para hotel` | ❌ | ❌ | 0/2 |
| 7 | `fornecedor de lençol para hotéis` | ❌ | ❌ | 0/2 |
| 8 | `lençol para hotel com pronta entrega` | ❌ | ❌ | 0/2 |
| 9 | `fornecedor de enxoval hoteleiro em São Paulo` | ❌ | ❌ | 0/2 |
| 10 | `onde comprar enxoval profissional para hotel` | ❌ | ❌ | 0/2 |
| 11 | `quais empresas vendem lençol para hotel no Brasil` | ❌ | ❌ | 0/2 |
| 12 | `compare fornecedores de enxoval para hotéis` | ❌ | ❌ | 0/2 |
| 13 | `qual empresa fornece roupa de cama para pousadas` | ❌ | ❌ | 0/2 |
| 14 | `Conamore é uma boa empresa para enxoval hoteleiro?` | ✅ | ✅ | **2/2** |
| 15 | `empresa de enxoval para hotelaria` | ❌ | ❌ | 0/2 |

**Reconciliação:** esperado 30; submetido 30; respostas/evidências válidas 30; não executado 0.

---

## Evidências representativas

### R1P14 — intenção de marca (menção, reputacional)

> "A Conamore é uma empresa estabelecida no segmento de enxoval profissional (cama, mesa e banho para hotéis, pousadas, motéis, anfitriões de Airbnb e hotelaria hospitalar) e apresenta uma reputação geral positiva… No Reclame AQUI, mantém histórico de vários anos com reputação classificada como "Ótima", nota média na casa de 8,3/10…"

### R2P14 — intenção de marca (menção, reputacional, com dados quantitativos)

> "…CNPJ regular… No Reclame AQUI… nota média em torno de 8,3/10… alto índice de resolução (cerca de 85,7% a 93,3%)… responde às reclamações (100% no recorte de maio a outubro de 2026, tempo médio próximo de 1 dia e 23 horas)… CNPJ 16.499.070/0001-76."

### Contraste — P7 fornecedor (R2, SEM menção à Conamore)

> "…os principais fornecedores e fabricantes no Brasil dividem-se entre grandes indústrias têxteis (que vendem direto para redes) e distribuidores especializados em hotelaria…" — cita apenas Teka, Altenburg, Buddemeyer, Karsten, Santista.

**Nota de precisão:** P14 contém alegações quantitativas específicas (nota 8,3/10, CNPJ 16.499.070/0001-76, 85,7%–93,3% de resolução, 100% de resposta no recorte maio–outubro/2026, tempo médio de resposta). São plausíveis e consistentes com o Reclame Aqui, mas **devem ser validadas antes de qualquer uso comercial**.

---

## URLs e camada de fonte

**Nenhuma URL clicável de qualquer domínio Conamore foi capturada em nenhuma das 30 respostas** (0/30). A presença da Conamore neste ciclo deu-se exclusivamente por:

| Evidência | Fonte observada | Classificação |
|---|---|---|
| P14 (R1/R2) | chip `Reclame AQUI` | Terceiro — reputacional |
| Demais prompts | (nenhuma) | Sem menção |

A landing page prioritária **`/lencol-para-hotelaria` segue sem citação confirmada** (nem como fonte, nem como menção) — 6º ciclo consecutivo sem citação.

---

## Concorrentes citados

Contagem de respostas em que cada marca monitorada apareceu, sobre 30 respostas:

| Marca | Respostas | Taxa | Variação vs 19/10 |
|---|---:|---:|---:|
| **Teka** | 22/30 | 73,3% | +12 (era 10/30) |
| **Karsten** | 22/30 | 73,3% | +14 (era 8/30) |
| **Altenburg** | 22/30 | 73,3% | +11 (era 11/30) |
| Santista | 11/30 | 36,7% | +4 (era 7/30) |
| Buddemeyer | 10/30 | 33,3% | +1 (era 9/30) |
| Buettner | 5/30 | 16,7% | +3 |
| Dohler | 3/30 | 10,0% | +3 |
| Zelo | 3/30 | 10,0% | −1 |
| Niazi Chohfi | 2/30 | 6,7% | 0 |
| **Conamore** | 2/30 | **6,7%** | **−9 (era 11/30 = 36,7%)** |
| MMartan | 1/30 | 3,3% | 0 |
| Artex | 1/30 | 3,3% | −4 |
| **Profitel** | 1/30 | 3,3% | **−10 (era 11/30 = 36,7%)** |
| Proficione / ServHotel / ParaHotel / OnixProtel / Sabanalia / Lepine | 0/30 | 0,0% | zeraram |

**Leitura crítica:** a assinatura é de **resposta sem busca web** — o triunvirato de marcas têxteis de varejo (Teka, Karsten, Altenburg) saltou para 73,3% cada, enquanto *todos* os especialistas em hotelaria (Conamore, Profitel, ParaHotel, ServHotel, Proficione) colapsaram a ~0–7%. É exatamente o padrão esperado quando o modelo responde de conhecimento de treinamento (onde as grandes marcas dominam) e deixa de buscar na web (onde os B2B regionais apareciam via blog/catálogo).

---

## Comparação com o ciclo anterior — mesma plataforma, mesmos prompts, duas rodadas

| Ciclo | R1 | R2 | Total de menções | Taxa consolidada |
|---|---:|---:|---:|---:|
| 12/10/2026 | 7/15 (46,7%) | 10/15 (66,7%) | 17/30 | 56,7% |
| 19/10/2026 | 5/15 (33,3%) | 6/15 (40,0%) | 11/30 | 36,7% |
| **23/11/2026** | **1/15 (6,7%)** | **1/15 (6,7%)** | **2/30** | **6,7%** |

### Mudanças por intenção

- **Colapso do grupo Comparação/Marca (P11–P15):** caiu de 90% (9/10) em 19/10 para 20% (2/10), restando apenas P14 branded. P11, P12, P13 e P15 — que estavam 2/2 — **zeraram**.
- **Produto (P1–P5) zerou** (0/10): P1 ("lençol para hotel"), que em 19/10 havia recuperado para 2/2 via chip do blog, voltou a 0/2.
- **Compra/Fornecedor (P6–P10) segue zerado** (0/10), como no ciclo anterior.

⚠️ A queda de −30,0 pp foi medida em **duas rodadas consistentes** (R1 e R2 idênticas em 6,7%). Pelo protocolo, merece investigação — **mas** o colapso simultâneo de todos os especialistas em hotelaria + ascensão das marcas de varejo é a assinatura de busca web desligada, o que impede classificar a queda como estrutural sem uma rodada de confirmação com busca web ativa.

---

## Precisão e riscos de conteúdo

- O Gemini atribuiu à Conamore (em P14) reputação "Ótima" no Reclame Aqui, nota 8,3/10, CNPJ 16.499.070/0001-76 e índices de resposta. **Validar antes de uso comercial.**
- P14 continua fortemente influenciado por **Reclame Aqui** (reputacional), não por páginas comerciais próprias.
- **Busca web inativa na maioria das respostas** — o número de 6,7% não deve ser lido como medida limpa de indexação do domínio. É uma fotografia do Flash-Lite sem busca web.

---

## Leitura executiva e próximas ações

1. **Confirmar se é artefato ou queda real — prioridade máxima.** O dado bruto (6,7%) é extremo e sustentado em 2 rodadas, mas a ausência de citações em 28/30 respostas indica busca web desligada. **Próxima rodada deve (a) verificar se a busca web está ativa e (b) preferencialmente testar também em um contexto com busca web confirmada** antes de tratar como perda estrutural de visibilidade.
2. **Não tomar decisão de conteúdo com base apenas neste ciclo.** Aguardar uma medição com busca web ativa. Se a queda persistir com busca web ativa, aí sim tratar como colapso estrutural.
3. **Reforçar a associação a atributos de compra** (fornecedor, pronta entrega, pedido mínimo) em títulos, headings, FAQs e dados estruturados — para quando a busca web voltar, a Conamore competir melhor nas queries de compra.
4. **Manter e monitorar o território reputacional (P14):** é o único ponto de presença atual, fortemente ancorado no Reclame Aqui. Preservar nota/reputação e resposta a reclamações é hoje o principal ativo de visibilidade em IA.
5. **Converter indexação indireta em citação de domínio:** `/lencol-para-hotelaria` segue sem citação (6º ciclo). Reforçar autoridade da landing e do blog apontando para `www.conamore.com.br`.
6. **Diagnosticar por que a busca web não foi acionada** no ambiente headless — possível detecção de `HeadlessChrome` no User-Agent degradando a experiência. Avaliar com Matias/TI se um navegador com UA padrão altera o comportamento.

---

## Status final

| Executado | Evidência | Status |
|---|---|---|
| Gemini R1 | 15/15 respostas; 1 menção (6,7%) | ✅ Completo |
| Gemini R2 | 15/15 respostas; 1 menção (6,7%) | ✅ Completo |
| Consolidado | 30/30 respostas; 2 menções (6,7%) | ✅ Confirmado |
| Concorrência | Teka/Karsten/Altenburg 73,3%; especialistas hotelaria colapsaram | ✅ Concluído |
| URLs | Nenhuma URL clicável do domínio Conamore | ✅ Observado |
| Comparação histórica | 36,7% → 6,7% vs 19/10 (−30,0 pp) | ⚠️ Comparável, mas confundido por busca web inativa |
| Relatório Obsidian | `Agentes/Flávia/SEO - Visibilidade IA - 2026-11-23.md` | ✅ Salvo |

**Status analítico:** **CONFIRMADO — ciclo completo, mas com limitação metodológica.** A Conamore atingiu **6,7% de menção no painel Gemini** (−30,0 pp vs 19/10), a menor taxa do histórico, sustentada nas duas rodadas (ambas 6,7%). As únicas menções vieram do prompt de marca P14 (reputacional, via Reclame Aqui). **A queda não pode ser atribuída a perda estrutural de visibilidade sem confirmação, porque a busca web esteve essencialmente inativa neste ciclo** (0 citações de fonte em 28/30 respostas) — o que favorece as marcas de varejo presentes no treino e apaga os B2B regionais que dependiam de citação web. Próxima rodada deve validar a ativação da busca web antes de qualquer conclusão de tendência.

*Relatório gerado por Flávia (Marketing) em 23/11/2026, 09:26 BRT.*
