# Padrão de Diferenciação GEO — Conamore

**Data:** 26/08/2026 · **Definido com Sérgio (lote 2)**

## Motivação

Feedback do Sérgio: descrições e tags idênticas entre produtos parecidos geram:
1. **Thin content** — o Google não dá valor a página sem diferencial e pode deixar de indexar variações.
2. **Canibalização de keywords** — páginas da mesma família competem entre si pela mesma busca.
3. **Violação da regra da biblioteca** — *"variar perguntas por família; evitar repetição mecânica"*.

## Regra central

Cada SKU precisa de um **núcleo único** (abertura + FAQs específicas + keywords focadas), mantendo enxuto apenas o comum: composição, cuidado de lavanderia e "onde comprar".

## Mapas de diferenciação

### Cor (papel no enxoval)
| Cor | Papel |
|---|---|
| Branca | limpeza, inspeção, padronização |
| Cinza | neutro, disfarça uso, contemporâneo |
| Bege | quente, suaviza ambientes claros |
| Azul | diferencia categoria de quarto |
| Rosé | acolhedor, personalidade |
| Verde | frescor |
| Lilás | delicado |
| Argila | terroso, sofisticado |

### Tamanho / cama
| Cama | Aplicação |
|---|---|
| Solteiro | quartos econômicos, ocupação individual |
| Casal | ocupação dupla padrão |
| Queen | intermediário/superior |
| King | suítes, alto padrão |

### Tipo de toalha (função)
- **Banho** → pós-banho, absorção/volume
- **Rosto** → kit por banheiro, higiene
- **Piso** → saída do banho, piso seco

### Linha (diferenciador próprio)
- **Aura** → 100% algodão, fio cardado 24/2
- **Select** → maciez + durabilidade premium
- **Imperial** → fio retorcido, alta gramatura
- **Pezinhos** → desenho de pezinhos em relevo

### Fragrância (amenities)
- **Capim-limão** → cítrico, revigorante
- **Herbal** → suave, neutro

## Aplicação por campo

| Campo | Regra |
|---|---|
| `description` | 1ª frase combina cor+tipo+tamanho+linha (única). FAQs: 3 específicas (1 da cor + 1 do tamanho/tipo) + 3 decisão + 2 autoridade |
| `meta_keywords` | tipo + cor + gramatura + medida (nicho específico); remover genéricos repetidos |
| `meta_description` | especificação única (tipo+tamanho+gramatura+composição); não repetir frase longa da cor (estoura 160) |
| `meta_title` | tipo + linha + cor, ≤ 60 chars |

## Checklist de validação

- [ ] Aberturas da mesma família todas únicas (ex.: 15 Aura → 15 aberturas distintas)
- [ ] Concordância de gênero: "na cor **branca**" vs "lençol **branco**"
- [ ] Sem "é linha em X" (quebrado) → "faz parte da linha X"
- [ ] `title` ≤ 60 · `meta_description` ≤ 160
- [ ] Sem termos banidos (telefones, e-mails, "Nós Fabricamos", "Pronta entrega", "Experimente!")

## Referências

- [[GEO - Biblioteca de 100 FAQs - Conamore|Biblioteca GEO (135 FAQs)]]
- Entregas: `Agentes/Flávia/GEO/Entregas/`
