# Checagem de Segurança Linux — 2026-08-01

## Resumo executivo

### Status geral

- **Rede/exposição:** ⚠️
- **SSH e autenticação:** ✅
- **Proteções do kernel:** ✅
- **Hardening e serviços de segurança:** ⚠️
- **Persistência/artefatos suspeitos:** ✅

## Achados principais

### Exposição de rede

- IP público observado: `4.242.57.119`
- Interface VPN ativa: `tun0`
- Rotas relevantes para `10.9.0.0/24` e `172.169.0.0/24` via túnel
- Portas escutando localmente:
  - `22/tcp` — SSH
  - `8644/tcp` — serviço `hermes`
- `net.ipv4.ip_forward = 0`
- `net.ipv6.conf.all.forwarding = 0`

### SSH

- `authorized_keys` presente em `/home/sergio-ladeira/.ssh/authorized_keys`
- Permissões corretas: `0600`
- Quantidade de chaves: `1`
- Fragmento efetivo de configuração lido:
  - `PasswordAuthentication no`
  - `ClientAliveInterval 120`
- Conclusão: login por senha do SSH está desabilitado; acesso depende de chave SSH.

### Proteções do sistema

- `fail2ban`: ativo e habilitado
- `apparmor`: ativo e habilitado
- `unattended-upgrades`: ativo e habilitado
- `auditd`: inativo
- Proteções relevantes do kernel observadas como ativas:
  - ASLR
  - `kptr_restrict=1`
  - `dmesg_restrict=1`
  - `yama.ptrace_scope=1`
  - `unprivileged_bpf_disabled=2`
  - hardlinks/symlinks protegidos
  - `tcp_syncookies=1`
  - redirects ICMP desabilitados para IPv4/IPv6
  - `rp_filter=2`

### Itens que pedem revisão

- `net.ipv4.conf.all.send_redirects = 1`
- `net.ipv4.conf.default.send_redirects = 1`
- `DefaultLimitCORE=infinity` no systemd, embora `ulimit -c` tenha retornado `0`
- `auditd` está inativo
- Não foi possível verificar regras reais de firewall/`sshd` via `sudo` porque o comando exigiu senha

## Verificações que falharam por falta de privilégio

- `ss -lntup` com `sudo`
- `ufw status verbose`
- `nft list ruleset`
- `iptables -S`
- `sshd -T` com leitura privilegiada do config efetivo
- `fail2ban-client status`
- `journalctl -u ssh.service` com `sudo`
- `lastb`

## Risco prático

- O servidor está com SSH por chave e tem `fail2ban`/`apparmor` ativos, o que é bom.
- Há um serviço Hermes exposto em `8644/tcp`; isso deve ser tratado como superfície operacional legítima, mas precisa estar restrito ao necessário.
- O maior ponto de atenção é a ausência de validação privilegiada do firewall, então a política real de bloqueio ainda não foi confirmada.

## Recomendações

1. Confirmar firewall real com acesso administrativo em janela segura.
2. Revisar se `8644/tcp` precisa permanecer exposto fora da rede/VPN.
3. Avaliar ativação do `auditd` se houver requisito de trilha forense local.
4. Rever `send_redirects=1` se a máquina não atuar como roteador.
5. Manter `fail2ban` e `unattended-upgrades` ativos.
6. Não desabilitar autenticação por senha de SSH sem chave testada — já há chave configurada.

## Evidências coletadas

- `/etc/ssh/sshd_config.d/60-cloudimg-settings.conf` → `PasswordAuthentication no`
- `/etc/ssh/sshd_config.d/50-cloudimg-settings.conf` → `ClientAliveInterval 120`
- `/etc/fail2ban/jail.d/defaults-debian.conf` → `[sshd] enabled = true`
- `authorized_keys` → uma chave, permissão `0600`
- `ss -lntup` → portas `22` e `8644` abertas
