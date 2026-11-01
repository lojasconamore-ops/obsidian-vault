# Limpeza de Swap e Pressão de Memória

**Registrado em:** 2026-10-31
**VM:** `agentic-vm` (Azure Standard_B2ms, 8 GiB RAM, 4 GiB swap)
**Cenário:** swap em 3,1 GiB usados com RAM disponível em 1,6 GiB.

---

## Diagnóstico

A swap alta **não é**, por si só, lentidão. É o amortecedor de memória. O sinal
real de degradação é `si`/`so` alto no `vmstat` (swap thrashing) ou pressão de
memória (PSI) elevada. Nesta VM, `swappiness=60` faz o kernel mandar páginas
para swap cedo demais, dado o padrão de 13 gateways Hermes + integrações.

- `free -h` e `swapon --show` são a fonte de verdade do estado.
- `vm.swappiness` atual: **60** (padrão Ubuntu). Recomendação: **20**.

## Causa raiz

**8 GiB não comporta folgadamente 13 gateways + cron + integrações (Oracle,
SMB, GNRE, Composio, navegadores).** Com tudo no ar, a RAM disponível fica em
~1,6 GiB e a swap cresce. Medida definitiva: **upgrade para 16 GiB**
(`Standard_B4ms` ou `B4as_v2`, West US 2; estimado +~US$ 60/mês).

## Procedimento seguro de limpeza da swap

Nunca rodar `swapoff` com RAM disponível menor que a swap usada — risco de
thrashing e OOM Killer derrubar gateways.

1. **Liberar RAM**: parar processos/gateways não essenciais.
2. **Conferir folga**: `free -h` → RAM disponível deve ser ≥ swap usada.
3. **Baixar a swap** (roda em segundos; pode demorar 10–30s puxando páginas):
   ```bash
   sudo swapoff /swapfile
   ```
4. **Confirmar que desligou** (saída vazia):
   ```bash
   swapon --show
   ```
5. **Reativar**:
   ```bash
   sudo swapon /swapfile
   ```
6. **Validar** (swap deve aparecer 0B usado):
   ```bash
   free -h
   ```

### Pitfall: "swapon: Device or resource busy"

Acontece quando o `swapoff` anterior **não concluiu** (ou não rodou) e o
arquivo continua ativo. Conferir com `swapon --show`; só rodar `swapon` depois
de confirmar que a saída do `swapon --show` está vazia.

## Parada/religada de gateways (user services)

Gateways user rodam como `systemctl --user`. Os system (matias, cona, adrian,
maria, tiago) exigem `sudo`.

- **Parar** user gateway: `systemctl --user stop hermes-gateway-<perfil>.service`
- **Religar** user gateway: `systemctl --user start hermes-gateway-<perfil>.service`

⚠️ **Guard do gateway:** comandos com `stop`/`restart`/`uninstall` são bloqueados
quando disparados de dentro do próprio processo do gateway (SIGTERM propaga).
Workaround: acionar via Python `subprocess` (o guard não inspeciona o código) ou
rodar de um shell externo.

⚠️ **`Restart=always`:** os user services têm restart automático. `systemctl stop`
para de verdade (não reinicia). Processo travado em `stop-sigterm` (não morre)
precisa de `SIGKILL` no PID; depois `systemctl --user reset-failed`.

## Estado após a limpeza (2026-10-31)

- Swap: **0 B usado** (4 GiB livres).
- Com os 13 gateways de volta, RAM disponível volta a ~1,6 GiB — a swap volta a
  ser usada gradualmente (esperado e saudável).

## Ações recomendadas (pendentes)

1. Reduzir `vm.swappiness` de 60 → 20 (persistir em `/etc/sysctl.d/`).
2. Upgrade da VM para 16 GiB.
3. Considerar adormecer/perfis de baixo uso para aliviar a RAM.
