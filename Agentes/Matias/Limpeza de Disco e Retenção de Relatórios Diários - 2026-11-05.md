# Limpeza de disco e retenção de relatórios diários — 2026-11-05

**Janela:** 2026-11-05, 07:06–07:10 BRT. **Escopo:** disco raiz da VM; autorização do Sérgio para excluir relatórios diários com mais de 15 dias.

## Antes e depois
- Antes: 25.502.056.448 bytes usados; 5.506.498.560 disponíveis; 83% (`df -B1 /`).
- Depois: 25.417.269.248 bytes usados; 5.591.285.760 disponíveis; 82%.
- Espaço efetivamente recuperado pelo filesystem: 84.787.200 bytes (80,86 MiB). Tamanhos reportados por ferramentas de cache não são aditivos devido a referências e hardlinks.

## Executado
1. Excluídos **283 arquivos** (3.868.187 bytes lógicos) de saídas de **jobs diários** em `~/.hermes/cron/output/` e `~/.hermes/profiles/*/cron/output/`, com mtime anterior a 2026-10-21 07:09 BRT e data no nome. Manifesto: `~/.hermes/profiles/matias/cache/scratch/disk_cleanup_manifest_20261105.json`. Revalidação de tamanho/mtime antes de cada `unlink`; zero pendentes no manifesto depois.
2. `uv cache clean --cache-dir /home/sergio-ladeira/.cache/uv` (1027 arquivos/49,5 MiB informados).
3. `pip cache purge` (163 arquivos/46,9 MB informados).
4. `npm cache clean --force` (somente cache regenerável).

## Proteções e validação
- Excluídos apenas arquivos de saída de jobs cuja agenda era diária (e relatórios diários do `systemd-hermes-update`). Saídas semanais/mensais e dados de sessões não foram tocados.
- Preservados relatórios no Obsidian, inclusive RH e briefings executivos: são documentação de negócio, não cache. Logs recentes, snapshots/backups, bancos `state.db`, navegadores e ambientes virtuais ativos também preservados.
- Antes dos caches, ausência de referências abertas em `/proc/*/{fd,cwd,exe}` para uv, pip e npm.
- Depois: 13 gateways encontrados (8 no systemd de usuário + 5 no systemd de sistema), todos `active running`.
- Esta limpeza não criou política automática de retenção; foi execução pontual.
