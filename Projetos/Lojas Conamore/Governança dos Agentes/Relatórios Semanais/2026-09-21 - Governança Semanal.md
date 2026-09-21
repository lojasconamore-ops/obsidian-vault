# Revisão Semanal de Governança — 2026-09-21

**Janela analisada:** 2026-09-14 05:00:34 a 2026-09-21 05:00:34 — America/Sao_Paulo  
**Horizonte de decisões:** 2026-09-21 a 2026-09-27  
**Responsáveis:** Sérgio Ladeira e Cona  
**Fonte técnica:** coleta read-only de configurações, gateways, crons, sessões e logs; campos de modelo verificados novamente nos 12 YAMLs ao vivo às 05:01 BRT  

## Resumo executivo

**Conclusão primeiro:** a frota segue operacional na maior parte, mas a governança da semana é **vermelha** por uma regressão transversal de configuração: **0/12 perfis mantêm o fallback aprovado `openai-codex:gpt-5.4-mini`**; todos apontam agora para `openai-codex:gpt-5.6-luna`. Além disso, Marketing e Tiago continuam com primários fora do mapa aprovado, Elias mantém `api_max_retries=3`, e Fabrícia está parada com falha recente de saldo/autenticação do provider. Não houve evidência de violação de permissão ou exposição de segredo.

- **Frota:** 12 agentes de IA; o perfil humano/reservado foi excluído corretamente.
- **Gateways:** 11/12 em execução no inventário; Fabrícia consta parada. Telegram aparece conectado nos outros 11.
- **Atividade registrada:** 175 sessões, 1.702 chamadas de API, 2.654 chamadas de ferramenta e 197 mensagens classificadas como `user_messages`.
- **Consumo registrado:** 9.646.391 tokens de entrada e 1.100.302 de saída.
- **Crons:** 35 habilitados e 13 desabilitados. Nenhum habilitado traz `last_status=error` no snapshot; um compromisso futuro ainda não executado não possui status anterior.
- **Modelos primários:** 10/12 aderentes. Desvios: Marketing e Tiago.
- **Fallback:** 0/12 aderentes ao padrão aprovado; houve regressão em relação à revisão anterior, que registrava 12/12 aderentes.
- **Retries:** 11/12 aderentes; Elias permanece em 3, contra o padrão 1.
- **Confiabilidade:** 118 sessões encerraram como `cron_complete`; 10 como `cron_incomplete_no_output`, sendo 9 da Natália e 1 do default.
- **Custo:** US$ 0 registrado/estimado localmente; **custo real desconhecido**, pois a cobrança pode não ser mensurável pelos providers.
- **Valor:** não há validação humana ou indicador de negócio na coleta. Para toda atividade: **valor aguardando validação humana**.
- **Linha de base:** as quatro primeiras revisões já foram concluídas. O semáforo permanece qualitativo para comparação, sem funcionar como nota de desempenho.

### Semáforo executivo

- 🟢 **Verdes:** 11 gateways em execução; 11 Telegrams conectados; 10/12 modelos primários aderentes; 35 crons habilitados sem erro vigente registrado; Matias voltou ao primário aprovado; o cron semanal do Tiago concluiu com `ok` em 14/09.
- 🟡 **Amarelos:** valor e qualidade aguardam validação humana; custo real desconhecido; 10 sessões `cron_incomplete_no_output`; warnings recorrentes de transporte Telegram foram recuperados e não comprovam indisponibilidade vigente; API server do default permanece desconectado, sem requisito atual confirmado; lacuna entre crons do Rian e telemetria de sessões.
- 🔴 **Vermelhos:** fallback errado nos 12 perfis; Marketing e Tiago fora do mapa primário aprovado; Elias com retries fora do padrão; Fabrícia parada e com falha recente do provider; 9 sessões incompletas sem saída na Natália.

## 1. Saúde da frota

| Agente | Gateway / integrações | Modelo/provider ao vivo | Fallback / retries | Status |
|---|---|---|---|---|
| Cona / default | Running; Telegram e webhook conectados; API server desconectado | `openai-codex:gpt-5.6-sol` — aderente | `gpt-5.6-luna` incorreto / 1 | 🔴 configuração |
| Adrian | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-luna` — aderente | incorreto / 1 | 🔴 configuração |
| Bianco | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-luna` — aderente | incorreto / 1 | 🔴 configuração; baixo uso |
| Elias | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — aderente | incorreto / **3** | 🔴 configuração |
| Fabrícia | Perfil parado; Telegram desconectado | `opencode-go:deepseek-v4-pro` — aderente | incorreto / 1 | 🔴 disponibilidade/provider |
| Maria | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — aderente | incorreto / 1 | 🔴 configuração |
| Flávia / Marketing | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — fora do padrão `opencode-go:deepseek-v4-pro` | incorreto / 1 | 🔴 primário/fallback |
| Matias | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — aderente | incorreto / 1 | 🔴 fallback; primário corrigido desde a semana anterior |
| Natália | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-luna` — aderente | incorreto / 1 | 🔴 fallback/saídas incompletas |
| Rian | Running; Telegram conectado | `openai-codex:gpt-5.6-luna` — aderente | incorreto / 1 | 🔴 fallback; telemetria amarela |
| Tiago | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — fora do padrão `gpt-5.6-luna` | incorreto / 1 | 🔴 primário/fallback |
| Tobias | Running; Telegram/Octadesk conectados | `opencode-go:deepseek-v4-pro` — aderente | incorreto / 1 | 🔴 fallback; baixo uso |

A coleta e a releitura seletiva dos YAMLs concordam quanto aos modelos. Nenhuma configuração foi alterada.

## 2. Atividade observada e valor

| Agente | Evidência na janela | Resultado técnico observável | Valor |
|---|---|---|---|
| Cona / default | 29 sessões; 357 chamadas de API; 20 `cron_complete`; 1 incompleta | Coordenação, rotinas diárias e extrações registradas | valor aguardando validação humana |
| Adrian | 2 sessões; 7 chamadas de API | Trabalho jurídico consultivo registrado | valor aguardando validação humana |
| Bianco | 1 sessão de teste; 1 chamada de API | Apenas smoke test observável; crons próprios desabilitados | valor aguardando validação humana |
| Elias | 18 sessões; 17 `cron_complete` | Agenda, ShinePhone e resumo de reuniões executados | valor aguardando validação humana |
| Fabrícia | 1 sessão de teste; 0 chamadas de API | Teste falhou por saldo insuficiente do provider; sem entrega | valor aguardando validação humana |
| Maria | 2 sessões, incluindo smoke test e sessão aberta; 1 chamada de API | Crons de RH aparecem com último status `ok` | valor aguardando validação humana |
| Flávia / Marketing | 59 sessões; 614 chamadas de API; 55 `cron_complete` | Sites, Ads, GA4 e monitoramentos executados | valor aguardando validação humana |
| Matias | 9 sessões; 111 chamadas de API; 6 `cron_complete` | Manutenção Hermes e automações fiscais registradas | valor aguardando validação humana |
| Natália | 49 sessões; 425 chamadas de API; 19 completas e 9 incompletas sem saída | Relatórios comerciais executados, com confiabilidade a revisar | valor aguardando validação humana |
| Rian | 1 sessão de smoke test; crons diários com `ok` | Execução dos jobs indicada, mas sem telemetria de sessão correspondente | valor aguardando validação humana |
| Tiago | 3 sessões; 42 chamadas de API; cron semanal concluído | Análise de crédito e cruzamento semanal registrados | valor aguardando validação humana |
| Tobias | 1 sessão de teste; 0 chamadas de API | Sem entrega substantiva no perfil; crons próprios desabilitados | valor aguardando validação humana |

Os 12 perfis possuem ao menos um registro de sessão, mas em 5 deles a evidência recente se limita a smoke test, sessão aberta ou execução de cron sem telemetria atribuída. Volume técnico não comprova utilidade, qualidade, economia ou impacto.

## 3. Qualidade, confiabilidade e riscos

| Agente/fluxo | Evidência | Avaliação | Ação recomendada |
|---|---|---|---|
| Fallback da frota | 12/12 YAMLs apontam para `gpt-5.6-luna`, contra padrão `gpt-5.4-mini`; semana anterior registrava conformidade total | 🔴 regressão transversal e menor garantia de failover conforme política | Sérgio decidir; Matias corrigir apenas após autorização e validar smoke test |
| Marketing | Primário `gpt-5.6-sol`, padrão aprovado `deepseek-v4-pro/opencode-go` | 🔴 drift persistente | Registrar decisão explícita: restaurar ou formalizar exceção |
| Tiago | Primário `gpt-5.6-sol`, padrão aprovado `gpt-5.6-luna/openai-codex` | 🔴 drift persistente | Registrar decisão explícita e testar se aprovado |
| Elias | `api_max_retries=3`; erro interno de ferramenta em 20/09, embora cron tenha terminado `ok` | 🔴 política; 🟡 possível sucesso parcial | Conferir artefato do ciclo e normalizar retries somente com aprovação |
| Fabrícia | Gateway parado; em 18/09 o provider retornou saldo insuficiente e o fallback não foi utilizável no runtime | 🔴 indisponibilidade confirmada no teste | Manter adormecida ou restaurar provider/fallback com teste, conforme decisão |
| Natália | 9 `cron_incomplete_no_output`; execuções recentes aparecem em `gpt-5.6-sol` apesar do primário `gpt-5.6-luna` | 🔴 confiabilidade/possível pin de job | Identificar jobs afetados e confirmar entregas; não inferir sucesso pelo volume |
| Rian | 4 crons com `ok`, mas só 1 sessão de smoke test na base | 🟡 atribuição de telemetria inconsistente | Documentar onde workers e artefatos são registrados |
| Rede Telegram | Warnings recentes em vários perfis, seguidos de recuperação; 11 conectados no snapshot | 🟡 intermitência recuperada, não outage vigente | Observar falhas reais de entrega e recorrência |
| Octadesk/Matias | Erros HTTP 500 em 20/09; integração consta conectada no estado atual | 🟡 falha histórica recuperada ou intermitente | Correlacionar com chat/entrega antes de declarar incidente |
| Custo | US$ 0 no banco local | Desconhecido | Não tomar decisão financeira com base no zero local |

Nenhuma violação de credencial, permissão ou escopo foi identificada na coleta. Isso não equivale a auditoria completa de segurança. Nenhuma conclusão de qualidade ou autonomia foi atribuída sem artefato ou validação humana.

## 4. Portfólio

### Agentes

| Agente | Classificação | Justificativa |
|---|---|---|
| Cona / default | **Melhorar** | Uso alto e gateway estável, mas fallback fora da política; valor aguardando validação humana |
| Adrian | **Melhorar** | Uso consultivo recente; fallback incorreto e valor pendente |
| Bianco | **Adormecer** | Apenas smoke test e dois crons desabilitados; preservar para uso sob demanda |
| Elias | **Melhorar** | Uso recorrente, mas fallback, retries e erro interno exigem correção/verificação |
| Fabrícia | **Adormecer** | Perfil parado e provider sem saldo no teste; não reativar sem objetivo e correção aprovada |
| Maria | **Melhorar** | Crons tecnicamente estáveis, mas fallback incorreto e valor pendente |
| Flávia / Marketing | **Melhorar** | Alta atividade; primário e fallback divergem do padrão |
| Matias | **Melhorar** | Primário voltou ao padrão, mas fallback está incorreto; integrações tiveram sinais recuperados |
| Natália | **Melhorar** | Alta atividade, porém 9 saídas incompletas e possível pin de modelo nos jobs |
| Rian | **Observar** | Crons com `ok`, mas telemetria de sessões não permite confirmar execução/entrega |
| Tiago | **Melhorar** | Cron semanal recuperado, porém primário e fallback divergem do padrão |
| Tobias | **Adormecer** | Sem atividade substantiva e três crons próprios desabilitados; preservar para demanda logística |

### Automações

| Grupo | Classificação | Justificativa |
|---|---|---|
| 35 crons habilitados | **Melhorar** | Sem `last_status=error` vigente, mas há 10 sessões incompletas, drift de modelos e valor não validado |
| Relatórios comerciais da Natália | **Melhorar** | Nove sessões incompletas sem saída e possível modelo fixado fora do primário |
| Agenda/ShinePhone/resumo do Elias | **Melhorar** | Jobs terminam `ok`, porém houve erro interno de ferramenta e configuração divergente |
| Rotinas de RH da Maria | **Observar** | Últimos status `ok`; recebimento e utilidade não foram validados |
| Monitoramentos de Marketing | **Melhorar** | Alta frequência e status técnico estável, mas modelo fora do padrão e valor pendente |
| Automações fiscais do Matias | **Observar** | Execuções recentes `ok`; valor/recebimento aguardam validação humana |
| Relatórios de lojas do Rian | **Observar** | Status `ok`, mas telemetria não mostra as sessões correspondentes |
| Cruzamento semanal do Tiago | **Observar** | Execução de 14/09 concluiu `ok`, recuperando o erro anterior; resultado ainda não validado |
| 13 crons desabilitados | **Adormecer** | Não reativar sem processo, proprietário, indicador e autorização |
| Encerramentos | **Observar** | Nenhum encerramento recomendado nesta semana; qualquer encerramento exige Sérgio |

Não há item classificado como **Manter** nesta semana porque falta validação humana de valor e toda a frota possui drift no fallback. `Adormecer` preserva perfil/documentação e não significa exclusão.

## 5. Decisões da semana

| # | Decisão proposta | Responsável sugerido | Prazo | Critério de conclusão |
|---:|---|---|---|---|
| 1 | Aprovar ou rejeitar a restauração do fallback `openai-codex:gpt-5.4-mini` nos 12 perfis, dos primários de Marketing/Tiago e de `api_max_retries=1` no Elias | Sérgio decide; Matias executa somente se aprovado | 2026-09-22 | Decisão registrada; se aprovada, 12 YAMLs relidos com fallback correto, primários/retry aderentes ou exceções documentadas, e smoke tests bem-sucedidos nos providers afetados |
| 2 | Resolver o bloco de confiabilidade de Fabrícia, Natália, Elias e Rian | Matias, com validação dos gestores das áreas | 2026-09-24 | Fabrícia explicitamente mantida adormecida ou teste ponta a ponta aprovado; 9 incompletas da Natália atribuídas e entregas conferidas; artefato do Elias validado; origem da telemetria do Rian documentada |
| 3 | Registrar validação humana mínima dos fluxos ativos antes de ampliar ou reativar automações | Gestores humanos das áreas; Cona consolida; Sérgio decide | 2026-09-25 | Ao menos um resultado recente de cada grupo ativo marcado como aceito, corrigido ou sem valor, com fonte/artefato e responsável; trabalho sem validação fica explicitamente deferido |

Nenhuma decisão foi executada por esta revisão. Ficam **deferidos**: novos agentes, reativação dos 13 crons desabilitados, encerramentos, novas integrações e decisões financeiras sem billing confiável.

## 6. Pendências anteriores

| Compromisso anterior | Situação em 21/09 | Próxima ação |
|---|---|---|
| Regularizar mapa de modelos, retries e pins de cron | Parcial: Matias voltou ao primário aprovado; Marketing, Tiago e Elias seguem divergentes; o fallback regrediu em 12/12 | Decisão 1; nenhuma alteração automática |
| Recuperar cruzamento semanal do Tiago | Recuperação técnica observada: execução de 14/09 terminou `ok` | Validar o artefato e a utilidade com o responsável financeiro |
| Esclarecer Elias, Matias e Rian | Elias ainda tem erro interno; Matias teve sinais Octadesk recuperados; Rian segue com lacuna de telemetria | Decisão 2 com evidência por fluxo |
| Definir situação dos perfis de baixo uso | Sem decisão registrada; Bianco, Fabrícia e Tobias seguem candidatos a adormecimento | Preservar e não reativar sem objetivo aprovado |
| Validar valor dos fluxos ativos | Não há validação humana registrada na coleta | Decisão 3 |

Silêncio ou ausência de registro não foi tratado como conclusão.

## 7. Próxima semana e capacidade

O plano está limitado às três decisões acima. A carga fixa observável inclui 35 automações habilitadas, concentradas em Marketing, Matias, Natália, Maria, Elias, Rian, Tiago e default. Não foi disponibilizado calendário executivo; portanto, os prazos são metas operacionais propostas, não reservas confirmadas de agenda. Para proteger capacidade, ficam fora do foco novas automações, reativação de rotinas legadas e análise financeira sem dados externos de cobrança.

## 8. Cobertura e limitações

- **Cobertura temporal:** retrospectiva exata de 2026-09-14 05:00:34 a 2026-09-21 05:00:34 BRT; horizonte de decisões de 21/09 a 27/09.
- **Fontes cobertas:** 12 perfis de IA, modelos/providers/base URLs, fallback/retries, estados de gateway e integrações, 48 crons, 175 sessões, atividade/tokens e sinais recentes de log. O perfil humano/reservado foi excluído.
- **Verificação de modelo:** os 12 arquivos YAML de agentes foram relidos de forma seletiva, sem expor credenciais e sem mutação.
- **Fontes indisponíveis:** calendário executivo, inboxes de tarefas/notas, conteúdo integral de todas as entregas, confirmação de recebimento, indicadores de negócio, correções humanas e billing externo.
- **Custos não mensuráveis:** zero no banco local não confirma custo zero; custo real permanece desconhecido.
- **Valor aguardando validação humana:** toda atividade técnica observada.
- **Qualidade/autonomia:** não mensuráveis de forma confiável apenas por sessões, tokens e status de cron.
- **Logs:** timestamps foram comparados com o estado atual. Warnings recuperados não foram declarados como falha vigente; Fabrícia foi marcada indisponível porque o inventário atual está parado e o teste recente falhou.
- **Sessões:** títulos de smoke test e contadores foram usados apenas para distinguir atividade substantiva; ausência de sessão não prova ausência de execução.
- **Pendências:** a coleta não contém registro formal de aprovação das decisões anteriores; silêncio não foi tratado como conclusão.
- **Mutações:** nenhum modelo, provider, fallback, retry, permissão, gateway, cron, integração ou arquivo de configuração foi alterado. Somente este relatório autorizado foi salvo no Obsidian.
