# Agenda iCloud ↔ Google — Caldir

## Status

- Rust/Cargo instalados no perfil `matias` em `~/.cargo`
- `caldir` instalado e disponível em `~/.cargo/bin`
- Providers instalados:
  - `caldir-provider-google`
  - `caldir-provider-icloud`
  - `caldir-provider-caldav`
  - `caldir-provider-webcal`
  - `caldir-provider-outlook`

## Verificação feita

- `caldir --version` → `caldir-cli 0.9.1`
- `caldir config` → usa:
  - config: `~/.config/caldir/config.toml`
  - calendário local: `~/caldir`

## Próximo passo para sincronizar de verdade

Ainda falta autenticação das contas:

1. Google Calendar
   - rodar `caldir connect google`
   - seguir o fluxo de OAuth

2. iCloud
   - rodar `caldir connect icloud`
   - usar senha específica de app da Apple, se necessário

3. Sincronização inicial
   - primeiro `caldir status`
   - depois `caldir sync`

## Observação operacional

- Recomenda-se definir um calendário principal para evitar conflito entre edições no iCloud e no Google.
- Para o caso do Elias, o desenho mais seguro é:
  - iCloud como origem
  - Google como espelho de visualização
