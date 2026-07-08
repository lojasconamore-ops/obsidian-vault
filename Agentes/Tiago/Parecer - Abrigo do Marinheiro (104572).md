# Parecer de Crédito — ABRIGO DO MARINHEIRO (REVISADO)

**Data da análise:** 08/07/2026
**Analista:** Tiago (Gerente Financeiro)
**Pedido:** 0104572
**Bureau:** Equifax | Boa Vista — 08/07/2026 17:28

---

## Dados do Cliente

| Campo | Valor |
|---|---|
| **Razão Social** | ABRIGO DO MARINHEIRO |
| **Nome Fantasia** | DPTO REG DO ABRIGO DO MARINHEIRO EM NOVA FRIBURGO |
| **CNPJ** | 72.063.654/0019-02 |
| **ID_DEBX** | A5549 |
| **Endereço** | Av. Gov. Geremias de Mattos Fontes, S/N, Centro, Nova Friburgo-RJ |
| **Natureza Jurídica** | Associação Privada (399-9) |
| **Abertura** | 28/10/2009 (16+ anos) |
| **Situação** | ATIVA |
| **Faixa de funcionários** | 100 a 499 |
| **Contato** | Jonathan — (22) 99813-0577 |
| **E-mail** | abrigo@abrigo.org.br |
| **Vendedora** | BRENDA KALIANE CAMPOS DOS SANTOS |

---

## Dados do Pedido

| Campo | Valor |
|---|---|
| **Nº Orçamento** | 0104572 |
| **Emissão** | 22/05/2026 |
| **Validade** | 06/07/2026 |
| **Condição solicitada** | BOLETO 30/60/90 DIAS |
| **Entrada** | R$ 0,00 |
| **Total produtos** | R$ 11.520,00 |
| **Frete** | R$ 50,00 |
| **Total pedido** | **R$ 11.570,00** |

---

## Etapa 0 — Lista Negra Conamore

✅ **Cliente NÃO pertence à Lista Negra Conamore.**

---

## Etapa 1 — Histórico Interno Conamore

**Hotel Finder (SQL Server):** Cliente localizado — ID_DEBX A5549.

**debx.PDV_Detalhes:**
| Pedido | Data | Status | Valor | Condição |
|---|---|---|---|---|
| 0104572 | 22/05/2026 | Orçamento | R$ 11.570,00 | À VISTA |
| 0104520 | 22/05/2026 | Orçamento | R$ 9.355,22 | À VISTA |

- **2 registros, ambos ORÇAMENTO — nenhum faturado.**
- **Sem histórico real de pagamento na Conamore.**

**Classificação:** ⚠️ Sem histórico — primeira compra efetiva.

---

## Etapa 2 — Score / Bureau (Equifax | Boa Vista)

| Indicador | Valor | Avaliação |
|---|---|---|
| **Score Aprovação PJ** | **741** | 🟢 Forte (700-749) |
| **Probabilidade de Inadimplência** | **4,0%** | 🟢 Excelente (até 5%) |
| **Cadastro Positivo** | Participante com informação | 🟢 Positivo |
| **Pagamento Pontual** | **100%** nos últimos 12 meses | 🟢 Impecável |
| **Atraso médio** | **0 dias** | 🟢 |
| **Pendências financeiras** | Nada Consta | 🟢 |
| **Cheques devolvidos** | Nada Consta | 🟢 |

### 🚨 PROTESTOS — ATIVOS

| # | Data | Valor | Cartório | Cidade/UF | Vencimento |
|---|---|---|---|---|---|
| 1 | 09/01/2025 | R$ 17.878,85 | 3º Cartório | Rio de Janeiro-RJ | 18/12/2024 |
| 2 | 14/03/2024 | R$ 265,90 | 2º Cartório | São Pedro da Aldeia-RJ | 18/01/2023 |

**Total protestado: R$ 18.144,75**

### ⚠️ REGRA DA POLÍTICA:

> **"Restrição ativa relevante SUPERA score."**
> *Exemplo da política: score 750 + dívida ativa relevante → ❌ reprovar faturado*

**Aqui temos:** Score 741 (bom) + **2 protestos ativos** (R$ 18.144,75) → a restrição SUPERA o score.

---

## Etapa 3 — Coerência Operacional do Pedido

✅ **100% coerente.** Mix hoteleiro (fronhas + toalhas) para um hotel real (Casa do Velho Marinheiro).

---

## Etapa 4 — Exposição Real da Conamore

| Item | Valor |
|---|---|
| Total do pedido | R$ 11.570,00 |
| Entrada | R$ 0,00 |
| **Exposição líquida** | **R$ 11.570,00 (100%)** |

---

## Etapa 5 — Validação Operacional Online

| Fonte | Resultado | Sinal |
|---|---|---|
| **Google Maps** | "Casa do Velho Marinheiro" — Hotel, **4.8★** | 🟢 |
| **Site institucional** | abrigo.org.br — ativo | 🟢 |
| **CNPJ (Receita WS)** | 16+ anos, ativo | 🟢 |
| **Equifax** | 19 consultas nos últimos 12 meses | 🟢 |

**Classificação:** 🟢 **Operação forte.** O hotel é real e bem avaliado.

---

## PARECER FINAL (REVISADO)

### ❌ NÃO CONCEDER CRÉDITO FATURADO

**Nível de risco:** 🔴 **ALTO** — Protestos ativos superam score.

### Justificativa técnica:

O bureau Equifax revelou **2 protestos ativos** totalizando **R$ 18.144,75**, sendo o mais recente de **09/01/2025** (R$ 17.878,85 — 3º Cartório Rio de Janeiro). A política de crédito é inequívoca:

> *"Restrição ativa relevante supera score. Exemplo: score 750 + dívida ativa relevante → reprovar faturado."*

O score 741 e os 100% de pagamento pontual são **anulados** pela presença de protestos ativos e recentes — a dívida de R$ 17.878,85 venceu em dez/2024 e foi protestada em jan/2025, há apenas 6 meses.

### Condições permitidas (sem risco Conamore):

| Método | Detalhe |
|---|---|
| ✅ **PIX antecipado** | Pagamento integral antes do faturamento |
| ✅ **TED antecipado** | Pagamento integral antes do faturamento |
| ✅ **Cartão de crédito** | À vista ou parcelado (risco da operadora) |

### Se insistir em faturado:

Aprovação somente mediante **autorização excepcional da diretoria (Sérgio Ladeira)**, com análise qualitativa dos protestos (origem, contestação, baixa pendente) e possivelmente com entrada maior que 25%.

---

## Resumo visual

| Fator | Sinal | Peso |
|---|---|---|
| Score Equifax 741 | 🟢 Forte | — |
| PD 4,0% | 🟢 Excelente | — |
| Pagamento 100% pontual | 🟢 Impecável | — |
| **🚨 2 protestos ativos (R$ 18.144,75)** | 🔴 **GRAVE** | **SUPERA TUDO** |
| Histórico Conamore | ⚠️ Sem histórico | Primeira compra |
| Operação real (Google Maps 4.8★) | 🟢 Confirmada | Não mitiga protesto |

---

*Análise conduzida conforme Política de Crédito Conamore v1.0 — 6 etapas obrigatórias.*
*Parecer revisado em 08/07/2026 após recebimento do relatório Equifax | Boa Vista.*
