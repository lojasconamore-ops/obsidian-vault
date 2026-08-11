# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 11/08/2026 ~09:00 BRT  
**Escopo:** 15 prompts fixos, Gemini (browser direto) + alternativa Composio/Exa  
**Status:** PARCIAL — Gemini BLOQUEADO, Exa completo (15/15). ChatGPT/Perplexity/Copilot não testados.

---

## Resumo Executivo

**Gemini:** ❌ BLOQUEADO — Flash-Lite mode agora requer login Google. Não foi possível executar nenhuma das 2 rodadas planejadas.

**Alternativa — busca assistida por IA (Composio/Exa):** ✅ Completo — Conamore citada em **11/15 prompts (73%)**.

⚠️ **IMPORTANTE:** Os resultados Exa NÃO são comparáveis aos ciclos anteriores (Gemini direto). A Exa é uma busca web indexada, não um modelo generativo. A taxa naturalmente mais alta reflete a presença da Conamore no índice web, não sua "recomendação" por IA generativa.

### Comparação histórica (NÃO comparável diretamente)

| Ciclo | Plataforma | Rodadas | Menção |
|---|---|---|---|
| 03/08 | Gemini direto | 1 | 9/15 (60%) |
| 08/08 | Gemini direto | 2 | 6/15 (40%) |
| **11/08** | **Gemini ⛔ / Exa** | **0 / 1** | **N/A / 11/15 (73%)** |

---

## Plataformas

| Plataforma | Status | Observação |
|---|---|---|
| **Gemini** | ❌ BLOQUEADO | Flash-Lite agora exige login Google. Sign-in page detectada. |
| **Composio/Exa** | ✅ Completo | Busca web assistida. 15/15 prompts. |
| ChatGPT | ❌ Não testado | Cloudflare (mantido) |
| Perplexity | ❌ Não testado | Cloudflare (mantido) |
| Copilot | ❌ Não testado | Região (mantido) |

---

## Resultados Completos — Exa (busca web assistida)

| # | Prompt | Exa | Conamore URLs |
|---:|---|---|---|
| 1 | lençol para hotel | ✅ | conamore.com.br |
| 2 | qual o melhor lençol para hotel | ✅ | /lencol-solteiro-branco... |
| 3 | lençol profissional para pousada | ✅ | 2 URLs (solteiro, king) |
| 4 | lençol para Airbnb | ✅ | /lencol-para-hotelaria, conamore.com.br |
| 5 | enxoval para hotel | ✅ | conamore.com.br |
| 6 | onde comprar lençol para hotel | ✅ | /lencol-king-sem-elast... |
| 7 | fornecedor de lençol para hotéis | ✅ | conamore.com.br |
| 8 | lençol para hotel com pronta entrega | ✅ | hospitalar.conamore.com.br + hotelaria |
| 9 | fornecedor de enxoval hoteleiro em SP | ✅ | conamore.com.br |
| 10 | onde comprar enxoval profissional para hotel | ❌ | — |
| 11 | quais empresas vendem lençol para hotel | ✅ | conamore.com.br |
| 12 | compare fornecedores de enxoval | ❌ | — |
| 13 | qual empresa fornece roupa de cama pousadas | ❌ | — |
| 14 | Conamore é uma boa empresa? | ✅ | 7 URLs (blog, FAQ, site) |
| 15 | empresa de enxoval para hotelaria | ❌ | — |

**Legenda:** ✅ = Conamore citada em answer ou citations | ❌ = ausente

---

## Métricas

| Métrica | Exa |
|---|---|
| Menção textual (answer) | 9/15 (60%) |
| Menção ou citação | **11/15 (73%)** |
| Citações com URL Conamore | 11/15 (73%) |
| URLs Conamore únicas | 12 |

### Por grupo de intenção

| Grupo | Exa |
|---|---|
| Produto (P1-P5) | 5/5 (100%) |
| Compra/Fornecedor (P6-P10) | 4/5 (80%) |
| Comparação/Marca (P11-P15) | 2/5 (40%) |

---

## Análise Cruzada: Gemini 08/08 vs Exa 11/08

⚠️ **Não são comparáveis diretamente**, mas a análise cruzada revela padrões interessantes:

### Prompts com Conamore em AMBOS (Gemini + Exa)
- P1: lençol para hotel ✅✅
- P6: onde comprar lençol para hotel ✅✅
- P11: quais empresas vendem ✅✅
- P14: branded ✅✅

### Prompts com Conamore apenas na Exa (Gemini cego)
- P2: melhor lençol para hotel (Exa: ✅, Gemini: ❌❌)
- P3: lençol profissional pousada (Exa: ✅, Gemini: ❌❌)
- P4: lençol para Airbnb (Exa: ✅, Gemini: ❌❌)
- P5: enxoval para hotel (Exa: ✅, Gemini: ❌❌)
- P7: fornecedor de lençol hotéis (Exa: ✅, Gemini: ⚠️)
- P8: pronta entrega (Exa: ✅, Gemini: ⚠️)
- P9: fornecedor SP (Exa: ✅, Gemini: ❌❌)

### Prompts cegos em AMBOS (maior preocupação)
- P10: onde comprar enxoval profissional ❌❌
- P12: compare fornecedores ❌❌
- P15: empresa de enxoval para hotelaria ❌❌

### Gemini via mas Exa não (queda no índice web)
- P13: roupa de cama pousadas (Gemini: ✅✅, Exa: ❌)

---

## URLs da Conamore Citadas (Exa)

1. `conamore.com.br` — P1, P4, P5, P7, P9, P11, P14
2. `conamore.com.br/lencol-para-hotelaria` — P4
3. `conamore.com.br/lencol-solteiro-branco-sem-elastico-200-algodao-hotelaria` — P2, P3, P8
4. `conamore.com.br/lencol-king-sem-elast-280x250cm-percal-180-fios...` — P3, P6
5. `hospitalar.conamore.com.br/lencol-casal-supreme...` — P8
6. `hotelaria.conamore.com.br/23-anos-de-conamore...` — P14
7. `hotelaria.conamore.com.br/da-sacaria-ao-enxoval-hotelaria...` — P14
8. `hotelaria.conamore.com.br/22-anos-de-conamore...` — P14
9. `conamore.com.br/faq` — P14
10. `conamore.com.br/toalhas-para-hoteis-pousadas` — P14
11. `br.44rev.com/businesses/conamore.com.br` — P14

---

## Concorrentes Identificados (Exa)

| Concorrente | Aparições | Destaque |
|---|---|---|
| **Matinali Têxtil** | 13/15 | Onipresente — maior concorrente em índice web |
| **ParaHotel** | 8/15 | Forte em pousadas, Airbnb, compra |
| **MCS Têxtil** | 8/15 | Forte em buscas de produto |
| **Buddemeyer** | 6/15 | Presente em comparativos e fornecedores |
| **Sabie** | 5/15 | Destaque em enxoval profissional e SP |
| **Teka** | 4/15 | Institucional e hotelaria |
| **Proficione** | 3/15 | Nicho: lençol branco hotel |

### Alerta: ParaHotel
- Domina P13 (roupa de cama pousadas) — 1ª citação, Conamore AUSENTE
- Forte em P4 (Airbnb), P5 (enxoval), P7 (fornecedor), P10 (enxoval profissional)
- Concorrente mais agressivo em intenções de compra

---

## Diagnóstico: Gemini Bloqueado

O Gemini (gemini.google.com/app) em modo Flash-Lite agora requer autenticação Google:

1. Navegação bem-sucedida até a página
2. Textbox disponível e funcional
3. Prompt enviado com sucesso (texto aparece na conversa)
4. **Resposta NÃO é gerada** — página mostra prompt enviado + "Gemini is AI and can make mistakes."
5. Botão "Sign in" visível — redireciona para accounts.google.com
6. Comportamento confirmado em múltiplas tentativas (fill_input, CDP key events, diferentes URLs)

**Causa provável:** Mudança na política do Google — Flash-Lite gratuito agora requer conta Google.

**Impacto:** Sem Gemini direto nos próximos ciclos. A menos que seja providenciado um login Google para a conta de teste.

---

## Recomendações

1. **🔴 P10, P12, P15: duplo-cegos** — ausentes tanto no Gemini (08/08) quanto no índice web (Exa). Criar conteúdo dedicado urgente:
   - P10: landing page "Enxoval Profissional para Hotel"
   - P12: artigo comparativo "Fornecedores de Enxoval: Compare as Melhores Opções"
   - P15: fortalecer página institucional com SEO para "empresa de enxoval para hotelaria"

2. **🟡 P13: prioridade máxima** — aparecia no Gemini (✅✅) mas SUMIU do índice web Exa. ParaHotel domina. Verificar se houve desindexação ou perda de ranking.

3. **🟢 Fortalecer contra Matinali** — aparece em 13/15 buscas. Analisar estratégia de conteúdo deles.

4. **🔧 Resolver bloqueio do Gemini** — avaliar criar uma conta Google para testes ou usar outro browser com perfil autenticado.

5. **📊 Próximo ciclo (17/08):** priorizar resolver o Gemini OU assumir Exa como baseline web + buscar alternativa para Generative AI (Bing Copilot se disponível na região).

---

## Status Final

```
Executado                       | Evidência                          | Status
Gemini direto                  | Bloqueado (requer login Google)    | ❌ Bloqueado
Exa/Composio (alternativa)     | 11/15 menções (73%)                | ✅ Completo
ChatGPT                        | —                                  | ❌ Não testado
Perplexity                     | —                                  | ❌ Não testado
Copilot                        | —                                  | ❌ Não testado
```

**Ciclo 11/08:** PARCIAL — Gemini bloqueado. Exa executado como alternativa rotulada. NÃO comparável diretamente com ciclos anteriores (Gemini direto).

---

*Relatório gerado por Flávia (Marketing) em 11/08/2026, 09:00 BRT (job 542783c5d7eb).*
*Próximo ciclo: segunda-feira 17/08/2026 09:00 BRT.*
