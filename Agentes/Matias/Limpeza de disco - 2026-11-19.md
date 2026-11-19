# Limpeza seletiva de disco — 2026-11-19

Às 06:32 BRT, `/` tinha 26.308.759.552 bytes usados (85%) e 4.699.795.456 bytes livres. Por pedido do Sergio, reavaliados caches e aplicações antes da limpeza.

## Executado

- `uv cache clean --cache-dir /home/sergio-ladeira/.cache/uv`: 4.916 arquivos (431,5 MiB lógicos informados pelo uv).
- `uv cache clean --cache-dir /home/sergio-ladeira/.hermes/cache/uv`: 10.460 arquivos (500,7 MiB lógicos informados pelo uv).
- `pip cache purge`: 68 arquivos, 149 diretórios (13,8 MB informados pelo pip).

Antes da limpeza, nenhum processo mantinha descritor aberto nos três diretórios e não havia processo `uv`, `pip`, `cargo`, `rustc`, `rustup`, `pnpm` ou `npm` ativo. Os caches uv foram removidos pelos próprios comandos. Às 06:34 BRT, `/` tinha 25.845.067.776 bytes usados (84%), 5.163.487.232 livres. **Ganho real no filesystem: 463.691.776 bytes (~442,2 MiB)**; os valores do uv/pip não devem ser somados como espaço recuperado por causa de hardlinks/deduplicação. `uv --version`, `pip --version` e `hermes profile list` passaram; gateways antes ativos permaneceram `running` e `thiagoribeiro` permaneceu parado.

## Preservado / bloqueado

- `~/.cache/puccinialin` (~695 MiB) reapareceu após exclusão de 17/11; conteúdo Rust/toolchain teve mtime em 18/11. Preservado por potencial reconstrução recorrente e para não gerar downloads/recompilação desnecessários. Investigar quem o recria se o crescimento persistir.
- Revisões Snap desabilitadas e cache APT mantidos. `sudo -n true` retornou status 1, sem privilégio não interativo. Nunca apagar Snap diretamente; não solicitar senha no chat.
- Navegadores/perfis, bancos SQLite, GNRE XML/PDF/estado, node_modules e stores compartilhados intactos.

## Complemento GNRE — 06:39 BRT

Por autorização do Sergio para dados e logs até ontem, inventariado o job `13b0904ff094` (único GNRE identificado em `cron/jobs.json` Matias). Excluídas **30 saídas Markdown de 18/11/2026** de `cron/output/13b0904ff094/`, com dupla verificação de data no nome e mtime anterior a 19/11 BRT, extensão, inode, tamanho, ausência de symlink/hardlink. **122.880 bytes efetivamente liberados**, 20 saídas de 19/11 preservadas e nenhuma saída anterior restante neste job.

**Dados fiscais não foram apagados:** `runtime/production/archive/` contém 384 XML/PDF (cerca de 98 MB alocados), inclusive evidência de requisição, resposta e resultado fiscal; `runtime/production/state.db` e WAL registram estado e bloqueio contra reenvio; `runtime/production/inbox/` contém XMLs de origem. Esses arquivos não são logs descartáveis, e a idade não prova quitação ou fim da obrigação de guarda. Apagá-los sem retenção aprovada e reconciliação verificável pode perder evidência e induzir envio duplicado. Cópia operacional `GNRE_STATUS_GUIAS.txt` não foi alterada.
