# Governança dos Agentes de IA | Lojas Conamore

## Objetivo

Garantir que os agentes gerem resultado empresarial confiável sem aumentar desnecessariamente a complexidade, o risco ou o custo da operação.

> Governança não é reunião sobre tecnologia. É decisão sobre valor, confiabilidade, risco e prioridade.

## Responsáveis

- **Sérgio Ladeira:** aprova prioridades estratégicas, mudanças de autoridade, modelos, providers, infraestrutura e ações de alto risco.
- **Cona / DigitalCEO:** coleta evidências, consolida o relatório, questiona desvios, propõe decisões e acompanha os responsáveis.
- **Matias / TI:** valida confiabilidade técnica quando houver incidente, integração, gateway, segurança ou infraestrutura.
- **Gestor humano da área:** valida se a entrega do agente teve valor operacional real.
- **Agentes:** fornecem fatos e evidências; não aprovam sozinhos o próprio valor.

## Cadência

### Semanal — segunda-feira, 05:00 BRT

Relatório automático com janela dos sete dias anteriores:

1. saúde da frota;
2. uso e entregas;
3. qualidade e falhas;
4. riscos e permissões;
5. classificação do portfólio;
6. até três decisões propostas para a semana.

### Mensal

Revisão de retorno, processos automatizados, horas poupadas, impacto financeiro, custo/consumo, confiabilidade e necessidade de manter, ampliar, adormecer ou encerrar agentes e automações.

### Por incidente

Revisão imediata em caso de credenciais expostas, acesso indevido, envio externo incorreto, alteração não autorizada, erro financeiro material, uso da fonte errada ou declaração falsa de conclusão.

## Scorecard inicial

Durante as quatro primeiras semanas, usar semáforo em vez de uma nota artificialmente precisa.

| Critério | Verde | Amarelo | Vermelho |
|---|---|---|---|
| Uso | Usado em processo real | Uso eventual | Sem uso |
| Valor | Gerou ação, economia ou decisão confirmada | Entrega consultiva | Nenhum resultado identificado |
| Qualidade | Aceito sem correção relevante | Precisou ajustes | Erro material ou fonte incorreta |
| Confiabilidade | Entregou corretamente | Falha recuperável | Não entregou ou ação não confirmada |
| Autonomia | Concluiu ponta a ponta | Exigiu intervenção parcial | Sérgio precisou conduzir tudo |
| Risco | Dentro das regras | Exceção controlada | Violação de permissão, segurança ou escopo |
| Custo | Compatível com o valor | Precisa análise | Custo sem benefício demonstrado |

## Classificação do portfólio

- **Manter:** entrega valor confirmado e opera de forma confiável.
- **Melhorar:** tem valor, mas precisa de correção específica.
- **Observar:** pouco uso ou resultado ainda não demonstrado.
- **Adormecer:** não justifica operação permanente; preservar perfil e documentação.
- **Encerrar:** duplicado, obsoleto ou sem propósito; exige autorização do Sérgio.

## Regras de decisão

1. **Novo agente ou integração:** precisa de processo, proprietário humano, fonte, permissões, resultado esperado, indicador, teste e reversão.
2. **Três semanas sem valor confirmado:** entra em revisão para adormecimento.
3. **Erro crítico:** pausa o fluxo afetado até identificar causa, corrigir, testar e autorizar retorno.
4. **Evidência obrigatória:** entregas relevantes devem trazer consulta, arquivo, ID, resposta da API, fonte ou confirmação equivalente.
5. **Máximo de três prioridades semanais:** toda decisão deve ter responsável, prazo e critério de conclusão.
6. **Sem mudanças automáticas:** o relatório recomenda; não altera modelos, providers, permissões, infraestrutura nem exclui agentes.
7. **Fonte ao vivo prevalece:** configurações, serviços e logs atuais prevalecem sobre memória, documentação antiga ou resposta anterior.

## Limitações dos dados

- Sessão ou mensagem contabilizada mede atividade, não valor.
- Custo pode aparecer como zero ou desconhecido quando o provider não fornece cobrança mensurável.
- Falha histórica em log ou cron não significa falha atual; conferir data e estado vigente.
- Valor, qualidade e impacto financeiro exigem validação humana ou indicador objetivo.

## Artefatos

- [[Template - Revisão Semanal de Governança]]
- Pasta de relatórios: `Relatórios Semanais/`
- Coletor técnico: `~/.hermes/scripts/governanca-agentes-coleta.py`
- Relatório entregue ao Sérgio pelo Telegram toda segunda-feira às 05:00 BRT.

## Fase inicial

As quatro primeiras revisões formam a linha de base. Nesse período, o objetivo é descobrir quais dados são confiáveis e quais agentes/processos realmente produzem valor antes de automatizar decisões ou criar notas numéricas.
