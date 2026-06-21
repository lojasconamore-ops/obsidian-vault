---
title: Relatório de Ordens de Separação — 19 Jun 2026
tags:
  - logistica
  - debx
  - ordem-separacao
  - cron
date: 2026-06-19
---

# Relatório de Ordens de Separação (OS) — 19/06/2026

## Contexto

Sérgio solicitou análise das **ordens de separação (OS)** apontadas no dia **19/06/2026**, detalhando por:
- Separador responsável
- Quantidade de volumes
- Valor
- Todos os schemas do banco Oracle DEBX

## Abordagem

Como a tabela exata de ordens de separação no DEBX não era conhecida de antemão, foi criado um **script adaptativo** que:

1. Conecta ao Oracle DEBX
2. Faz **descoberta automática** de tabelas relacionadas a ordens de separação (busca por `SEPAR`, `ORDEM`, `PICKING`, `WMS`, `EXPED`, `ROMANE`, `OS_`, `_OS`, `VOLUME`, `EMBALA`, `CONFER`, `CARGA`)
3. Identifica colunas relevantes por heurística (data, separador, volumes, valor, número OS, status)
4. Consulta os dados da data-alvo
5. Gera relatório formatado

## Scripts

| Script | Caminho |
|--------|---------|
| Principal | `~/.hermes/profiles/tobias/scripts/ordem-separacao-relatorio.py` |
| Wrapper | `~/.hermes/profiles/tobias/scripts/ordem-separacao-relatorio.sh` |

### Uso manual

```bash
cd ~/.hermes/profiles/tobias
source .env
python3 scripts/ordem-separacao-relatorio.py --data 2026-06-19
```

## Cron Job

| Campo | Valor |
|-------|-------|
| Job ID | `87be658565fa` |
| Nome | Relatório de Ordens de Separação — 19 Jun |
| Execução | 20/06/2026 às 08:20 BRT (11:20 UTC) |
| Modo | `no_agent` — saída direta do script |
| Entrega | Telegram (origin → Sergio Ladeira) |
| Script | `scripts/ordem-separacao-relatorio.sh` |

## Observações

- Oracle DEBX estava fora da janela operacional (08:00–18:00 BRT) no momento da criação do script, retornando ORA-01033 — não foi possível testar a descoberta de tabelas
- O script foi projetado para ser robusto: se a tabela não for encontrada, lista todas as disponíveis
- Se o Oracle continuar fora do ar amanhã, o script reportará o erro de conexão
