# Revisão Semanal de Governança — 2026-08-09

**Janela analisada:** 2026-08-02 18:09:23.129335 a 2026-08-09 18:09:23.129335 — America/Sao_Paulo  
**Execução:** inaugural — semana 1 de 4 para formação da linha de base  
**Responsáveis:** Sérgio Ladeira e Cona  
**Fonte técnica:** coleta read-only de configurações, inventário de perfis, gateways, crons, sessões e logs ao vivo  
**Regra:** atividade técnica não equivale a valor confirmado.

## Resumo executivo

**Conclusão primeiro:** a frota está majoritariamente operacional e o padrão de modelos está íntegro, mas a linha de base começa com três pontos que exigem decisão: Fabrícia aparece parada e com Telegram desconectado; o relatório diário de Google Ads da Flávia falhou por falta de pinagem após mudança de modelo; e respostas de voz estão degradadas por cota esgotada do ElevenLabs. Nenhuma alteração foi executada por esta revisão.

- **12 agentes de IA** inventariados; o perfil humano/reservado `thiagoribeiro` foi corretamente excluído.
- **11 de 12 gateways** aparecem como `running` no inventário atual; Fabrícia aparece como `stopped`. O artefato de estado de Fabrícia ainda traz PID/“running”, uma divergência que precisa de diagnóstico.
- **10 de 12 agentes** tiveram sessões nos sete dias; Fabrícia e Tobias não tiveram sessões em seus bancos de perfil. Tobias, porém, teve rotina diária executada no perfil default, portanto ausência no banco próprio não prova ausência operacional.
- **183 sessões, 425 mensagens de usuário, 2.549 chamadas de modelo e 3.312 chamadas de ferramenta** foram observadas.
- **15.134.775 tokens registrados**: 13.678.651 de entrada e 1.456.124 de saída.
- **43 crons cadastrados:** 31 habilitados e 12 desabilitados. Um cron habilitado está em erro confirmado: `Relatório Diário Google Ads - Conamore`.
- **12 de 12 modelos/providers primários** correspondem ao padrão aprovado; **12 de 12** têm fallback `openai-codex:gpt-5.4-mini`. O `api_max_retries` está em 1 em 11 perfis; Elias está em 3, fora do padrão de failover rápido.
- O custo registrado foi **US$ 0,00**, mas deve ser tratado como **desconhecido/não mensurável**, e não como gratuidade.
- **Valor confirmado:** nenhum registro de validação humana foi fornecido nesta coleta. Para todas as entregas citadas abaixo: **valor aguardando validação humana**.

### Semáforo da semana — linha de base 1/4

#### 🟢 Verdes

- Padrão primário de modelo/provider aderente nos 12 agentes.
- Fallback global correto nos 12 agentes.
- 11 gateways listados como ativos e Telegram conectado em 11 perfis no estado coletado.
- A maior parte dos crons com execução recente apresentou `last_status: ok`.
- Reconexões transitórias do Telegram em Adrian, Maria, Marketing, Natália e Rian tiveram registro posterior de reinício do polling e o estado atual coletado aparece conectado.

#### 🟡 Amarelos

- Atividade elevada em Marketing, Natália, Cona, Elias e Maria, mas sem validação humana de resultado, qualidade ou impacto.
- Elias está com `agent.api_max_retries: 3`, enquanto o padrão aprovado com fallback exige 1.
- Contextos muito longos em sessões de Cona e Elias acionaram limite de TTFB; não houve falha final comprovada, mas há risco de latência e instabilidade.
- Uma rotina de Natália terminou com status geral `ok`, embora os logs internos registrem erros de ferramenta/Oracle e uma ação pendente de aprovação; entrega e qualidade precisam ser conferidas.
- Matias teve timeout/HTTP 500 do Octadesk às 14:57 de 09/08. Como o marcador de plataforma é anterior a esse evento, falta evidência posterior para declarar recuperação ou falha vigente.
- Custos não são mensuráveis com segurança pelos providers desta coleta.

#### 🔴 Vermelhos

- **Fabrícia:** inventário atual mostra gateway parado; Telegram está desconectado desde 09/07. Há conflito com o arquivo de estado que ainda informa `running`, portanto o diagnóstico deve usar processo/health check ao vivo.
- **Marketing / Google Ads:** cron habilitado falhou em 09/08 às 08:30 por mudança do modelo global sem pinagem explícita. A próxima execução está prevista para 10/08 às 08:30.
- **Voz / ElevenLabs:** falhas 401 por `quota_exceeded` ocorreram repetidamente em 09/08 em Cona e Elias; também houve ocorrências em Tiago em 08/08. Restavam 5 créditos nos registros, insuficientes para as solicitações. O texto pode continuar operando, mas a resposta automática por voz está degradada.

## 1. Saúde da frota

| Agente | Gateway atual | Modelo/provider primário | Fallback | Crons | Saúde qualitativa |
|---|---|---|---|---:|---|
| Cona / default | Running | gpt-5.6-sol / openai-codex | Conforme | 5 habilitados / 5 desabilitados | 🟡 TTS degradado e contextos longos |
| Adrian | Running | gpt-5.6-luna / openai-codex | Conforme | 0 | 🟢 conexão atual normal |
| Bianco | Running | gpt-5.6-luna / openai-codex | Conforme | 0 / 2 desabilitados | 🟡 uso direto mínimo |
| Elias | Running | gpt-5.6-sol / openai-codex | Conforme | 5 habilitados | 🟡 TTS degradado; retries fora do padrão |
| Fabrícia | **Stopped no inventário** | deepseek-v4-pro / opencode-go | Conforme | 0 | 🔴 Telegram desconectado e estado divergente |
| Maria | Running | gpt-5.6-sol / openai-codex | Conforme | 1 habilitado | 🟢 atividade e conexão observadas |
| Flávia / marketing | Running | deepseek-v4-pro / opencode-go | Conforme | 8 habilitados / 1 desabilitado | 🔴 cron de Google Ads em erro |
| Matias | Running | gpt-5.6-sol / openai-codex | Conforme | 3 habilitados | 🟡 erro recente do Octadesk sem confirmação posterior |
| Natália | Running | gpt-5.6-luna / openai-codex | Conforme | 4 habilitados / 1 desabilitado | 🟡 erros internos em cron concluído |
| Rian | Running | gpt-5.6-luna / openai-codex | Conforme | 4 habilitados | 🟢 automações com status recente ok; uso direto mínimo |
| Tiago | Running | gpt-5.6-luna / openai-codex | Conforme | 1 habilitado | 🟡 TTS falhou em 08/08; texto conectado |
| Tobias | Running | deepseek-v4-pro / opencode-go | Conforme | 0 / 3 desabilitados no perfil | 🟡 sem sessão própria; rotina diária executada via default |

## 2. Atividade observada e valor

| Agente | Atividade observada em 7 dias | Evidência de processo | Valor |
|---|---:|---|---|
| Cona | 29 sessões; 373 chamadas de modelo; 678 ferramentas | Rotinas diárias de Tiago, Tobias e Elias; governança agendada | valor aguardando validação humana |
| Adrian | 3 sessões; 14 chamadas; 15 ferramentas | Conversa de disponibilidade e sessões CLI | valor aguardando validação humana |
| Bianco | 1 sessão; 1 chamada; 0 ferramentas | Sessão técnica mínima | valor aguardando validação humana |
| Elias | 25 sessões; 345 chamadas; 438 ferramentas | Agenda, ShinePhone, Granola e solicitações executivas observadas | valor aguardando validação humana |
| Fabrícia | 0 sessões | Nenhuma atividade de sessão na janela | valor aguardando validação humana |
| Maria | 15 sessões; 188 chamadas; 307 ferramentas | Análises de documentos SST e rotina de folha | valor aguardando validação humana |
| Flávia / marketing | 38 sessões; 891 chamadas; 787 ferramentas | GA4, health checks, visibilidade em IA e Google Ads | valor aguardando validação humana |
| Matias | 11 sessões; 54 chamadas; 189 ferramentas | Atualização Hermes, limpeza de sessões e verificação de sync | valor aguardando validação humana |
| Natália | 53 sessões; 522 chamadas; 645 ferramentas | Relatórios B2B, Casa e análise DEBX | valor aguardando validação humana |
| Rian | 1 sessão; 1 chamada; 0 ferramentas | Quatro automações de análise de lojas físicas cadastradas | valor aguardando validação humana |
| Tiago | 7 sessões; 160 chamadas; 253 ferramentas | Análises de crédito e títulos em aberto | valor aguardando validação humana |
| Tobias | 0 sessões no perfil | `tobias-daily` executado com sucesso no perfil default | valor aguardando validação humana |

**Leitura de governança:** volume alto não confirma valor. A primeira linha de base mostra onde há operação, mas ainda não demonstra economia, impacto financeiro, aceitação sem correção ou decisão empresarial gerada.

## 3. Qualidade, confiabilidade e riscos

| Agente/fluxo | Evidência | Avaliação | Ação recomendada |
|---|---|---|---|
| Padrão de modelos | 12/12 primários e 12/12 fallbacks conformes | 🟢 confiável na coleta | Preservar; somente Sérgio autoriza mudanças |
| Fabrícia / Telegram | Perfil listado stopped e Telegram disconnected | 🔴 indisponibilidade provável | Diagnóstico de processo e health check ao vivo por Matias |
| Marketing / Google Ads | Cron bloqueado por drift de modelo não pinado | 🔴 entrega não executada | Pinagem explícita somente após autorização do Sérgio e teste controlado |
| Voz / ElevenLabs | 401 `quota_exceeded` repetido em 08–09/08 | 🔴 canal de voz degradado | Sérgio decidir renovar cota ou desabilitar voz automática; preservar texto |
| Natália / relatório Casa | Status final ok, mas erros internos e aprovação pendente | 🟡 qualidade não confirmada | Conferir artefato entregue, fonte e destinatário antes de aceitar o resultado |
| Matias / Octadesk | Timeout e HTTP 500 em 09/08 14:57 | 🟡 evento recente, estado atual inconclusivo | Validar health check posterior e registrar recuperação |
| Cona e Elias / sessões longas | Limite de TTFB acionado em contextos de ~150–158 mil tokens | 🟡 risco de latência | Avaliar encerramento/compactação de sessões longas sem alterar modelos |
| Elias / failover | `api_max_retries: 3`, padrão é 1 | 🟡 drift de configuração | Propor correção em janela aprovada; não alterar nesta revisão |
| Custos | US$ 0,00 reportado por providers | 🟡 mensuração insuficiente | Tratar como custo desconhecido até haver fonte financeira confiável |

Não foi observada, na coleta fornecida, evidência de violação de permissão, exposição de credencial ou mudança não autorizada. Isso não equivale a auditoria completa de segurança.

## 4. Portfólio

### Agentes

Na execução inaugural, sem validação humana de valor, a classificação prudente é **Observar**, e não “Manter”. Fabrícia recebe recomendação de **Adormecer** enquanto indisponível, preservando perfil e documentação. Nenhum encerramento é proposto.

| Agente | Classificação | Justificativa |
|---|---|---|
| Cona / default | **Observar** | Uso intenso e rotinas reais; valor ainda não validado; voz degradada |
| Adrian | **Observar** | Uso eventual e sem resultado validado |
| Bianco | **Observar** | Uso direto mínimo; dois crons já desabilitados |
| Elias | **Observar** | Uso intenso; valor pendente; TTS e retry drift exigem acompanhamento |
| Fabrícia | **Adormecer** | Sem sessões, gateway listado parado e Telegram desconectado; preservar até decisão do Sérgio |
| Maria | **Observar** | Operação real observada, mas sem validação humana de valor/qualidade |
| Flávia / marketing | **Observar** | Operação intensa; um fluxo crítico degradado; valor pendente |
| Matias | **Observar** | Rotinas técnicas executadas; benefício e recuperação do Octadesk não validados |
| Natália | **Observar** | Maior número de sessões; qualidade de pelo menos um fluxo precisa ser verificada |
| Rian | **Observar** | Automações cadastradas e execução recente ok; uso direto mínimo e valor pendente |
| Tiago | **Observar** | Análises financeiras observadas; resultado e aceitação pendentes |
| Tobias | **Observar** | Sem atividade no banco próprio, mas rotina via default; ownership precisa ser esclarecido |

### Automações

| Grupo/automação | Quantidade | Classificação | Justificativa |
|---|---:|---|---|
| Automações habilitadas sem erro vigente confirmado | 30 | **Observar** | Operação/status técnico não basta para confirmar valor na semana 1 |
| Relatório Diário Google Ads - Conamore | 1 | **Melhorar** | Habilitado, mas falhou por ausência de pinagem explícita |
| Automações desabilitadas | 12 | **Adormecer** | Já não operam; preservar até revisão de necessidade, sem excluir |

**Distribuição:** agentes — 11 Observar, 1 Adormecer; automações — 30 Observar, 1 Melhorar, 12 Adormecer; 0 Encerrar.

## 5. Decisões da semana

| # | Decisão proposta | Responsável sugerido | Prazo | Critério de conclusão |
|---:|---|---|---|---|
| 1 | Autorizar Matias a diagnosticar Fabrícia e apresentar opção de restabelecimento ou adormecimento formal | Sérgio aprova; Matias executa diagnóstico | 2026-08-11 18:00 BRT | Inventário, processo e Telegram verificados ao vivo; smoke test documentado se houver restabelecimento; nenhuma mudança sem aprovação |
| 2 | Autorizar correção controlada do cron `Relatório Diário Google Ads - Conamore`, fixando provider/model aprovados | Sérgio aprova; Matias e Flávia executam/validam | 2026-08-10 08:15 BRT | Cron explicitamente pinado ao padrão aprovado da Flávia, execução de teste concluída e resultado lido de volta antes do ciclo das 08:30 |
| 3 | Instituir validação humana mínima para os cinco fluxos mais ativos (Marketing, Natália, Cona, Elias e Maria), incluindo decisão sobre a voz ElevenLabs | Sérgio define validadores; gestores das áreas validam | 2026-08-14 18:00 BRT | Um registro por fluxo com entrega, fonte, aceitação/correção e resultado; decisão documentada de renovar cota ou manter voz automática desabilitada/degradada |

## 6. Pendências anteriores

Esta é a execução inaugural. Não há pendências de revisões semanais anteriores. Compromissos identificados apenas por nomes de sessão ou cron não foram marcados como concluídos sem confirmação.

## 7. Cobertura e limitações

- A janela técnica foi coberta integralmente de **2026-08-02 18:09:23.129335 a 2026-08-09 18:09:23.129335**, America/Sao_Paulo.
- Foram cobertos 12 agentes de IA, 43 registros de cron, configuração primária/fallback, gateways, sessões agregadas e sinais recentes de log. O perfil humano/reservado `thiagoribeiro` foi excluído corretamente.
- A coleta é read-only e nenhuma configuração, modelo, provider, permissão, gateway, cron ou integração foi alterada.
- Custos: os providers reportaram zero, mas a cobrança pode não ser mensurável; custo real permanece desconhecido.
- Valor, qualidade, autonomia, economia e impacto financeiro não foram confirmados por gestor humano nesta fonte. **Valor aguardando validação humana** para todas as entregas.
- Logs podem conter eventos históricos. Foram usados timestamps e estado coletado; quando não havia evidência posterior, o item foi marcado como inconclusivo em vez de falha vigente.
- O conflito de Fabrícia entre `profile list` (stopped) e o artefato de gateway (running/PID) impede conclusão técnica definitiva sem health check ao vivo.
- Não foram consultados calendário executivo, e-mail, RD Station, Oracle/DEBX, artefatos finais dos relatórios, destinatários externos nem indicadores financeiros. Assim, esta revisão mede atividade e saúde técnica, não retorno empresarial.
- A ausência de sessão no banco próprio não prova ausência total de trabalho: Tobias teve rotina observada no perfil default.
- Não se inferiu conclusão a partir de silêncio, `last_status: ok` ou volume de tokens.
- Esta é a **semana 1 de 4 da linha de base**. Comparações de tendência e gatilho de três semanas sem valor confirmado só serão possíveis nas próximas revisões.
