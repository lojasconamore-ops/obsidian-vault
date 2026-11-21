---
data: 2026-11-20
fonte: Pluggy (conector MeuPluggy) — conexão Itaú
item_id: 8a730bba-9782-4d3b-be92-35688caa1db6
tipo: snapshot de posição financeira
---

# Posição de Investimentos — 20/11/2026

Snapshot registrado para comparação futura. Fonte: API Pluggy (open finance), conexão Itaú via MeuPluggy.

## Resumo

- **Total investido: R$ 696.390,64**
- Fundos: R$ 478.576,75
- Renda fixa (CDBs com saldo): R$ 217.813,89

## Fundos

| Fundo | Tipo | Retorno 12m | Saldo |
|---|---|---|---|
| Privilege DI | Renda fixa (DI) | 12,32% | R$ 175.447,18 |
| Diferenciado Crédito Privado Renda Fixa | Renda fixa crédito privado | 12,31% | R$ 174.310,92 |
| Itaú Crédito Bancário Renda Fixa Crédito Privado | Renda fixa crédito privado | n/d | R$ 64.624,17 |
| Itaú Global Dinâmico Baixa Vol Multimercado | Multimercado | 11,95% | R$ 64.194,48 |
| Absolute Hidra CDI Seleção Infra Renda Fixa CP | Renda fixa crédito privado | resgatado | R$ 0 (resgatado) |

## CDBs / renda fixa

| CDB | Saldo | Taxa | Vencimento |
|---|---|---|---|
| FACTA Financeira S.A. | R$ 104.991,08 | 108% do CDI | 13/03/2028 |
| Banco BMG S.A. | R$ 104.339,63 | 14,07% a.a. (pré-fixado) | 13/03/2028 |
| Itaú Unibanco (CDB5262LBP9) | R$ 8.483,18 | 100% do CDI | 08/04/2031 |

*(+ 9 CDBs Itaú já zerados/vencidos — registros históricos.)*

## Contas (contexto — mesma data)

| Conta | Tipo | Saldo |
|---|---|---|
| Itaú | Conta corrente | R$ 13.219,29 |
| LATAM Pass Itaú Mastercard Black | Cartão | R$ 21.579,10 |
| Itaú Personnalité Visa Infinite | Cartão | R$ 9.965,77 |
| Personnalité MC Black | Cartão | R$ 94.901,34 |

## Observações

- Perfil conservador, concentrado em renda fixa (DI + crédito privado). Única exposição a mercado além do CDI: multimercado baixa vol (~R$ 64 mil).
- Concentração em crédito privado: fundos Diferenciado + Crédito Bancário (~R$ 239 mil) + CDBs de financeiras/bancos.
- Dois CDBs grandes vencem na mesma data (13/03/2028): FACTA (108% CDI) + BMG (14,07% a.a.) — ~R$ 209 mil juntos.
- Valores de cartão de crédito = fatura em aberto/saldo devedor (confirmar contra a fatura; MC Black R$ 94.901,34 é alto).
- Escopo: apenas o que a conexão Itaú expõe. Investimentos em outras instituições só aparecem se conectadas no Meu Pluggy.

## Como reler esta posição (para comparar)

Via API Pluggy com o `item_id` acima:

- `GET /investments?itemId=<item_id>&pageSize=500`
- `GET /accounts?itemId=<item_id>`
