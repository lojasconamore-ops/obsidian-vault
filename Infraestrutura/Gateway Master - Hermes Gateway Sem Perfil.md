# Gateway Master — Hermes Gateway Sem Perfil

> **Data:** 2026-07-03
> **Verificado por:** Matias (TI)
> **Status:** 🟢 ESSENCIAL — NUNCA DESLIGAR

---

## O que é

O service `hermes-gateway.service` (PID atual: `304039`, sem `--profile`) é o **gateway master/orquestrador** da infraestrutura Hermes da Conamore. Ele não é um órfão — é o núcleo central que sustenta operações globais.

---

## O que ele faz

| Função | Detalhe |
|--------|---------|
| **Cron scheduler master** | Executa jobs agendados globais (`flavia-daily`, `tobias-daily`, etc.) |
| **Gateway padrão (fallback)** | Quando um profile não tem gateway dedicado, o tráfego cai aqui |
| **State central** | Mantém `state.db` (~319 MB), `response_store.db`, logs MCP |
| **MCP Proxy compartilhado** | Filho `composio-mcp-proxy.py` atende requisições de múltiplos profiles |
| **Lock global** | `~/.hermes/gateway.lock` aponta para este PID |

---

## Evidências técnicas

```
HERMES_HOME=/home/sergio-ladeira/.hermes
Portas: 127.0.0.1:8642 (localhost) + 0.0.0.0:8644 (público)
Conexões: 2x Telegram (149.154.166.110:443) ativas
Bancos: state.db (319 MB), response_store.db, state.db-wal
Cron jobs globais: 182 entradas em ~/.hermes/cron/jobs.json
```

---

## Arquitetura da Frota Hermes

```
hermes-gateway.service           ← MASTER (sem perfil)
├── hermes-gateway-matias.service
├── hermes-gateway-tiago.service
├── hermes-gateway-adrian.service
├── hermes-gateway-bianco.service
├── hermes-gateway-elias.service
├── hermes-gateway-fabricia.service
├── hermes-gateway-marketing.service
├── hermes-gateway-natalia.service
├── hermes-gateway-tobias.service
└── hermes-gateway-maria.service
```

**Total:** 11 services = 1 master + 10 profiles

---

## Service file

Caminho: `/etc/systemd/system/hermes-gateway.service`

```ini
[Unit]
Description=Hermes Agent Gateway - Messaging Platform Integration
After=network-online.target
Wants=network-online.target
StartLimitIntervalSec=0

[Service]
Type=simple
User=sergio-ladeira
Group=sergio-ladeira
ExecStart=/home/sergio-ladeira/.hermes/hermes-agent/venv/bin/python -m hermes_cli.main gateway run
WorkingDirectory=/home/sergio-ladeira/.hermes
Environment="HOME=/home/sergio-ladeira"
Environment="USER=sergio-ladeira"
Environment="LOGNAME=sergio-ladeira"
Environment="PATH=/home/sergio-ladeira/.hermes/hermes-agent/venv/bin:..."
Environment="VIRTUAL_ENV=/home/sergio-ladeira/.hermes/hermes-agent/venv"
Environment="HERMES_HOME=/home/sergio-ladeira/.hermes"
Restart=always
RestartSec=5
RestartForceExitStatus=75
KillMode=mixed
KillSignal=SIGTERM
ExecReload=/bin/kill -USR1 $MAINPID
TimeoutStopSec=210
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target
```

> **Nota:** O master **não usa `--replace`** porque ele detém o lock global. Se usasse, correria risco de se auto-matar.

---

## Ações proibidas

| Ação | Risco |
|------|-------|
| `systemctl stop hermes-gateway.service` | Derruba cron jobs globais, perda de estado, gateways profiles perdem fallback |
| `kill 304039` | Mesmo risco acima |
| Reiniciar sem garantir que ele sobe **antes** dos profiles | Profiles podem falhar por lock ou por não encontrar o master |

---

## Procedimento de reinicialização (se necessário)

Caso a VM precise ser reiniciada:

1. Verificar se `hermes-gateway.service` subiu primeiro
2. Só depois, iniciar os services dos profiles
3. Validar que `~/.hermes/gateway.lock` aponta para o PID do master

---

## Histórico de manutenção

| Data | Ação | Responsável |
|------|------|-------------|
| 2026-07-03 | Diagnóstico e documentação do gateway master | Matias |
| 2026-07-03 | Criação de services systemd para 6 profiles órfãos | Matias |
| 2026-07-03 | Correção do service da Maria (loop de 78.500 restarts) | Matias |

---

## Links relacionados

- [[Stack Tecnológica]]
- [[Integrações, Automação e Monitoramento]]
- [[Infraestrutura, Segurança e Suporte]]
