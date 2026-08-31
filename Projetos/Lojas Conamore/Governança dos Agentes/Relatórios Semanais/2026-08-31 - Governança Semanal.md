# Revisão Semanal de Governança — 2026-08-31

**Janela analisada:** 2026-08-24 05:00:31 a 2026-08-31 05:00:31 — America/Sao_Paulo  
**Responsáveis:** Sérgio Ladeira e Cona  
**Fonte técnica:** snapshot read-only de configurações, gateways, crons, sessões e logs ao vivo

## Resumo executivo

- **Agentes de IA revisados:** 12
- **Agentes com atividade na janela:** 8/12
- **Modelos/providers no padrão aprovado:** 12/12
- **Desvios de configuração direta:** 1 perfil com `api_max_retries` fora do padrão (Elias = 3; padrão = 1 com fallback)
- **Automações vermelhas:** 2 crons de marketing em `drift_skip`
- **Valor confirmado:** 0 evidências com validação humana registrada
- **Valor pendente:** toda a atividade técnica observada está em **valor aguardando validação humana**

Conclusão: a frota está majoritariamente saudável e aderente ao padrão de modelos/providers, mas a revisão ainda está formando linha de base. Há um ponto claro de melhoria no perfil Elias e duas automações de marketing que ficaram vermelhas por drift de configuração desde a criação.

### Semáforo da revisão

- **Verdes:** 8 agentes
- **Amarelos:** 3 agentes
- **Adormecido:** 1 agente (Fabricia)
- **Vermelhos:** 2 automações (marketing)

## Saúde da frota

| Agente | Gateway | Modelo/provider | Crons | Integrações | Status |
|---|---|---|---|---|---|
| Cona / default | running | `openai-codex:gpt-5.6-sol` | ok | Telegram/Webhook conectados | Verde / Manter |
| Adrian | running | `openai-codex:gpt-5.6-luna` | sem crons | Telegram/Octadesk conectados | Verde / Manter |
| Bianco | running | `openai-codex:gpt-5.6-luna` | 2 crons desativados | Telegram/Octadesk conectados | Verde / Manter |
| Elias | running | `openai-codex:gpt-5.6-sol` | 3 crons ok | Telegram/Octadesk conectados | Amarelo / Melhorar |
| Fabricia | stopped | `opencode-go:deepseek-v4-pro` | sem crons | Telegram desconectado | Amarelo / Adormecer |
| Maria | running | `openai-codex:gpt-5.6-sol` | 3 crons ok | Telegram/Octadesk conectados | Verde / Manter |
| Marketing | running | `opencode-go:deepseek-v4-pro` | 11 crons ok, 2 em drift_skip | Telegram/Octadesk conectados | Amarelo / Melhorar |
| Matias | running | `opencode-go:deepseek-v4-pro` | 5 crons ok | Telegram/Octadesk conectados | Verde / Manter |
| Natália | running | `openai-codex:gpt-5.6-luna` | 4 crons ok | Telegram/Octadesk conectados | Verde / Manter |
| Rian | running | `openai-codex:gpt-5.6-luna` | 4 crons ok | Telegram conectado | Verde / Manter |
| Tiago | running | `openai-codex:gpt-5.6-sol` | 1 cron ok | Telegram/Octadesk conectados | Verde / Manter |
| Tobias | running | `opencode-go:deepseek-v4-pro` | 3 crons desativados | Telegram/Octadesk conectados | Amarelo / Observar |

## Uso e valor

| Agente | Atividade observada | Entrega/resultado | Validador humano | Valor |
|---|---|---|---|---|
| Cona / default | 30 sessões, 7 mensagens; governança semanal e sessões operacionais | Coordenação e coleta de evidências | Não registrado | valor aguardando validação humana |
| Adrian | Sem atividade recente | Sem entrega nova na janela | Não registrado | valor aguardando validação humana |
| Bianco | Sem atividade recente | Sem entrega nova na janela | Não registrado | valor aguardando validação humana |
| Elias | 21 sessões, 21 mensagens; agenda diária, ShinePhone e resumo Granola | Rotinas recorrentes concluídas | Não registrado | valor aguardando validação humana |
| Fabricia | Sem atividade recente | Perfil sem uso na janela | Não registrado | valor aguardando validação humana |
| Maria | 21 sessões, 21 mensagens; radar de ponto e atrasos | Rotinas de RH executadas | Não registrado | valor aguardando validação humana |
| Marketing | 53 sessões, 164 mensagens; relatórios GA4, Ads e monitoramentos | Entregas recorrentes, com 2 automações em drift_skip | Não registrado | valor aguardando validação humana |
| Matias | 18 sessões, 41 mensagens; GNRE, Obsidian sync e status Brasília | Rotinas de TI/infra concluídas | Não registrado | valor aguardando validação humana |
| Natália | 48 sessões, 49 mensagens; vendas B2B, relatórios da casa e hotelaria | Relatórios recorrentes concluídos | Não registrado | valor aguardando validação humana |
| Rian | Sem atividade recente | Crons de lojas físicas permanecem disponíveis | Não registrado | valor aguardando validação humana |
| Tiago | 3 sessões, 5 mensagens; cruzamento semanal Oracle × lista negra | Um cron semanal concluído | Não registrado | valor aguardando validação humana |
| Tobias | 1 sessão; controle de modelo usado por agente | Sem entrega operacional nova na janela | Não registrado | valor aguardando validação humana |

## Qualidade, confiabilidade e autonomia

| Agente/fluxo | Evidência | Correção/intervenção | Classificação |
|---|---|---|---|
| Cona / default | Modelo/provider aderentes; gateway estável | Nenhuma intervenção necessária | Estável |
| Elias | `api_max_retries=3` acima do padrão; fallback presente | Ajuste recomendado no próximo ciclo | A observar / melhorar |
| Marketing — Monitoramento de visibilidade em IA | `last_status=error` com `drift_skip`; cron pulado para evitar gasto involuntário | Necessita pinagem explícita | Degradado |
| Marketing — Monitoramento Clone Parasita radiotuzla | `last_status=error` com `drift_skip`; cron pulado para evitar gasto involuntário | Necessita pinagem explícita | Degradado |
| Fabricia | Perfil sem uso e gateway Telegram desconectado | Definir se continua adormecida | Baixa atividade |
| Telegram nas plataformas | Há reconexões e timeouts históricos, mas estado atual segue conectado | Monitorar recorrência, sem declarar falha vigente | Intermitente |

## Riscos e permissões

| Item | Gravidade | Escopo | Contenção recomendada |
|---|---|---|---|
| Dois crons de marketing em drift_skip | Alta | Automação de marketing | Pin explícito do provider/modelo do cron antes do próximo ciclo |
| Elias com `api_max_retries` acima do padrão | Média | Perfil de execução do agente | Normalizar a configuração no próximo ajuste aprovado |
| Fabricia parada e sem uso recente | Média | Capacidade ociosa | Manter adormecida até haver demanda clara |
| Sinais históricos de instabilidade Telegram | Baixa | Mensageria | Observar recorrência; não tratar como falha atual sem novo evento |
| `api_server` desconectado no perfil default | Baixa | Integração da workspace | Confirmar se é requisito ativo antes de qualquer ação |

## Portfólio

| Agente/automação | Manter | Melhorar | Observar | Adormecer | Encerrar | Justificativa |
|---|:---:|:---:|:---:|:---:|:---:|---|
| Cona / default | X |  |  |  |  | Padrão aderente e operação estável |
| Adrian | X |  |  |  |  | Padrão aderente, sem desvios | 
| Bianco | X |  |  |  |  | Padrão aderente |
| Elias |  | X |  |  |  | `api_max_retries` fora do padrão aprovado |
| Fabricia |  |  |  | X |  | Sem atividade recente e perfil parado |
| Maria | X |  |  |  |  | Padrão aderente e rotinas ok |
| Marketing |  | X |  |  |  | 2 automações em `drift_skip` |
| Matias | X |  |  |  |  | Padrão aderente e automações ok |
| Natália | X |  |  |  |  | Padrão aderente e uso consistente |
| Rian | X |  |  |  |  | Padrão aderente |
| Tiago | X |  |  |  |  | Padrão aderente |
| Tobias |  |  | X |  |  | Baixa atividade na janela; manter sob observação |

## Decisões da semana

| # | Decisão | Responsável | Prazo | Critério de conclusão |
|---:|---|---|---|---|
| 1 | Pinagem explícita dos dois crons de marketing em drift_skip e novo teste de execução | Matias + Flávia/Marketing | 2026-09-01 | Ambos os jobs voltarem a `last_status=ok` sem novo drift_skip |
| 2 | Normalizar `api_max_retries` do Elias para o padrão 1, mantendo o fallback aprovado | Matias | 2026-09-02 | Config live do Elias mostrar `api_max_retries: 1` e fallback preservado |
| 3 | Definir se Fabricia permanece adormecida ou volta a operar com objetivo claro | Sérgio | 2026-09-03 | Decisão registrada com status final e próxima ação explícita |

## Cobertura e limitações

- **Fontes cobertas:** inventário vivo de 12 perfis de IA, gateways, crons, sessões e sinais recentes de log.
- **Janela coberta:** 2026-08-24 05:00:31 a 2026-08-31 05:00:31 — America/Sao_Paulo.
- **Custos não mensuráveis:** custo reportado como zero em todos os perfis; isso não confirma ausência de cobrança pelo provider.
- **Valor aguardando validação humana:** toda atividade técnica observada na janela.
- **Suposições evitadas:** não tratei silêncio como conclusão, não declarei falha vigente com base em log histórico e não inferi valor financeiro sem evidência humana ou objetiva.
- **Limitação da linha de base:** esta revisão ainda está na fase inicial; os semáforos servem para formar referência e não para pontuação definitiva.
