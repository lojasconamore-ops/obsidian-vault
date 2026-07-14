# Parecer de Crédito — Laércio Bomtempo Hotéis Ltda

**Data da análise:** 15/06/2026
**Analista:** Tiago (Gerente Financeiro)
**Origem:** Orçamento nº 107400 + Relatório Equifax/Boa Vista + tela DEBX (print Sérgio)

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

**Fontes:** SQL Server `hotel-finder` + tela DEBX ERP (print Sérgio Ladeira)

**Cadastro:** ID_DEBX A2051, cliente antigo.

### Histórico de Pedidos (3 faturados + 1 orçamento atual)

| # | Pedido | Data | Status | Valor | Condição |
|---|---|---|---|---|---|
| 1 | 0012234 | 03/10/2024 | Expedição | R$ 2.590,00 | Cartão 5x |
| 2 | 0027120 | 28/03/2025 | Expedição | R$ 3.729,16 | Cartão 5x |
| 3 | 0062797 | 13/10/2025 | Expedição | R$ 1.260,00 | Entrada 50% + 30 dias |
| 4 | 0107400 | 12/06/2026 | **Orçamento** | R$ 3.403,00 | Entrada 50% + 30/60 dias |

### Detalhamento por pedido

**0012234** (03/10/2024) — Cartão 5x — R$ 2.590,00
- 100 un. Fronha Avulsa 50×70cm Percal 180 fios — R$ 9,50/un
- 50 un. Toalha de Banho Suit 70×140cm 408g/m² — R$ 31,80/un

**0027120** (28/03/2025) — Cartão 5x — R$ 3.729,16
- 10 un. Lençol Solteiro 160×250cm Percal 180 fios — R$ 36,76/un
- 8 un. Lençol Casal 220×250cm Percal 180 fios — R$ 50,05/un
- 40 un. Fronha Avulsa 50×70cm Percal 180 fios — R$ 9,60/un
- 6 un. Lençol Queen 250×250cm Percal 180 fios — R$ 59,66/un
- 40 un. Toalha de Banho Suit 70×140cm — R$ 30,85/un
- 40 un. Toalha de Piso Prime 50×80cm — R$ 23,38/un

**0062797** (13/10/2025) — Entrada 50% + 30 dias — R$ 1.260,00
- 100 un. Protetor Travesseiro Impermeável 50×70cm — R$ 12,10/un

### Resumo

| Indicador | Valor |
|---|---|
| Total histórico faturado | R$ 7.579,16 |
| Pedidos faturados | **3** |
| Ticket médio | R$ 2.526,39 |
| Maior pedido | R$ 3.729,16 |
| Primeira compra | 03/10/2024 (20 meses) |
| Última compra faturada | 13/10/2025 |
| Frequência | ~1 pedido a cada 6 meses |

### Evolução do Ticket

R$ 2.590 → R$ 3.729 → R$ 1.260 → R$ 3.403 (atual)

📈 **Crescimento estável.** O pedido atual (R$ 3.403) está dentro do intervalo histórico e 35% acima do ticket médio — variação normal. Todos os pedidos foram faturados com sucesso (Expedição), zero cancelamentos.

### Condições já operadas com sucesso

- ✅ Cartão 5x (2 vezes)
- ✅ Entrada 50% + 30 dias (1 vez)

### Classificação: **Classe B — Bom**
Cliente regular, 20 meses de relacionamento, 3 pedidos faturados com zero cancelamentos. Já operou entrada + prazo com sucesso. Bom histórico.

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
- **Histórico de itens:** Protetores de travesseiro (1ª compra) → toalhas e fronhas (atual) — evolução natural de sortimento
- **Crescimento de ticket:** Dentro do intervalo histórico (R$ 1.260–R$ 3.729), 35% acima da média

✅ **Pedido totalmente coerente** com o segmento, porte e histórico do cliente.

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

Histórico Conamore: Cliente desde 10/2024 (20 meses). 3 pedidos faturados (100% Expedição).
  Total histórico R$ 7,6k | Ticket médio R$ 2,5k | Maior pedido R$ 3,7k.
  Evolução estável. Já operou Entrada 50% + 30 dias e Cartão 5x com sucesso.
  Classe B — Bom.

Score / Bureau: 🏆 789 (Muito Forte) | Prob. 3,0% | 100% pagamento pontual 12 meses.
  Zero atrasos, zero restrições, zero protestos. CNPJ ativo há 18 anos.
  Perfil de bureau EXCEPCIONAL.

Coerência do pedido: Totalmente coerente. Hotel comprando reposição de enxoval
  (toalhas + fronhas). Ticket dentro do intervalo histórico. Mix compatível.

Validação operacional online: 🟢 Operação Forte. Hotel Bomtempo no Google Maps (3.6★),
  telefone ativo, endereço consistente com orçamento.

Condição recomendada: MANTER CONDIÇÕES DA PROPOSTA
  • Entrada 50% (~R$ 1.676,50)
  • Saldo 30/60 dias (~R$ 863,25 + ~R$ 863,25)
  • Exposição líquida de apenas R$ 1.726,50

Justificativa técnica objetiva: Cliente com 20 meses de relacionamento, 3 pedidos
  faturados com sucesso e zero cancelamentos. Bureau excepcional: score 789, 100%
  de pagamentos pontuais, 18 anos de CNPJ. Pedido atual dentro do intervalo histórico
  e coerente com o segmento hoteleiro. Exposição líquida baixíssima (R$ 1.726).
  Condição proposta (50% entrada + 30/60) já operada com sucesso em pedido anterior.
  Soma de histórico interno positivo + bureau impecável + operação real = risco baixo.
```

---

> **Princípio aplicado:** *"Vender com risco inteligente."* — Cliente com bom histórico interno, bureau excepcional e operação real comprovada. Aprovar fortalece o relacionamento.

---

## ⚠️ Nota Técnica — Divergência SQL Server vs DEBX (RESOLVIDA)

**Causa identificada:** O ID_DEBX mudou de formato ao longo do tempo:

| Período | ID_DEBX | ID_DEBX2 |
|---|---|---|
| 2024–03/2025 | `02051` (sem "A", com zero) | 102051 |
| 10/2025 em diante | `A2051` (com "A") | 2051 |

A consulta original `WHERE ID_DEBX = 'A2051'` só capturou os pedidos recentes. Os pedidos 0012234 e 0027120 usam `ID_DEBX = '02051'`. **Mesmo cliente, dois formatos de ID no banco.** Isso indica provável migração ou mudança de padrão no DEBX entre março e outubro de 2025.

**Lição aprendida:** Para garantir cobertura completa, buscar por `Razao_Social` + `ID_DEBX2` (customer id = 2051) em vez de confiar apenas no `ID_DEBX` varchar.
