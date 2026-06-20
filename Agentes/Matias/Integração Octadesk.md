# Integração Octadesk ↔ Hermes Agent

## Objetivo
Permitir que gerentes humanos da Conamore conversem com os agentes Hermes (Matias, Flávia, Tobias, etc.) através do Octadesk. Todas as conversas ficam documentadas na plataforma para auditoria e orientação dos gerentes.

## Status
- ✅ Plugin criado e registrado no Hermes Gateway
- ✅ Polling implementado (busca mensagens a cada 30s)
- ✅ Envio de respostas via API REST
- ⏳ Aguardando API Key da Conamore para ativar

## Arquitetura
```
Gerente Humano (Octadesk)
    ↓ (envia mensagem no chat)
Octadesk API
    ↓ (polling a cada 30s)
Hermes Gateway (OctadeskAdapter)
    ↓ (MessageEvent)
Agente Hermes (Matias/Flávia/etc)
    ↓ (resposta)
Hermes Gateway (OctadeskAdapter)
    ↓ (POST /chat/{id}/messages)
Octadesk API
    ↓
Gerente Humano vê a resposta
```

## Arquivos
| Arquivo | Descrição |
|---------|-----------|
| `~/.hermes/profiles/matias/plugins/octadesk/plugin.yaml` | Manifest do plugin |
| `~/.hermes/profiles/matias/plugins/octadesk/adapter.py` | Adapter com polling e API client |
| `~/.hermes/profiles/matias/plugins/octadesk/__init__.py` | Entry point do plugin |
| `~/.hermes/profiles/matias/config.yaml` | Configuração da plataforma |

## Configuração Necessária
Adicionar ao `~/.hermes/profiles/matias/config.yaml`:
```yaml
octadesk:
  enabled: true
  extra:
    api_key: 'SUA_API_KEY_AQUI'
    subdomain: 'conamore'
    agent_email: 'matias@conamore.com'
    poll_interval: 30
    base_url: 'https://api.octadesk.com'
    allowed_users: []  # lista de emails autorizados; vazio = todos
    allow_all: false
```

Ou via variáveis de ambiente (preferido para secrets):
```bash
export OCTADESK_API_KEY="sua-key"
export OCTADESK_SUBDOMAIN="conamore"
export OCTADESK_AGENT_EMAIL="matias@conamore.com"
export OCTADESK_POLL_INTERVAL="30"
```

## Ativação
1. Configurar API key e subdomain
2. Reiniciar o Hermes Gateway (de um shell separado)
3. Verificar logs do gateway

## Endpoints Octadesk Utilizados
| Método | Endpoint | Função |
|--------|----------|--------|
| GET | `/chat?limit=50&sort=updatedAt&order=desc` | Listar chats recentes |
| GET | `/chat/{id}/messages` | Buscar mensagens de um chat |
| POST | `/chat/{id}/messages` | Enviar resposta do agente |

## Segurança
- API Key nunca é logada em texto plano
- Filtro de `allowed_users` por e-mail
- Ignora mensagens enviadas pelo próprio agente (loop prevention)
- Conexão via HTTPS apenas

## Próximos Passos
- [ ] Receber API Key da Conamore
- [ ] Testar conexão real com a API
- [ ] Validar fluxo completo gerente → agente → gerente
- [ ] Documentar orientação para gerentes humanos
- [ ] Avaliar webhook outbound do Octadesk (substituir polling futuramente)

## Notas
- Polling a cada 30s é o padrão. Pode ser ajustado via `poll_interval`.
- Sem webhook outbound confirmado no Octadesk da Conamore → polling é a solução mais segura.
- O plugin foi criado no profile `matias` e habilitado em `plugins.enabled`.
