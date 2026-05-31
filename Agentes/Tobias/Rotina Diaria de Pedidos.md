# Rotina Diária de Acompanhamento de Pedidos

**Última atualização:** 31/05/2026
**Autor:** Tobias — Gerente de Logística e Supply Chain

---

## Ferramentas Integradas

| Fonte | Função |
|-------|--------|
| **SQL Server (Hotel Finder)** | Pedidos abertos, status, valores, fretes, clientes |
| **Intelipost API** | Tracking individual de pedidos |
| **Script `daily-order-check.py`** | Relatório automatizado |

## O Script

**Localização:** `~/.hermes/profiles/tobias/scripts/daily-order-check.py`

```bash
# Relatório completo (resumo + status + pedidos parados + top fretes)
cd ~/.hermes/profiles/tobias
source .env
python3 scripts/daily-order-check.py

# Apenas resumo executivo
python3 scripts/daily-order-check.py --summary

# Resumo + tracking Intelipost nos pedidos mais críticos
python3 scripts/daily-order-check.py --track-critical

# Personalizar quantidade de pedidos no top
python3 scripts/daily-order-check.py --top 30
```

## O Relatório Gera

### 1. 📊 Resumo Executivo
- Últimas 24h: pedidos, receita, frete total/médio, clientes
- Últimos 7 dias: mesma visão consolidada

### 2. 📋 Status dos Pedidos Abertos
Distribuição por status (Expedição, Orçamento, Aprovado, etc.)

### 3. ⚠️ Pedidos Parados (>7 dias)
Lista pedidos que não avançaram — faturamento em risco

### 4. 💰 Maiores Fretes em Aberto
Top 15 pedidos com maior valor de frete

### 5. 🏆 Top Pedidos por Valor
Top 20 com cliente, vendedor, cidade/UF

### 6. 🔍 Tracking Intelipost (opcional, `--track-critical`)
Para cada pedido do top N, consulta status atualizado na Intelipost

## Sugestão de Rotina

| Horário | Tarefa | Duração |
|---------|--------|---------|
| **08:30** | Rodar relatório diário | 1 min (automático) |
| **08:35** | Revisar pedidos parados e maiores fretes | 5 min |
| **09:00** | Se houver críticos, tracking Intelipost | 5 min |
| **14:00** | Checagem rápida de pedidos com entrega prevista para hoje | 5 min |

## Observações Técnicas

- O `Numero_Pedido` do banco (ex: `6117`) é **diferente** do formato Intelipost (`100-XXXXXXXX-X`)
- Para cruzar com Intelipost, é preciso mapear a relação entre os sistemas
- Script já preparado para quando esse mapeamento existir
