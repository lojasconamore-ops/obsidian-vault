# Limpeza de disco e retenção de relatórios diários — 2026-11-15

**Janela:** 2026-11-15 07:39–07:42 BRT. **Escopo:** disco raiz da VM; pedido do Sergio para limpar e excluir relatórios diários com mais de 15 dias.

## Resultado medido

- Antes da remoção: 28.433.084.416 bytes usados, 92% do disco raiz (medição imediatamente antes da exclusão).
- Depois: 25.848.963.072 bytes usados, 84%; 4,9 GiB disponíveis (`df -h`).
- Recuperado pelo filesystem: **2.584.121.344 bytes (2,407 GiB)**. Não somar os tamanhos relatados por ferramentas de cache devido a hardlinks, alocação e atividade concorrente.

## Escopo removido

1. **232 arquivos Markdown de saída de jobs com agenda realmente diária**, em `~/.hermes/cron/output/` e `~/.hermes/profiles/*/cron/output/` (2.607.418 bytes lógicos). Corte: 2026-10-31 07:41:30 BRT, isto é, mais de 15 dias antes da execução. Exigidos nome datado e `mtime` anteriores ao corte; arquivo, tamanho, `mtime_ns`, job e raiz no manifesto `~/.hermes/profiles/matias/cache/scratch/daily-report-cleanup-manifest-20261115.json`. Todos os 232 foram revalidados imediatamente antes do `unlink`; zero pulados e zero remanescentes. Excluídos jobs semanais, mensais, intervalares ou de múltiplas execuções diárias, inclusive GNRE.
2. `pip cache purge` no cache do usuário `~/.cache/pip` (256 arquivos e 498 diretórios reportados).
3. `uv cache clean` nos caches `~/.cache/uv` e `~/.hermes/cache/uv` (limpeza de arquivos regeneráveis).
4. `npm cache clean --force` no cache do npm; nenhum pacote instalado foi removido.

## Proteções e verificação

- Antes das limpezas de cache, não havia referências abertas em `/proc/*/{fd,cwd,exe}` para os quatro diretórios de cache selecionados.
- Preservados relatórios canônicos do Obsidian, RH, briefings executivos, XMLs/PDFs GNRE, logs ativos, bancos SQLite, sessões, snapshots/backups, Playwright, ambientes virtuais e instalações Hermes/Node.
- Node ativo permaneceu em `~/.hermes/node/bin/node` (v24.18.1). **13 gateways ativos** após a limpeza: 5 do systemd de sistema e 8 do systemd do usuário, nenhum falho.
- Limpeza pontual: **não** foi criada retenção automática nem agendamento novo.

## Complemento — perfis temporários de navegador em `/tmp`

Às 07:56 BRT, por autorização específica do Sergio, foram removidos **somente sete diretórios**: cinco `chrome-consent-*` (incluindo `chrome-consent-flavia`), um `chrome_bu_profile4` e um `agent-browser-chrome-*`. Todos eram diretórios reais sob `/tmp`, sem symlinks na raiz, e não havia referências nos `cwd`, `exe`, descritores abertos nem linhas de comando dos processos examinados imediatamente antes da remoção. Nenhum outro arquivo de `/tmp`, perfil persistente ou binário do navegador foi removido. Os sete caminhos não existem mais.

Medição do filesystem na operação: de **25.853.337.504** para **25.497.956.352 bytes usados**, recuperação observada de **355.381.248 bytes**. Disco raiz passou a **83% de uso**, com aproximadamente **5,2 GiB livres**. Os 13 gateways permaneceram ativos (5 systemd de sistema e 8 do usuário).
