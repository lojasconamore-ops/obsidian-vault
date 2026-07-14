# Parecer de Crédito — Sofia Homes Ltda

**Data da análise:** 15/06/2026
**Analista:** Tiago (Gerente Financeiro)
**Origem:** Orçamento nº 107696 + Relatório Equifax/Boa Vista

---

## Dados do Cliente

| Campo | Valor |
|---|---|
| Razão Social | SOFIA HOMES LTDA |
| CNPJ | 18.185.285/0001-48 |
| Nome Fantasia | Sofia Homes |
| ID_DEBX | 86831 |
| Endereço | Rua Gustavo Ambrust, 464 — Nova Campinas, Campinas-SP |
| Contato | Johnny Zanelli — johnny.zanelli@sofiahomes.com.br — (19) 97825-0652 |
| Representante | Carlos Manoel da Silva |
| Fundação | 24/05/2013 (13 anos) |
| Ramo | Ativ Interm Agenciamento Serv Neg Geral (7490-1/04) |
| Faixa func. | 1 a 19 |

---

## Pedido em Análise (Orçamento 107696)

| Item | Qtd | Valor Unit. | Total |
|---|---|---|---|
| Toalha Banhão Confort Plus 75×150cm 500g/m² | 100 | R$ 46,10 | R$ 4.610,00 |
| Toalha Rosto Confort Plus 50×80cm 500g/m² | 150 | R$ 14,20 | R$ 2.130,00 |
| **Total** | **250** | | **R$ 6.740,00** |

| Condição Proposta | Valor |
|---|---|
| Entrada 50% (Pix) | R$ 3.370,00 |
| Boleto 30 dias | R$ 1.685,00 |
| Boleto 60 dias | R$ 1.685,00 |
| Frete | Cliente retira |
| Validade | 15/06/2026 |

---

## Etapa 0 — Lista Negra

✅ **Cliente NÃO pertence à Lista Negra Conamore.**
CNPJ 18.185.285/0001-48 e razão social "SOFIA HOMES LTDA" não constam nos 62 registros bloqueados.

---

## Etapa 1 — Histórico Interno Conamore

**Base:** SQL Server `hotel-finder` — `conamore.Customers` + `debx.PDV_Detalhes`

**Cadastro:** ID_DEBX 86831, desde 17/12/2024 (~18 meses).

### Histórico de Pedidos (7 registros — todos Expedição)

| # | Pedido | Data | Valor | Condição | Vendedor |
|---|---|---|---|---|---|
| 1 | 0017069 | 18/12/2024 | R$ 97,50 | Cartão 1x (Master) | Gabriel Gonçalves |
| 2 | 0019667 | 06/02/2025 | R$ 3.815,00 | Cartão 5x (Master) | Carlos Manoel |
| 3 | 0026945 | 25/03/2025 | R$ 8.442,00 | Entrada 50% + 30/60 dias | Carlos Manoel |
| 4 | 0028901 | 04/04/2025 | R$ 54,90 | À Vista (amostra grátis) | Carlos Manoel |
| 5 | 0054154 | 12/08/2025 | R$ 9.045,00 | Entrada 50% + 30/60 dias | Carlos Manoel |
| 6 | 0092650 | 06/03/2026 | R$ 138,10 | Cartão 1x (Visa) | Carlos Manoel |
| 7 | 0093247 | 10/03/2026 | R$ 11.734,00 | Cartão 6x (Increazy) | Carlos Manoel |

### Resumo

| Indicador | Valor |
|---|---|
| Total histórico | R$ 33.326,50 |
| Ticket médio | R$ 4.760,93 |
| Maior pedido | R$ 11.734,00 (03/2026) |
| Primeira compra | 18/12/2024 |
| Última compra | 10/03/2026 |
| Frequência | ~1 pedido a cada 2-3 meses |
| Status | 7/7 Expedição (100% faturados, zero cancelamentos) |

### Evolução do Ticket

R$ 97 → R$ 3.815 → R$ 8.442 → R$ 9.045 → R$ 11.734

📈 **Crescimento gradual e saudável.** O pedido atual (R$ 6.740) está dentro do intervalo histórico e abaixo do maior pedido (R$ 11.734).

### Condições já operadas com sucesso

- ✅ Cartão 1x, 5x, 6x
- ✅ Entrada 50% + saldo 30/60 dias (2x — pedidos 0026945 e 0054154)
- ✅ À vista / amostra

### Classificação: **Classe B — Bom**
Cliente regular, confiável, sem atrasos registrados no fluxo de expedição. Todos os pedidos foram faturados com sucesso. Já operou a mesma condição proposta (Entrada 50% + 30/60) em duas ocasiões anteriores.

---

## Etapa 2 — Score / Bureau (Equifax/Boa Vista)

| Indicador | Valor | Classificação |
|---|---|---|
| Score | 702 | 🟢 Forte (700–749) |
| Prob. inadimplência | 6,0% | 🟡 Administrável (6–8%) |
| Cadastro Positivo | Participante com informação | 🟢 Positivo |
| Pendências/restrições | Nada Consta | 🟢 Limpo |
| Protestos | Nada Consta | 🟢 Limpo |
| Cheques devolvidos | Nada Consta | 🟢 Limpo |
| Situação CNPJ | Ativo (desde 24/05/2013) | 🟢 13 anos |
| Consultas (12 meses) | 5 (2 da Conamore) | Normal |

**Conclusão Bureau:** Perfil limpo, score forte, sem qualquer restrição. Empresa madura (13 anos). Probabilidade de inadimplência de 6% é administrável.

---

## Etapa 3 — Coerência Operacional do Pedido

**Sofia Homes** é uma administradora profissional de imóveis para temporada (Airbnb, Booking, Expedia), com **+95 unidades sob gestão** e **85% de taxa de ocupação**.

- **Segmento:** Gestão de short-stay / Airbnb — compatível com hotelaria
- **Mix:** Toalhas banhão (100 un) + rosto (150 un) — reposição de enxoval para múltiplas unidades
- **Volume:** 250 peças para 95+ unidades → ~2,6 peças por unidade — coerente com reposição
- **Personalização:** Não identificada (sem bordado/silk)

✅ **Pedido totalmente coerente** com o porte e operação do cliente.

---

## Etapa 4 — Exposição Real da Conamore

| Componente | Valor |
|---|---|
| Total do pedido | R$ 6.740,00 |
| Entrada (50% Pix) | R$ 3.370,00 |
| **Exposição líquida** | **R$ 3.370,00** |

🟢 **Exposição baixa** — 50% do pedido já coberto na entrada. Saldo parcelado em 30 e 60 dias (R$ 1.685 por parcela).

---

## Etapa 5 — Validação Operacional Online

| Fonte | Status | Evidência |
|---|---|---|
| Site próprio | ✅ | sofiahomes.com.br — profissional, ativo |
| Google Maps | ✅ | Endereço comercial: Rua Ana Jarvis, 38, Cambuí, Campinas |
| Airbnb/Booking | ✅ | Integração confirmada no site |
| Instagram | ✅ | Link no site |
| LinkedIn | ✅ | Link no site |
| Imprensa | ✅ | Menções no GRI Club |

**Dados do site:**
- "+95 unidades sob gestão"
- "85% taxa de ocupação"
- "+19.800 noites alugadas"
- "+1.400 reviews de hóspedes"
- "Maior gestora de short-stay de Campinas"
- Equipe própria de limpeza, manutenção e governança

🟢 **Operação Forte** — empresa real, madura, com presença digital robusta e consistente.

---

## Parecer Final

```
Etapa 0 — Lista Negra: ✅ NÃO consta
Parecer: ✅ APROVAR

Nível de risco: BAIXO

Histórico Conamore: Cliente desde 12/2024. 7 pedidos faturados (100% Expedição).
  Total histórico R$ 33,3k | Ticket médio R$ 4,7k | Maior pedido R$ 11,7k.
  Evolução saudável e gradual. Já operou Entrada 50% + 30/60 com sucesso (2x).
  Classe B — Bom.

Score / Bureau: 702 (Forte) | Prob. 6,0% | Cadastro Positivo ativo.
  Sem restrições, protestos ou cheques. CNPJ ativo há 13 anos.

Coerência do pedido: Totalmente coerente. Gestora de 95+ unidades de temporada
  comprando reposição de enxoval (toalhas). Volume proporcional ao porte.

Validação operacional online: 🟢 Operação Forte. Site profissional, presença em
  múltiplas plataformas, imprensa, +1.400 reviews.

Condição recomendada: MANTER CONDIÇÕES DA PROPOSTA
  • Entrada 50% (R$ 3.370,00) via Pix
  • Saldo 30/60 dias (R$ 1.685,00 + R$ 1.685,00) via boleto
  • Cliente retira

Justificativa técnica objetiva: Cliente recorrente com 18 meses de histórico
  limpo (7/7 pedidos faturados, zero cancelamentos), score forte (702), sem
  qualquer restrição, operação real comprovada (95+ unidades, site ativo,
  imprensa). Já operou a mesma condição proposta em 2 ocasiões anteriores.
  Pedido atual (R$ 6.740) abaixo do maior ticket histórico (R$ 11.734).
  Exposição líquida de apenas R$ 3.370 (50% do pedido). Risco baixo.
```

---

> **Princípio aplicado:** *"Vender com risco inteligente."* — Cliente com histórico interno positivo e operação comprovada. Aprovar fortalece o relacionamento e a recorrência.
