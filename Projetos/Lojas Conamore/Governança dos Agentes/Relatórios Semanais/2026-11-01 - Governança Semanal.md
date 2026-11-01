# Revisão Semanal de Governança — 2026-11-01

**Janela exata:** 2026-10-25T08:37:43.807442-03:00 a 2026-11-01T08:37:43.807442-03:00 — America/Sao_Paulo. **Horizonte proposto:** 02–08/11/2026 (não reservado em calendário). **Fonte:** coleta read-only pré-run de 01/11 08:37, inspeção dos campos de modelo/fallback/retries dos YAMLs ao vivo e revisão anterior [[2026-10-19 - Governança Semanal]]. Nenhuma configuração ou automação alterada.

## Resumo executivo

**Conclusão: 🟡 frota conectada, 🔴 confiança na entrega ainda insuficiente.** Os 13 agentes de IA têm gateway `running` e Telegram `connected` no snapshot, mas isso não comprova resposta funcional nem qualidade das entregas. **236 sessões em sete perfis com sessões contabilizadas, 2.182 chamadas de API e 3.168 chamadas de ferramentas** são atividade técnica, não impacto: **valor aguardando validação humana** para todos. Os seis perfis sem sessões na base respectiva não são prova de ausência de trabalho: alguns crons desses perfis constam com `ok` e jobs com o mesmo nome existem no perfil default. Custo real **desconhecido**; US$ 0 no ledger não prova gratuidade.

**Modelo registrado:** 13/13 primários nos YAMLs correspondem ao padrão aprovado por Sérgio em 01/11 (8 `gpt-6-sol/openai-codex`, 5 `deepseek-v4-pro/opencode-go`), com URLs-base coerentes. Todos os 13 registram fallback `gpt-5.6-luna/openai-codex`; elegibilidade e resposta efetiva não foram testadas. Elias está com `api_max_retries: 3`, distinto da orientação de 1 com fallback. Sessões cron recentes de Elias e Tobias usam `gpt-5.6-luna`, embora seus primários registrados sejam respectivamente `gpt-6-sol` e `deepseek-v4-pro`: verificar override/fixação/failover antes de concluir desvio de configuração ou causa. Natália tem sessões de **subagentes** `gpt-5.6-sol`, que não definem seu primário. Não houve troca de modelo nesta revisão.

### Semáforo qualitativo

- 🟢 **Sinal técnico:** 13/13 gateways e Telegram conectados na coleta; relatórios diários e mensais de Rian com último `ok` (mensais em 01/11), assim como crons recentes de áreas ativas. Isto não equivale a aceite.
- 🟡 **A comprovar:** modelo efetivamente usado nos cron jobs de Elias/Tobias; fallback/entitlement, faturamento, entregas e aceite dos gestores. Os jobs diários no default não são atribuíveis automaticamente ao perfil homônimo. A revisão semanal anterior (26/10) falhou por gateway em `update_paused`; próximo agendamento em 02/11, sem prova de recuperação daquela execução.
- 🔴 **Risco de entrega a investigar, não indisponibilidade comprovada:** log de Matias em 01/11 08:17 registra descarte de mensagem Telegram recebida por falta de handler; gateway reiniciou às 08:18 e consta conectado no snapshot, mas **não houve teste de recepção posterior**. Elias tem erros de refresh OAuth 400 até 08:36 em 01/11; fluxo e impacto não identificados. Marketing registrou CDP/porta 9222 indisponível e tentativas de reconexão às 08:03, embora cron de consentimento GA4 indique `ok`; o teste funcional pode ter ficado incompleto. Verificar evidência antes de tratar como incidente persistente.

## 1. Saúde da frota, modelos e uso

| Agente | Primário YAML (padrão 01/11) | Sessões 7d no próprio banco | Último sinal relevante | Portfólio provisório |
|---|---|---:|---|---|
| Cona/default | gpt-6-sol / openai-codex | 23 | Dois crons diários Elias/Tiago no default `ok`; governança anterior `error` 26/10 | Observar |
| Adrian | gpt-6-sol / openai-codex | 0 | Gateway conectado; aviso de unidade systemd antiga em 01/11 | Observar |
| Bianco | deepseek-v4-pro / opencode-go | 0 | Gateway conectado; dois relatórios cron desabilitados | Observar |
| Elias | gpt-6-sol / openai-codex | 21 | cron runtime gpt-5.6-luna; refresh OAuth 400; retry 3 | Melhorar |
| Fabrícia | deepseek-v4-pro / opencode-go | 0 | Gateway conectado; sem cron no perfil | Observar |
| Maria | gpt-6-sol / openai-codex | 0 | Crons RH recentes `ok` apesar de zero sessões contabilizadas | Observar |
| Flávia/marketing | gpt-6-sol / openai-codex | 58 | Crons `ok`; CDP indisponível no teste GA4 | Melhorar |
| Matias | gpt-6-sol / openai-codex | 9 | Log de mensagem recebida descartada antes de restart; crons recentes `ok` | Melhorar |
| Melia | gpt-6-sol / openai-codex | 0 | Crons ML recentes `ok`; resultado final não auditado | Observar |
| Natália | deepseek-v4-pro / opencode-go | 117 | Subagentes gpt-5.6-sol; crons comerciais `ok`; 6 transcrições antigas retidas em replay | Observar |
| Rian | deepseek-v4-pro / opencode-go | 0 | Mensais ACL/GCL `ok` em 01/11; diários `ok` em 31/10 | Observar |
| Tiago (Financeiro) | gpt-6-sol / openai-codex | 1 | Semanal no perfil `ok` em 26/10; daily no default `ok` em 01/11 | Observar |
| Tobias | deepseek-v4-pro / opencode-go | 7 | cron runtime gpt-5.6-luna; admission unverified 08:02, cron final `ok` 08:04 | Melhorar |

`thiagoribeiro` é perfil reservado humano e está fora da frota. Os campos `model` nulos do coletor não são inferência de falta de modelo: conferimos os YAMLs e a saída de `hermes profile list`. As URLs-base são Codex (`chatgpt.com/backend-api/codex`) e opencode-go (`opencode.ai/zen/go/v1`), respectivamente. Os 13 fallbacks são Codex/gpt-5.6-luna. A indicação de runtime nos registros de sessão pode refletir fixação de cron, fallback ou execução histórica; sem log de chamada de API não se atribui causa.

## 2. Atividade, valor e confiabilidade

- **Atividade observada:** rotinas de agenda/Granola/ShinePhone (Elias), marketing (GA4/Ads), infraestrutura (Matias), relatórios comerciais (Natália), logística (Tobias), financeiro (Tiago) e jobs de RH/ML/loja física com status no scheduler. Esses títulos e status não validam conteúdo nem destinatário.
- **Valor confirmado nesta cobertura:** nenhum aceite humano ou indicador objetivo foi anexado à coleta; **valor aguardando validação humana**. Nenhuma conclusão sobre economia, receita, qualidade final ou horas poupadas. Sem aceites na coleta ≠ ausência de valor na empresa.
- **Confiabilidade:** gateway conectado ≠ bot recebendo mensagens (exemplo Matias). Job `ok` ≠ exame funcional concluído (exemplo Marketing/CDP). O job `tobias-daily` registrou resultado de admissão não verificado por desconexão às 08:02 em 01/11 e, depois, `last_status=ok` às 08:04; reconciliar sessão/entrega antes de alegar perda ou duplicação. `FOREIGN KEY constraint failed` no replay de Elias/Natália em 01/11 refere-se a mensagens/transcrições antigas retidas, sem evidência de perda de entrega atual. OAuth Elias 08:36 permanece sem escopo funcional determinado.
- **Risco de dados:** mensal Rian registrou `ok` em 01/11, superando o erro histórico da revisão 19/10; não auditar resultado de venda física como PED. Nenhuma consulta Oracle foi feita nesta revisão. Uma janela Oracle fora de 08:00–18:00 BRT não basta para declarar indisponibilidade indevida.
- **Segurança:** permissões não auditadas ponta a ponta, nenhum segredo consultado; não há prova de violação. Modelo/provedor não foi alterado. Somente Sérgio delibera eventual ajuste.

## Portfólio

- **Melhorar (4):** Elias (runtime/retry/OAuth), Flávia/marketing (consentimento GA4 depende de CDP funcional), Matias (teste de recepção Telegram e logs), Tobias (runtime e reconciliação da admissão). A classificação indica investigação específica, **não valor já comprovado**.
- **Observar (9):** Cona, Adrian, Bianco, Fabrícia, Maria, Melia, Natália, Rian, Tiago. Evidência insuficiente para julgar valor; perfis com zero sessões podem ter automações em outros contextos. Não há agente qualificado como **Manter** por falta de aceite humano e confirmação ponta a ponta; não propor **Adormecer** ou **Encerrar** com esta coleta isolada.
- **Automações específicas:** governança semanal default — **Melhorar** (erro 26/10, execução presente não repara histórico); consentimento GA4 08h — **Melhorar** (CDP indisponível no log de 01/11); `tobias-daily` — **Melhorar** (reconciliar execução/entrega); mensais ACL/GCL Rian — **Observar** (último `ok` em 01/11, validar artefato); crons legados já desabilitados — **Adormecer** apenas como estado operacional atual, sem proposta de reativação ou exclusão. Nenhum encerramento autorizado.

## Decisões da semana

1. **Verificar recebimento e entregas dos fluxos afetados**, sem mudança operacional nesta revisão. **Responsável sugerido:** Matias, com donos de Elias/Marketing/Tobias. **Prazo proposto:** 02/11, 17h BRT. **Concluído quando:** registrar teste read-only/funcional de recebimento do Telegram Matias após 08:18, escopo do OAuth Elias, evidência do teste GA4 com CDP e reconciliação do `tobias-daily` 01/11; registrar se houve ou não entrega, sem exposição de credenciais. Se houver incidente material, escalar ao Sérgio antes de intervenção.
2. **Reconciliar execução efetiva versus modelos aprovados.** **Responsável sugerido:** Matias; deliberação exclusiva de Sérgio. **Prazo proposto:** 04/11, 17h BRT. **Concluído quando:** documentar job-level overrides, sessão e linha de API de Elias/Tobias (e amostra de Natália), retries Elias e smoke test autorizado da elegibilidade `gpt-5.6-luna` por provider, distinguindo fixação de fallback. Sem alteração automática.
3. **Obter aceite operacional das entregas prioritárias.** **Responsável sugerido:** Cona para coordenação e gestores humanos das áreas de Marketing, Comercial e Logística para validação. **Prazo proposto:** 06/11, 17h BRT. **Concluído quando:** ao menos um artefato de cada fluxo selecionado tiver fonte, período, destinatário, correções necessárias e aceite/rejeição explícito; caso contrário manter “valor aguardando validação humana”.

**Deferido:** expansão da frota, reativação de legados, cálculo de ROI, mudança de modelo/provedor, alteração de crons/infra, adormecimento ou encerramento de agentes. Prazos são propostas, não compromissos confirmados em calendário.

## Pendências anteriores

- Revisão [[2026-10-19 - Governança Semanal]] solicitou diagnóstico de OAuth Elias, replay e saúde dos gateways até 20/10; há novos logs de 01/11, mas não há comprovante de conclusão nessa coleta. **Matias**, reavaliar em 02/11. Silêncio não significa resolvido.
- Deliberação de modelos/fallback até 22/10: o primário **agora coincide** com o padrão expressamente aprovado em 01/11; não transportar a divergência antiga como atual. Persistem runtime cron divergente em Elias/Tobias e retry Elias. **Matias/Sérgio**, rever em 04/11.
- Mensais Rian antes de 01/11: ambos constam `ok` em 01/11 05:21; a falha antiga de dependência não é vigente no scheduler, mas o conteúdo e aceite do relatório permanecem não verificados. **Rian/gestor da área**, rever em 06/11.

## Cobertura e limitações

- Coleta do intervalo completo indicado; dados de sessões/custo por banco local, não do billing dos providers. Sete perfis com sessão contabilizada; seis sem sessão contabilizada. Falta auditoria de conteúdo completo das sessões, mensagens recebidas, artefatos de crons e confirmação externa de entrega. Uso de modelo efetivo observado apenas nas sessões listadas, não em toda chamada; fallback não testado. Custo real **desconhecido** apesar de US$ 0 nos contadores; tokens não equivalem a custo.
- Logs listados são amostras recentes: timestamps conferidos contra a janela; estado no snapshot conferido antes de inferir falha. Nenhum teste funcional posterior ao evento Matias, à falha CDP ou ao refresh OAuth foi executado aqui. Cron de governança anterior registrou `GatewayUnavailableError` em 26/10; este relatório não certifica reconciliação daquela execução.
- Não consultados: calendário pessoal retrospectivo/horizonte, captura de tarefas, e-mail (restrito ao Elias), faturamento de providers, indicadores de negócio e aceite humano. Capacidade semanal não quantificada; horizonte e datas são sugestões, sem criar bloqueios. Fonte de verdade da política de modelos: aprovação expressa de Sérgio informada no pedido em 01/11, superior ao documento de 19/10. Existem mais de quatro relatórios históricos; semáforo é qualitativo por ausência de evidência de valor, **não** por alegar que estamos nas primeiras quatro execuções. Nenhuma configuração, permissão, integração, gateway ou cron foi modificada.
