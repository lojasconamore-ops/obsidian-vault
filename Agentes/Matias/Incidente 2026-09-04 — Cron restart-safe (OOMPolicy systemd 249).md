# Incidente 2026-09-04 — Cron restart-safe falha (OOMPolicy vs systemd 249)

**Status:** Corrigido (patch local + persistência no update diário)
**Data:** 2026-09-04
**Impacto:** Relatório diário de atualização não entregue; watchdogs GNRE e DUA-e parados desde 03/09.

## Sintoma

Todos os cron jobs "restart-safe" falhavam no dispatch com:

```
Restart-safe cron worker dispatch failed: cannot create restart-safe
systemd scope for gateway child: systemd-run --user --scope is unavailable
```

Jobs afetados:
- `hermes-update-status-brasilia` (relatório diário) — failure_streak 2
- `Transmitir e reconciliar lotes GNRE automaticamente` — failure_streak 6
- `Detectar retorno do DUA-e SEFAZ-ES` — failure_streak 1

## Causa raiz

O update de 03/09 trouxe o commit `3373e9769` ("preserve active runs across
gateway restart"), que passou a exigir um systemd scope "restart-safe" para os
workers de cron. Esse scope é criado com:

```
systemd-run --user --scope ... --property OOMPolicy=kill ...
```

`OOMPolicy` só existe a partir do **systemd 250**. Esta VM roda **systemd 249**
(Ubuntu 22.04.5 LTS), então o probe falha com:

```
Unknown assignment: OOMPolicy=kill
```

O probe retorna rc≠0 → `_systemd_run_user_scope_available()` retorna False →
`restart_safe_gateway_child_argv()` levanta `RuntimeError`.

## Correção

1. Removido `--property OOMPolicy=kill` do probe e do build em
   `tools/process_registry.py` (o `MemoryMax` já limita o worker via cgroup
   `memory.max`, então a proteção contra OOM permanece — apenas troca quem mata,
   de systemd-oomd para o kernel oom-killer).
2. Criado `scripts/fix-systemd-oompolicy.py` (idempotente) para reaplicar o patch.
3. Integrado ao `scripts/hermes-update-daily-systemd.sh`: após `hermes update`,
   reaplica o patch e reinicia os gateways se o patch mudou algo.

## Pendências

- O gateway só recarrega o código no próximo restart (update diário 05:00).
  Reiniciar de dentro do gateway é bloqueado pelo Hermes (evita SIGTERM
  auto-infligido). Até lá, GNRE e DUA-e permanecem parados.
- Reportar o bug ao upstream (Nous Research): `OOMPolicy=kill` deve ser
  condicional à versão do systemd (≥250), ou o probe deve degradar graciosamente.
- `hermes-gateway-marketing.service` está `failed` desde 26/08 (status 1/FAILURE);
  o processo marketing roda de fato via systemd --user (PID 738), então não é
  outage, mas a unidade system precisa de limpeza. Fora do escopo deste incidente.
