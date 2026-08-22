# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 22/08/2026 ~11:42 BRT (execução sob demanda)
**Escopo:** 15 prompts fixos — Gemini (alvo primário) + iAsk.ai (IA de busca acessível, alternativa rotulada)
**Status:** PARCIAL — Gemini BLOQUEADO (login obrigatório, reconfirmado). iAsk.ai completo (15/15).

---

## Resumo Executivo

**Gemini (alvo):** ❌ BLOQUEADO — Flash-Lite aceita o prompt (aparece na conversa) mas **não gera resposta** sem conta Google. Botão "Sign in" presente. Reconformado 22/08 (4º ciclo seguido bloqueado).

**iAsk.ai (IA de busca, alternativa):** ✅ Completo — **Conamore NÃO mencionada em 0/15 respostas (0%).** Nenhuma citação de fonte, nenhuma menção no texto gerado.

⚠️ **Sinal relevante:** mesmo na pergunta direta "Conamore é uma boa empresa para enxoval hoteleiro?" (P14), a IA **não reconheceu a Conamore** — devolveu resposta genérica sobre "como avaliar fornecedor de enxoval" sem citar a marca. Enquanto isso, concorrentes (Profitel, ParaHotel, ServHotel, OnixProtel, Lépine, TEKA, Karsten, Altenburg) **foram citados naturalmente** nas respostas.

---

## Plataformas

| Plataforma | Status | Evidência |
|---|---|---|
| **Gemini** | ❌ Bloqueado (login) | Flash-Lite: prompt "lençol para hotel" enviado, sem resposta após 55s. "Sign in" presente. |
| **iAsk.ai** | ✅ Completo | AI search engine sem login. 15/15 prompts respondidos. |
| ChatGPT | ❌ Cloudflare | "Just a moment..." |
| Perplexity | ❌ Cloudflare | Ray ID a2f28bfd4d7ecdf7 |
| Copilot | ❌ Região | "Not available in your region" |

---

## Resultados — iAsk.ai (15/15 testados)

| # | Prompt | Menção texto | Fonte | Vídeo | Concorrentes citados |
|---:|---|---|---|---|---|
| 1 | lençol para hotel | ❌ | ❌ | — | Lépine, OnixProtel, Profitel |
| 2 | qual o melhor lençol para hotel | ❌ | ❌ | — | — |
| 3 | lençol profissional para pousada | ❌ | ❌ | — | — |
| 4 | lençol para Airbnb | ❌ | ❌ | — | Renata Decorações, OnixProtel |
| 5 | enxoval para hotel | ❌ | ❌ | ✅ (canal próprio) | GA Confort |
| 6 | onde comprar lençol para hotel | ❌ | ❌ | — | — |
| 7 | fornecedor de lençol para hotéis | ❌ | ❌ | — | — |
| 8 | lençol para hotel com pronta entrega | ❌ | ❌ | — | TEKA Profiline, Karsten, Altenburg, Profitel, ServHotel |
| 9 | fornecedor de enxoval hoteleiro em São Paulo | ❌ | ❌ | — | — |
| 10 | onde comprar enxoval profissional para hotel | ❌ | ❌ | — | — |
| 11 | quais empresas vendem lençol para hotel no Brasil | ❌ | ❌ | — | — |
| 12 | compare fornecedores de enxoval para hotéis | ❌ | ❌ | — | **Profitel, ParaHotel, ServHotel** |
| 13 | qual empresa fornece roupa de cama para pousadas | ❌ | ❌ | — | — |
| 14 | Conamore é uma boa empresa? | ❌ | ❌ | — | (resposta genérica, não reconheceu a marca) |
| 15 | empresa de enxoval para hotelaria | ❌ | ❌ | — | — |

**Legenda:** Menção texto = "Conamore" na resposta gerada | Fonte = URL Conamore nas citações | Vídeo = canal no YouTube relacionado

**Resultado: 0/15 menções de texto · 0/15 citações de fonte · 1/15 vídeo relacionado (canal próprio "Conamore Casa").**

---

## Concorrentes citados (iAsk.ai — share of voice deles)

| Concorrente | Prompts | Observação |
|---|---|---|
| **Profitel** | P1, P8, P12 | Mais citado — pronta entrega, sem pedido mínimo |
| **ServHotel** | P8, P12 | Enxoval profissional para redes/hospitais |
| **ParaHotel** | P12 | Alto giro, pousadas, Airbnb, PJ |
| **OnixProtel** | P1, P4 | Roupa de cama para hotel |
| **Lépine Enxovais** | P1 | Lençol avulso hotelaria |
| **TEKA / Karsten / Altenburg** | P8 | Marcas de referência em lençol profissional |

---

## Leitura executiva

1. **Conamore está fora do "conhecimento" das IAs de busca**, apesar de estar bem indexada no índice web (Exa mostrava 73% no ciclo 17/08). Índice web ≠ conhecimento do modelo.
2. **Concorrentes dominam o corpus:** Profitel e ParaHotel aparecem consistentemente como referências de enxoval hoteleiro nas respostas geradas.
3. **P14 é o sintoma mais claro:** perguntada diretamente, a IA não soube dizer quem é a Conamore — sinal de autoridade de marca fraca no conteúdo que alimenta esses modelos.
4. A única "presença" foi orgânica: vídeo do canal próprio "Conamore Casa" no YouTube em vídeos relacionados do P5.

---

## Recomendações

1. **Gemini API (prioridade):** provisionar chave Google AI Studio (`generativelanguage.googleapis.com`) para medir IA generativa real sem depender de navegador/login.
2. **Autoridade de marca no corpus:** reforçar presença em fontes que alimentam IAs de busca — Wikipedia/DBpédia de hotelaria, artigos em portais do setor, associações (ABIH, Equipotel), e conteúdo citável em sites de terceiros.
3. **Conteúdo de marca comparativo:** criar páginas/artigos "Conamore vs concorrentes" e "quem é a Conamore" para dar aos modelos material citável sobre a empresa.
4. **Manter o job semanal** (próxima: 24/08 09:00) alternando iAsk.ai + Exa como baseline duplo.

---

## Status Final

```
Executado                  | Evidência                          | Status
Gemini direto (alvo)       | Bloqueado (login Google)           | ❌ Bloqueado (0/15)
iAsk.ai (IA de busca)      | 0/15 menções (0%)                  | ✅ Completo (15/15)
ChatGPT / Perplexity       | Cloudflare                         | ❌ Não testado
Copilot                    | Região                             | ❌ Não testado
```

**Ciclo 22/08 (sob demanda):** Gemini bloqueado. iAsk.ai executado como IA de busca alternativa: Conamore **ausente em 15/15 respostas**, com concorrentes (Profitel, ParaHotel, ServHotel, OnixProtel, Lépine) citados. Sinal de autoridade de marca fraca no corpus das IAs de busca.

---

*Relatório gerado por Flávia (Marketing) em 22/08/2026, 11:42 BRT (execução sob demanda).*
*Próximo ciclo agendado: segunda-feira 24/08/2026 09:00 BRT (job 542783c5d7eb).*
