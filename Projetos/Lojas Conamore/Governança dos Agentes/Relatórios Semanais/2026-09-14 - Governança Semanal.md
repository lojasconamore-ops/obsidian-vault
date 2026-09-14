# Revisão Semanal de Governança — 2026-09-14

**Janela analisada:** 2026-09-07 05:00:29 a 2026-09-14 05:00:29 — America/Sao_Paulo  
**Horizonte de decisões:** 2026-09-14 a 2026-09-20  
**Responsáveis:** Sérgio Ladeira e Cona  
**Fonte técnica:** coleta read-only de configurações, gateways, crons, sessões e logs; arquivos YAML verificados ao vivo  

## Resumo executivo

**Conclusão primeiro:** a frota está majoritariamente operacional, mas a governança continua **amarela**. Há **11/12 gateways em execução**, **36/37 automações habilitadas com último status sem erro** e recuperação técnica das automações de Maria e Natália que estavam degradadas na revisão anterior. Permanecem **3 desvios de modelo/provider** (Marketing, Matias e Tiago), **1 desvio de retries** (Elias), **1 perfil parado** (Fabrícia) e **1 cron habilitado com último status de erro** (Tiago). A instabilidade de rede do Telegram é recorrente nos logs, porém 11 perfis estavam conectados no snapshot atual; portanto, não foi declarada indisponibilidade vigente.

- **Agentes de IA revisados:** 12; o perfil humano/reservado `thiagoribeiro` foi excluído corretamente.
- **Atividade na janela:** 8/12 agentes com sessões; 164 sessões, 1.857 chamadas de API, 2.699 chamadas de ferramenta e 207 mensagens classificadas como `user_messages` pelo runtime.
- **Consumo registrado:** 10.812.989 tokens de entrada e 1.438.437 tokens de saída.
- **Custo:** US$ 0 reportado/estimado no banco local; **custo real desconhecido**, pois a cobrança pode não ser mensurável pelos providers.
- **Gateways:** 11 perfis em `running`; Fabrícia em `stopped` no inventário vivo.
- **Crons:** 37 habilitados e 12 desabilitados; 1 habilitado mantém último status de erro.
- **Padrão de modelos:** 9/12 primários aderentes; fallback `openai-codex:gpt-5.4-mini` correto em 12/12; `api_max_retries=1` em 11/12.
- **Valor confirmado:** nenhuma validação humana ou indicador objetivo constou da coleta. Para toda atividade observada: **valor aguardando validação humana**.
- **Linha de base:** as quatro primeiras revisões já foram concluídas. O semáforo continua qualitativo para comparabilidade, sem ser tratado como nota de desempenho.

### Semáforo executivo

- 🟢 **Verdes:** 11 gateways ativos; Telegram conectado em 11/12 perfis; fallback correto em 12/12; 36/37 crons habilitados sem último erro; Maria e Natália voltaram a apresentar `last_status=ok` nos jobs que estavam degradados.
- 🟡 **Amarelos:** atividade sem validação humana de valor; 4 agentes sem sessões; warnings recorrentes de rede Telegram, embora recuperados no estado atual; possível lacuna de telemetria no Rian; API server do default desconectado desde julho sem requisito vigente confirmado; custo não mensurável.
- 🔴 **Vermelhos:** Marketing, Matias e Tiago fora do mapa primário aprovado; Elias com `api_max_retries=3`; Fabrícia parada; cron semanal do Tiago ainda com último status de erro; avisos de possível envio duplicado no Matias sem ocorrência material confirmada.

## 1. Saúde da frota

| Agente | Gateway / integrações | Modelo/provider ao vivo | Crons | Status |
|---|---|---|---|---|
| Cona / default | Running; Telegram e webhook conectados; API server desconectado | `openai-codex:gpt-5.6-sol` — aderente | 5 habilitados | 🟢 |
| Adrian | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-luna` — aderente | Sem crons | 🟡 uso eventual |
| Bianco | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-luna` — aderente | 2 desabilitados | 🟡 sem uso |
| Elias | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — primário aderente; retries = 3 | 3 habilitados, últimos status ok | 🔴 configuração |
| Fabrícia | Perfil `stopped`; Telegram desconectado | `opencode-go:deepseek-v4-pro` — aderente | Sem crons | 🔴 disponibilidade |
| Maria | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — aderente | 3 habilitados, últimos status ok | 🟢 técnico |
| Flávia / Marketing | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — **fora do padrão** `opencode-go:deepseek-v4-pro` | 12 habilitados; últimos status ok; 1 desabilitado em erro histórico | 🔴 modelo |
| Matias | Running; Telegram/Octadesk conectados | `opencode-go:deepseek-v4-pro` — **fora do padrão** `openai-codex:gpt-5.6-sol` | 5 habilitados, últimos status ok | 🔴 modelo |
| Natália | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-luna` — aderente | 4 habilitados, últimos status ok | 🟡 possível pin de cron |
| Rian | Running; Telegram conectado | `openai-codex:gpt-5.6-luna` — aderente | 4 habilitados, últimos status ok | 🟡 telemetria |
| Tiago | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — **fora do padrão** `openai-codex:gpt-5.6-luna` | 1 habilitado, último status erro | 🔴 modelo/cron |
| Tobias | Running; Telegram/Octadesk conectados | `opencode-go:deepseek-v4-pro` — aderente | 3 desabilitados | 🟡 sem uso no perfil |

**Fallback:** os 12 perfis de IA têm `openai-codex:gpt-5.4-mini` com a base URL aprovada. Nenhuma configuração foi alterada.

## 2. Atividade observada e valor

| Agente | Evidência na janela | Resultado técnico observável | Valor |
|---|---|---|---|
| Cona / default | 32 sessões; 330 chamadas de API | Coordenação, avaliações e extrações registradas | valor aguardando validação humana |
| Adrian | 2 sessões; análise contratual e atestado | Trabalho consultivo registrado | valor aguardando validação humana |
| Bianco | 0 sessões | Sem entrega registrada | valor aguardando validação humana |
| Elias | 20 sessões; 18 `cron_complete` | Agenda, ShinePhone e resumo Granola executados | valor aguardando validação humana |
| Fabrícia | 0 sessões | Sem entrega registrada | valor aguardando validação humana |
| Maria | 1 sessão; crons diários com status ok | Análise de afastamento e rotinas de ponto registradas | valor aguardando validação humana |
| Flávia / Marketing | 57 sessões; 55 `cron_complete` | GA4, Ads, sites e monitoramentos executados | valor aguardando validação humana |
| Matias | 9 sessões; 8 `cron_complete` | Manutenção Hermes, GNRE e DUA-e registradas | valor aguardando validação humana |
| Natália | 42 sessões; 24 `cron_complete` e 16 subagentes concluídos | Relatórios comerciais e conexão Oracle registrados | valor aguardando validação humana |
| Rian | 0 sessões na base do perfil; 4 crons com status ok | Execução indicada por cron, sem sessão atribuída | valor aguardando validação humana |
| Tiago | 1 sessão | Análise de crédito registrada; cron semanal ainda com último erro | valor aguardando validação humana |
| Tobias | 0 sessões; crons próprios desabilitados | Rotina homônima roda no default, não atribuída ao perfil Tobias | valor aguardando validação humana |

Atividade técnica, volume de tokens, `cron_complete` e `last_status=ok` não comprovam utilidade, qualidade, economia, impacto financeiro ou recebimento correto.

## 3. Qualidade, confiabilidade e autonomia

| Agente/fluxo | Evidência | Avaliação | Recomendação |
|---|---|---|---|
| Maria — três automações | Nesta janela, os três jobs têm último status `ok` | 🟢 recuperação técnica observada; entrega humana não validada | Confirmar recebimento e utilidade com RH antes de encerrar a pendência |
| Natália — relatórios | Quatro jobs ativos com último status `ok` | 🟢 falha anterior não está vigente; valor pendente | Confirmar artefato e aceitação do gestor comercial |
| Tiago — cruzamento semanal | Última execução em 07/09 terminou em erro de `systemd-run --user --scope`; próxima prevista para 14/09 08:05 | 🔴 falha ainda não substituída por execução bem-sucedida | Matias diagnosticar e validar um ciclo completo, sem alterar infraestrutura sem aprovação |
| Elias — resumo Granola | Último cron consta `ok`, mas há um erro interno de ferramenta em 13/09 20:00 | 🟡 possível sucesso parcial | Conferir o artefato/entrega do ciclo e se o erro foi recuperado |
| Matias — Telegram | Logs em 13/09 22:34 e 22:46 alertam sobre possível envio duplicado | 🟡 risco técnico sem duplicidade material confirmada | Verificar IDs/mensagens do canal antes de concluir incidente |
| Rede Telegram | Warnings recentes em vários perfis; estados atuais conectados | 🟡 intermitência recuperada, não outage vigente | Observar recorrência e falhas reais de entrega |
| Rian — telemetria | Crons `ok`, porém 0 sessões/0 chamadas na base do perfil | 🟡 atribuição inconsistente | Validar onde os workers registram sessões e artefatos |
| Modelos primários | Marketing, Matias e Tiago divergem do mapa aprovado | 🔴 desvio de governança | Sérgio decidir; Matias só ajustar se houver autorização explícita |
| Política de retries do Elias | `api_max_retries=3`, padrão = 1 | 🔴 desvio persistente | Normalizar apenas após aprovação e smoke test |
| Custo | US$ 0 local para toda a frota | Desconhecido | Não inferir gratuidade; obter billing externo se a decisão depender de custo |

Não houve evidência suficiente para pontuar qualidade ou autonomia por agente. Quatro sessões ficaram classificadas como `cron_incomplete_no_output`; isso é sinal de revisão, não prova automática de falha material.

## 4. Riscos e permissões

| Item | Gravidade | Escopo | Contenção recomendada |
|---|---|---|---|
| Drift de modelo/provider | Alta | Marketing, Matias e Tiago | Congelar mudanças e submeter correção/documentação à decisão do Sérgio |
| Retry fora do padrão | Média | Elias | Decisão explícita e teste antes de qualquer ajuste |
| Cron semanal em erro | Alta | Tiago | Diagnóstico read-only e teste controlado após autorização aplicável |
| Possível duplicidade de envio | Média | Matias/Telegram | Verificar evidência do destino; não assumir duplicidade pelo warning |
| Perfil parado | Média | Fabrícia | Manter adormecido até existir objetivo, dono e critério de sucesso |
| Custo não observável | Média | Frota inteira | Evitar decisão financeira baseada no zero local |
| Oracle/DEBX | Controlado nesta revisão | Sessões comerciais/financeiras | Não reinterpretar PED como venda física; validar sessão, schema e coluna nas consultas operacionais |

Nenhuma violação de credencial, permissão ou acesso sensível foi identificada na coleta fornecida. Isso não equivale a auditoria completa de segurança.

## 5. Portfólio

Classificação provisória baseada em uso, saúde e evidência técnica. Sem validação humana de valor, `Manter` não é atribuído como conclusão definitiva nesta semana.

| Agente/automação | Classificação | Justificativa |
|---|---|---|
| Cona / default | Observar | Uso alto e operação técnica estável; valor aguardando validação humana |
| Adrian | Observar | Uso consultivo recente; impacto e aceitação aguardam validação humana |
| Bianco | Adormecer | Sem atividade e duas automações desabilitadas; preservar perfil sob demanda |
| Elias | Melhorar | Uso recorrente, mas retries fora do padrão e erro interno a esclarecer |
| Fabrícia | Adormecer | Perfil parado e sem atividade; preservar sem reativação automática |
| Maria | Observar | Recuperação técnica dos crons; valor aguardando validação humana |
| Flávia / Marketing | Melhorar | Alta atividade e crons estáveis, mas modelo/provider diverge do aprovado |
| Matias | Melhorar | Automações ativas, porém modelo/provider diverge e há warnings de possível duplicidade |
| Natália | Melhorar | Alta atividade e crons recuperados; execuções recentes de cron em modelo diferente do primário requerem decisão/documentação |
| Rian | Observar | Crons estáveis, mas há lacuna entre status dos jobs e telemetria de sessões |
| Tiago | Melhorar | Modelo primário divergente e cron semanal ainda com último erro |
| Tobias | Adormecer | Sem atividade no perfil e três crons desabilitados; preservar para demanda logística |
| Crons desabilitados legados | Adormecer | 12 jobs desabilitados; não reativar sem propósito e responsável confirmados |
| Encerramentos | Observar | Nenhum encerramento recomendado nesta semana; qualquer encerramento exige Sérgio |

## 6. Decisões da semana

| # | Decisão proposta | Responsável sugerido | Prazo | Critério de conclusão |
|---:|---|---|---|---|
| 1 | Aprovar ou rejeitar a regularização dos modelos de Marketing, Matias e Tiago, do retry do Elias e da exceção de modelo dos crons da Natália | Sérgio decide; Matias executa somente se aprovado | 2026-09-15 | Decisão registrada; se aprovada, arquivos/jobs lidos de volta aderentes ou exceções documentadas e smoke test bem-sucedido |
| 2 | Recuperar e validar o cruzamento semanal do Tiago e esclarecer os sinais de sucesso parcial/telemetria em Elias, Matias e Rian | Matias, com Tiago/Elias/Rian validando os respectivos resultados | 2026-09-17 | Tiago com um ciclo `last_status=ok` e entrega confirmada; Elias com artefato conferido; Matias sem duplicidade confirmada ou com incidente registrado; Rian com origem da telemetria documentada |
| 3 | Registrar validação humana mínima de valor dos fluxos ativos e decidir o estado dos perfis ociosos | Gestores humanos das áreas; Cona consolida; Sérgio decide | 2026-09-18 | Ao menos um resultado recente por fluxo ativo marcado como aceito, corrigido ou sem valor; Bianco, Fabrícia e Tobias com decisão explícita de permanecer adormecidos ou reativar com objetivo |

Nenhuma decisão foi executada por esta revisão. Ficam **deferidos**: encerramento de perfis, reativação de crons legados, expansão de integrações e mudanças de infraestrutura sem relação comprovada com falha atual.

## 7. Pendências anteriores

| Compromisso anterior | Situação em 14/09 | Próxima ação |
|---|---|---|
| Regularizar mapa de modelos, retry do Elias e pins da Natália | Não concluído: os desvios permanecem ao vivo | Decisão explícita do Sérgio; nenhuma alteração automática |
| Recuperar automações de Maria e Natália | Recuperação técnica observada: jobs atuais com `last_status=ok` | Validar recebimento e utilidade com responsáveis humanos |
| Definir situação da Fabrícia e demais perfis sem uso | Sem decisão registrada; Fabrícia segue parada, Bianco/Tobias sem sessões | Manter como adormecimento provisório e decidir com critério de propósito |
| Validar valor dos agentes ativos | Não há registro de validação humana na coleta | Executar amostragem mínima até 18/09 |

Silêncio ou ausência de registro não foi tratado como conclusão.

## 8. Próxima semana e capacidade

O plano está limitado às três decisões acima. A carga fixa observável inclui 37 automações habilitadas, com concentração diária em Marketing, Matias, Natália, Maria, Elias e no default. Não foi disponibilizado calendário executivo; os prazos são metas operacionais propostas, não reservas confirmadas de agenda. Para preservar capacidade, ficam fora do foco semanal novas automações, reativação de rotinas legadas e avaliação financeira sem dados de billing.

## 9. Cobertura e limitações

- **Cobertura temporal:** retrospectiva exata de 2026-09-07 05:00:29 a 2026-09-14 05:00:29 BRT; horizonte de decisões de 14/09 a 20/09.
- **Fontes cobertas:** 12 perfis de IA, configurações primárias, base URLs, fallback/retries, gateways, integrações declaradas, 49 crons, sessões, contadores de atividade/tokens e sinais recentes de log. O perfil humano/reservado foi excluído.
- **Verificação adicional:** os 13 arquivos YAML existentes foram lidos ao vivo; `thiagoribeiro` foi classificado separadamente como humano e não entrou no portfólio de IA.
- **Fontes indisponíveis:** calendário executivo, inboxes de tarefas/notas, conteúdo integral de todas as entregas, confirmação de recebimento, indicadores de negócio, correções humanas e billing externo.
- **Custos não mensuráveis:** zero no banco local não confirma custo zero; custo real permanece desconhecido.
- **Valor aguardando validação humana:** toda atividade técnica observada.
- **Qualidade/autonomia:** não mensuráveis de forma confiável apenas por sessões, tokens e status de cron.
- **Logs:** timestamps foram comparados ao estado atual; warnings recuperados não foram declarados como falha vigente.
- **Telemetria:** status de cron e sessões podem divergir, como observado no Rian; ausência de sessão não prova ausência de execução.
- **Oracle/DEBX:** nenhuma consulta ao banco foi feita nesta revisão. PED não foi tratado como venda física; atividade de sessões foi usada apenas como evidência técnica.
- **Mutações:** nenhuma configuração, modelo, provider, permissão, gateway, cron ou integração foi alterada; somente este relatório autorizado foi salvo no Obsidian.
