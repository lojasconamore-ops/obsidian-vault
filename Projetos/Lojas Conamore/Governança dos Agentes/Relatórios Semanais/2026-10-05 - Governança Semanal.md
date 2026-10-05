# Revisão Semanal de Governança — 2026-10-05

**Janela exata:** 2026-09-28 05:00:14.501206 a 2026-10-05 05:00:14.501206 — America/Sao_Paulo (BRT).  
**Horizonte proposto:** 05 a 11/10/2026. **Responsáveis:** Sérgio Ladeira e Cona.  
**Fontes:** coleta read-only anexada; releitura seletiva dos 12 YAMLs de configuração, relatórios de 14 e 21/09, conferência de PIDs/systemd. Sem alteração operacional.

## Resumo executivo

**Conclusão primeiro: governança 🔴, operação 🟡.** Há atividade técnica relevante, mas **valor aguardando validação humana** em todos os fluxos; a configuração da frota continua fora da política, duas automações mensais do Rian falharam por falta de `oracledb`, e três jobs semanais guardam erro de autenticação da execução de 28/09. A revisão atual não corrige nada automaticamente.

- **12 agentes de IA**; `thiagoribeiro` é perfil humano reservado, excluído. **6/12 com sessões** na base de seu próprio perfil; **208 sessões**, 2.191 chamadas de API, 3.384 chamadas de ferramenta e 210 `user_messages` técnicos. **10.757.605 tokens de entrada e 1.195.849 de saída**. Execuções por crons em outros perfis não foram atribuídas artificialmente ao agente homônimo.
- **48 crons:** 35 habilitados, 13 desabilitados. Entre os habilitados, **5 guardam último status de erro/bloqueio** (governança default: 1; Marketing: 2; mensais Rian: 2). Status é do último ciclo, não prova de falha em curso; os dois mensais só voltam a rodar em 01/11.
- **Modelos ao vivo:** **9/12 primários conformes**. Divergem Cona (`gpt-6-sol`, aprovado `gpt-5.6-sol`), Flávia/marketing (`gpt-5.6-sol/openai-codex`, aprovado `deepseek-v4-pro/opencode-go`) e Tiago (`gpt-5.6-sol`, aprovado `gpt-5.6-luna`). **0/12 fallbacks conformes**: todos usam `openai-codex:gpt-5.6-luna`, em vez de `openai-codex:gpt-5.4-mini`. Elias ainda tem `api_max_retries=3` (padrão 1). Bases URL dos providers são coerentes com os providers efetivamente configurados. Não se alterou configuração.
- **Gateways:** 11 PIDs do snapshot seguem presentes; o PID da Fabrícia está ausente e seu Telegram consta desconectado desde 09/07. O campo `gateway_state` da coleta dizia `running` para ela, mas `hermes profile list` no mesmo pré-run dizia `stopped`; conferir serviço com Matias. Nos demais, Telegram constava conectado no snapshot, sem teste de entrega ponta a ponta. `profile list` também chamou Adrian, Maria, Matias e Tiago de `stopped`, embora os respectivos PIDs persistam e unidades systemd ativas tenham sido vistas; **divergência de instrumentos**, não declarar indisponibilidade desses quatro sem teste.
- **Custo:** banco local registra US$ 0; **custo real desconhecido**, não equivale a gratuidade. Sem validação humana/indicador de negócio, não há economia, qualidade ou impacto confirmados. As quatro primeiras revisões já passaram; o semáforo segue qualitativo, sem nota artificial.

### Semáforo

- 🟢 **Verdes técnicos:** rotinas diárias recentes de Elias, Natália e Marketing com último status `ok`; cron semanal do Tiago concluiu `ok` em 28/09; 11 PIDs observados. Isto não atesta entrega útil.
- 🟡 **Amarelos:** atividade desigual, seis perfis sem sessões próprias; custos e valor desconhecidos; rede Telegram com falhas transitórias nos logs de 04–05/10 seguidas de recuperação, sem prova de outage atual; API server do default desconectado desde julho sem necessidade atual comprovada; `profile list` contradiz PIDs/systemd.
- 🔴 **Vermelhos de governança/confiabilidade:** 3 primários fora do mapa, 12 fallbacks divergentes e retry do Elias fora do padrão; Fabrícia sem Telegram/PID; falhas mensais de Rian em 01/10 (`ModuleNotFoundError: oracledb`); três jobs de 28/09 com último erro de autenticação (default e dois Marketing). O aviso de atualização Hermes inacabada apareceu no comando read-only de 05/10; verificar estado e risco de módulos mistos antes de qualquer intervenção.

## Saúde da frota e atividade observada

| Agente | Primário ao vivo / status | Sessões próprias em 7 dias | Crons / observação | Valor |
|---|---|---:|---|---|
| Cona/default | `openai-codex:gpt-6-sol` — divergente; PID presente | 32 | Governança semanal: último erro 28/09 por refresh de autenticação; rotina diária de Elias/Tiago/Tobias roda neste perfil | valor aguardando validação humana |
| Adrian | `openai-codex:gpt-5.6-luna` — conforme; PID presente, `profile list` diz parado | 0 | Nenhum cron | valor aguardando validação humana |
| Bianco | `openai-codex:gpt-5.6-luna` — conforme; PID presente | 0 | Dois crons desabilitados | valor aguardando validação humana |
| Elias | `openai-codex:gpt-5.6-sol` — conforme; PID presente | 20 | Três rotinas ativas com `ok`; retries fora da política | valor aguardando validação humana |
| Fabrícia | `opencode-go:deepseek-v4-pro` — conforme; PID ausente/Telegram desconectado | 0 | Sem crons próprios | valor aguardando validação humana |
| Maria | `openai-codex:gpt-5.6-sol` — conforme; PID presente, `profile list` diz parada | 0 | Três rotinas ativas com `ok`; solicitar folha no 4º dia útil requer confirmar disparo/semântica: último `ok` em domingo 04/10 não prova mensagem enviada | valor aguardando validação humana |
| Flávia/marketing | `openai-codex:gpt-5.6-sol` — divergente; PID presente | 49 | 11 habilitados, 1 desabilitado; dois semanais bloqueados em 28/09, outros diários com `ok` recente | valor aguardando validação humana |
| Matias | `openai-codex:gpt-5.6-sol` — conforme; PID presente, `profile list` diz parado | 8 | Quatro habilitados, um desabilitado; GNRE/DUA-e com `ok` recente | valor aguardando validação humana |
| Natália | `openai-codex:gpt-5.6-luna` — conforme; PID presente | 98 | Quatro habilitados com `ok`, um desabilitado; 72 `agent_close` de subagentes e 26 `cron_complete` | valor aguardando validação humana |
| Rian | `openai-codex:gpt-5.6-luna` — conforme; PID presente | 0 | Dois diários com `ok`; dois mensais com erro em 01/10; lacuna entre cron e sessões próprias | valor aguardando validação humana |
| Tiago | `openai-codex:gpt-5.6-sol` — divergente; PID presente, `profile list` diz parado | 1 | Semanal com `ok` em 28/09; execução de 05/10 ainda futura no corte | valor aguardando validação humana |
| Tobias | `opencode-go:deepseek-v4-pro` — conforme; PID presente | 0 | Três crons próprios desabilitados; diário homônimo do default não pertence a este perfil | valor aguardando validação humana |

**Qualidade, confiabilidade e riscos:** `cron_complete`/`last_status=ok` apenas indicam conclusão técnica, sem conferência da entrega final. O snapshot de Rian registra erro de importação do driver nas duas rotinas mensais; há caminho de script e traceback, mas nenhum teste de correção. As falhas de autenticação dos três semanais são datadas de 28/09, não evidência de token atualmente inválido; conferir próximo ciclo e artefatos. Alertas de Telegram em 04–05/10 foram seguidos por mensagens de recuperação; não confundir com pane vigente. Não houve prova nesta coleta de violação de permissões, mas isso não é auditoria de segurança. Não se inspecionaram credenciais nem arquivos `.env`.

## Portfólio

Classificações **provisórias** de saúde/uso, não julgamento final de valor. `Manter` exige valor confirmado e confiabilidade; nenhum agente recebe essa classificação conclusiva nesta semana. `Adormecer` é recomendação de prioridade, **não ação executada**.

- **Melhorar:** Cona (primário/fallback, semanal em erro anterior), Elias (fallback/retries), Flávia (primário/fallback e dois semanais bloqueados), Matias (fallback e esclarecer estado), Natália (fallback e validação das entregas), Rian (mensais quebrados e lacuna de telemetria), Tiago (primário/fallback).
- **Observar:** Adrian (sem sessão própria, estado contraditório), Maria (crons `ok` sem sessão própria, estado contraditório e conferência de folha), Tobias (demanda eventual e diário do default separado).
- **Adormecer — proposta:** Bianco (sem sessão, crons próprios desligados), Fabrícia (sem sessão e Telegram/PID indisponíveis; preservar perfil e documentação).
- **Automações:** **Melhorar** — dois mensais Rian e três semanais com último erro/bloqueio; **Observar** — diários com `ok` e valor ainda não validado; **Adormecer — proposta** — 13 crons já desabilitados, sem reativação automática. **Encerrar:** nenhum item recomendado; exige decisão de Sérgio.

## Decisões da semana

1. **Política de modelos/fallback e retry:** Sérgio decide até **06/10** restaurar o mapa nos três primários divergentes, nos 12 fallbacks e no retry do Elias, ou registrar exceções expressas; Matias executa somente após autorização. **Concluído quando:** decisão documentada; se aprovada, YAMLs relidos, exceções registradas e smoke tests representativos bem-sucedidos.
2. **Confiabilidade dos fluxos falhos e estado dos gateways:** Matias diagnostica read-only até **08/10** os dois mensais de Rian, três semanais com erro de 28/09, Fabrícia e a divergência `profile list` × PIDs/systemd, incluindo aviso de update inacabado. **Concluído quando:** causas e escopo por job/perfil registrados; último ciclo/artefato ou teste controlado verificado onde permitido; plano de correção submetido a Sérgio antes de alterações.
3. **Validar utilidade e decidir prioridade:** gestores humanos das áreas validam até **09/10** ao menos um artefato recente por fluxo ativo prioritário (com aceite, correção ou sem valor); Cona consolida, Sérgio decide sobre Bianco/Fabrícia. **Concluído quando:** fonte, resultado e validador registrados, com próxima ação ou pausa explícita; custo financeiro só após billing confiável.

**Pendências anteriores:** a proposta de 21/09 para corrigir fallback/primários/retry não aparece concluída no estado ao vivo; os três semanais trazem erro de 28/09 e os mensais de Rian falharam em 01/10. Não foi localizado relatório semanal de 28/09 na pasta; ausência de relatório ou de sessão não prova ausência de trabalho/decisão. Próximo acompanhamento sugerido: 06/10 para Sérgio/Matias (configuração), 08/10 para Matias (falhas), 09/10 para gestores/Cona (aceitação). **Deferidos:** novos agentes, reativar crons legados, mudar integrações e encerrar perfis.

## Cobertura e limitações

- Retrospectiva integral de sete dias pelo script; horizonte 05–11/10 é **proposta**, não agenda confirmada. Não houve acesso a calendário executivo, inbox de tarefas, e-mails, todas as notas de compromisso, billing externo, entregas integrais ou aceite humano; compromissos e capacidade real da semana não foram reconciliados. Três decisões limitam a carga sugerida; não se reservaram horários.
- A coleta imprime `model` nulo para todos os perfis, portanto o mapa acima vem dos YAMLs lidos ao vivo (campos permitidos apenas), não do campo nulo; 12/12 fallbacks continuam `gpt-5.6-luna`. Sessões/tokens vêm dos bancos locais, mas alguns cron workers executam em outro perfil; ausência de sessão própria não prova ausência de trabalho.
- Inventário de gateway conflita internamente: Fabrícia com `running` no `gateway_state` mas `stopped` no `profile list`; o PID associado não existe. Quatro perfis também têm `profile list=stopped` apesar dos PIDs e serviços observados. O comando `hermes profile list` tentado nesta revisão parou no aviso de atualização e expirou, sem novo inventário completo; consulta read-only ao systemd/PIDs não valida entrega Telegram. Escalonar diagnóstico sem alterar infraestrutura.
- US$ 0 reportado no banco local: custo **desconhecido**. Sem artefato validado ou indicador, para todos os agentes: **valor aguardando validação humana**. Não inferir qualidade, economia, sucesso comercial ou impacto a partir de volume técnico.
- Nenhum modelo, provider, permissão, gateway, cron, integração ou configuração foi modificado; só esta nota autorizada foi escrita. Nenhuma consulta Oracle/DEBX nem acesso a e-mail foi realizado.
