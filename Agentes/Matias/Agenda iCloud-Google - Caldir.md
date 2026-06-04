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
- Para a operação atual da Conamore, o desenho validado é:
  - Google como fonte de verdade
  - iPhone gravando direto no Google
  - iCloud/calendário local em modo somente leitura para evitar divergência

## Rotina de checagem do Caldir

### Frequência
- Diária, no início do expediente
- Sempre após ajustes de conta, token, provider ou mudança de calendário no iPhone
- Sempre que um evento “sumir” ou deixar de aparecer no Google

### Checagem rápida
1. Verificar se o binário está acessível:
   - `PATH="$HOME/.cargo/bin:$PATH" caldir --version`
2. Verificar o estado dos calendários:
   - `PATH="$HOME/.cargo/bin:$PATH" caldir status`
3. Se houver erro de autenticação, renovar a sessão do Google e repetir o status
4. Se o status estiver limpo, fazer um teste controlado:
   - criar um evento curto no calendário Google
   - rodar `PATH="$HOME/.cargo/bin:$PATH" caldir sync`
   - confirmar que o evento apareceu no mirror local
5. Confirmar limpeza do ambiente:
   - repetir `caldir status`
   - o esperado é `No changes`

### Sinais de que está funcionando adequadamente
- O Google aparece sem erro 401/Unauthorized
- `caldir status` mostra `No changes`
- Eventos criados no iPhone aparecem no Google porque o calendário padrão é o Google
- O espelho local do Google recebe os eventos sem intervenção manual

### Sinais de falha
- `401 Unauthorized` em qualquer provider Google
- Evento existe no iPhone mas não aparece no Google
- `caldir status` mostra alterações inesperadas
- O calendário errado está selecionado no iPhone para criação de eventos

### Ação corretiva padrão
- Revalidar o token Google local
- Conferir se o iPhone está criando eventos no calendário Google
- Rodar `caldir sync` e reavaliar `caldir status`
