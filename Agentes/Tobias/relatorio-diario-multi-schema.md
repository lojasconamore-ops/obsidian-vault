# Padrão do Relatório Diário — Tobias (Multi-Schema)

**Atualizado:** 27/06/2026

## Formato oficial

O relatório diário agora consulta **todos os schemas** Oracle DEBX:

| Schema | Perfil |
|--------|--------|
| TEST_MATRIZ | Conamore SSL — Matriz (B2B Hotelaria/Hospitalar) |
| TEST_ACL | Loja/Varejo — E-commerce B2C |
| TEST_GCL | Atacado/Regional |
| TEST_BRG | B2B Regional |
| TEST_CHC | (monitorar) |

## Estrutura (2 partes)

1. **Gerencial** — resumo comparativo entre schemas + total consolidado
2. **Tabela horária (BRT)** — NFs por hora de 07:00 a 20:00, somando todos os schemas

## Cruzamento

- **Todos os schemas:** `F_SAIDAS` (NF, valor, frete, código cliente)
- **Apenas TEST_ACL:** cruzamento completo com `F_MOVTO`, `F_PEDVENDA`, `FI_MAG_PEDIDOS`, `SSL_CAIXA_DETALHADO_MATERIAL`, `FI_MAG_DEPA_TRANSP`

## Script

- `scripts/daily-order-check.py --days 15`
- `scripts/daily-order-check.sh` (wrapper com .env)

## Cron

- Job `56941ab08acb`: diário às 8:30 BRT, entrega via Telegram
