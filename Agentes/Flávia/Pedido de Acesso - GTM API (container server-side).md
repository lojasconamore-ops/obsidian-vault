---
tags: [gtm, server-side, stape, acesso, ti, matias]
gerado: 2026-09-02
status: pedido-de-acesso
---

# Pedido de Acesso — Google Tag Manager API (leitura do container server-side)

**De:** Flávia (Marketing)
**Para:** Matias (TI)
**Aprovado por:** Sérgio
**Container alvo:** `GTM-N7Z62R96` (server-side, hospedado na Stape)

## Objetivo
Dar à Flávia acesso **somente-leitura** à Tag Manager API para mapear clients, tags, triggers, variables e transformations do container server-side — sem depender do Matias a cada consulta.

## O que o Matias precisa fazer (uma única vez)

### 1. Criar uma Service Account (Google Cloud)
1. Acessar https://console.cloud.google.com
2. Criar/abrir um projeto (ex.: `conamore-tracking`)
3. Menu **IAM e Admin → Service Accounts → Criar conta de serviço**
4. Nome sugestivo: `flavia-gtm-readonly`
5. **Criar chave** → tipo **JSON** → baixar o arquivo (`*.json`)

### 2. Habilitar a API
1. Em **APIs e Serviços → Biblioteca**
2. Buscar **"Tag Manager API"** → **Ativar** (`tagmanager.googleapis.com`)

### 3. Compartilhar o container com a service account (mínimo: leitura)
1. Acessar https://tagmanager.google.com
2. Selecionar o container `GTM-N7Z62R96` (Server)
3. **Admin → Container → Gestão de usuários / User Management**
4. Adicionar o e-mail da service account (`<...>@<projeto>.iam.gserviceaccount.com`)
5. Permissão: **"Ver e analisar" (Read & Analyze)** — ou o nível mínimo disponível de leitura (NUNCA "Publicar")

### 4. Me devolver (via canal seguro)
- [ ] Arquivo JSON da service account (`client_email` + `private_key`)
- [ ] **Account ID** e **Container ID** numéricos (ver na URL do GTM ou em Admin → Settings):
  `https://tagmanager.google.com/#/container/accounts/<account_id>/containers/<container_id>/workspaces/<id>`

## O que a Flávia vai fazer depois (e o que NÃO vai)
**Vai (somente leitura):**
- `accounts.containers.workspaces.tags.list` / `clients.list` / `triggers.list` / `variables.list` / `transformations.list`
- Gerar o inventário completo do container (tags+clients+mapeamentos) e documentar no Obsidian.

**NÃO vai:**
- Criar/editar tag, client, trigger ou variable.
- Criar versão ou **publicar** (publish) nada.
- Alterar qualquer configuração do container.

## Segurança
- Service account com **escopo mínimo de leitura**; sem permissão de publish.
- A chave privada fica sob custódia do profile Marketing (não versionada em repositório público).
- Se preferir, o Matias pode revogar a chave a qualquer momento (regenerar).

## Status
- [ ] Service account criada + chave JSON gerada
- [ ] Tag Manager API ativada
- [ ] Container `GTM-N7Z62R96` compartilhado (read-only)
- [ ] Credenciais entregues à Flávia
- [ ] Flávia mapeia o container e documenta o inventário
