# Integração Octadesk ↔ Hermes Agent

## Objetivo
Permitir que gerentes humanos da Conamore conversem com os agentes Hermes (Matias, Flávia, Tobias, etc.) através do Octadesk. Todas as conversas ficam documentadas na plataforma para auditoria e orientação dos gerentes.

## Status
- ✅ Plugin criado e registrado no Hermes Gateway
- ✅ Polling implementado (busca mensagens a cada 30s)
- ✅ Envio de respostas via API REST
- ✅ Roteamento por email (user_routing) implementado
- ✅ Conectado à API da Conamore

## Arquitetura
```
Gerente Humano (Octadesk)
    ↓ (envia mensagem no chat)
Octadesk API
    ↓ (polling a cada 30s)
Hermes Gateway (OctadeskAdapter)
    ↓ (verifica user_routing)
Agente Hermes correspondente
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
| `~/.hermes/profiles/matias/plugins/octadesk/adapter.py` | Adapter com polling, API client e roteamento |
| `~/.hermes/profiles/matias/plugins/octadesk/__init__.py` | Entry point do plugin |
| `~/.hermes/profiles/matias/config.yaml` | Configuração da plataforma + roteamento |

## Configuração

### Base (já configurada)
```yaml
octadesk:
  enabled: true
  extra:
    api_key: ''                    # via OCTADESK_API_KEY env
    subdomain: 'conamore'
    agent_email: 'ti@conamore.com.br'
    poll_interval: 30
    base_url: 'https://conamore.api003.octadesk.services'
    allowed_users: []              # vazio = todos permitidos
    allow_all: false
```

### Roteamento por Gerente → Agente (user_routing)
Adicione no `config.yaml` do profile `matias`:
```yaml
    user_routing:
      'gerente.logistica@conamore.com.br': 'tobias'
      'gerente.marketing@conamore.com.br': 'flavia'
      'gerente.financeiro@conamore.com.br': 'tiago'
      'gerente.rh@conamore.com.br': 'maria'
      'gerente.comercial@conamore.com.br': 'natalia'
      'fabrica@conamore.com.br': 'fabricia'
      'executivo@conamore.com.br': 'elias'
      'juridico@conamore.com.br': 'adrian'
      'compras@conamore.com.br': 'bianco'
      'ceo@conamore.com.br': 'cona'
```

**Como funciona:**
- Quando um gerente manda mensagem, o plugin verifica o email no `user_routing`
- Se encontrar match, aplica um `channel_prompt` com a persona do agente designado
- O agente responde **como se fosse o agente mapeado** (ex: Tobias responde perguntas de logística)
- A resposta volta pelo Octadesk com a identidade do "sistema"

**Agentes suportados:**
| Profile | Agente | Especialidade |
|---------|--------|---------------|
| `matias` | Matias | TI, infraestrutura, sistemas |
| `flavia` | Flávia | Marketing, RD Station, comunicação |
| `tobias` | Tobias | Logística, Intelipost, transporte |
| `tiago` | Tiago | Financeiro, ERP, contabilidade |
| `bianco` | Bianco | Compras |
| `natalia` | Natália | Comercial |
| `maria` | Maria | RH |
| `fabricia` | Fabricia | Fábrica |
| `elias` | Elias | Executivo, briefings |
| `adrian` | Adrian | Jurídico, compliance |
| `cona` | Cona/DigitalCEO | Estratégia, diretoria |

## Ativação / Reinício
Após alterar o config, reinicie o gateway (de um shell separado):
```bash
sudo /home/sergio-ladeira/.local/bin/hermes gateway restart
```

## Teste
1. Gerente envia mensagem no Octadesk
2. Aguarde até 30 segundos (intervalo de polling)
3. Verifique se o agente respondeu no mesmo chat

## Endpoints Octadesk Utilizados
| Método | Endpoint | Função |
|--------|----------|--------|
| GET | `/chat?limit=50&sort=updatedAt&order=desc` | Listar chats recentes |
| GET | `/chat/{id}/messages` | Buscar mensagens de um chat |
| POST | `/chat/{id}/messages` | Enviar resposta do agente |

## Segurança
- API Key via variável de ambiente (`OCTADESK_API_KEY`)
- Nunca logada em texto plano
- Filtro `allowed_users` por e-mail
- Loop prevention (ignora mensagens do próprio agente)
- HTTPS apenas

## Próximos Passos
- [ ] Mapear emails reais dos gerentes no `user_routing`
- [ ] Testar fluxo completo com cada agente
- [ ] Documentar orientação para gerentes humanos
- [ ] Avaliar webhook outbound do Octadesk (substituir polling)
