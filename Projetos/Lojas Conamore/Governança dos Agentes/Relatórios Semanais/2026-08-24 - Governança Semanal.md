# Revisão Semanal de Governança — 2026-08-24

**Janela analisada:** 2026-08-17 05:00:15 a 2026-08-24 05:00:15 — America/Sao_Paulo  
**Responsáveis:** Sérgio Ladeira e Cona  
**Fonte técnica:** coleta read-only de configurações, gateways, crons, sessões e sinais de log ao vivo  
**Fase:** formação da linha de base — semáforo qualitativo, sem nota numérica  

## Resumo executivo

**Conclusão primeiro:** a frota está operacional, mas a governança deve tratar três desvios antes de ampliar autonomia: configuração de modelo fora do padrão em Flávia/marketing e Matias; disponibilidade não resolvida da Fabrícia; e ausência de validação humana estruturada sobre o valor das entregas. Não foi identificada evidência de violação de permissão ou falha material vigente na coleta. Os episódios de rede do Telegram se recuperaram e os estados atuais, salvo Fabrícia, aparecem conectados.

- **12 agentes de IA** inventariados; o perfil humano reservado foi corretamente excluído.
- **10 agentes com sessões na janela**; Fabrícia e Tobias tiveram zero sessões em seus próprios perfis. Há, porém, uma rotina `tobias-daily` executada pelo perfil default, deixando ambígua a titularidade técnica dessa automação.
- **165 sessões**, **2.656 chamadas de API**, **3.417 chamadas de ferramentas** e **291 mensagens de usuário**.
- **12.070.418 tokens de entrada** e **2.142.589 tokens de saída** registrados.
- **34 automações habilitadas** no inventário. As rotinas recorrentes com execução registrada não apresentaram `last_status=error`; houve uma falha histórica de entrega em uma automação pontual do Bianco em 2026-08-18.
- **11 gateways reportados em execução** pelo inventário de perfis; Fabrícia aparece `stopped`, com Telegram desconectado. O estado técnico detalhado dela é contraditório (`gateway_state=running`), exigindo confirmação operacional.
- **Valor confirmado:** nenhum resultado empresarial, economia, impacto financeiro ou qualidade foi validado por humano nesta coleta. Para toda atividade abaixo, **valor aguardando validação humana**.
- **Custos:** os registros retornaram US$ 0; isso não comprova custo zero. **Custo real desconhecido/não mensurável pelos dados disponíveis.**

## Semáforo da semana

### 🟢 Verdes

- Cona, Adrian, Bianco, Elias, Maria, Flávia/marketing, Matias, Natália, Rian, Tiago e Tobias aparecem com gateway em execução; os canais Telegram atuais aparecem conectados nesses perfis.
- Todos os 12 perfis têm fallback `openai-codex:gpt-5.4-mini` com a URL esperada.
- Cona, Adrian, Bianco, Maria, Fabrícia, Natália, Rian, Tiago e Tobias estão com `api_max_retries: 1` e primário conforme o padrão aprovado, exceto os desvios listados em amarelo.
- As desconexões de Telegram registradas em 2026-08-23/24 mostram recuperação posterior; portanto, não são classificadas como falha vigente.
- Não houve evidência, nesta coleta, de exposição de credenciais, alteração de permissão ou ação destrutiva.

### 🟡 Amarelos

- **Flávia/marketing:** primário ao vivo está `gpt-5.6-luna/openai-codex`, mas o padrão aprovado é `deepseek-v4-pro/opencode-go`.
- **Matias:** primário ao vivo está `gpt-5.6-luna/openai-codex`, mas o padrão aprovado é `gpt-5.6-sol/openai-codex`.
- **Elias:** primário correto, mas `api_max_retries: 3`; a política da frota determina `1` quando há fallback.
- Sessões recentes de Adrian, Maria, Natália e Tiago registraram `deepseek-v4-pro` apesar de seus primários aprovados serem Codex. Isso pode decorrer de modelo fixado em cron, teste ou fallback; requer inventário do modelo efetivo das automações, sem inferir alteração do primário.
- Flávia/marketing teve tentativas repetidas de iniciar uma segunda instância às 04:58–05:00 de 2026-08-24. O gateway principal permaneceu em execução e conectado, mas a origem do acionamento duplicado deve ser eliminada.
- Bianco teve falha histórica de entrega Telegram em automação pontual de 2026-08-18 (`Chat not found`). Não é falha vigente, mas a entrega não foi confirmada.
- O `api_server` do perfil default aparece desconectado desde 2026-07-28. A coleta não informa se esse conector deveria estar ativo; validar necessidade antes de classificar como incidente.
- Custos e valor permanecem sem medição confiável.

### 🔴 Vermelhos

- **Fabrícia:** `hermes profile list` informa gateway parado; Telegram está desconectado e não houve atividade em sete dias. Há contradição com o campo agregado `gateway_state=running`. Enquanto não houver verificação/smoke test, a disponibilidade real do agente não está confirmada.

## 1. Saúde da frota

| Agente | Gateway/canais | Modelo/provider ao vivo | Fallback/retries | Crons e sinais | Status |
|---|---|---|---|---|---|
| Cona / default | Running; Telegram e webhook conectados; API server desconectado | gpt-5.6-sol / openai-codex | Correto / 1 | 3 rotinas operacionais diárias e governança; execuções OK | 🟢/🟡 |
| Adrian | Running; Telegram conectado | gpt-5.6-luna / openai-codex | Correto / 1 | Sem cron; rede recuperada | 🟢 |
| Bianco | Running; Telegram conectado | gpt-5.6-luna / openai-codex | Correto / 1 | Falha histórica em entrega pontual | 🟡 |
| Elias | Running; Telegram conectado | gpt-5.6-sol / openai-codex | Fallback correto / **3** | 3 crons ativos, últimas execuções OK | 🟡 |
| Fabrícia | **Stopped** no inventário; Telegram desconectado | deepseek-v4-pro / opencode-go | Correto / 1 | Sem cron e sem atividade | 🔴 |
| Maria | Running; Telegram conectado | gpt-5.6-sol / openai-codex | Correto / 1 | 3 crons ativos, últimas execuções OK; recuperação de rede observada | 🟢 |
| Flávia / marketing | Running; Telegram conectado | **gpt-5.6-luna / openai-codex** | Correto / 1 | 9 crons ativos; tentativas de segunda instância | 🟡 |
| Matias | Running; Telegram/Octadesk conectados | **gpt-5.6-luna / openai-codex** | Correto / 1 | 5 crons ativos; últimas execuções OK | 🟡 |
| Natália | Running; Telegram conectado | gpt-5.6-luna / openai-codex | Correto / 1 | 4 crons ativos; últimas execuções OK | 🟡 |
| Rian | Running; Telegram conectado | gpt-5.6-luna / openai-codex | Correto / 1 | 4 crons ativos; últimas execuções OK | 🟢 |
| Tiago | Running; Telegram conectado | gpt-5.6-luna / openai-codex | Correto / 1 | 1 cron ativo; última execução OK | 🟡 |
| Tobias | Running; Telegram conectado | deepseek-v4-pro / opencode-go | Correto / 1 | Crons próprios desabilitados; rotina diária executada no default | 🟡 |

## 2. Atividade observada e valor

| Agente | Sessões | Atividade observada | Valor |
|---|---:|---|---|
| Cona | 33 | Governança, reuniões e rotinas executivas/operacionais | Valor aguardando validação humana |
| Adrian | 2 | Apoio jurídico/documental | Valor aguardando validação humana |
| Bianco | 2 | Compras, comparação documental e comunicação | Valor aguardando validação humana |
| Elias | 23 | Agenda, Granola e ShinePhone | Valor aguardando validação humana |
| Fabrícia | 0 | Nenhuma sessão observada | Valor aguardando validação humana |
| Maria | 7 | Ponto, atrasos e desenvolvimento de pessoas | Valor aguardando validação humana |
| Flávia / marketing | 46 | GA4, Google Ads, sites e monitoramentos | Valor aguardando validação humana |
| Matias | 18 | Infraestrutura Hermes, GNRE/DUA-e e suporte técnico | Valor aguardando validação humana |
| Natália | 30 | Relatórios comerciais B2B/Casa e DEBX | Valor aguardando validação humana |
| Rian | 1 | Uma interação conversacional; automações de lojas executadas fora das sessões listadas | Valor aguardando validação humana |
| Tiago | 3 | Crédito, documentos e cruzamento semanal | Valor aguardando validação humana |
| Tobias | 0 | Sem sessão no perfil; rotina logística observada no default | Valor aguardando validação humana |

> Contagens medem atividade técnica, não resultado, qualidade, economia ou impacto.

## 3. Qualidade, confiabilidade e riscos

| Agente/fluxo | Evidência | Avaliação | Ação recomendada |
|---|---|---|---|
| Telegram da frota | Timeouts, Bad Gateway e ReadError em 2026-08-23/24, seguidos por mensagens de reinício e estado atual conectado | Falha recuperável, sem prova de indisponibilidade vigente | Observar recorrência e duração; escalar ao Matias se houver perda de entrega |
| Fabrícia | Inventário `stopped`, Telegram desconectado e zero atividade; campo agregado contraditório | Disponibilidade não confirmada | Verificar serviço e executar smoke test antes de depender do agente |
| Flávia/marketing | Primário fora do padrão e tentativas de gateway duplicado | Drift de configuração/orquestração | Matias diagnosticar e preparar correção para aprovação do Sérgio |
| Matias | Primário fora do padrão | Drift de configuração | Preparar restauração do padrão para aprovação do Sérgio |
| Elias | `api_max_retries=3` com fallback | Drift da política de failover | Preparar ajuste para `1`, sujeito à aprovação do Sérgio |
| Modelos efetivos em sessões | DeepSeek apareceu em sessões de perfis Codex | Origem não determinada | Comparar modelos fixados em crons e logs de fallback |
| Bianco — entrega pontual | `Chat not found` em 2026-08-18 | Entrega externa não confirmada | Validar destino antes de reutilizar a automação |
| Custos | US$ 0 reportado para todos os perfis | Não mensurável | Não usar zero como evidência de gratuidade |
| Qualidade das entregas | Sem aceite/correção humana estruturada na coleta | Desconhecida | Amostrar entregas e registrar aceito/corrigido/rejeitado |

## 4. Portfólio

| Agente/automação | Classificação | Justificativa |
|---|---|---|
| Cona | **Manter** | Alta atividade e configuração conforme padrão; valor aguardando validação humana |
| Adrian | **Observar** | Uso baixo, sem falha vigente; valor aguardando validação humana |
| Bianco | **Observar** | Uso baixo e uma falha histórica de entrega pontual; valor aguardando validação humana |
| Elias | **Melhorar** | Operação recorrente estável, mas retries divergem da política; valor aguardando validação humana |
| Fabrícia | **Adormecer** | Já aparece parada, sem atividade e sem disponibilidade confirmada; preservar perfil e documentação. Qualquer encerramento exigiria Sérgio |
| Maria | **Manter** | Uso real e rotinas recorrentes com execução OK; valor aguardando validação humana |
| Flávia / marketing | **Melhorar** | Volume alto, porém primário fora do padrão e acionamento duplicado do gateway; valor aguardando validação humana |
| Matias | **Melhorar** | Atividade alta e infraestrutura ativa, porém primário fora do padrão; valor aguardando validação humana |
| Natália | **Melhorar** | Rotinas comerciais ativas, mas modelo efetivo das sessões diverge do primário configurado; valor aguardando validação humana |
| Rian | **Manter** | Automações recorrentes executadas sem erro registrado; valor aguardando validação humana |
| Tiago | **Observar** | Uso moderado/baixo e ocorrência de modelo efetivo divergente; valor aguardando validação humana |
| Tobias | **Melhorar** | Gateway ativo, mas zero sessões próprias e automação diária sob o perfil default; esclarecer titularidade e entrega |
| Automação pontual do Bianco de 2026-08-18 | **Encerrar** | Execução única já vencida e entrega falhou; recomendação apenas, sujeita à autorização do Sérgio |

## 5. Decisões da semana

| # | Decisão proposta | Responsável sugerido | Prazo | Critério de conclusão |
|---:|---|---|---|---|
| 1 | Autorizar plano de correção dos desvios de modelo/retries e auditoria dos modelos fixados em crons, sem mudança prévia à aprovação | Matias, com aprovação do Sérgio | 2026-08-26 | Inventário pós-correção mostra Flávia=`deepseek-v4-pro/opencode-go`, Matias=`gpt-5.6-sol/openai-codex`, Elias retries=`1`; crons divergentes documentados e smoke tests aprovados |
| 2 | Definir disponibilidade e titularidade operacional de Fabrícia e Tobias | Matias + gestores humanos de Fábrica e Logística | 2026-08-27 | Fabrícia tem estado único confirmado e smoke test; rotina `tobias-daily` tem perfil, destino e responsável documentados |
| 3 | Implantar validação humana mínima para o baseline semanal | Cona + gestores humanos das áreas | 2026-08-28 | Ao menos uma entrega relevante por área ativa registrada como aceita, corrigida ou rejeitada, com fonte/ID e validador; custos marcados como mensuráveis ou desconhecidos |

## 6. Pendências e horizonte operacional

- Próxima governança semanal indicada pela coleta: **2026-08-31 05:00 BRT**.
- Na manhã de 2026-08-24 há concentração de rotinas entre 05:00 e 09:00, especialmente Matias, Natália, Maria, Elias, Tiago e marketing. Evitar mudanças não aprovadas nessa janela.
- Não carregar automaticamente toda baixa atividade como prioridade: Adrian, Bianco e Tiago ficam em observação; Fabrícia requer decisão explícita; Tobias requer correção de governança da automação.
- Não foi possível reconciliar promessas ou itens aguardando terceiros a partir da coleta técnica. Silêncio não foi tratado como conclusão.

## 7. Cobertura e limitações

- Cobertura temporal completa da coleta: **2026-08-17 05:00:15 a 2026-08-24 05:00:15**, America/Sao_Paulo.
- Foram cobertos configs ao vivo, fallback/retries, estado dos gateways/canais, crons, sessões, mensagens, tokens e sinais recentes de log dos 12 agentes de IA.
- Calendários, tarefas, notas de projeto, conteúdo integral das entregas, indicadores financeiros e aceite humano não fizeram parte da coleta; portanto, a revisão é de governança técnica/operacional, não uma comprovação de resultado empresarial.
- Os sinais de log são amostras recentes, não uma leitura exaustiva. Eventos históricos foram distinguidos do estado atual sempre que o timestamp e o estado permitiram.
- **Custos não mensuráveis:** US$ 0 foi registrado, mas o custo real é desconhecido quando o provider não fornece cobrança.
- **Valor aguardando validação humana:** todos os agentes e automações citados.
- A contagem de 34 automações habilitadas inclui rotinas futuras/sem execução prévia; status OK só foi atribuído quando havia execução registrada.
- A coleta não trouxe o campo de modelo de cada cron; por isso, modelos divergentes em sessões foram sinalizados para investigação, não tratados como mudança comprovada do primário.
- A contradição de estado da Fabrícia impede afirmar com segurança que o gateway está plenamente ativo ou totalmente indisponível sem teste específico.
- Nenhuma configuração, modelo, provider, permissão, gateway, cron ou integração foi alterado por esta revisão.
