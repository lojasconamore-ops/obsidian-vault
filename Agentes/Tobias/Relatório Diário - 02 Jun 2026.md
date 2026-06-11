# 📊 Relatório Diário — Tobias (Logística)
**Data:** 02/06/2026 | **Período analisado:** Últimos 60 dias (03/04 a 02/06/2026)

## 🔌 Intelipost API
- **Status:** ✅ Online (1.0ms)
- **Transportadoras ativas:** 8/15
  - Correios Sedex, Frota Interna, Via Pajucara, Jamef, Rodonaves, Pacífico, Rápido Figueiredo, Favorita Transportes
- **Chave API:** ✅ Configurada e funcional
- **Cotação de frete:** ✅ Operacional (teste Campinas→SP respondeu com 4 opções)
- **Tracking:** ✅ Operacional (ex: pedido 100-0011640-2 rastreado)

## 📈 Resumo 60 dias (rolling)

| Indicador | Ontem (01/06) | Hoje (02/06) | Δ |
|-----------|:-------------:|:------------:|:-:|
| Pedidos | 1.110 | 1.107 | -3 |
| Receita | R$ 3.673.818,26 | R$ 3.649.093,58 | -R$ 24.724,68 |
| Frete total | R$ 48.073,66 | R$ 48.087,52 | +R$ 13,86 |
| Frete médio | R$ 43,31 | R$ 43,44 | +R$ 0,13 |
| Ticket médio | R$ 3.309,75 | R$ 3.296,38 | -R$ 13,37 |
| Clientes | 905 | 904 | -1 |

> Nota: Rolling 60d — entrada de Jun/01 (18 pedidos, R$ 40,6K) compensou saída de Abr/03.

## 📋 Distribuição por Status

| Status | Pedidos | % | Valor | Frete | Δ vs Ontem |
|--------|:-------:|:-:|-------|-------|:----------:|
| **Expedição** | 935 | 84,5% | R$ 2.879.737,66 | R$ 39.613,33 | +22 🟢 |
| Aprovado | 86 | 7,8% | R$ 313.220,48 | R$ 4.399,17 | -31 🟢 |
| Status D | 20 | 1,8% | R$ 273.636,91 | R$ 1.050,00 | **+8 🟡** |
| Status G | 30 | 2,7% | R$ 105.949,24 | R$ 1.350,00 | -2 |
| Financeiro | 19 | 1,7% | R$ 40.391,01 | R$ 925,00 | — |
| Orçamento | 15 | 1,4% | R$ 34.435,18 | R$ 700,00 | — |
| Pendente | 2 | 0,2% | R$ 1.723,10 | R$ 50,02 | — |

## ⚠️ Alertas Críticos

### 🟡 1. Pedidos Pendentes Antigos (>60 dias)
**Mesmos 8 pedidos do dia anterior, agora +1 dia parados.**
R$ 12.428,81 parados — sem evolução:

| Pedido | Dias | Valor | Vendedor |
|--------|:---:|-------|----------|
| 0082982 | **146** | R$ 251,40 | Carmem L. |
| 0086636 | **124** | R$ 167,90 | Rian B. |
| 0090819 | **99** | R$ 212,00 | Jociellen |
| 0091187 | **97** | R$ 4.630,00 | Mônica S. |
| 0093473 | **83** | R$ 149,80 | Conamore SSL |
| 0087307 | **82** | R$ 2.777,32 | Brenda K. |
| 0094138 | **78** | R$ 1.506,64 | Mônica C. |
| 0094329 | **64** | R$ 2.733,75 | Vânia M. |

### 🟡 2. Status D — Crescimento Acelerado (+67% em 1 dia)
Status D saltou de **12 → 20 pedidos** desde ontem.
R$ 273.636,91 em pedidos com classificação indefinida.
**⚠️ Necessário validar o significado de "D" e "G" com TI/ERP.**

### 🟡 3. Pedido 100-0011640-2 — Risco de Atraso
- **Transportadora:** Via Pajucara Standard (8 volumes, 53 kg)
- **Valor frete:** R$ 408,94
- **Previsão:** 02/06/2026 (hoje!)
- **Status:** Em trânsito — último scan: 01/06 06:15 em SÃO JOSÉ DOS CAMPOS
- **Destino:** CAMPOS DO JORDÃO-SP (distância ~100km de SJC)
- **Risco:** 🟡 Pode chegar hoje, mas timeline está apertada

### 🟢 4. Alta Concentração em Expedição (84,5%)
935 pedidos, R$ 2,88MM aguardando processamento/expedição.
↑ 22 pedidos desde ontem — fluxo positivo de Aprovado → Expedição.

## 🚛 Transporte & Custos

| Indicador | Valor |
|-----------|-------|
| Frete total (60d) | R$ 48.087,52 |
| Frete médio | R$ 43,44 |
| **Frete/Receita** | **1,32%** (benchmark: 3-4%) ✅ Saudável |
| Top frete | R$ 500,00 (pedido 0103881 — Vânia M.) |

### Top 5 Maiores Fretes (60d)
| Pedido | Frete | Valor Total | Vendedor |
|--------|:-----:|:-----------:|----------|
| 0103881 | R$ 500,00 | R$ 58.895,50 | Vânia M. |
| 0103412 | R$ 390,20 | R$ 4.245,67 | Vânia M. |
| 0098417 | R$ 350,00 | R$ 3.467,00 | Rian B. |
| 0103930 | R$ 300,00 | R$ 34.603,60 | Mônica C. |
| 0097488 | R$ 270,00 | R$ 2.608,80 | Rian B. |

## 🏆 Top 5 Vendedores (Receita)
| Vendedor | Pedidos | Receita | Ticket |
|----------|:-------:|:-------:|:------:|
| Carlos Manoel da Silva | 163 | R$ 1.002.577,91 | R$ 6.150,78 |
| Brenda K. Campos | 113 | R$ 489.535,49 | R$ 4.332,17 |
| Mônica C. da Silva | 132 | R$ 423.264,49 | R$ 3.206,55 |
| Mônica dos S. Reis | 155 | R$ 419.436,87 | R$ 2.706,04 |
| Vânia M. Oliveira | 102 | R$ 389.881,91 | R$ 3.822,37 |

## 📅 Atividade Recente (últimos 7 dias úteis)

| Data | Pedidos | Receita | Frete |
|:----:|:-------:|:-------:|:-----:|
| 25/05 | 40 | R$ 119.449 | R$ 2.181 |
| 26/05 | 33 | R$ 90.522 | R$ 1.350 |
| 27/05 | 31 | R$ 84.031 | R$ 1.200 |
| 28/05 | 20 | R$ 54.497 | R$ 975 |
| 29/05 | 52 | R$ 170.352 | R$ 1.724 |
| 01/06 | 18 | R$ 40.642 | R$ 900 |
| **Média** | **32/dia** | **R$ 93.248/dia** | **R$ 1.388/dia** |

## 🔍 Descoberta Técnica — Gap Intelipost ↔ ERP
- **Números de pedido do ERP** (ex: 0022046) **NÃO correspondem** ao formato usado na Intelipost
- **Formato Intelipost:** `100-{NF}-{série}` (ex: 100-0011640-2)
- **Impacto:** Tracking automático via consulta não funciona com os números do PDV_Detalhes
- **Ação necessária:** Mapear Numero_Pedido (ERP) → Intelipost order_number via NF

## ✅ Recomendações

1. **🔴 Alta — Validar Status D e G com TI/ERP**
   Status D saltou 67% (12→20) em 24h. R$ 273K+ sem classificação clara. Pode ser bottleneck ou erro de fluxo.

2. **🟡 Alta — Desbloquear 8 pedidos parados >60 dias**
   R$ 12.428,81 travados. Acionar vendedores hoje — 3 pedidos já passam de 100 dias.

3. **🟡 Média — Monitorar pedido 100-0011640-2 (Via Pajucara)**
   Previsão hoje, último scan ontem em SJC. Campos do Jordão fica a ~1h30 de SJC.

4. **🟢 Média — Mapear gap ERP → Intelipost**
   Sem mapeamento, tracking automático não funciona. Solicitar à TI view com NF por pedido.

5. **🟢 Baixa — Intelipost API saudável**
   Status, cotação e tracking operacionais. Nenhum incidente.

6. **💡 Oportunidade — Consolidar frete com Jamef/Rodonaves**
   1,32% frete/receita é baixo para o mercado. Com volume crescente, renegociar tabela pode gerar economia em fretes acima de R$ 200.

---

*Relatório gerado em 02/06/2026 08:09 BRT | Fonte: debx.PDV_Detalhes + Intelipost API*
