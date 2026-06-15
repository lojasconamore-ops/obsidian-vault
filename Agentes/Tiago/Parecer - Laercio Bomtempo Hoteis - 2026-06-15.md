# Parecer de Crédito — Laércio Bomtempo Hotéis Ltda

**Data da análise:** 15/06/2026
**Analista:** Tiago (Gerente Financeiro)
**Origem:** Orçamento nº 107400 + Relatório Equifax/Boa Vista

---

## Dados do Cliente

| Campo | Valor |
|---|---|
| Razão Social | LAERCIO BOMTEMPO HOTEIS LTDA |
| Nome Fantasia | LAERCIO BOMTEMPO HOTEIS |
| CNPJ | 09.463.062/0001-04 |
| ID_DEBX | A2051 |
| Endereço | Av. Pref. Erotides Batista, 244 — Jardim Ana Paula, São Gotardo-MG |
| Contato | Danyella — (34) 8883-2388 — hotelbomtempo.sg@gmail.com |
| Representante | Brenda Kaliane Campos dos Santos |
| Fundação | 25/02/2008 (18 anos) |
| Ramo | Hotéis (5510-8/01) |
| Classe Conamore | HOTEL |

---

## Pedido em Análise (Orçamento 107400)

| Item | Qtd | Valor Unit. | Total |
|---|---|---|---|
| Toalha de Piso Prime 50×80cm 570g/m² | 50 | R$ 24,10 | R$ 1.205,00 |
| Toalha de Banho Suit 70×140cm 408g/m² | 60 | R$ 24,40 | R$ 1.464,00 |
| Fronha Avulsa 50×70cm Percal 180 fios | 60 | R$ 11,40 | R$ 684,00 |
| Frete | — | — | R$ 50,00 |
| **Total** | **170** | | **R$ 3.403,00** |

| Condição Proposta | Valor |
|---|---|
| Entrada 50% | ~R$ 1.676,50 |
| Saldo 30 dias | ~R$ 863,25 |
| Saldo 60 dias | ~R$ 863,25 |
| Validade | 17/06/2026 |

---

## Etapa 0 — Lista Negra

✅ **Cliente NÃO pertence à Lista Negra Conamore.**
CNPJ 09.463.062/0001-04 e razão social "LAERCIO BOMTEMPO HOTEIS LTDA" não constam nos 62 registros bloqueados.

---

## Etapa 1 — Histórico Interno Conamore

**Base:** SQL Server `hotel-finder` — `conamore.Customers` + `debx.PDV_Detalhes`

**Cadastro:** ID_DEBX A2051, cliente desde data não especificada (cadastro antigo).

### Histórico de Pedidos (1 registro faturado + 1 orçamento atual)

| # | Pedido | Data | Valor | Status | Condição | Vendedor |
|---|---|---|---|---|---|---|
| 1 | 0062797 | 02/10/2025 | R$ 1.260,00 | Expedição | Entrada 50% + 30 dias | Brenda Kaliane |
| 2 | 0107400 | 12/06/2026 | R$ 3.403,00 | **Orçamento** | Entrada 50% + 30/60 dias | Brenda Kaliane |

### Detalhe do pedido anterior (0062797)

- 100 un. Protetor Travesseiro Impermeável 50×70cm — R$ 12,10/un
- Faturado e expedido com sucesso

### Resumo

| Indicador | Valor |
|---|---|
| Total histórico faturado | R$ 1.260,00 |
| Pedidos faturados | 1 |
| Ticket único | R$ 1.260,00 |
| Condição já operada | Entrada 50% + 30 dias ✅ |

⚠️ **Histórico curto** — apenas 1 compra anterior. O pedido atual (R$ 3.403) representa um crescimento de 2,7× sobre o ticket anterior. Sem dados de atraso ou pontualidade interna.

### Classificação: **Classe B — Bom (preliminar)**
Histórico interno insuficiente para classificação definitiva, mas o único pedido foi faturado com sucesso na mesma condição (entrada 50% + prazo). O bureau compensa a falta de histórico.

---

## Etapa 2 — Score / Bureau (Equifax/Boa Vista)

| Indicador | Valor | Classificação |
|---|---|---|
| **Score** | **789** | 🟢 **Muito Forte** (750+) |
| Prob. inadimplência | 3,0% | 🟢 **Excelente** (≤5%) |
| Pagamento pontual (12 meses) | **100%** em todos os meses | 🟢 **Impecável** |
| Atraso (qualquer faixa) | **Zero** | 🟢 Perfeito |
| Atraso médio | 0 dias | 🟢 |
| Cadastro Positivo | Participante com informação | 🟢 |
| Pendências/restrições | Nada Consta | 🟢 |
| Protestos | Nada Consta | 🟢 |
| Cheques | Nada Consta | 🟢 |
| Situação CNPJ | Ativo (desde 25/02/2008) | 🟢 **18 anos** |
| Consultas (12 meses) | 1 (Conamore 07/10/2025) | Normal |
| Última compra (mercado) | mai/2026 | Operação ativa |

**Conclusão Bureau:** 🏆 **Perfil excepcional.** Score 789, 100% de pagamentos pontuais por 12 meses consecutivos, zero atrasos em qualquer faixa, zero restrições. Empresa com 18 anos de atividade. Um dos melhores perfis de bureau vistos.

---

## Etapa 3 — Coerência Operacional do Pedido

**Hotel Bomtempo** é um hotel estabelecido em São Gotardo-MG.

- **Segmento:** Hotelaria — classe HOTEL no cadastro Conamore
- **Mix:** Toalhas de piso + banho + fronhas — itens típicos de reposição hoteleira
- **Volume:** 170 peças — coerente com hotel de pequeno/médio porte
- **Evolução:** De protetores de travesseiro (1ª compra) para toalhas e fronhas (2ª compra) — progressão natural de sortimento
- **Crescimento de ticket:** 2,7× (R$ 1.260 → R$ 3.403) — salto moderado, justificável como ampliação de mix

✅ **Pedido coerente** com o segmento e porte do cliente.

---

## Etapa 4 — Exposição Real da Conamore

| Componente | Valor |
|---|---|
| Total do pedido | R$ 3.403,00 |
| Entrada (50%) | ~R$ 1.676,50 |
| **Exposição líquida** | **~R$ 1.726,50** |

🟢 **Exposição baixa** — valor absoluto pequeno. Saldo parcelado em 30 e 60 dias (~R$ 863 por parcela).

---

## Etapa 5 — Validação Operacional Online

| Fonte | Status | Evidência |
|---|---|---|
| Google Maps | ✅ | Hotel Bomtempo — Av. Pref. Erotides Batista, 244, São Gotardo-MG |
| Avaliações | ✅ | 3.6★ — hotel ativo e avaliado |
| Telefone | ✅ | (34) 3671-2387 |
| Endereço | ✅ | Coincide com o do orçamento |
| Site próprio | ⚠️ | Não localizado |
| Booking/Expedia | ⚠️ | Não verificado diretamente |

🟢 **Operação Forte** — hotel real, estabelecido, presente no Google Maps com avaliações, endereço consistente com orçamento. CNPJ ativo há 18 anos.

---

## Parecer Final

```
Etapa 0 — Lista Negra: ✅ NÃO consta
Parecer: ✅ APROVAR

Nível de risco: BAIXO

Histórico Conamore: Cliente com 1 pedido anterior faturado (10/2025, R$ 1.260).
  Já operou Entrada 50% + 30 dias com sucesso. Histórico interno curto mas limpo.
  Classe B — Bom (preliminar).

Score / Bureau: 🏆 789 (Muito Forte) | Prob. 3,0% | 100% pagamento pontual 12 meses.
  Zero atrasos, zero restrições, zero protestos. CNPJ ativo há 18 anos.
  Perfil de bureau EXCEPCIONAL.

Coerência do pedido: Totalmente coerente. Hotel comprando reposição de enxoval
  (toalhas + fronhas). Mix compatível com o segmento. Evolução natural do 1º pedido.

Validação operacional online: 🟢 Operação Forte. Hotel Bomtempo no Google Maps (3.6★),
  telefone ativo, endereço consistente com orçamento.

Condição recomendada: MANTER CONDIÇÕES DA PROPOSTA
  • Entrada 50% (~R$ 1.676,50)
  • Saldo 30/60 dias (~R$ 863,25 + ~R$ 863,25)
  • Exposição líquida de apenas R$ 1.726,50

Justificativa técnica objetiva: Apesar do histórico interno curto (apenas 1 compra),
  o bureau é excepcional: score 789, 100% de pagamentos pontuais por 12 meses,
  zero atrasos, 18 anos de CNPJ ativo. Hotel real verificado no Google Maps.
  Exposição líquida baixíssima (R$ 1.726). Pedido coerente com o segmento.
  O risco de inadimplência de 3% é o menor observado entre as análises recentes.
```

---

> **Princípio aplicado:** *"Histórico Conamore vale mais que score externo — mas quando o histórico é curto e o score é excepcional, o bureau compensa."*
