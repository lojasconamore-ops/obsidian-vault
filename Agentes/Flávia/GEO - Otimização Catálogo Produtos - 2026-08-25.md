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
- [ ] Aguardar arquivos (planilha GEO otimizada + CSV otimizado) para aprender o estilo exato
- [ ] Calibrar estilo com Sérgio
- [ ] Escalar para o restante do catálogo

## Bloqueio de acesso

Os arquivos gerados ("Baixar a planilha GEO otimizada" e "Baixar o CSV otimizado") ficam atrás de **Cloudflare challenge** no endpoint `backend-anon/share/.../file_from_message/...` — não foi possível baixar sem login. Obter os arquivos diretamente com o Sérgio.

---

*Extraído por Flávia (Marketing) em 25/08/2026 do chat compartilhado por Sérgio.*
