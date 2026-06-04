# Agenda iCloud ↔ Google — Caldir

## Objetivo

Documentar o fluxo de calendário da Conamore para que a agenda principal fique estável, auditável e fácil de diagnosticar no Linux.

A arquitetura validada ficou assim:

- **iPhone** cria eventos direto no **Google Calendar**
- **Google** é a **fonte de verdade**
- **Caldir** mantém um **espelho local** e permite validação no Linux
- **iCloud** não é a origem principal e fica em modo de contenção para evitar divergência

---

## Por que o Caldir foi instalado

O Caldir foi necessário para três funções práticas:

### 1) Espelho local
Ele baixa os calendários para o Linux e permite auditar o estado da agenda fora do celular.

### 2) Diagnóstico de sincronização
Quando um evento não aparece, o Caldir ajuda a responder:

- o evento entrou no Google?
- o token está válido?
- o provider está funcionando?
- o espelho local está consistente?

### 3) Controle operacional
Sem o Caldir, a equipe fica dependente apenas do iPhone e do app Google Calendar.
Com ele, a TI consegue verificar o fluxo por fora do aparelho e detectar falhas antes de virar bagunça operacional.

---

## O que o Caldir não faz

É importante não criar expectativa errada:

- não transforma Google e iCloud em um único calendário nativo
- não faz merge mágico bidirecional entre Apple e Google
- não substitui a configuração do iPhone
- não corrige calendário criado no lugar errado

Ele é uma camada de **espelho + validação + sincronização local**.

---

## Arquitetura validada

### Fluxo correto
- **iPhone** → cria evento
- **Google Calendar** → recebe e armazena o evento
- **Caldir** → espelha o Google no Linux e permite verificação técnica

### Fluxo que deve ser evitado
- criar evento no **iCloud** esperando que ele apareça automaticamente no Google

Se o evento entrar no iCloud, ele fica fora da fonte principal.

---

## Estado atual da operação

### Configuração confirmada
- `caldir` instalado e funcional no perfil `matias`
- binário acessível em `~/.cargo/bin`
- Google Calendar autenticado localmente no perfil
- `default_calendar` do Caldir apontando para o calendário Google importado
- calendário `calendario` marcado como `read_only = true`

### Situação operacional
- eventos criados no iPhone já devem entrar direto no Google
- o espelho local do Google deve refletir o que foi enviado
- o iCloud não deve ser usado como calendário principal

---

## Como o iPhone deve ser configurado

No iPhone:

1. **Ajustes**
2. **Calendário**
3. **Contas** → adicionar/confirmar conta Google
4. deixar **Calendários** ativado
5. em **Calendário Padrão**, selecionar o calendário Google

### Regra prática
Se o evento for criado no iPhone, ele deve apontar para o calendário Google, não para o iCloud.

---

## Rotina de checagem do Caldir

### Frequência
- diariamente, no início do expediente
- após qualquer ajuste de conta, token, provider ou calendário no iPhone
- quando um evento “sumir” ou deixar de aparecer no Google

### Checagem rápida
1. Verificar se o binário está acessível:
   - `PATH="$HOME/.cargo/bin:$PATH" caldir --version`
2. Verificar o estado dos calendários:
   - `PATH="$HOME/.cargo/bin:$PATH" caldir status`
3. Se houver erro de autenticação, renovar a sessão do Google local
4. Fazer um teste controlado, se necessário:
   - criar um evento curto no calendário Google
   - rodar `PATH="$HOME/.cargo/bin:$PATH" caldir sync`
   - confirmar que o evento apareceu no espelho local
5. Repetir `caldir status`
   - o esperado é `No changes`

### Sinais de que está funcionando adequadamente
- o Google aparece sem erro 401/Unauthorized
- `caldir status` mostra `No changes`
- eventos criados no iPhone aparecem no Google porque o calendário padrão é o Google
- o espelho local do Google recebe os eventos sem intervenção manual

### Sinais de falha
- `401 Unauthorized` em qualquer provider Google
- evento existe no iPhone mas não aparece no Google
- `caldir status` mostra alterações inesperadas
- o calendário errado está selecionado no iPhone para criação do evento

### Ação corretiva padrão
- revalidar o token Google local
- conferir se o iPhone está criando eventos no calendário Google
- rodar `caldir sync` e reavaliar `caldir status`

---

## Comandos úteis

### Estado do ambiente
- `PATH="$HOME/.cargo/bin:$PATH" caldir --version`
- `PATH="$HOME/.cargo/bin:$PATH" caldir status`
- `PATH="$HOME/.cargo/bin:$PATH" caldir sync`

### Quando suspeitar de autenticação quebrada
- se surgir `401 Unauthorized`
- se o provider Google começar a falhar na leitura
- se `caldir status` deixar de enxergar os calendários normalmente

---

## Como interpretar os resultados

### Quando está saudável
- evento criado no iPhone entra no Google
- o espelho local acompanha sem erro
- `caldir status` volta limpo depois da sincronização

### Quando há problema de fluxo
- o evento foi criado no calendário errado no iPhone
- o iCloud recebeu o evento, mas o Google não
- o token local do Google expirou
- o provider do Caldir ficou sem autenticação válida

---

## Decisão técnica final

A decisão operacional da Conamore ficou assim:

- **Google como fonte de verdade**
- **iPhone gravando direto no Google**
- **Caldir como espelho e fiscal local**
- **iCloud fora da linha principal de escrita**

Isso reduz divergência e evita o problema de ter eventos em lugares diferentes.

---

## Resumo executivo

Em uma frase:

**o iPhone grava no Google, o Google manda, e o Caldir confirma no Linux se está tudo coerente.**
