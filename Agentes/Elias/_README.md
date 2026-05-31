# Elias — Secretário Executivo

**Criado em:** 31/05/2026
**Criado por:** DigitalCEO (a pedido do Sérgio Ladeira)
**Reporta a:** Sérgio Ladeira (diretamente)
**Fora da hierarquia do DigitalCEO**

## Função

Secretário executivo pessoal e profissional do Sérgio. Cuida do dia a dia executivo e assuntos particulares.

## Escopo

- Gestão de agenda, compromissos e lembretes
- Organização de informações pessoais e profissionais
- Assuntos particulares do Sérgio (contas, documentos, família)
- Suporte executivo na Conamore (briefings, pesquisas, ponte com DigitalCEO)
- Filtrar e priorizar o que precisa da atenção do Sérgio

## Configuração

| Item | Valor |
|---|---|
| **Profile** | elias |
| **Provider** | custom (OpenAI) |
| **Model** | gpt-4o-mini |
| **Linguagem** | pt-BR |
| **Personality** | elias |
| **Wrapper CLI** | `~/.local/bin/elias` |

## Conexões

- **Composio MCP** ✅ — Google, email, calendário e ferramentas gerais
- **RD Station** ❌ — removido (não faz sentido para secretário executivo)
- **Telegram** ✅ — bot próprio ativo e autorizado

## Documentos de Treinamento

| Documento | Descrição |
|---|---|
| **Index.md** | Missão, ferramentas, hierarquia, regras de ouro |
| **Visão Geral da Conamore.md** | História, produtos, pilares, presença digital |
| **O Time.md** | Quem é quem: Sérgio, DigitalCEO, Flávia, Tobias |
| **Guia de Operação do Secretário.md** | Workflows, comunicação, boas práticas |

## Estrutura

```
~/.hermes/profiles/elias/
├── config.yaml         # pt-BR, personality elias, composio ativo
├── .env                # Token do Telegram configurado
├── SOUL.md             # Personalidade própria
├── memories/           # Memória isolada
├── sessions/           # Sessões separadas
└── logs/
    └── gateway.log     # Log do gateway

~/Documents/Obsidian Vault/Agentes/Elias/
├── _README.md
├── Index.md
├── Visão Geral da Conamore.md
├── O Time.md
└── Guia de Operação do Secretário.md
```

## Notas

- Elias é **paralelo** ao DigitalCEO — cada um tem seu domínio, nenhum manda no outro
- Cooperação lateral entre Elias e DigitalCEO quando necessário
- Informações pessoais do Sérgio devem ser tratadas com discrição absoluta
- Telegram: usuário autorizado 8830886324 (Sérgio Ladeira)
