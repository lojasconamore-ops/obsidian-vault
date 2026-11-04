# Limpeza segura de disco — 2026-11-04

**Janela:** 2026-11-04, 06:54–06:56 BRT. **Escopo:** VM `agentic-vm`, disco raiz `/`.

## Antes e depois
- Antes: 26.174.115.840 bytes usados; 4.834.439.168 bytes disponíveis; 85% na apresentação `df`.
- Depois: 25.523.564.544 bytes usados; 5.484.990.464 bytes disponíveis; 83%.
- Recuperado efetivamente: 650.551.296 bytes (aprox. 620,4 MiB). Não somar tamanhos lógicos removidos dos caches: podem incluir hardlinks.

## Operações efetuadas
1. `uv cache clean --cache-dir /home/sergio-ladeira/.hermes/cache/uv`.
2. `uv cache clean --cache-dir /home/sergio-ladeira/.cache/uv`.
3. `pip cache purge` (cache do usuário).
4. `npm cache clean --force` (somente cache do npm; não removeu pacotes instalados).

Antes da execução, foram verificados os caminhos exatos e a ausência de processos com `cwd`, `exe` ou descritores abertos nesses caches. Logs ativos, bancos `state.db`, backups, scripts e arquivos de configuração não foram tocados.

## Verificação
- `df`: 83% e 5,2 GiB disponíveis (apresentação arredondada).
- 13 gateways verificados ativos (managers de sistema e usuário).
- `hermes --version`: v0.22.7; `node --version`: v24.18.1.

## Não removido deliberadamente
- Playwright (681 MiB): binários de browser podem ser necessários à automação.
- Store pnpm (1,4 GiB): potencialmente compartilhada por instalações ativas.
- Rustup/Cargo de Puccinialin (688 MiB): ferramenta/runtime, não classificado como cache puramente descartável.
- Logs de auditoria, backups de recuperação, sessões e SQLite.

**Próximo passo se o disco voltar a crescer:** auditar as stores/instalações com mapa de referências e, se for preciso liberar mais de 1 GiB, avaliar ampliação do disco ou janela de manutenção para componentes regeneráveis. Não limpar às cegas.
