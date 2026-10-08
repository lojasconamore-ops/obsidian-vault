# Manutenção de Disco e Topologia dos Gateways — 2026-10-08

## Resumo

Manutenção executada em 2026-10-08, no fuso de Brasília, com limpeza segura de disco e auditoria da topologia systemd dos gateways Hermes.

## Disco

- Antes: 87% utilizado, 4,0 GB livres.
- Depois: 82% utilizado, 5,5 GB livres.
- Espaço recuperado: aproximadamente 1,5 GiB.
- Inodes: 13% utilizados; sem pressão.

### Itens limpos

- Logs rotacionados e diagnósticos `gateway-exit-diag.log`.
- Logs ativos truncados sem remover arquivos abertos.
- Caches regeneráveis `uv` do usuário e do Hermes.
- Cache do `pip`.
- Browsers regeneráveis do Playwright, após confirmar ausência de processos usuários.
- Cache antigo `old_Cache_Data_000` do perfil de Marketing, após confirmar ausência de processos usuários.
- `hermes pm gc` executado; nenhuma geração adicional estava órfã.

### Itens preservados

- Bancos `state.db`, sessões e históricos.
- Credenciais e configurações.
- Runtime Node ativo `v24.18.1`.
- Checkout e ambiente do Hermes.
- Modelo local Faster Whisper/Hugging Face.
- Auditoria de armazenamento em SQLite.

## Topologia operacional

Foram validados 12 gateways com PIDs únicos e Telegram conectado:

- Sistema: `default`, `adrian`, `maria`, `matias`, `tiago`.
- Usuário: `bianco`, `elias`, `fabricia`, `marketing`, `natalia`, `rian`, `tobias`.
- `thiagoribeiro` permanece sem gateway próprio para evitar disputa do token Telegram compartilhado com `adrian`.

Não existem dois serviços ativos para o mesmo perfil. O serviço de usuário duplicado e inativo da Maria foi removido.

## Pendência administrativa

Continuam instaladas, porém desabilitadas e inativas, definições de serviço no system manager para:

- `bianco`
- `elias`
- `fabricia`
- `marketing`
- `natalia`
- `tobias`

A remoção definitiva exige autenticação `sudo`; a sessão não possui `NOPASSWD`. Esses arquivos não iniciam processos e não causam duplicidade operacional, mas ainda geram aviso de topologia ambígua em alguns comandos Hermes.

Backup das unidades antes da remoção administrativa:

`/home/sergio-ladeira/.hermes/profiles/matias/backups/systemd-topology-20261008-072202`

## Saúde final

- Disco: 82% utilizado.
- Memória disponível: 1,6 GiB.
- Swap: 629 MiB utilizados de 4,0 GiB.
- Load average: 0,40 / 0,45 / 0,51.
- Gateways vivos: 12.
- Telegram conectado: 12 de 12.
- PIDs duplicados: nenhum.
