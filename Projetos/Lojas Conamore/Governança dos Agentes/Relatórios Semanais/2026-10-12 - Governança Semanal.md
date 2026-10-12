# Revisão Semanal de Governança — 2026-10-12

**Janela exata analisada:** 2026-10-05T05:00:18.387738-03:00 a 2026-10-12T05:00:18.387738-03:00 — America/Sao_Paulo. **Horizonte de decisão:** 12 a 18/10/2026, sem agenda executiva consultada. **Responsáveis:** Sérgio Ladeira e Cona. Fonte principal: coleta read-only anexada, gerada em 12/10 às 05:00:18; conferência seletiva dos YAMLs e dos processos às ~05:01 BRT; referência: [[2026-10-05 - Governança Semanal]]. Nenhuma configuração alterada.

## Resumo executivo

**Conclusão primeiro — governança 🔴; operação 🟡 e disponibilidade em reavaliação.** O inventário não bate com a premissa de 12 agentes: há **13 perfis de IA** na coleta e no disco, incluindo **Melia**, fora do mapa aprovado fornecido; `thiagoribeiro` permanece excluído como humano. Apenas **4 dos 12 agentes com primário especificado** correspondem ao provider/modelo aprovado (Fabrícia, Flávia/marketing, Natália e Tobias); Melia não tem atribuição canônica informada, portanto não foi presumida. **0/13** fallbacks correspondem a `openai-codex:gpt-5.4-mini`: todos configuram `openai-codex:gpt-5.6-luna`; Elias conserva `api_max_retries=3`, demais 1. As URLs-base lidas são coerentes com os providers declarados. Isto é desvio de política, não autorização para trocar modelos. A elegibilidade real do fallback não foi testada; resposta final de sessão não prova qual modelo respondeu.

- **Atividade:** 213 sessões em 12/13 perfis, 2.432 chamadas de API, 3.276 chamadas de ferramenta, 11.571.897 tokens de entrada e 1.600.738 de saída. Tobias não tem sessão própria, mas a rotina homônima roda no default; ausência de sessão própria não significa inatividade da função. Parte das sessões é teste `OK` ou cron/subagente; atividade técnica não equivale a entrega aceita. **Entregas com valor confirmado nesta coleta: nenhuma documentada; valor aguardando validação humana.** Cobrança real **desconhecida**, apesar de US$ 0 no banco local.
- **Crons:** 51 registros, 38 habilitados e 13 desabilitados. Três habilitados guardam último status `error`: visitas Mercado Livre de Melia (401 em 11/10) e dois mensais de Rian (falta de `oracledb` em 01/10). O cron desabilitado de Marketing com erro de 05/09 é histórico, não falha corrente. `last_status=ok` não comprova entrega ou aceite.
- **Gateway:** a coleta às 05:00 marcava todos os 13 `gateway_state=running`, Telegram conectado; já `hermes profile list` marcava quatro como `stopped` (Adrian, Maria, Matias e Tiago), em conflito com PIDs e unidades systemd ativos desses quatro. Uma checagem posterior encontrou **só cinco PIDs antigos presentes** (default e esses quatro); os outros oito PIDs antigos ausentes, e tentativas de inicialização/atualização Hermes em andamento. Estado dos oito após o snapshot **não foi estabelecido**; checagem ponta a ponta é urgente com Matias, sem afirmar indisponibilidade definitiva a partir de PID isolado. Default teve API server `disconnected` desde julho no snapshot, sem uso requerido demonstrado; Octadesk de Matias teve timeout em 11/10, embora snapshot indique conexão.

### Semáforo qualitativo

- 🟢 **Sinais técnicos positivos:** crons diários de Elias, Natália, Marketing, Maria e os diários de Rian com último ciclo `ok`; Telegram recuperou transporte após `ConnectError` em logs de 11–12/10. Não se infere valor, qualidade ou entrega ponta a ponta.
- 🟡 **Indeterminado:** valor e custo reais sem validação; 13º perfil Melia sem mapa aprovado; status divergente `profile list` × processos; alertas transitórios de Telegram recuperados; capacidade da semana e aceites não conhecidos.
- 🔴 **Prioridades verificáveis:** oito primários divergentes dentre os 12 especificados, 13 fallbacks divergentes e retry do Elias; 401 do relatório de visitas Melia no último ciclo, dois mensais de Rian falhos em 01/10; ampla diferença entre snapshot de PIDs e estado observado logo depois, durante atividade de update/inicialização. Não se verificou violação de credenciais ou permissão nesta revisão; ausência de achado não equivale a auditoria de segurança.

## 1. Saúde da frota e uso

As leituras diretas abaixo prevalecem sobre os campos `model` nulos do pré-run e sobre `profile list`. URLs-base correspondem aos providers informados. Todos os 13 perfis têm fallback `openai-codex:gpt-5.6-luna` (não conforme ao padrão informado); nenhum foi alterado.

| Agente | Primário atual / comparação com padrão | Sessões em 7 dias | Crons habilitados / pontos de atenção | Classificação provisória |
|---|---|---:|---|---|
| Cona/default | `openai-codex:gpt-6-sol` ≠ `gpt-5.6-sol` | 31 | 5; governança semanal último `ok` 05/10; diários de Elias/Tiago/Tobias pertencem a este perfil | Melhorar |
| Adrian | `opencode-go:deepseek-v4-pro` ≠ `openai-codex:gpt-5.6-luna` | 2 (testes curtos) | 0; PID antigo presente, `profile list=stopped` | Melhorar |
| Bianco | `opencode-go:deepseek-v4-pro` ≠ `openai-codex:gpt-5.6-luna` | 1 (teste) | 0; dois legados desligados; PID antigo ausente na checagem posterior | Adormecer — proposta |
| Elias | `opencode-go:deepseek-v4-pro` ≠ `openai-codex:gpt-5.6-sol` | 20 | 3, últimos `ok`; timeout de ferramenta em 11/10 no resumo Granola, apesar de conclusão do cron; retry 3 | Melhorar |
| Fabrícia | `opencode-go:deepseek-v4-pro` conforme | 1 (teste) | 0; PID antigo ausente na checagem posterior | Observar |
| Maria | `opencode-go:deepseek-v4-pro` ≠ `openai-codex:gpt-5.6-sol` | 2 (testes) | 3, últimos `ok`; PID antigo presente, `profile list=stopped` | Melhorar |
| Flávia/marketing | `opencode-go:deepseek-v4-pro` conforme | 57 | 11; um legado desabilitado com erro histórico de 05/09 | Observar |
| Matias | `opencode-go:deepseek-v4-pro` ≠ `openai-codex:gpt-5.6-sol` | 6 | 4, últimos `ok`; timeout Octadesk em 11/10; PID antigo presente, `profile list=stopped` | Melhorar |
| Melia | `opencode-go:deepseek-v4-pro`; **padrão não fornecido** | 2 (uma conversa aberta) | 3; visitas 401 em 11/10, aviso de reautorização `ok`; PID antigo ausente depois | Melhorar |
| Natália | `openai-codex:gpt-5.6-luna` conforme | 87 (57 `agent_close` de subagentes) | 4, últimos `ok`; uma sessão cron sem saída; PID antigo ausente depois | Observar |
| Rian | `opencode-go:deepseek-v4-pro` ≠ `openai-codex:gpt-5.6-luna` | 1 (teste) | 4; dois mensais com erro em 01/10, dois diários `ok`; PID antigo ausente depois | Melhorar |
| Tiago | `opencode-go:deepseek-v4-pro` ≠ `openai-codex:gpt-5.6-luna` | 3 (inclui cron de 05/10) | 1 semanal `ok` em 05/10; PID antigo presente, `profile list=stopped` | Melhorar |
| Tobias | `opencode-go:deepseek-v4-pro` conforme | 0 | 0; três próprios desabilitados; diário homônimo executa no default; PID antigo ausente depois | Observar |

**Valor por agente:** valor aguardando validação humana em todos os 13. Nenhum `Manter` conclusivo é justificável sem aceite humano ou indicador; nenhum `Encerrar` recomendado. Checagem de PID ocorreu depois da janela e é sinal de estado atual, não reclassificação retroativa de atividade dos sete dias.

## 2. Qualidade, confiabilidade e riscos

- **Melia/visitas Mercado Livre:** job `783724b845eb`, `last_run_at=2026-10-11T07:10:55-03:00`, `last_status=error`, HTTP 401 em consulta de itens; próximo agendado 12/10 07:10. O monitoramento de perguntas/pedidos e lembretes de reautorização têm último `ok`, que não sana a falha do relatório. Diagnóstico e eventual reautorização só mediante escopo aprovado.
- **Rian/mensais ACL e GCL:** jobs `cf3f4cc1933f` e `0b0b5765f52e`, erro `ModuleNotFoundError: oracledb` em 01/10 05:20; próximas execuções 01/11. Isso é último resultado persistido, não comprovação de falha hoje; realizar teste não destrutivo com Matias antes do próximo ciclo, com treinamento Oracle/DEBX e distinção PED × venda física antes de qualquer consulta operacional.
- **Elias/Granola:** log de 11/10 20:04 registra timeout de ferramenta (180s) na sessão do resumo diário; cron terminou `ok` às 20:06. Conferir artefato e cobertura antes de chamar a entrega de íntegra. **Natália:** um `cron_incomplete_no_output` no período, sem identificação da rotina na coleta; requer identificação antes de atribuir falha a relatório específico.
- **Transporte e infraestrutura:** `ConnectError` Telegram em 11–12/10 seguido de recuperação em todos os exemplos recentes; não declarar outage sustentado. Octadesk Matias registrou `TimeoutError` em 11/10 16:36, com plataforma conectada no snapshot. A checagem de PIDs logo após o snapshot detectou que apenas default, Adrian, Maria, Matias e Tiago conservavam os PIDs antigos; processos de update/partida novos foram vistos. Não executar correção ou reinício nesta revisão; Matias verifica estado final, possíveis falhas de atualização e entrega real.
- **Permissões:** nenhuma credencial, conteúdo de `.env` ou material sensível foi inspecionado ou exposto; status de conexão não audita escopo. Custos US$ 0 em ledger local são **desconhecidos** em termos reais; não há métrica de impacto financeiro nem confirmação de qualidade por gestor.

## Portfólio

- **Melhorar:** Cona, Adrian, Elias, Maria, Matias, Melia, Rian, Tiago. Motivos específicos na seção de frota; para primários/fallbacks divergentes recomenda-se decisão documentada de Sérgio, não modificação automática. Automações de Melia/visitas e Rian/mensais: **Melhorar** com diagnóstico e teste.
- **Observar:** Fabrícia, Flávia/marketing, Natália e Tobias. As rotinas diárias com `ok` também ficam em **Observar** quanto ao valor até aceite humano; canal e gateway devem ser retestados após a atividade de update.
- **Adormecer — apenas proposta:** Bianco (somente teste e crons próprios desligados, sem valor confirmado). Manter perfil e documentação até decisão de Sérgio; seus dois crons já desabilitados e demais legados desabilitados permanecem sem reativação. Não inferir obsolescência definitiva pela falta de sessão.
- **Manter:** nenhum ainda comprovado conforme definição canônica de valor confirmado + confiabilidade. **Encerrar:** nenhum recomendado; exigiria autorização expressa de Sérgio.

## Decisões da semana

1. **Confiabilidade e alcance real da frota após o snapshot.** Responsável sugerido: **Matias**, prazo **12/10 até 12:00 BRT**. Critério: registrar por perfil estado atual dos gateways/processos, resultado de teste não destrutivo de entrega para os perfis críticos e conclusão da atividade de atualização; separar indisponibilidade comprovada de conflito entre instrumentos. Qualquer mudança de infra depende de autorização de Sérgio.
2. **Deliberar política de modelos e escopo de Melia.** Responsável: **Sérgio** (diagnóstico read-only: Matias), prazo **14/10**. Critério: decidir/documentar manter como exceção ou autorizar correção dos 8 primários divergentes, 13 fallbacks e retry Elias; explicitar se Melia integra o mapa aprovado e seu modelo primário; confirmar entitlement do fallback antes de eventual mudança. Nenhuma alteração feita neste relatório.
3. **Recuperar evidência e aceite de fluxos críticos.** Responsáveis sugeridos: **Matias** (diagnóstico técnico), **Melia/Rian/Elias** (artefatos) e **gestores humanos das áreas** (aceite), prazo **16/10**. Critério: causa e próximo teste dos jobs Melia/visitas e Rian/mensais registrados; conferência do resumo Granola 11/10 e do cron sem saída de Natália; ao menos um artefato prioritário com fonte, resultado, validador e decisão `aceito/ajustar/sem valor`. Credenciais/reautorizações ou instalação de dependências apenas após autorização aplicável.

**Deferidos:** novos agentes, reativação de crons legados, encerramento de perfis, mudança automática de modelos/providers, alteração de integrações e alegações de retorno financeiro. Sem agenda/capacidade executiva consultada, prazos são metas propostas, não blocos de calendário reservados.

## Pendências anteriores

As decisões propostas em [[2026-10-05 - Governança Semanal]] (mapa/fallback/retry, falhas Rian e validação de valor) não têm aprovação/conclusão documentada nesta coleta: primários/fallbacks ainda divergem, dois mensais mantêm último erro e valor continua sem aceite. O cron semanal de governança voltou a `ok` em 05/10, portanto o erro de 28/09 já não deve ser chamado de último erro vigente. A observação anterior de Fabrícia sem PID não foi confirmada como pane contínua: houve teste em 07/10 e snapshot Telegram conectado em 12/10; PID antigo ausente na checagem posterior precisa ser revisto em contexto de update. Não atribuir silêncio a conclusão. Seguimento sugerido: Sérgio/Matias 14/10, gestores/Cona 16/10.

## Cobertura e limitações

- Retrospectiva técnica dos sete dias completos e leitura dos 13 YAMLs de IA; premissa textual de 12 perfis conflita com Melia presente também na coleta. O perfil humano `thiagoribeiro` foi excluído. `profile list` diverge do snapshot e de PIDs/systemd em quatro perfis; status posterior de oito PIDs antigos ausentes ainda não equivale a diagnóstico de serviço. Não se fez smoke test de entitlement do fallback nem teste ponta a ponta Telegram.
- Não foram consultados calendário executivo da semana passada/próximas duas semanas, inbox de tarefas, e-mails, billing externo, entrega integral de cada cron ou aprovação dos gestores. A capacidade do plano e compromissos particulares não podem ser assegurados; a revisão é de governança técnica, não limpeza completa de inbox. Não se consultou Oracle/DEBX.
- Valores de custos `actual_cost_usd=0` e `estimated_cost_usd=0` são apenas registros locais, não custos reais demonstrados. Para toda a frota: **valor aguardando validação humana**. Não inferir horas poupadas, economia, faturamento, qualidade ou sucesso a partir de tokens/sessões.
- A fase inicial de quatro revisões já passou conforme histórico da pasta; o semáforo permanece qualitativo por ausência de validação suficiente para uma pontuação honesta. Somente este relatório foi escrito; nenhum modelo, provider, permissão, gateway, cron, integração ou arquivo de configuração foi modificado.
