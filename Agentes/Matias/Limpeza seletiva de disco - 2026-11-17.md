# Limpeza seletiva de disco — 2026-11-17

Às 05:31 BRT, a partição `/` tinha 28.542.033.920 bytes usados (93%) e 2.466.521.088 bytes disponíveis. Sergio autorizou executar a limpeza previamente sugerida; foi feita revalidação dos candidatos antes de remover.

## Exclusões executadas

- Quatro versões antigas do `cua-driver` em `~/.cua-driver/packages/releases/`: `0.26.0`, `0.27.0`, `0.28.0` e `0.28.1`. Conferido que o symlink ativo aponta para `0.28.2`, sem referências abertas aos quatro diretórios antigos. Comando `cua-driver --version` retornou `0.28.2` após a limpeza.
- `~/.cache/puccinialin`: somente cache/toolchain Rust (`cargo`, `rustup`, `rustup-init`); sem rustc/cargo no PATH, sem processo referenciando o diretório nem referências nos scripts consultados. Removido o diretório inteiro, sem tocar os navegadores.
- Apenas `__pycache__` dentro do venv antigo `~/.hermes/hermes-agent/venv` (Python 3.11): 1.188 diretórios. Venv preservado, sem referências abertas por processos; executável `venv/bin/python --version` continuou funcional. O runtime atual do Hermes utiliza Python 3.14.9.

**Medição pelo filesystem:** 27.418.050.560 bytes usados após a limpeza, ganho líquido observado de **1.123.983.360 bytes** (~1,05 GiB), 3.590.504.448 bytes livres e 89% de uso. `hermes --version` e o inventário de perfis continuaram funcionais; os gateways previamente ativos aparecem como `running`, e `thiagoribeiro` já estava parado.

## Candidatos preservados / bloqueados

- As seis revisões Snap desabilitadas (`core20`, `core22`, `core24`, `lxd`, `obsidian`, `snapd`) **não foram removidas**: `sudo -n snap remove core20 --revision=2866` exigiu senha e o comando sem sudo retornou `access denied`. Usar `snap remove --revision` sob sudo pelo operador; nunca apagar `.snap` diretamente.
- Índices regeneráveis do APT (`/var/cache/apt/pkgcache.bin` e `srcpkgcache.bin`, ~68 MiB cada) não removidos por exigir privilégio administrativo. `archives` não continha pacotes `.deb`.
- Caches `__pycache__` do runtime Hermes atualmente ativo (`~/.hermes/installs/`, >1 GiB compilados), bibliotecas e agentes foram preservados para evitar recompilação e pressão operacional. Também preservados `~/.hermes/hermes-agent/node_modules` (~397 MiB), pnpm store (~1,4 GiB), perfis de navegador Marketing, bancos `state.db`, histórico fiscal e dados GNRE.
- O candidato `~/.hermes/hermes-workspace/node_modules` e o cache Vite apontados antes não existiam mais na vistoria atual; `growatt-venv311` já havia sido removido em 15/11.

Não pedir nem registrar senha sudo no chat. Pendências privilegiadas dependem de execução do Sergio no terminal da VM ou disponibilização de um caminho de administração seguro.
