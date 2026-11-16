# SEO — Visibilidade em IA — Conamore — 16/11/2026

**Plataforma:** Gemini público (Flash-Lite), sem login. **Janela observada:** 09:07–09:23 BRT. **Escopo:** 15 prompts fixos × 2 rodadas = 30 respostas independentes. **Status: COMPLETO — 30/30 testadas.** ChatGPT, Perplexity e Copilot não executados (fora do escopo deste ciclo: apenas Gemini).

## Metodologia

Cada submissão em conversa nova e independente, validada pelo portão de frescor (`0` elementos `model-response` antes do envio + textbox `Enter a prompt for Gemini` visível) e pela estabilização do texto antes da captura. Prosa isolada do `message-content`; menção textual separada de chip de fonte. Evidência durável em `Agentes/Flávia/Evidências IA/2026-11-16-gemini.jsonl` (30 linhas, prompt + rodada + horário BRT + resposta integral + URL da sessão).

## Painel fixo — menção na resposta atual

| Nº | Prompt exato | R1 | R2 |
|---:|---|---:|---:|
| 1 | lençol para hotel | não | não |
| 2 | qual o melhor lençol para hotel | não | não |
| 3 | lençol profissional para pousada | não (recusa) | não |
| 4 | lençol para Airbnb | não | não |
| 5 | enxoval para hotel | não | não |
| 6 | onde comprar lençol para hotel | **sim** | não |
| 7 | fornecedor de lençol para hotéis | **sim** | não |
| 8 | lençol para hotel com pronta entrega | não | não |
| 9 | fornecedor de enxoval hoteleiro em São Paulo | não | não |
| 10 | onde comprar enxoval profissional para hotel | não | **sim** |
| 11 | quais empresas vendem lençol para hotel no Brasil | **sim** | **sim** |
| 12 | compare fornecedores de enxoval para hotéis | **sim** | **sim** |
| 13 | qual empresa fornece roupa de cama para pousadas | **sim** | **sim** |
| 14 | Conamore é uma boa empresa para enxoval hoteleiro? | **sim** | **sim** |
| 15 | empresa de enxoval para hotelaria | **sim** | **sim** |

## Métricas (Gemini, denominador = respostas testadas)

- **Menção textual:** **13/30 (43,3%)** — R1 7/15, R2 6/15.
- **Menção sem marca (exclui P14):** **11/28 (39,3%)**.
- **Prompt de marca P14:** 2/2 — ambas positivas ("Sim, a Conamore é considerada uma boa empresa e uma opção confiável…"; "…bastante reconhecida e respeitada no mercado de enxovais"). Não mede descoberta espontânea.
- **Citação clicável (âncora `a[href]` para conamore.com.br):** **0/30.** O domínio aparece em **chip de fonte não clicável** (ver abaixo).
- **Citação de domínio em chip:** confirmada em ao menos 1 resposta (R2 P15), onde `conamore.com.br` surge como texto do chip de citação (`citation-236`) e o chip de fonte `Conamore`. Demais chips "Conamore + N" observados em prosa, mas URLs não abertas individualmente.
- **Recusas/degradação:** 1 (R1 P3, resposta "além das minhas capacidades"), transitória — R2 P3 respondeu normalmente.

## Concorrentes citados (frequência de menção nas 30 respostas)

Teka (14) · Profiline (12) · Altenburg (9) · Santista (9) · Profitel (9) · Atacado Hoteleiro (8) · ServHotel (8) · Karsten (7) · Hoxtel (7) · Buddemeyer (6) · Artex (5) · ParaHotel (5) · Officinn (5) · Mmartan (4) · Buettner (3) · Trussardi, Umlar, Efetuar, Dohler, Zelo (2 cada).

**Share of voice:** Conamore (13) em empate técnico com Teka (14) no topo das menções. Profiline (12) em terceiro.

## Trechos representativos (gerados pela IA, não validados como fato comercial)

- **P6/R1** `a5bfde5511834017`: "Conamore Hotelaria: Especializada em lençóis para hotéis e Airbnbs, com linhas que vão de 180 a 400 fios (mistos e 100% algodão) e opções de personalização."
- **P11/R1** `058648b425f7551d`: "Conamore Hotelaria: Especializada em enxoval para hospedagens (hotéis, pousadas e Airbnb). Oferece linhas variadas … com pronta entrega e opções de personalização."
- **P14/R1** `3f68ea22c6f0ec89`: "Sim, a Conamore é considerada uma boa empresa e uma opção confiável para quem busca enxoval voltado à hotelaria, pousadas e anfitriões de aluguel por temporada (como Airbnb)."
- **P15/R2** `5c704aff874827e3`: "Conamore Hotelaria (conamore.com.br) — Foco: Roupas de cama e banho voltadas para hotelaria, pousadas e hospedagens de curta temporada (Airbnb)."

## Comparação com ciclos anteriores (mesmo painel, 2 rodadas, 30 respostas)

| Ciclo | Menção textual | Sem marca |
|---|---:|---:|
| 2026-10-26 | 14/30 (46,7%) | — |
| 2026-11-02 | 9/30 (30,0%) | 7/28 (25,0%) |
| 2026-11-09 (tarde) | 9/30 (30,0%) | 7/28 (25,0%) |
| **2026-11-16** | **13/30 (43,3%)** | **11/28 (39,3%)** |

**Leitura:** recuperação do platô de 30% dos dois ciclos anteriores para 43%, aproximando-se do nível de 26/10 (46,7%). Duas rodadas consistentes (7 e 6 menções), o que reduz o risco de ruído de rodada única. Variação concentrada nos prompts de compra/comparação (P10–P15); o grupo produto (P1–P5) e o fornecedor em SP (P9) seguem **sem nenhuma menção** em todos os ciclos recentes.

## Lacunas persistentes e ações

- **Grupo produto (P1–P5): 0 menções.** "lençol para hotel", "qual o melhor", pousada, Airbnb e "enxoval para hotel" nunca citam a Conamore. São as consultas de maior intenção B2B.
- **P9 "fornecedor de enxoval hoteleiro em São Paulo": 0 menções** em todos os ciclos — apesar de a Conamore ser de Campinas-SP.
- **Mencionada ≠ clicável:** 13 menções textuais, mas **0 âncoras clicáveis** para o domínio. O chip de fonte "Conamore" existe, porém não gera clique/tráfego. O gargalo permanece o link clicável, não a presença tópica.
- Ação recomendada: reforçar conteúdo B2B verificável e com URL própria para as consultas de produto e SP (sem publicar alegações de estoque, preço ou reputação geradas por IA). Conferir tráfego GA4 (medium `ai-assistant`/`dgen`) separadamente — visibilidade ≠ clique.

**Executado | Evidência | Status:** Gemini direto 30/30 | JSONL `2026-11-16-gemini.jsonl` (30 linhas) + URLs de sessão e trechos acima | **COMPLETO** (2 rodadas × 15 prompts, 13/30 menções textuais).
