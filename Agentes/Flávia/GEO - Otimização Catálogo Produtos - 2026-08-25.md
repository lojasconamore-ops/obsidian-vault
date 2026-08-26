# GEO — Otimização de Catálogo de Produtos (FAQ Site Conamore) | 25/08/2026

**Fonte:** ChatGPT (Sérgio Ladeira), chat compartilhado em 25/08/2026
**Link:** https://chatgpt.com/share/6a8e3cda-d614-83e9-b22a-af1b5576a81a
**Título do chat:** FAQ Site Conamore
**Tipo:** Execução de GEO/SEO em escala no catálogo de produtos
**Conexão:** dá continuidade à [[GEO - Auditoria ChatGPT - 2026-08-11]] (P0: corrigir inconsistências de produtos)

---

## O que é este projeto

Aplicar a estratégia **comercial + SEO/GEO** definida com o ChatGPT na auditoria de 11/08 **em escala ao catálogo de produtos** da Conamore. Começou como um "primeiro exercício" com **4 produtos** para calibrar o estilo antes de rodar o restante do catálogo.

---

## Escopo do trabalho (regras rígidas)

- **NÃO alterar:** `sku` e `name` — ficam exatamente como estão.
- **TRABALHAR SOMENTE em 4 campos:**
  1. `description` — incluir **FAQs específicas de cada produto** (lógica GEO)
  2. `meta_title`
  3. `meta_keywords`
  4. `meta_description`

## Formato de saída

CSV com as mesmas colunas e na MESMA ordem do arquivo de entrada:

```
sku, name, description, meta_title, meta_keywords, meta_description
```

## Método (lógica GEO)

- **FAQs embutidas na description** — perguntas específicas do produto para rankear em respostas de IA (generative engines).
- Seguir a **estratégia comercial + SEO/GEO** já definida (ver auditoria 11/08).
- Estilo deve ser **calibrado nos 4 primeiros produtos** antes de escalar.

## Controle de qualidade

- Criar aba **"Observações"** para sinalizar inconsistências — **NUNCA corrigir arbitrariamente**.
- **Exemplo real encontrado:** SKU `29113011` → `name` informa **150x220 cm**, mas a `description` original informa **1,50 x 2,00 m**. Sinalizar para conferência, não corrigir por conta própria.

## Produto de referência (exemplo visual do Sérgio)

- **Jogo de Lençol King Duplo Amore 150 Fios 100% Algodão**
- Description original tem: diferencial (percal 150 fios, 100% algodão, elástico), composição/conteúdo (medidas dos lençóis e fronhas), e chamada de cross-sell (combine com colchas/cobreleitos/cobertores Conamore).

---

## Status

- [x] Primeiro exercício (4 produtos) — feito pelo ChatGPT
- [x] Arquivo otimizado recebido do Sérgio (25/08) — estilo extraído
- [ ] Calibrar estilo com Sérgio
- [ ] Escalar para o restante do catálogo

---

## 📐 Guia de estilo — extraído dos 4 produtos otimizados

### Estrutura da `description` (HTML)

```
<p><strong>[Produto + especificação-chave] - Conamore</strong></p>
<p>[Parágrafo 1: benefício + posicionamento para hotelaria]</p>
<p>[Parágrafo 2: composição/material + características operacionais]</p>
<p><strong>Características:</strong></p>
<ul><li>...</li> (4–8 bullets)</ul>
[Opcional] <p><strong>Dimensões/Gramatura/Composição/Conteúdo:</strong> valor</p>
<h3>Perguntas frequentes</h3>
<p><strong>Q1?</strong><br />A1.</p>  ← 5–8 pares de Q&A
<p><strong>Onde comprar [categoria] para hotelaria?</strong><br />A Conamore é especializada...</p>  ← SEMPRE a última
```

### Regras de conteúdo

1. **Público B2B hoteleiro**, não consumidor final — citar sempre: hotéis, pousadas, motéis, imóveis de temporada/Airbnb.
2. **FAQ = perguntas que o dono/gestor faria ao ChatGPT.** Sequência típica:
   - "X é indicado para hotel?" → Sim, porque…
   - "X é indicado para pousada/motel?" → Sim…
   - "X é indicado para Airbnb?" → Sim…
   - Pergunta técnica (gramatura, fios, material, medida)
   - "Como escolher X para hotel?" / "Qual gramatura ideal?"
   - **Última (fixa):** "Onde comprar X para hotelaria?" → posiciona a Conamore como especialista.
3. **Respostas informativas, não venda agressiva** — tom consultivo, mas sempre concluem com autoridade Conamore.
4. **Inconsistência → sinalizar, nunca corrigir** (ex.: medidas divergentes). Preservar `name` sempre.

### `meta_title` (~47–52 caracteres)

Padrão: `[Produto] [especificação] | Conamore`
- "Cobertor Microfibra Solteiro para Hotel Bege | Conamore" (52)
- "Protetor de Travesseiro Impermeável 50x70 | Conamore" (52)
- "Fronha para Hotel 50x70 Confort 180 Fios | Conamore" (50)
- "Toalha de Banho Hotel Quality 410 g/m² | Conamore" (47)

### `meta_keywords` (~7–8 termos, minúsculas, vírgula+espaço)

Padrão: categoria + produto + especificação + públicos (pousada, motel, Airbnb) + "enxoval profissional".
- Ex.: `cobertor para hotel, cobertor microfibra solteiro, cobertor hotelaria, manta para hotel, cobertor para pousada, cobertor para Airbnb, enxoval profissional`

### `meta_description` (~126–137 caracteres)

Padrão: `[Produto + especificação] para hotelaria. [benefícios principais]. [indicação de público].`

---

## Produtos do exercício (referência)

| SKU | Produto |
|---|---|
| 29113011 | Cobertor para Hotel Microfibra Solteiro 150X220cm Bege |
| 15709 | Protetor Travesseiro Impermeável para Hotel 50x70cm |
| 16446 | Fronha para Hotel 50x70cm Confort Percal 180 Fios Misto |
| 18082 | Toalha de Banho Quality Hotelaria 70x140cm 410g/m² |

**Observação registrada:** SKU 29113011 → `name` diz 150x220 cm, description original diz 1,50 x 2,00 m (medida mantida e sinalizada como "Dimensões informadas no cadastro").

---

*Extraído por Flávia (Marketing) em 25/08/2026 do chat compartilhado por Sérgio.*
