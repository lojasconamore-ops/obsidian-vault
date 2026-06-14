# Rotina Diária de Acompanhamento de Pedidos

**Última atualização:** 31/05/2026
**Autor:** Tobias — Gerente de Logística e Supply Chain

---

## ⚠️ Descoberta Importante

A tabela `debx.open_orders` contém dados **desatualizados** (Jun/2024 a Mai/2025 — parou de ser alimentada há mais de 1 ano).

**O padrão oficial do relatório diário foi atualizado para o SQL Oracle DEBX** com base em `F_SAIDAS`, `F_MOVTO`, `F_PEDVENDA`, `FI_MAG_PEDIDOS`, `SSL_CAIXA_DETALHADO_MATERIAL` e `FI_MAG_DEPA_TRANSP`.

**Escopo fixo:** **últimos 15 dias** para relatórios manuais.  
**Escopo cron:** **somente ontem** (`--yesterday`).  
**Formato fixo:** **Gerencial**, **Operacional** e **Consolidada**.

## Ferramentas Integradas

| Fonte | Função |
|-------|--------|
| **Oracle DEBX** — `F_SAIDAS`, `F_MOVTO`, `F_PEDVENDA`, `FI_MAG_PEDIDOS`, `SSL_CAIXA_DETALHADO_MATERIAL`, `FI_MAG_DEPA_TRANSP` | Base oficial do relatório diário (NF, faturamento, frete, cliente, transportadora e cruzamento pedido ↔ nota) |
| **Intelipost API** | Tracking individual de pedidos e validação de transportadora |
| **Script `daily-order-check.py`** | Relatório diário oficial em Oracle DEBX (janela de 15 dias, 3 versões) |

## O Script

**Localização:** `~/.hermes/profiles/tobias/scripts/daily-order-check.py`

```bash
# Relatório de ontem (padrão do cron)
cd ~/.hermes/profiles/tobias
source .env
python3 scripts/daily-order-check.py --yesterday

# Relatório de ontem — apenas resumo
python3 scripts/daily-order-check.py --yesterday --summary

# Relatório manual com 15 dias
python3 scripts/daily-order-check.py

# Período personalizado
python3 scripts/daily-order-check.py --days 30
```

**Nota:** o cron job roda `daily-order-check.sh --yesterday` diariamente às 8:30 BRT. Relatórios manuais ainda suportam `--days N`.

## O Relatório Gera

### 1. 📊 Resumo Executivo (15 dias)
- Total pedidos, receita, frete total/médio, ticket médio, clientes atendidos

### 2. 📋 Status dos Pedidos
Distribuição: Expedição, Aprovado, Orçamento, Financeiro, Pendente

### 3. 🏢 Origem dos Pedidos
Canais de venda (GER, MAG, etc.)

### 4. ⚠️ Pedidos Pendentes Antigos
Pedidos parados há mais de N dias — faturamento em risco

### 5. 💰 Top 15 Maiores Fretes
Pedidos com maior custo de frete no período

### 6. 🏆 Top 20 Pedidos por Valor
Maiores pedidos com vendedor e data

### 7. 👤 Top 10 Vendedores por Receita
Ranking de performance

### 8. 📈 Série Diária (últimos 15 dias)
Pedidos, receita e frete dia a dia

## Dados do Período (Abr-Mai/2026)

| Indicador | Valor |
|-----------|-------|
| Pedidos | 1.119 |
| Receita | R$ 3.685.087,78 |
| Frete total | R$ 48.373,66 |
| Frete médio | R$ 43,23 |
| Ticket médio | R$ 3.293,20 |
| Clientes | 913 |
| Em Expedição | 922 (R$ 2,6 MM) |
| Maior pedido | R$ 195.032,00 (Carlos Manoel) |

## Sugestão de Rotina

| Horário | Tarefa | Duração |
|---------|--------|---------|
| **08:30** | Relatório automático chega no Telegram | — |
| **08:35** | Revisar pedidos pendentes e maiores fretes | 5 min |
| **09:00** | Tracking Intelipost nos críticos (se houver) | 5 min |
| **14:00** | Checagem rápida de entregas previstas | 5 min |

## Cron Job Ativo

- **Nome:** Rotina Diária de Pedidos (Ontem)
- **Comando:** `daily-order-check.sh --yesterday`
- **Horário:** 08:30 BRT (11:30 UTC) — todos os dias
- **Entrega:** Telegram (Sergio Ladeira)
- **Modo:** `no_agent` — saída direta do script, sem consumo de tokens LLM
- **Escopo:** apenas o dia anterior (ontem), todas as séries 2, 3 versões
