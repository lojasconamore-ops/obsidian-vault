# Revisão Semanal de Governança — 2026-09-07

**Janela analisada:** 2026-08-31 05:00:32 a 2026-09-07 05:00:32 — America/Sao_Paulo  
**Responsáveis:** Sérgio Ladeira e Cona  
**Fonte técnica:** coleta read-only de configurações, gateways, crons, sessões e logs; validação ao vivo dos arquivos de configuração e do serviço principal  

## Resumo executivo

**Conclusão primeiro:** a frota está operacional, mas não está pronta para ser considerada integralmente aderente ou com valor comprovado. Há **3 desvios de modelo/provider**, **1 desvio de política de retries**, **4 automações habilitadas com último status de erro** e **1 perfil parado**. O serviço principal estava ativo na verificação, e os sinais recentes de instabilidade do Telegram não configuravam indisponibilidade vigente.

- **Agentes de IA revisados:** 12; perfil humano/reservado corretamente excluído.
- **Atividade na janela:** 7/12 agentes, 144 sessões, 2.153 chamadas de API, 2.856 chamadas de ferramenta e 260 mensagens classificadas como `user_messages` pelo runtime.
- **Consumo registrado:** 10.627.777 tokens de entrada e 1.834.565 tokens de saída.
- **Custo:** US$ 0 reportado/estimado pelo coletor; **custo real desconhecido**, pois os providers podem não expor cobrança mensurável.
- **Gateways:** 11 perfis em `running`; Fabrícia em `stopped` no inventário vivo.
- **Crons:** 37 habilitados e 13 desabilitados; 4 habilitados terminaram a última execução com erro.
- **Padrão de modelos:** 9/12 primários aderentes; fallback `openai-codex:gpt-5.4-mini` presente em 12/12; `api_max_retries=1` em 11/12.
- **Valor confirmado:** nenhuma validação humana ou indicador objetivo foi registrado na coleta. Para toda atividade observada: **valor aguardando validação humana**.
- **Linha de base:** os quatro relatórios anteriores completaram a fase inicial. Esta é a primeira revisão após essa linha de base; o semáforo permanece qualitativo, não é nota de desempenho.

### Semáforo executivo

- 🟢 **Verdes:** serviço principal ativo; 11 gateways em execução; 11 conexões Telegram vigentes; fallback correto em 12/12; 33/37 automações habilitadas sem último erro.
- 🟡 **Amarelos:** valor ainda sem validação humana; 5 agentes sem sessões; sinais recentes e recuperados de rede Telegram; API server do perfil default desconectado desde julho, sem requisito ativo confirmado; modelos de crons nem sempre seguem o modelo primário do perfil.
- 🔴 **Vermelhos:** 3 perfis fora do padrão primário aprovado; Elias com retries fora do padrão; 3 crons da Maria sem iniciar por indisponibilidade de `systemd-run --user --scope`; 1 cron da Natália interrompido por shutdown; Fabrícia parada.

## 1. Saúde da frota

| Agente | Gateway / integração | Modelo/provider ao vivo | Crons | Semáforo |
|---|---|---|---|---|
| Cona / default | Gateway ativo; Telegram e webhook conectados | `openai-codex:gpt-5.6-sol` — aderente | 5 habilitados | 🟢 |
| Adrian | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-luna` — aderente | Sem crons | 🟡 baixo uso |
| Bianco | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-luna` — aderente | 2 desabilitados | 🟡 baixo uso |
| Elias | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — primário aderente; retries = 3 | 3 habilitados, últimos status ok | 🔴 configuração |
| Fabrícia | `stopped`; Telegram desconectado | `opencode-go:deepseek-v4-pro` — aderente | Sem crons | 🔴 disponibilidade |
| Maria | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — aderente | 3 habilitados, 3 com último status de erro | 🔴 automações |
| Flávia / Marketing | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — **fora do padrão** `opencode-go:deepseek-v4-pro` | 12 habilitados; últimos status dos habilitados ok | 🔴 modelo |
| Matias | Running; Telegram/Octadesk conectados | `opencode-go:deepseek-v4-pro` — **fora do padrão** `openai-codex:gpt-5.6-sol` | 5 habilitados, últimos status ok | 🔴 modelo |
| Natália | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-luna` — aderente | 4 habilitados; 1 com último status de erro; todos pinados em `deepseek-v4-pro` | 🔴 automação/configuração |
| Rian | Running; Telegram conectado | `openai-codex:gpt-5.6-luna` — aderente | 4 habilitados, últimos status ok | 🟢 técnico |
| Tiago | Running; Telegram/Octadesk conectados | `openai-codex:gpt-5.6-sol` — **fora do padrão** `openai-codex:gpt-5.6-luna` | 1 habilitado, último status ok | 🔴 modelo |
| Tobias | Running; Telegram/Octadesk conectados | `opencode-go:deepseek-v4-pro` — aderente | 3 desabilitados | 🟡 baixo uso |

**Fallback:** todos os 12 perfis têm `openai-codex:gpt-5.4-mini` com a base URL aprovada. Nenhum arquivo de configuração foi alterado.

## 2. Atividade observada e valor

| Agente | Evidência na janela | Resultado observável | Valor |
|---|---|---|---|
| Cona / default | 32 sessões; coordenação, relatórios diários e exportação Granola | Execuções técnicas registradas | valor aguardando validação humana |
| Adrian | 0 sessões | Sem entrega registrada | valor aguardando validação humana |
| Bianco | 0 sessões | Sem entrega registrada | valor aguardando validação humana |
| Elias | 21 sessões; agenda, ShinePhone e resumo Granola | 16 crons concluídos/sessões finalizadas por cron | valor aguardando validação humana |
| Fabrícia | 0 sessões | Sem entrega registrada | valor aguardando validação humana |
| Maria | 0 sessões; 3 tentativas de cron falharam antes do worker | Nenhuma entrega confirmada | valor aguardando validação humana |
| Flávia / Marketing | 58 sessões; GA4, Ads, sites e monitoramentos | 52 sessões encerradas por cron | valor aguardando validação humana |
| Matias | 12 sessões; atualização, sync, limpeza, GNRE e DUA-e | 6 sessões encerradas por cron; jobs atuais com último status ok | valor aguardando validação humana |
| Natália | 19 sessões; DEBX e relatórios comerciais | 18 sessões encerradas por cron; uma automação interrompida | valor aguardando validação humana |
| Rian | 1 sessão; análises de lojas com crons ativos | Jobs de ACL/GCL com último status ok | valor aguardando validação humana |
| Tiago | 1 sessão; cruzamento semanal Oracle × lista negra | Cron semanal concluído | valor aguardando validação humana |
| Tobias | 0 sessões no perfil; rotina diária homônima executada pelo default | Não há entrega recente atribuível ao perfil Tobias | valor aguardando validação humana |

Atividade técnica, volume de tokens e encerramento `cron_complete` não provam utilidade, qualidade, economia nem impacto financeiro.

## 3. Qualidade, confiabilidade e riscos

| Item | Evidência | Avaliação | Contenção recomendada |
|---|---|---|---|
| Modelos primários fora do padrão | Marketing, Matias e Tiago divergem do mapa aprovado | Alto — governança/configuração | Sérgio decidir; Matias só ajustar após autorização explícita e testar cada perfil |
| Política de fallback do Elias | Primário e fallback corretos, mas `api_max_retries=3` | Médio — failover mais lento que o padrão | Normalizar para 1 apenas após aprovação e smoke test |
| Crons da Maria | 3 jobs habilitados em erro em 06/09: worker restart-safe não criou escopo de usuário | Alto — ausência de entrega | Matias diagnosticar `systemd-run --user --scope`, testar e ler de volta o status |
| Cron comercial da Natália | Relatório individual terminou em erro por shutdown em 06/09 | Médio — falha recuperável | Reexecutar/testar no próximo ciclo e confirmar artefato/entrega |
| Pins dos crons da Natália | 4 jobs usam `deepseek-v4-pro`, embora o perfil padrão seja Luna | Médio — possível exceção não documentada | Sérgio confirmar exceção ou autorizar padronização |
| Telegram | Warnings entre 06/09 e 07/09; default reconectou às 22:13; estados atuais conectados | Médio — intermitência, não falha vigente | Observar recorrência e taxa de entregas; não reiniciar sem incidente atual |
| Fabrícia | Perfil parado, conexão antiga desconectada e sem atividade | Médio — capacidade indisponível/ociosa | Preservar adormecida ou reativar somente com objetivo e responsável claros |
| API server default | Estado `disconnected` desde 28/07; gateway principal segue ativo | Baixo/ambíguo | Confirmar se a API é requisito vigente antes de tratar como incidente |
| Custo | Coletor reporta zero para todos | Desconhecido | Não inferir gratuidade; obter fonte de billing se decisão depender de custo |

### Qualidade e autonomia

Não há amostra de aceitação humana, correções solicitadas, entregas lidas de volta ou indicadores de negócio suficientes para pontuar qualidade e autonomia por agente. A confiabilidade técnica é parcialmente mensurável pelos estados de gateway/cron; o valor permanece pendente.

## 4. Portfólio

Classificação provisória baseada em uso, saúde técnica e evidência disponível. Como não há valor humano confirmado, `Manter` não é atribuído como conclusão definitiva nesta semana.

| Agente/automação | Classificação | Justificativa |
|---|---|---|
| Cona / default | Observar | Uso alto e saúde técnica verde; valor aguardando validação humana |
| Adrian | Adormecer | Sem atividade, sem crons e sem resultado registrado; preservar perfil sob demanda |
| Bianco | Adormecer | Sem atividade e automações desabilitadas; preservar documentação e perfil |
| Elias | Melhorar | Uso recorrente, mas retries permanecem fora do padrão |
| Fabrícia | Adormecer | Perfil parado e sem atividade; nenhuma recomendação de encerramento |
| Maria | Melhorar | Três automações habilitadas não entregaram por falha de dispatch |
| Flávia / Marketing | Melhorar | Alta atividade e jobs em execução, mas modelo primário diverge do aprovado |
| Matias | Melhorar | Automações tecnicamente ativas, mas modelo primário diverge do aprovado |
| Natália | Melhorar | Uma falha de shutdown e pins de cron divergentes do modelo aprovado do perfil |
| Rian | Observar | Automações tecnicamente estáveis; valor aguardando validação humana |
| Tiago | Melhorar | Modelo primário diverge do padrão aprovado, apesar do cron semanal ok |
| Tobias | Adormecer | Sem atividade no perfil e três crons desabilitados; preservar para demanda logística |
| Crons desabilitados legados | Adormecer | 13 jobs desabilitados; manter sem execução até revisão de propósito |
| Encerramentos | Observar | Nenhum encerramento recomendado sem revisão de duplicidade, propósito e autorização do Sérgio |

## 5. Pendências anteriores

| Compromisso anterior | Situação em 07/09 | Próxima ação |
|---|---|---|
| Recuperar dois monitoramentos de marketing | Os jobs estão habilitados e com último status ok, mas agora executam com modelo diferente do padrão aprovado do perfil | Validar configuração pretendida e registrar a decisão |
| Normalizar `api_max_retries` do Elias para 1 | Não concluído; configuração ao vivo permanece em 3 | Manter pendente de autorização e execução por Matias |
| Definir situação da Fabrícia | Não há decisão registrada na coleta; perfil segue parado | Sérgio confirmar adormecimento ou objetivo de reativação |

Silêncio ou ausência de registro não foi tratado como conclusão.

## 6. Decisões da semana

| # | Decisão proposta | Responsável sugerido | Prazo | Critério de conclusão |
|---:|---|---|---|---|
| 1 | Sérgio aprovar ou rejeitar a correção do mapa de modelos de Marketing, Matias e Tiago, do retry do Elias e das exceções de modelo nos crons da Natália | Sérgio decide; Matias executa se aprovado | 2026-09-08 | Decisão registrada; se aprovada, configs e jobs lidos de volta aderentes ao mapa/exceções documentadas e smoke test bem-sucedido |
| 2 | Recuperar as 3 automações da Maria e validar o cron interrompido da Natália | Matias + Maria + Natália | 2026-09-09 | Cada job executar uma vez com `last_status=ok`, artefato/entrega confirmado e registro lido de volta |
| 3 | Fechar a validação humana de valor e decidir o estado dos perfis sem uso | Gestores humanos das áreas; consolidação pelo Cona; decisão final do Sérgio | 2026-09-11 | Ao menos um resultado por agente ativo classificado como aceito, corrigido ou sem valor; Adrian, Bianco, Fabrícia e Tobias com decisão explícita de manter sob demanda/adormecer/reativar |

Nenhuma decisão foi executada por esta revisão.

## 7. Próxima semana e capacidade

Priorizar somente as três decisões acima. Ficam **deferidos**: encerramento de perfis, reativação de crons legados, mudança de infraestrutura não ligada às falhas atuais e qualquer expansão de integrações. Não há calendário executivo disponível nesta coleta; portanto, prazos são metas operacionais propostas, não reservas confirmadas de agenda.

## 8. Cobertura e limitações

- **Cobertura temporal:** retrospectiva completa de 2026-08-31 05:00:32 a 2026-09-07 05:00:32 BRT; horizonte proposto até 2026-09-11, sem leitura de calendário.
- **Fontes cobertas:** 12 configurações de agentes, fallback/retries, inventário de gateways, 50 crons, sessões, contadores de tokens e sinais recentes de log. O perfil humano/reservado foi excluído.
- **Verificação adicional:** arquivos YAML lidos ao vivo; serviço `hermes-gateway.service` confirmado `active (running)` em 07/09 às 05:01 BRT. O status completo via comando com `sudo` não pôde ser obtido sem terminal interativo, mas o `systemctl` do sistema e o snapshot do coletor forneceram o estado atual necessário.
- **Fontes indisponíveis:** calendário/capacidade, inboxes, conteúdo integral das entregas, confirmação de recebimento, indicadores de negócio e billing externo.
- **Custos não mensuráveis:** zero no banco local não confirma custo zero.
- **Valor aguardando validação humana:** toda atividade técnica observada.
- **Limite de atribuição:** uma rotina executada no perfil default com nome de outro agente não foi automaticamente atribuída como atividade daquele perfil.
- **Logs:** eventos com timestamp foram comparados ao estado atual; warnings recuperados não foram declarados como falha vigente.
- **Oracle/DEBX:** esta revisão não consultou o banco e não reinterpretou PED como venda física; as sessões de relatórios foram tratadas apenas como evidência técnica de execução.
- **Mutação:** nenhuma configuração, gateway, cron, integração, permissão ou modelo foi alterado.
