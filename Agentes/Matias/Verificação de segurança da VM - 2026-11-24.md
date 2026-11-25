# Verificação de segurança da VM — 2026-11-24

**Janela:** 22:23 BRT, após atualização de pacotes e reboot. **Modalidade:** somente leitura, sem alterações em firewall, SSH ou gateways.

## Confirmado

- Ubuntu/kernel `6.8.0-1074-azure`, `apt list --upgradable` sem pacotes, sem reboot pendente. `unattended-upgrades`, SSH, UFW e fail2ban ativos; AppArmor habilitado (`/sys/module/apparmor/parameters/enabled = Y`). Disco `/` 84%, cerca de 4,7 GB livres.
- `ss -lntup`: SSH em `0.0.0.0:22` e `[::]:22`; webhook Hermes em `0.0.0.0:8644`; demais listeners TCP do Hermes em `127.0.0.1`. Bind local não comprova publicação na internet, que depende do NSG/firewall da Azure.
- Webhook configurado no perfil padrão com segredo não vazio, diferente de `INSECURE_NO_AUTH`; GET `/health` respondeu HTTP 200 sem autenticação (health público, não prova acesso às rotas protegidas). Código do adapter exige segredo/HMAC para rotas; enforcement externo e TLS/NSG não foram testados. Config de bind em `0.0.0.0` exige revisão de ingressos e transporte HTTPS.
- Desde o reboot, journal do SSH registrou 15 tentativas **malsucedidas** de senha, 3 eventos de usuário inválido, de 6 IPs distintos; nenhuma linha `Accepted password`/`Accepted publickey` observada no mesmo journal. Isso é varredura/tentativa, **não** prova de acesso. Fail2ban está ativo, mas a consulta ao socket exigiu root; bans/regras não verificados.
- `.hermes/config.yaml`, `.env` do Matias, credencial SMB, banco/índice GNRE e `authorized_keys` em modo `0600`; diretório `.ssh` `0700`, `.hermes` `0700`; OpenVPN `conamore.conf` root `0600`. Em 48 itens inspecionados, único `0644` era chave **pública** `.pub`, normal. `authorized_keys` não vazio não prova que o login por chave foi testado de outra sessão.
- Ubuntu Pro/ESM Apps não habilitado: `pro security-status` indica 16 atualizações de segurança ESM Apps fora do canal padrão. Não confundir com pacotes apt pendentes (zero).

## Limites e prioridades

1. **Alta:** confirmar ACL efetiva do firewall UFW/NSG Azure para 22 e 8644; restringir origens autorizadas sem derrubar SSH ou webhook legítimo. `ufw status verbose`/`fail2ban-client status sshd` retornaram falta de root; `sudo -n` não autorizado. NSG Azure não consultado. Não inferir segurança de `systemctl is-active ufw` sozinho.
2. **Alta:** confirmar configuração SSH **efetiva** com `sudo sshd -T` (o principal `sshd_config` é root `0600`). Um drop-in público indica `PasswordAuthentication no`, porém o journal registra `Failed password for root`; não concluir que senha/root estão desabilitados sem a configuração efetiva. Não desativar senha sem testar chave SSH em uma sessão alternativa e preservar acesso de recuperação.
3. **Média:** confirmar TLS e HMAC do webhook por teste controlado da rota legítima e limitar porta 8644 no NSG/host conforme integração. Não desligar listener sem mapear assinantes.
4. **Média:** avaliar assinatura Ubuntu Pro/ESM Apps conforme exposição de pacotes Universe/Multiverse e política de suporte.
5. **Média:** verificar backups/snapshots e restauração; não cobertos por esta auditoria rápida.

`journalctl -b -p err` mostrou mensagens de DHCP e `sshd`/tentativas; não há unidades em falha no systemd. Este relatório não é um pentest nem confirma ausência de comprometimento.
