# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 17/08/2026 ~09:10 BRT
**Escopo:** 15 prompts fixos — Gemini (browser direto, alvo principal) + Exa/Composio (alternativa claramente rotulada)
**Status:** PARCIAL — Gemini BLOQUEADO (login obrigatório), Exa completo (15/15).

---

## Resumo Executivo

**Gemini (alvo do ciclo):** ❌ BLOQUEADO — Flash-Lite não gera mais resposta sem conta Google. Comportamento idêntico ao ciclo de 11/08: o prompt é aceito e aparece na conversa, mas **nenhuma resposta é produzida** (botão "Sign in" presente; sem gate explícito de erro após o envio). **0/30 submissões concluídas** (2 rodadas × 15 não executadas).

**Alternativa — busca assistida por IA (Composio/Exa):** ✅ Completo — Conamore citada em **11/15 prompts (73%)**, mesmo patamar do ciclo anterior.

⚠️ **IMPORTANTE:** Os resultados Exa NÃO são comparáveis a Gemini direto. A Exa é busca sobre índice web, não modelo generativo. A taxa reflete presença no índice, não "recomendação" de IA generativa.

### Comparação histórica (Exa — comparável; Gemini — não comparável entre si pela mudança de política)

| Ciclo | Plataforma | Rodadas | Menção Exa | Menção Gemini |
|---|---|---|---|---|
| 03/08 | Gemini direto | 1 | — | 9/15 (60%) |
| 08/08 | Gemini direto | 2 | — | 6/15 (40%) |
| 11/08 | Gemini ⛔ / Exa | 0 / 1 | 11/15 (73%) | N/A |
| **17/08** | **Gemini ⛔ / Exa** | **0 / 1** | **11/15 (73%)** | **N/A** |

---

## Plataformas

| Plataforma | Status | Observação |
|---|---|---|
| **Gemini** | ❌ BLOQUEADO | Flash-Lite exige login Google. Prompt enviado, resposta não gerada (reconfirmado 17/08). |
| **Composio/Exa** | ✅ Completo | Busca web assistida (Exa API). 15/15 prompts. |
| ChatGPT | ❌ Não testado | Cloudflare (mantido) |
| Perplexity | ❌ Não testado | Cloudflare (mantido) |
| Copilot | ❌ Não testado | Região (mantido) |

---

## Resultados Completos — Exa (busca web assistida)

| # | Prompt | Texto | Citação | Conamore URLs | Concorrentes |
|---:|---|---|---|---|---|
| 1 | lençol para hotel | ✅ | ✅ | solteiro 200 algodão; king 180 | Profitel, MCS, Pinhaltex, Matinali, Cotton Made |
| 2 | qual o melhor lençol para hotel | ❌ | ✅ | blog como-escolher; king 180 | Profitel, Proficione, direct-hotellerie |
| 3 | lençol profissional para pousada | ✅ | ✅ | king 180; solteiro 200 | MCS, Empório do Lençol, Profitel, Master Hotelaria, Proficione |
| 4 | lençol para Airbnb | ❌ | ✅ | casal prime 200 | Proficione, Profitel, MCS, Empório, Anfitriões de Aluguel |
| 5 | enxoval para hotel | ❌ | ❌ | — | Profitel, Proficione, **ParaHotel**, Luvi, Matinali |
| 6 | onde comprar lençol para hotel | ❌ | ❌ | — | MCS, Matinali, Empório, Pinhaltex, Miler De Marchi, TextilMed, JN, Profitel |
| 7 | fornecedor de lençol para hotéis | ✅ | ✅ | conamore.com.br (via Exa org) | Matinali, **ParaHotel**, MCS, Empório, Miler De Marchi |
| 8 | lençol para hotel com pronta entrega | ✅✅ | ✅ | solteiro; king; hospitalar queen | MCS, Empório, Profitel, Lisam |
| 9 | fornecedor de enxoval hoteleiro em SP | ✅ | ✅ | conamore.com.br (via Exa org) | Empório, Enxoval Profissional, G3, Sabie, Gifran, Kountry Line |
| 10 | onde comprar enxoval profissional para hotel | ❌ | ❌ | — | Sabie, Matinali, Atacado Hoteleiro, Kountry Line, Aliança, Proficione, Buddemeyer, JN |
| 11 | quais empresas vendem lençol para hotel no Brasil | ✅ | ✅ | conamore.com.br (via Exa org) | Buddemeyer, Matinali, Ciça, MCS, Trousseau, Miler De Marchi, Pinhaltex |
| 12 | compare fornecedores de enxoval para hotéis | ✅ | ✅ | blog da-sacaria | Döhler Pro, Buddemeyer, Matinali, **ParaHotel**, Proficione, Novo Toque |
| 13 | qual empresa fornece roupa de cama para pousadas | ❌ | ❌ | — | Private Label, Proficione, Trousseau, Gifran, **ParaHotel**, Sonho & Conforto, Profitel |
| 14 | Conamore é uma boa empresa? | ✅ | ✅ | 8 URLs (site, FAQ, 3 blogs, toalhas, 44rev) | — (branded) |
| 15 | empresa de enxoval para hotelaria | ✅ | ✅ | conamore.com.br (via Exa org) | Teka, Buddemeyer, Sabie, Kountry Line, Matinali, Ciça, Têxtil Arte |

**Legenda:** Texto = menção no texto da resposta | Citação = URL Conamore nas fontes | ✅✅ = recomendação primária | ❌ = ausente

---

## Métricas (Exa, 15/15 testados)

| Métrica | 17/08 | 11/08 |
|---|---|---|
| Menção textual (answer) | 9/15 (60%) | 9/15 (60%) |
| Menção ou citação | **11/15 (73%)** | **11/15 (73%)** |
| Citação com URL Conamore | 11/15 (73%) | 11/15 (73%) |
| URLs Conamore únicas | ~11 (domínio) | 12 |

### Por grupo de intenção

| Grupo | 17/08 | 11/08 |
|---|---|---|
| Produto (P1–P5) | 4/5 (80%) | 5/5 (100%) |
| Compra/Fornecedor (P6–P10) | 3/5 (60%) | 4/5 (80%) |
| Comparação/Marca (P11–P15) | 4/5 (80%) | 2/5 (40%) |

---

## Mudanças vs ciclo anterior (Exa 11/08 → 17/08)

**Mesma taxa (73%), mas com movimentação de prompts:**

| Prompt | 11/08 | 17/08 | Variação |
|---|---|---|---|
| P5 enxoval para hotel | ✅ | ❌ | 🔴 perdeu |
| P6 onde comprar lençol para hotel | ✅ | ❌ | 🔴 perdeu |
| P12 compare fornecedores | ❌ | ✅ | 🟢 ganhou |
| P15 empresa de enxoval para hotelaria | ❌ | ✅ | 🟢 ganhou |

- **🟢 Destaque:** P12 e P15 eram "duplo-cegos" apontados em 11/08 como prioridade de conteúdo. Ambos agora citam Conamore (P12 via artigo "Da sacaria ao enxoval", P15 via indexação da empresa). Sinal de que o conteúdo recente do blog está sendo absorvido.
- **🔴 Alerta:** P5 e P6 perderam presença. São intenções de alto valor comercial (enxoval para hotel / onde comprar). Monitorar no próximo ciclo para distinguir ruído de tendência.

---

## URLs da Conamore Citadas (Exa, 17/08)

1. `conamore.com.br` (raiz, via indexação Exa org) — P7, P9, P11, P14, P15
2. `conamore.com.br/lencol-solteiro-branco-sem-elastico-200-algodao-hotelaria` — P1, P3, P8
3. `conamore.com.br/lencol-king-sem-elast-280x250cm-percal-180-fios-50-algod-o-e-50-poliester` — P1, P2, P3, P8
4. `conamore.com.br/lencol-casal-prime-c-elast-140x190x30cm-percal-200-fios-100-algod-o` — P4
5. `hospitalar.conamore.com.br/lencol-queen-classic-c-elast-160x200x25cm...` — P8
6. `hotelaria.conamore.com.br/como-escolher-os-melhores-lencois-para-sua-hospedagem...` — P2
7. `hotelaria.conamore.com.br/da-sacaria-ao-enxoval-hotelaria-historia-conamore` — P12, P14
8. `hotelaria.conamore.com.br/22-anos-de-conamore...` — P14
9. `hotelaria.conamore.com.br/23-anos-de-conamore...` — P14
10. `conamore.com.br/faq` — P14
11. `conamore.com.br/toalhas-para-hoteis-pousadas` — P14
12. `br.44rev.com/businesses/conamore.com.br` — P14 (avaliações, terceiro)

**Nota de indexação indireta:** P7, P9, P11, P15 citam Conamore via `exa.ai/library/organization/mv286s2gz6q` (índice de empresa da Exa, derivado de LinkedIn), exibindo URL `conamore.com.br`. Mesmo padrão "indireto" já observado com Scribd no Gemini — menção ≠ crawl direto do domínio.

**Segmentos:** Hotelaria B2B (P1, P3, P4, P8) · Hospitalar (P8) · Blog/Institucional (P2, P12, P14). A LP `/lencol-para-hotelaria` **não** foi citada neste ciclo (apareceu em 11/08 no P4).

---

## Concorrentes Identificados (Exa, 17/08)

| Concorrente | Aparições | Observação |
|---|---|---|
| **Profitel** | 8/15 | Mais onipresente em produto |
| **Matinali Têxtil** | 8/15 | Forte em fornecedor/compra |
| **MCS Têxtil** | 7/15 | Forte em produto e fábrica |
| **Proficione** | 7/15 | Crescendo — pousadas, Airbnb, kits |
| **Empório do Lençol** | 6/15 | Forte em compra/SP (Brás) |
| **ParaHotel** | 4/15 | P5, P7, P12, P13 — segue agressivo em enxoval/kit |
| **Hotelaria Buddemeyer** | 4/15 | Comparação e institucional |
| **Sabie / Kountry Line** | 3/15 cada | Enxoval profissional e SP |

### Alerta: ParaHotel
- Presente em P5 (enxoval), P7 (fornecedor), P12 (comparação), P13 (pousadas — domina).
- P13 (roupa de cama pousadas) segue **cego para Conamore** nos dois ciclos Exa — ParaHotel lidera.

---

## Diagnóstico: Gemini Bloqueado (reconfirmado)

O Gemini (gemini.google.com/app) em modo Flash-Lite segue exigindo autenticação Google para gerar respostas:

1. Navegação OK — página carrega, textbox `Enter a prompt for Gemini` disponível.
2. Prompt "lençol para hotel" enviado com sucesso (aparece na conversa).
3. **Resposta NÃO é gerada** após 45s+ — página mostra só o prompt + "Gemini is AI and can make mistakes."
4. Botão "Sign in" presente (header) — sem gate explícito pós-envio, mas resposta nunca chega.

**Impacto:** 3º ciclo consecutivo sem Gemini direto. Sem conta Google de teste, a medição de visibilidade em IA generativa fica dependente de alternativa (Exa) que mede índice, não geração.

---

## Recomendações

1. **🔧 Resolver o Gemini (prioridade máxima):** provisionar conta Google dedicada para testes OU avaliar Gemini via API (Google AI Studio — `generativelanguage.googleapis.com`) que não exige login de navegador e aceita chave. Isso destravaria de novo a medição de IA generativa de verdade.
2. **🔴 P5 e P6 (perdas):** reforçar conteúdo/SEO para "enxoval para hotel" e "onde comprar lençol para hotel" — são intenções comerciais de alto valor.
3. **🟡 P13 (pousadas):** continua cego nos 2 ciclos Exa. ParaHotel domina. Criar conteúdo dedicado "roupa de cama para pousadas".
4. **🟢 Capitalizar P12/P15:** os ganhos vieram de conteúdo de blog/institucional. Continuar produção de artigos comparativos e de autoridade.
5. **📊 Próximo ciclo (24/08):** persistir na tentativa Gemini; se bloqueado, manter Exa como baseline e tentar Gemini API como proxy generativo rotulado.

---

## Status Final

```
Executado                       | Evidência                          | Status
Gemini direto (alvo)            | Bloqueado (login Google)           | ❌ Bloqueado (0/30)
Exa/Composio (alternativa)      | 11/15 menções (73%)                | ✅ Completo (15/15)
ChatGPT / Perplexity            | Cloudflare (mantido)               | ❌ Não testado
Copilot                         | Região (mantido)                   | ❌ Não testado
```

**Ciclo 17/08:** PARCIAL — Gemini bloqueado (0/30 submissões). Exa executado como alternativa rotulada (15/15). Taxa estável em 73% vs 11/08, com ganhos em P12/P15 e perdas em P5/P6.

---

*Relatório gerado por Flávia (Marketing) em 17/08/2026, 09:10 BRT (job 542783c5d7eb).*
*Próximo ciclo: segunda-feira 24/08/2026 09:00 BRT.*
