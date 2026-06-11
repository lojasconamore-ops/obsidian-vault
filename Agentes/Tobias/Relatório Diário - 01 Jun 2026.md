# 📊 Relatório Diário — Tobias (Logística)
**Data:** 01/06/2026 | **Período analisado:** Últimos 60 dias (02/04 a 01/06/2026)

## 🔌 Intelipost API
- **Status:** ✅ Online (0.3ms)
- **Transportadoras ativas:** 8/15
  - Correios Sedex, Frota Interna, Via Pajucara, Jamef, Rodonaves, Pacífico, Rápido Figueiredo, Favorita Transportes
- **Chave API:** ✅ Configurada

## 📈 Resumo 60 dias
| Indicador | Valor |
|-----------|-------|
| Pedidos | 1.110 |
| Receita | R$ 3.673.818,26 |
| Frete total | R$ 48.073,66 (1,31% da receita) |
| Frete médio | R$ 43,31 |
| Ticket médio | R$ 3.309,75 |
| Clientes | 905 |

## 📋 Distribuição por Status
| Status | Pedidos | Valor | Frete |
|--------|--------|-------|-------|
| **Expedição** | 913 (82,3%) | R$ 2.630.827,01 | R$ 38.599,47 |
| Aprovado | 117 (10,5%) | R$ 589.253,87 | R$ 5.549,17 |
| Status D | 12 (1,1%) | R$ 253.987,25 | R$ 750,00 |
| Status G | 32 (2,9%) | R$ 117.230,64 | R$ 1.450,00 |
| Financeiro | 19 (1,7%) | R$ 46.315,67 | R$ 975,00 |
| Orçamento | 15 (1,4%) | R$ 34.480,72 | R$ 700,00 |
| Pendente | 2 (0,2%) | R$ 1.723,10 | R$ 50,02 |

## ⚠️ Alertas Críticos

### 1. Pedidos Pendentes Antigos (>60 dias)
8 pedidos, R$ 12.428,81 parados:
- **0082982** — 145 dias | R$ 251,40 (Carmem L.)
- **0086636** — 123 dias | R$ 167,90 (Rian B.)
- **0090819** — 98 dias | R$ 212,00 (Jociellen)
- **0091187** — 96 dias | R$ 4.630,00 (Mônica S.)
- **0093473** — 82 dias | R$ 149,80 (Conamore SSL)
- **0087307** — 81 dias | R$ 2.777,32 (Brenda K.)
- **0094138** — 77 dias | R$ 1.506,64 (Mônica C.)
- **0094329** — 63 dias | R$ 2.733,75 (Vânia M.)

### 2. Status Não Classificados (D e G)
44 pedidos, R$ 371.217,89 — sem classificação clara no ERP
- Status D: 12 pedidos / R$ 253.987,25
- Status G: 32 pedidos / R$ 117.230,64
- **Recomendação:** Validar com TI/ERP o significado e se estão em fluxo normal

### 3. Alta Concentração em Expedição
913 pedidos (82,3%) em "Expedição" — bottleneck potencial no CD Valinhos
- R$ 2,63MM aguardando processamento/expedição
- **Recomendação:** Monitorar turnaround do picking no CD

### 4. Top 3 Maiores Fretes (últimos 60 dias)
| Pedido | Frete | Valor Total | Vendedor |
|--------|-------|-------------|----------|
| 0103881 | R$ 500,00 | R$ 58.895,50 | Vânia M. |
| 0103412 | R$ 390,20 | R$ 4.245,67 | Vânia M. |
| 0098417 | R$ 350,00 | R$ 3.467,00 | Rian B. |

## 🚛 Transporte
- **Frete médio:** R$ 43,31 (dentro do esperado)
- **Custo frete/receita:** 1,31% — abaixo do benchmark de 3-4%
- **Risco:** Dependência de 8 transportadoras ativas para todo território nacional
- **Oportunidade:** Negociar tabela com transportadoras de maior volume (Jamef, Rodonaves)

## 📅 Última Semana (25-30 Mai)
- ~182 pedidos, ~R$ 549K em receita
- Média diária: ~30 pedidos/dia
- Pico: 29/05 com 55 pedidos (R$ 182K)

## 🏆 Top Vendedores
| Vendedor | Pedidos | Receita | Ticket |
|----------|---------|---------|--------|
| Carlos Manoel da Silva | 165 | R$ 1.006.332,31 | R$ 6.098,98 |
| Brenda K. Campos | 116 | R$ 510.668,49 | R$ 4.402,31 |
| Mônica C. da Silva | 131 | R$ 420.637,49 | R$ 3.210,97 |

## ✅ Recomendações

1. **🟡 Alta — Validar status D e G** — 44 pedidos / R$ 371K sem classificação clara. Solicitar à TI o meaning desses códigos no ERP
2. **🟡 Alta — Pedidos parados >60 dias** — 8 pedidos / R$ 12,4K. Acionar vendedores para desbloqueio ou cancelamento
3. **🟢 Média — Expedição concentrada** — 82% dos pedidos em "Expedição". Verificar se o CD Valinhos está com capacidade OK
4. **🟢 Baixa — Intelipost API healthy** — sem incidentes. Manter monitoramento
5. **💡 Oportunidade — Negociação frete** — Custo frete/receita em 1,31% é baixo, mas pode-se consolidar volume com Jamef/Rodonaves para reduzir tarifas

---

*Relatório gerado em 01/06/2026 08:06 BRT | Fonte: debx.PDV_Detalhes + Intelipost API*
