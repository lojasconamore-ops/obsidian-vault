# Revisão Semanal de Governança — 2026-10-19

**Janela exata:** 2026-10-12T05:00:18.103988-03:00 a 2026-10-19T05:00:18.103988-03:00 — America/Sao_Paulo. **Horizonte de decisões proposto:** 19 a 25/10/2026. **Responsáveis:** Sérgio Ladeira e Cona. Fontes: coleta read-only do pré-run, leitura direta dos campos de modelo nos YAMLs e `hermes profile list`/existência de PIDs às 05:02 BRT; referência: [[2026-10-12 - Governança Semanal]]. Sem alterações em configuração ou operação.

## Resumo executivo

**Conclusão — governança 🔴; execução técnica 🟡.** Há rotinas frequentes e gateways sinalizados como conectados, mas não há aceite humano nem indicador de negócio anexado que permita declarar valor ou qualidade: **valor aguardando validação humana**. O maior desvio de governança é o mapa de modelos: **5 dos 12 agentes com padrão explicitado estão conformes; 7 divergem**. Melia é o **13º perfil de IA**, ativo na coleta mas fora da lista de 12 com padrão no pedido; não se presume aprovação do seu primário. Todos os **13 fallbacks** nos YAMLs são `openai-codex:gpt-5.6-luna`, diferentes do fallback geral informado `openai-codex:gpt-5.4-mini`; **Elias** tem `api_max_retries=3` (política recomenda 1). Isto é recomendação para deliberação de Sérgio, não autorização para alterar modelos.

- **Números:** 13 perfis IA (humano `thiagoribeiro` excluído), **234 sessões**, **2.406 chamadas de API**, **3.341 chamadas de ferramentas**; **10.466.457 tokens de entrada e 1.919.708 de saída**. Todos os 13 têm ao menos uma sessão, mas parte é teste `OK`, subagente ou cron; nenhuma entrega com valor confirmado foi identificada **nestas fontes**. Ledger local indica US$ 0 em todos os perfis; **custo real desconhecido**, não gratuidade.
- **Automações:** 52 registros, **38 habilitados e 14 desabilitados**. Dois habilitados (mensais ACL/GCL do Rian) conservam `last_status=error` de **01/10**, por `ModuleNotFoundError: oracledb`, anterior à janela; diários ACL/GCL registraram `ok` em 18/10. Um desabilitado de Marketing tem erro antigo de 05/09, não falha vigente. Outros últimos `ok` não comprovam entrega ponta a ponta.
- **Saúde:** a coleta de 05:00 registra 13/13 `gateway_state=running` e Telegram conectado; às 05:02 todos os 13 PIDs informados existiam. `hermes profile list` exibe Adrian, Maria e Matias como `stopped`, em conflito com o snapshot/PIDs; falta teste funcional do canal. CLI avisa **“a source update is unfinished”**; não executar `hermes update` nesta revisão. Default mostra API server `disconnected` com atualização antiga de julho, sem impacto de uso demonstrado.

### Semáforo qualitativo

- 🟢 **Sinais operacionais:** tarefas diárias recentes de Elias, Marketing, Natália, Maria e Rian com último status `ok`; canais Telegram conectados no snapshot, apesar de falhas transitórias de rede nos logs de 18/10. São sinais técnicos, não aceite de negócio.
- 🟡 **A esclarecer:** conflito `profile list` × PIDs em três perfis; uso efetivo de fallback, custo real, entregas integrais e aceites; Melia fora do mapa fornecido; histórico de risco no mensal Rian. Sem agenda executiva consultada, capacidade e prazos abaixo são propostos, não reservados.
- 🔴 **Desvio de política / risco técnico:** sete primários fora do mapa aprovado, 13 fallbacks divergentes, retry Elias fora da orientação; dois últimos resultados mensais com erro e avisos recentes de **refresh OAuth 400** no log de Elias em 19/10 às 04:49–04:59. O último `ok` do resumo Elias em 18/10 não comprova o refresh de hoje; Matias deve verificar integração afetada e entrega, sem expor tokens.

## 1. Saúde da frota e atividade observada

Os YAMLs ao vivo prevalecem sobre os campos `model` nulos do script e sobre nomes de modelo de sessões históricas. As URLs-base do primário lidas são coerentes com `openai-codex` (`chatgpt.com/backend-api/codex`) e `opencode-go` (`opencode.ai/zen/go/v1`); fallback de todos aponta para Codex. **Entitlement do fallback não foi testado**, e um fallback idêntico ao primário de alguns perfis não assegura redundância efetiva. Nenhuma troca de configuração ocorreu.

| Agente | Primário ao vivo vs. padrão | Sessões 7d | Crons habilitados | Classificação provisória |
|---|---|---:|---:|---|
| Cona/default | `openai-codex:gpt-6-sol` ≠ `gpt-5.6-sol` | 33 | 5 | Melhorar |
| Adrian | `openai-codex:gpt-5.6-luna` conforme | 2 | 0 | Observar |
| Bianco | `openai-codex:gpt-5.6-luna` conforme | 2 | 0 (2 desabilitados) | Observar |
| Elias | `openai-codex:gpt-5.6-luna` ≠ `gpt-5.6-sol`; retry 3 | 26 | 3 | Melhorar |
| Fabrícia | `openai-codex:gpt-5.6-luna` ≠ `opencode-go:deepseek-v4-pro` | 2 | 0 | Melhorar |
| Maria | `openai-codex:gpt-5.6-luna` ≠ `gpt-5.6-sol` | 1 | 3 | Melhorar |
| Flávia/marketing | `opencode-go:deepseek-v4-pro` conforme | 59 | 11 | Observar |
| Matias | `opencode-go:deepseek-v4-pro` ≠ `openai-codex:gpt-5.6-sol` | 8 | 4 | Melhorar |
| Melia | `opencode-go:deepseek-v4-pro`; fora do mapa de 12 informado | 3 | 3 | Observar |
| Natália | `openai-codex:gpt-5.6-luna` conforme | 94 | 4 | Observar |
| Rian | `openai-codex:gpt-5.6-luna` conforme; mensais com último erro | 1 | 4 | Melhorar |
| Tiago | `opencode-go:deepseek-v4-pro` ≠ `openai-codex:gpt-5.6-luna` | 1 | 1 | Melhorar |
| Tobias | `openai-codex:gpt-5.6-luna` ≠ `opencode-go:deepseek-v4-pro` | 2 | 0 (3 desabilitados) | Melhorar |

**Atividade ≠ resultado:** Elias executou resumos Granola, agenda e ShinePhone; Flávia, relatórios GA4/Ads; Natália, análises e relatórios comerciais; Matias, rotinas de infraestrutura; demais perfis incluem testes ou conversas pontuais. Jobs homônimos Tobias/Tiago/Elias existem no *default* além de perfis próprios; não atribuir seu resultado ao agente separado sem rastrear execução. Para **todos**, valor aguardando validação humana. Nenhum responsável humano registrou aceite nestas fontes. Não se comprovou economia, impacto financeiro ou qualidade dos relatórios.

## 2. Qualidade, confiabilidade e riscos

- **Rian, mensais ACL/GCL:** jobs `cf3f4cc1933f` e `0b0b5765f52e` com último erro `oracledb` em 01/10 05:20, próximos em 01/11. Não significa falha nova nesta janela. Diagnóstico de dependência/runtime e teste não destrutivo com Matias antes do ciclo; consultar treinamento Oracle/DEBX antes de consultas, distinguindo PED de venda física e sem tratar `PDV_STATUS X` como cancelamento.
- **Elias/OAuth:** log do agente com `Token refresh failed: 400` e `OAuth flow error` em 19/10 04:49–04:59; associação exata ao fluxo e estado de autenticação **não verificados**. Validar com Matias sem usar correio eletrônico pelo Cona, sem ler credenciais e sem reautorizar automaticamente.
- **Gateway/Telegram:** falhas de conexão e reconexões em 18/10 constam dos logs; conectividade sinalizada depois no snapshot. `profile list` marca três perfis parados enquanto seus PIDs estão vivos; não assumir disponibilidade funcional nem outage. Unidade de Adrian, Matias e Tiago registrou aviso de `TimeoutStopSec` antigo (18/10), risco de interrupção no drain em reinício, não prova incidente em curso. Marketing/Natália têm avisos de replay pendente por `FOREIGN KEY constraint failed` em 18/10; confirmar se há entrega não recuperada antes de alegar perda.
- **Melia:** monitoramento de ML, visitas e aviso de reautorização têm último cron `ok` em 18/10, ao contrário do erro 401 da revisão anterior; sem leitura de artefato, não afirmar que autorização e entrega ponta a ponta estejam sanadas.
- **Segurança/limites:** nenhuma credencial ou `.env` lido, nenhuma auditoria de permissões feita. A observação de logs não equivale a diagnóstico causal ou teste funcional. **Custo desconhecido** apesar dos registros de US$ 0.

## Portfólio

- **Melhorar:** Cona, Elias, Fabrícia, Maria, Matias, Rian, Tiago, Tobias. Primários divergentes exigem decisão explícita de Sérgio antes de ação; Elias também requer diagnóstico do refresh; Rian requer teste dos dois mensais. Automação **mensais ACL/GCL Rian: Melhorar**.
- **Observar:** Adrian, Bianco, Flávia/marketing, Melia, Natália. Baixo uso de Adrian/Bianco é insuficiente para concluir ausência de propósito; automações diárias com `ok` seguem **Observar** até aceite humano. Monitoramento e relatório ML de Melia: **Observar**, pois só há status de cron, não aceite da saída.
- **Manter:** nenhum com valor **confirmado** e confiabilidade ponta a ponta comprovada nesta coleta. **Adormecer:** nenhum proposto nesta semana; sugestão anterior de Bianco requer reavaliar após novo uso/teste e responsável humano. **Encerrar:** nenhum recomendado, e sempre dependeria de Sérgio. Crons já desabilitados permanecem apenas inventariados, sem reativação proposta.

## Decisões da semana

1. **Diagnosticar autenticidade da saúde técnica, sem reinício:** responsável sugerido **Matias**, até **20/10, 17:00 BRT**. Critério: registrar status funcional dos três perfis em conflito, resultado da pendência de atualização de fonte, identificação do fluxo OAuth do Elias e verificação de replay Marketing/Natália, com evidência de entrega ou falha; nenhuma alteração de infraestrutura sem autorização de Sérgio.
2. **Deliberar o mapa aprovado da frota e fallback:** responsável **Sérgio** (levantamento read-only por Matias), até **22/10, 17:00 BRT**. Critério: registrar decisão explícita para sete primários divergentes, escopo/modelo de Melia, 13 fallbacks e retry Elias; incluir teste de elegibilidade do fallback por provider/modelo antes de aprovar eventual aplicação. Esta revisão não efetua alteração.
3. **Obter prova de operação e aceite, priorizando falhas pendentes:** responsáveis sugeridos **Matias + Rian** (mensais) e **gestores humanos de RH/Comercial/Marketing ou Secretaria** (amostra de artefatos), coordenação Cona, até **23/10, 17:00 BRT**. Critério: teste não destrutivo documentado dos mensais Rian antes de 01/11 e pelo menos dois artefatos de rotinas prioritárias com fonte, destinatário, resultado e aceite/ajuste do gestor; só então qualificar valor. Envolvimento de Elias em e-mail, se necessário, cabe exclusivamente a Elias.

**Deferido:** novos agentes, reativar legados, encerramento ou adormecimento automático, alterações de modelos/infraestrutura, afirmações de ROI. Prazos são sugestões, sem bloqueios de calendário.

## Pendências anteriores

- Revisão [[2026-10-12 - Governança Semanal]] propôs checagem de gateways/update até 12/10: snapshot atual é melhor (13 PIDs presentes), mas `profile list` ainda conflita em três perfis e CLI reporta source update incompleto. **Matias**, revisão proposta 20/10; conclusão não comprovada.
- Deliberação de modelos/Melia até 14/10: primários e fallback permanecem divergentes da política atual; nenhuma aprovação foi encontrada na coleta. **Sérgio**, proposta de revisão 22/10. Não interpretar silêncio como decisão.
- Aceite de artefatos e mensais Rian até 16/10: os dois últimos resultados mensais ainda mostram erro de 01/10; nenhum aceite humano nas fontes consultadas. **Matias e gestores humanos**, proposta de revisão 23/10.

## Cobertura e limitações

- Janela técnica completa dos sete dias; 13 YAMLs de IA lidos apenas para primário, URL-base, fallback e retries; `thiagoribeiro` excluído. O enunciado dizia “12 agentes”; inventário lista **13** incluindo Melia, portanto contagens identificam essa diferença. Não fizemos smoke test real do fallback ou dos canais; PID e status conectado não demonstram resposta a usuário.
- Não foram consultados calendário retrospectivo nem horizonte de 1–2 semanas, inbox de tarefas, e-mails, billing externo, saídas integrais dos 52 crons, registros de aceite de gestores ou logs completos de cada incidente. A capacidade da semana não está estabelecida; esta é revisão de governança, não revisão pessoal completa. **0 aceites encontrados nas fontes ≠ 0 valor no negócio**: valor aguardando validação humana. Custo real desconhecido.
- Já há mais de quatro relatórios anteriores na pasta: fase inaugural de quatro semanas transcorreu; usa-se semáforo qualitativo por insuficiência de evidência para nota precisa, não por afirmar que ainda estamos nas primeiras quatro execuções. Nenhum modelo, provider, permissão, cron, gateway, integração ou configuração foi alterado; somente este relatório foi criado.
