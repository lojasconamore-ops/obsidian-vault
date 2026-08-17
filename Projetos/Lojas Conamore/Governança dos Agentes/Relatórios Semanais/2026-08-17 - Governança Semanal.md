# Revisão Semanal de Governança — 2026-08-17

**Janela analisada:** 2026-08-10 05:00:20 a 2026-08-17 05:00:20 — America/Sao_Paulo  
**Responsáveis:** Sérgio Ladeira e Cona  
**Fonte técnica:** coleta read-only de configurações, gateways, crons, sessões e logs; verificação ao vivo de `hermes profile list`; documentos canônicos de governança  
**Fase:** linha de base em formação — semáforo qualitativo, sem nota numérica  

## Resumo executivo

**Conclusão primeiro:** a frota está operacional, mas ainda não há base para afirmar valor empresarial consolidado. Dos 12 agentes de IA, 11 gateways estão em execução e 1 está parado (Fabrícia). Nove agentes tiveram sessões na janela e três não tiveram atividade direta registrada. Os 12 perfis estão alinhados ao modelo/provider primário aprovado e têm o fallback geral aprovado; há, porém, um desvio em `api_max_retries` no Elias e quatro crons da Natália executando com override explícito diferente do modelo primário aprovado do perfil. Nenhuma configuração foi alterada nesta revisão.

- **Atividade observada:** 168 sessões, 283 mensagens de usuário, 2.390 chamadas de API e 3.106 chamadas de ferramentas.
- **Consumo técnico:** 10.901.848 tokens de entrada e 1.582.627 de saída. O custo monetário está **desconhecido**: o valor coletado foi US$ 0,00, mas os providers podem não fornecer cobrança mensurável.
- **Automações:** 34 crons habilitados em 8 perfis. A maioria dos últimos estados observados estava `ok`; o cron semanal de governança teve falha de conexão em 10/08 e está executando novamente nesta data.
- **Valor:** não houve validação humana consolidada anexada à coleta. Para as entregas e rotinas citadas abaixo, **valor aguardando validação humana**.
- **Decisões propostas:** (1) aprovar saneamento das divergências técnicas e do TTS; (2) decidir se o override de modelo dos crons da Natália é exceção aprovada; (3) validar valor e decidir o estado de perfis sem uso direto.

### Semáforo da semana

#### 🟢 Verdes

- 12/12 perfis com modelo/provider primário conforme o padrão aprovado.
- 12/12 perfis com fallback `openai-codex / gpt-5.4-mini` configurado.
- 11/12 gateways em execução na verificação atual; Telegram conectado nos perfis operacionais informados.
- Crons recorrentes recentes de Marketing, Elias, Maria, Matias, Natália, Rian, Tiago e Tobias encerraram majoritariamente com estado `ok`.
- Reconexões temporárias de Telegram em Cona, Maria e Natália se recuperaram; não foram classificadas como falha atual.

#### 🟡 Amarelos

- **Valor e qualidade:** alto volume técnico, mas sem validação humana consolidada; atividade não foi convertida em alegação de impacto.
- **Elias:** `agent.api_max_retries: 3`, enquanto o padrão da frota com fallback é `1`.
- **Natália:** perfil primário aprovado em `gpt-5.6-luna/openai-codex`, mas os quatro crons habilitados estão explicitamente fixados em `deepseek-v4-pro/opencode-go`. Os jobs estão funcionando, porém a exceção não está registrada nesta revisão como aprovada por Sérgio.
- **TTS/voz:** falhas recentes por quota excedida, chave inválida ou chave ausente em Elias, Matias, Rian e Tiago. O texto e os gateways principais continuaram operacionais, portanto o problema é uma degradação do canal de voz, não indisponibilidade geral.
- **Governança semanal:** a execução anterior, em 10/08, falhou por erro de conexão. A execução atual produziu este artefato; a entrega final ainda depende do encerramento do cron.
- **Atribuição:** o cron `tobias-daily` executa no scheduler do Cona com `profile: tobias`; a atividade aparece no banco do perfil default, enquanto Tobias tem zero sessões diretas. Isso dificulta medir uso por agente.
- **Baixo uso:** Adrian teve 1 sessão; Bianco, Fabrícia e Tobias não tiveram sessões diretas no banco de seus perfis.

#### 🔴 Vermelhos

- **Fabrícia:** gateway atualmente `stopped`, Telegram historicamente desconectado e nenhuma sessão na janela. Não há evidência de incidente crítico ou violação, mas o agente não está disponível no estado atual.
- Nenhuma exposição de credencial, alteração não autorizada, erro financeiro material ou violação de permissão foi confirmada na coleta.

## 1. Saúde da frota

| Agente | Gateway atual | Modelo/provider primário | Fallback | Crons habilitados | Semáforo |
|---|---|---|---|---:|---|
| Cona / default | running | gpt-5.6-sol / openai-codex | conforme | 6 | 🟡 |
| Adrian | running | gpt-5.6-luna / openai-codex | conforme | 0 | 🟡 |
| Bianco | running | gpt-5.6-luna / openai-codex | conforme | 0 | 🟡 |
| Elias | running | gpt-5.6-sol / openai-codex | conforme | 3 | 🟡 |
| Fabrícia | stopped | deepseek-v4-pro / opencode-go | conforme | 0 | 🔴 |
| Maria | running | gpt-5.6-sol / openai-codex | conforme | 3 | 🟢 técnico / 🟡 valor |
| Flávia / marketing | running | deepseek-v4-pro / opencode-go | conforme | 9 | 🟢 técnico / 🟡 valor |
| Matias | running | gpt-5.6-sol / openai-codex | conforme | 4 | 🟡 |
| Natália | running | gpt-5.6-luna / openai-codex | conforme | 4 | 🟡 |
| Rian | running | gpt-5.6-luna / openai-codex | conforme | 4 | 🟡 |
| Tiago | running | gpt-5.6-luna / openai-codex | conforme | 1 | 🟡 |
| Tobias | running | deepseek-v4-pro / opencode-go | conforme | 0 no perfil; rotina delegada no default | 🟡 |

**Conflito resolvido pela fonte ao vivo:** a coleta continha um PID antigo associado a Fabrícia, mas `hermes profile list` consultado durante a revisão informou `stopped`; o estado atual ao vivo prevaleceu.

## 2. Atividade observada e valor

| Agente | Atividade na janela | Evidência operacional observada | Valor |
|---|---:|---|---|
| Cona | 32 sessões | rotinas diárias, governança e consolidação Granola | valor aguardando validação humana |
| Adrian | 1 sessão | apoio jurídico sobre penhora de aluguel | valor aguardando validação humana |
| Bianco | 0 sessões | dois crons antigos desabilitados | valor aguardando validação humana |
| Elias | 25 sessões | agenda, Granola e ShinePhone | valor aguardando validação humana |
| Fabrícia | 0 sessões | sem atividade; gateway parado | valor aguardando validação humana |
| Maria | 3 sessões | integração Secullum; crons de ponto e atrasos com último estado `ok` | valor aguardando validação humana |
| Flávia / marketing | 39 sessões | GA4, Google Ads, saúde de sites e monitoramentos | valor aguardando validação humana |
| Matias | 15 sessões | manutenção Hermes, sync Obsidian, GNRE e suporte técnico | valor aguardando validação humana |
| Natália | 44 sessões | relatórios comerciais, DEBX, Casa e Hotelaria | valor aguardando validação humana |
| Rian | 4 sessões | análises de lojas físicas e investigação de cron | valor aguardando validação humana |
| Tiago | 5 sessões | análises de crédito, Pagar.me e rotina financeira | valor aguardando validação humana |
| Tobias | 0 sessões diretas | `tobias-daily` executado 7 vezes no default, último estado `ok` | valor aguardando validação humana |

Não foram encontrados, na coleta fornecida, aceite humano explícito, indicador de economia, receita incremental, horas poupadas ou impacto financeiro que permita promover atividade a valor confirmado.

## 3. Qualidade, confiabilidade e riscos

| Agente/fluxo | Evidência | Situação | Classificação qualitativa |
|---|---|---|---|
| Modelos primários da frota | inventário ao vivo dos 12 perfis | todos conforme o padrão aprovado | 🟢 |
| Fallback geral | 12 perfis com gpt-5.4-mini/openai-codex | conforme | 🟢 |
| Elias — retries | configuração ao vivo com valor 3 | divergente do padrão 1 | 🟡 |
| Natália — quatro crons | jobs fixados em deepseek-v4-pro/opencode-go | diferente do primário aprovado do perfil; execução `ok`, aprovação da exceção não comprovada | 🟡 |
| Fabrícia | `hermes profile list`: stopped | indisponível e sem uso na janela | 🔴 |
| Telegram | timeouts/Bad Gateway recentes, seguidos de polling reiniciado e estado conectado | falha transitória recuperada | 🟡 observar |
| TTS/voz | 401 por quota, chave inválida ou ausente | voz degradada em quatro perfis; texto não demonstrou indisponibilidade | 🟡 |
| Governança semanal | erro de conexão em 10/08 | falha anterior; execução atual gerou relatório | 🟡 |
| Mensagem única ao Thiago | `Chat not found` em 10/08; job já desabilitado | falha histórica de entrega, sem recorrência ativa | 🟡 histórico |
| Segurança/permissões | nenhuma violação confirmada | sem alerta crítico comprovado | 🟢 |

### Riscos prioritários

1. **Governança de modelos:** overrides de cron podem fazer a execução real divergir do padrão do perfil sem visibilidade executiva.
2. **Observabilidade de autoria:** rotinas delegadas pelo default podem inflar o uso do Cona e zerar artificialmente o agente responsável.
3. **Canal de voz:** falhas recorrentes de TTS geram ruído operacional e podem dar aparência de erro geral quando apenas a resposta em áudio falhou.
4. **Validação de valor:** sem aceite humano por entrega, não é possível distinguir automação útil de produção de relatórios não utilizados.
5. **Custo:** tokens são mensuráveis, mas custo financeiro não; US$ 0,00 não foi tratado como gratuidade.

## 4. Portfólio

A classificação abaixo é provisória durante a formação da linha de base. “Manter” não foi usado para agentes sem valor humano confirmado, mesmo quando tecnicamente ativos.

| Agente/automação | Classificação | Justificativa |
|---|---|---|
| Cona / default | **Melhorar** | alto uso técnico; cron de governança falhou na semana anterior e há mistura de rotinas delegadas; valor aguardando validação humana |
| Adrian | **Observar** | uso real, porém apenas 1 sessão e sem validação de resultado |
| Bianco | **Adormecer** | zero sessões e nenhum cron habilitado; preservar perfil e documentação até demanda confirmada |
| Elias | **Melhorar** | rotinas ativas, mas retries fora do padrão e TTS degradado |
| Fabrícia | **Adormecer** | gateway parado, zero sessões e nenhum cron; reativação somente com processo e dono humano definidos |
| Maria | **Observar** | integração e crons ativos com estados recentes `ok`; valor ainda não validado |
| Flávia / marketing | **Observar** | maior cadência de automações, sem evidência de uso das recomendações ou resultado confirmado |
| Matias | **Melhorar** | operação técnica ativa; TTS com chave inválida e necessidade de consolidar confiabilidade/observabilidade |
| Natália | **Melhorar** | alta atividade e crons `ok`, mas execução de crons diverge do modelo primário aprovado do perfil |
| Rian | **Melhorar** | análises recorrentes `ok`; TTS sem configuração e valor ainda sem aceite humano |
| Tiago | **Melhorar** | atividade financeira e cron semanal; TTS sem quota e valor ainda sem aceite humano |
| Tobias | **Observar** | rotina diária funciona por delegação no default, mas o perfil não registra sessões diretas; valor não validado |
| Crons recorrentes ativos | **Observar** | execução técnica majoritariamente saudável; falta aceite humano por fluxo |
| Governança semanal | **Melhorar** | falha de conexão na execução anterior; artefato atual gerado |
| TTS/voz da frota | **Melhorar** | falhas recorrentes de quota/autenticação/configuração em quatro perfis |
| Crons Pagar.me antigos e relatórios antigos de Bianco/Tobias | **Adormecer** | já desabilitados; manter preservados até decisão explícita sobre retomada ou encerramento |
| Jobs one-shot concluídos | **Encerrar** como registro, sem exclusão automática | já executados e desabilitados; eventual remoção exige autorização de Sérgio |

## 5. Decisões da semana

| # | Decisão proposta | Responsável sugerido | Prazo | Critério de conclusão |
|---:|---|---|---|---|
| 1 | Autorizar um plano de saneamento técnico para Elias/TTS e confiabilidade do cron semanal, sem mudança de modelo primário fora de aprovação | Sérgio aprova; Matias executa | 2026-08-24 06:00 BRT | `api_max_retries` do Elias decidido e verificado; política de TTS definida (corrigida ou voz desativada conscientemente); próxima governança encerra sem erro e gera relatório |
| 2 | Decidir se os quatro crons da Natália podem permanecer em deepseek-v4-pro/opencode-go como exceção ou devem seguir o primário gpt-5.6-luna/openai-codex | Sérgio, com parecer de Matias e Natália | 2026-08-21 | decisão registrada; inventário de jobs identifica claramente a regra aprovada; qualquer alteração, se aprovada, é verificada ao vivo por Matias |
| 3 | Validar valor de uma amostra das rotinas mais frequentes e confirmar o estado de Bianco/Fabrícia | Sérgio + gestores humanos das áreas | 2026-08-21 | pelo menos uma entrega de Marketing, Natália, Elias, Maria e Tobias marcada como aceita/ajustar/dispensável; Bianco e Fabrícia confirmados como adormecidos ou com caso de uso, dono e próximo passo |

## 6. Pendências e próximos acompanhamentos

- **Governança semanal:** revisar o resultado do próximo disparo em 24/08 às 05:00 BRT.
- **Fabrícia:** confirmar se o gateway parado é intencional; não reiniciar automaticamente.
- **Tobias:** ajustar futuramente a atribuição de métricas para que sessões da rotina apareçam no agente responsável.
- **Natália:** documentar a exceção de modelo dos crons antes de tratar o estado atual como padrão aprovado.
- **TTS:** separar saúde do canal de voz da saúde do agente para evitar falsos incidentes.

## 7. Cobertura e limitações

- **Cobertura temporal:** 2026-08-10 05:00:20 a 2026-08-17 05:00:20, America/Sao_Paulo.
- **Fontes cobertas:** 12 perfis de IA; configurações; fallback; gateways; sessões; mensagens; tokens; crons; últimos estados e sinais de log; verificação atual de `hermes profile list`.
- **Perfil humano excluído:** `thiagoribeiro`, corretamente tratado como humano/reservado e não contado na frota de IA.
- **Custo:** US$ 0,00 foi coletado, porém cobrança do provider não é mensurável de forma confiável; custo real classificado como desconhecido.
- **Valor aguardando validação humana:** todas as entregas citadas, salvo estados técnicos de execução.
- **Qualidade:** estados `ok` e volume de ferramentas comprovam execução, não correção substantiva do conteúdo.
- **Logs:** eventos anteriores só foram tratados como falha vigente quando corroborados pelo estado atual. Timeouts de Telegram foram classificados como recuperados; Fabrícia foi classificada pelo estado atual `stopped`.
- **Calendário, e-mail e task store:** não integraram esta revisão, pois o escopo fornecido foi governança da frota e a coleta não incluiu essas fontes. Não houve mutação de tarefas, calendário, e-mail ou notas além da gravação deste relatório aprovado pelo cron.
- **Sessões:** ausência de sessão em um perfil não prova ausência de trabalho; Tobias demonstrou o problema de atribuição via execução delegada no default.
- **Mudanças:** nenhum modelo, provider, permissão, gateway, cron, integração ou arquivo de configuração foi alterado. Este documento contém recomendações, não autorizações.
