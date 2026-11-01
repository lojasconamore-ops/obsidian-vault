# Auditoria de segurança da VM — 2026-11-01

**Escopo:** agentic-vm (Ubuntu 22.04.5 LTS), inspeção local somente leitura em 2026-11-01, aproximadamente 10:33–10:35 BRT. Não houve alterações. A auditoria não inclui Azure NSG, varredura externa, revisão completa de aplicações nem auditoria com privilégios root.

## Resumo executivo

**Estado: atenção moderada a alta.** Não há evidência de invasão nesta coleta, mas há superfície exposta e tentativas automatizadas de SSH. O firewall e as proteções SSH não puderam ser auditados integralmente sem sudo. O disco raiz está em 82% e há atualizações pendentes.

## Achados

1. **Alta — superfície de rede e SSH:** `ss` mostra TCP 22 em `0.0.0.0` e `[::]`, além de webhook Hermes TCP 8644 em `0.0.0.0`. Isso é bind local em todas as interfaces; **não prova exposição pela Internet** (Azure NSG não consultado). O webhook tem segredo configurado; GET local `/health` retorna 200, enquanto `/` e `/docs` retornam 404. Não foram feitos testes POST nem bypass de autenticação. Confirmar NSG, origem permitida, TLS/proxy e autenticação do webhook antes de qualquer mudança.
2. **Alta — ruído de ataque a SSH:** em 24h no journal de `ssh`, 486 linhas com `Failed password`, 121 com `Invalid user` e 2 com `Accepted publickey`; não houve `Accepted password` nessa amostra. A proteção fail2ban está ativa e há configuração visível de jail sshd (`maxretry=3`, `bantime=1h`), mas estado/banimentos não puderam ser lidos sem root. Um fragmento de SSH visível contém `PasswordAuthentication no`, porém `sshd -T`/`sshd -t` exigiram privilégios; **não afirmar que a política efetiva foi validada**. Há `authorized_keys` não vazio (291 bytes, modo 600), sem teste externo da chave. Nunca alterar SSH nem firewall antes de verificar acesso alternativo funcional.
3. **Média — atualizações:** `apt list --upgradable` apresentou 21 pacotes atualizáveis mais cabeçalho; entre eles krb5, netplan, snapd, libaudit. Não há `/var/run/reboot-required`. `apt-daily` e `apt-daily-upgrade` têm timers ativos. Fazer triagem de CVEs e atualização em janela com snapshot e plano de reversão; não executar atualização cega em produção.
4. **Média — dependências Hermes:** `hermes doctor` indica 0 CVEs críticos, 1 high + 5 moderate no workspace web, 1 high + 1 moderate no TUI; a correção persistente depende de lockfile upstream. O Hermes stable v0.22.5 está atualizado na data da coleta.
5. **Média — capacidade:** 1,2 GiB RAM disponível, 1,6 GiB swap usada, disco raiz 82% (5,4 GiB livres). Monitorar pressão de memória e crescimento; planejar expansão/limpeza auditada sem tocar dados de produção às cegas.
6. **Baixa — permissões locais:** `.hermes` e `.ssh` modo 700; `.env`, `auth.json`, configs e bancos principais modo 600; 43 candidatos sensíveis verificados. `google_client_secret.json` do Matias é 644, mas está em diretório de perfil 700 e home 750, portanto outros usuários locais não conseguem atravessar o caminho nesta configuração. Endurecer para 600 em manutenção; não tratar como vazamento comprovado.
7. **Controles observados:** AppArmor ativo; serviços `ufw` e `fail2ban` ativos; administrador interativo local identificado como `sergio-ladeira` no grupo sudo. `ufw` indica política padrão DROP em arquivo, mas o **ruleset ativo não pôde ser lido** sem sudo. Nenhum serviço systemd em `failed` na checagem precedente.

## Prioridades e validações pendentes

- **P1 (Sérgio/Matias):** no Portal Azure, revisar NSG de entrada para TCP 22 e 8644 e IPs permitidos. Confirmar necessidade do webhook público, autenticação e TLS. Não fechar SSH sem caminho alternativo de acesso previamente testado.
- **P1 (Matias com sudo, somente leitura):** verificar `ufw status verbose`, `nft list ruleset`, `fail2ban-client status sshd`, `/usr/sbin/sshd -T` e últimos eventos de autenticação; correlacionar IPs e bans sem divulgar identificadores sensíveis.
- **P2 (Matias/Sérgio):** agendar atualizações Ubuntu e limpeza/expansão de disco após snapshot/backup e plano de reversão; acompanhar correção upstream dos alertas npm.
- **P3 (Matias):** restringir permissões do arquivo OAuth a 600 em janela controlada e testar integração.

**Limitações:** consulta Azure Monitor/NSG indisponível nesta VM; sudo não interativo requer senha, portanto firewall ativo, configuração SSH efetiva e banimentos fail2ban não foram auditados. Teste externo e revisão de código/autorização do webhook não foram realizados. Nenhuma conclusão de comprometimento ou de blindagem total é possível com esta amostra.
