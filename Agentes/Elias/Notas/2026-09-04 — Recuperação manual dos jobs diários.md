# 2026-09-04 — Recuperação manual dos jobs diários

## Incidente
Os três jobs recorrentes do perfil Elias falharam antes de iniciar o agente:

- Agenda diária — `205ca944c900`
- ShinePhone geração diária — `a408fee01f1b`
- Resumo diário do Granola e pendências — `a551d0a76c8d`

Erro registrado:
`Restart-safe cron worker dispatch failed: cannot create restart-safe systemd scope for gateway child: systemd-run --user --scope is unavailable`

## Recuperação executada
- Agenda e e-mails recuperados diretamente via Google Calendar/Gmail (Composio).
- Growatt consultado diretamente pela API pública.
- Granola coletado por sub-Hermes no perfil padrão, com dados brutos em `/home/sergio-ladeira/.hermes/profiles/elias/tmp_granola_hoje.md`.

## Verificação técnica
- Gateway `hermes-gateway-elias.service`: ativo.
- `systemd-run --user --scope` com `MemoryAccounting` e `MemoryMax`: passou após o incidente.
- Função Hermes `_systemd_run_user_scope_available()`: retornou `True`.
- O mecanismo possui cache negativo de 60 segundos; o próximo disparo deve refazer a sondagem.

## Resultado
Os três relatórios de 04/09/2026 foram produzidos manualmente e entregues em resposta consolidada ao Sergio.
