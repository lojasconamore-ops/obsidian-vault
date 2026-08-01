# Faxina de Arquivos e Perfis — 2026-08-01

## Escopo

Organização conservadora dos 12 perfis Hermes e do Vault Obsidian da Conamore, com corte operacional em `2026-07-20`.

## Política aplicada

- Preservar integralmente históricos de Telegram e Octadesk.
- Preservar relatórios estratégicos, auditorias, pareceres e relatórios individuais.
- Remover somente séries recorrentes de relatórios/briefings operacionais anteriores ao corte.
- Remover saídas antigas de cron, logs antigos e caches reconstruíveis.
- Fazer backup consistente dos bancos antes da poda.

## Resultado

| Item | Resultado |
|---|---:|
| Relatórios/briefings recorrentes removidos | 141 |
| Logs anteriores ao corte removidos | 57 |
| Saídas antigas de cron removidas | 485 |
| Sessões antigas de cron/subagentes removidas | 281 |
| Registros órfãos preexistentes reparados | 8.070 |
| Links de Vault centralizados | 2 |
| Espaço retirado do conjunto operacional | 497,1 MiB |
| Backup de rollback | 314 MiB |
| Ganho líquido estimado com backup mantido | 183,1 MiB |

## Consolidação do Obsidian

As cópias locais abaixo foram substituídas por links simbólicos para o Vault central:

- Perfil Marketing: `~/.hermes/profiles/marketing/obsidian`
- Perfil Tiago: `~/.hermes/profiles/tiago/home/Documents/Obsidian Vault`

Fonte canônica:

`~/Documents/Obsidian Vault`

Os índices de briefings e relatórios de Elias, Natália e Flávia foram atualizados para remover referências aos documentos excluídos.

## Bancos Hermes

- Backup online criado antes de qualquer exclusão.
- Telegram e Octadesk mantiveram suas contagens.
- Todos os bancos passaram em `PRAGMA integrity_check`.
- Violações de chave estrangeira preexistentes foram eliminadas.

## Rollback

Backup da operação:

`~/.hermes/backups/faxina-20260801T131529-0300`

Conteúdo:

- Bancos `state.db` comprimidos por perfil.
- Checksums SHA-256.
- Manifesto dos relatórios removidos.
- Cópias anteriores dos Vaults locais substituídos por links.
- Resultado técnico da execução.

## Frota de agentes

- Gateway master: 1 instância ativa.
- Perfis ativos e sem duplicidade: Matias, Tiago, Bianco, Elias, Marketing, Natália, Tobias, Maria e Rian.
- Perfis sem gateway, condição já existente antes da faxina: Adrian, Fabricia e Thiago Ribeiro.
- Processos zumbis: nenhum.
- Memória total observada da frota: aproximadamente 3.890 MB.

Nenhum gateway foi iniciado ou removido nesta operação. A ativação permanente dos três perfis ausentes depende de decisão operacional separada.

## Exceção de segurança

Foi detectada uma credencial SQL em texto puro dentro da documentação. Por decisão executiva, a credencial e o arquivo não foram alterados nesta operação. O risco permanece pendente para tratamento futuro.
