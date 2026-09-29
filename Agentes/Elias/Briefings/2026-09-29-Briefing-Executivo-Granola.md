# Resumo executivo — 29/09/2026

## Reuniões do dia

### 10:43 — Apuração de impostos, erros de notas canceladas e evolução do SPED com Anderson
- **Classificação:** reunião real, capturada por Sergio e com conteúdo operacional da **Conamore**, em interação com a MWA.
- **Participação registrada pelo Granola:** Sergio Ladeira. O resumo do Granola também identifica Alexandre Cunha, Anderson, Jaqueline e Juliana Sanches pela MWA; a presença individual não pôde ser validada na transcrição.
- **Principais assuntos:** erro fiscal causado pela importação de nota cancelada como ativa; conferência incompleta antes da emissão da guia de ICMS; atraso recorrente na entrega das guias; riscos das planilhas manuais; divergências de saldos de PIS/COFINS; teste do SPED Fiscal gerado pelo ERP da Conamore.
- **Escopo registrado:** discussão do SPED referente à SSL/lucro real; lojas físicas do Simples Nacional não incluídas nesse escopo.

> **Rastreabilidade:** fatos abaixo foram extraídos do resumo estruturado do Granola. A transcrição literal não ficou disponível porque o plano retornou: “Transcripts are only available to paid Granola tiers”.

## Decisões e encaminhamentos — fatos extraídos
- Fixado o **dia 15 de cada mês** como prazo de entrega das guias de impostos, sem exceção; Jaqueline deve registrar o prazo em agenda.
- A MWA deve eliminar o copiar/colar manual: Alexandre Cunha avaliará com Anderson, Jaqueline, Zé e TI uma saída automatizada da planilha diretamente do SCI.
- A **fonte da verdade fiscal será o SCI**, e o processo deverá ser documentado para não depender de pessoas específicas.
- A Conamore deverá gerar o **SPED de agosto** e enviá-lo à MWA; a MWA importará o arquivo no SCI, fará a auditoria e devolverá as críticas.
- Sergio enviará as planilhas de PIS/COFINS a Anderson, que investigará por que o saldo final de um mês não coincide com o saldo inicial do mês seguinte.
- A causa raiz da divergência de PIS/COFINS **ainda não foi confirmada**.

## Pendências prioritárias

| Prioridade | Pendência | Responsável | Prazo | Sugestão para amanhã — Elias |
|---|---|---|---|---|
| **P0 — fiscal/compliance** | Enviar a Anderson as planilhas de PIS/COFINS com as divergências identificadas | Sergio | Não registrado | **Manhã, 20 min:** separar os arquivos, marcar os meses/linhas divergentes e solicitar retorno com causa raiz e correção proposta. |
| **P0 — fiscal/compliance** | Gerar e enviar à MWA o SPED de agosto para auditoria no SCI | Conamore; responsável individual não registrado | Não registrado | **Manhã, 60–90 min:** validar no ERP a competência e o escopo SSL/lucro real, gerar o arquivo e fazer checagem técnica antes do envio. |
| **P1 — controle fiscal** | Garantir a entrega mensal das guias até o dia 15 e impedir emissão antes do término da conferência | Jaqueline e Anderson | Dia 15 de cada mês | **Início da tarde, 20 min:** obter da MWA confirmação formal do fluxo, pontos de conferência e responsáveis. |
| **P1 — processo/automação** | Avaliar e automatizar a planilha de fechamento diretamente a partir do SCI | Alexandre Cunha, com Anderson, Jaqueline, Zé e TI da MWA | Não registrado | **Início da tarde, 45 min:** pedir plano curto com solução, dono, prazo, testes e contingência até a automação entrar em produção. |
| **P1 — investigação fiscal** | Investigar a divergência dos saldos de PIS/COFINS | Anderson | Não registrado | **Após o envio das planilhas:** solicitar previsão de retorno; reservar **30 min no fim da tarde** apenas se houver diagnóstico para decisão. |
| **P2 — governança de processo** | Documentar o processo fiscal para reduzir dependência de pessoas | Responsável não registrado | Não registrado | **Fim da tarde, 30 min:** solicitar à MWA um fluxograma/checklist com fonte de dados, conferências, aprovador e evidências de fechamento. |

## Recomendação para o próximo dia — análise do Elias
1. **Primeiro, fechar os dois insumos sob controle da Conamore:** planilhas de PIS/COFINS e SPED de agosto. Sem isso, a investigação e a auditoria da MWA não avançam.
2. **Exigir controle verificável, não apenas novo prazo:** checklist de conferência, evidência de cancelamento capturada via CIEG e validação antes da guia de ICMS.
3. **Tratar o SPED como piloto controlado:** fazer backup, validar competência/schema/arquivo no ERP e envolver **Matias** se houver dúvida técnica de geração ou integração; não ampliar o escopo às lojas do Simples Nacional.
4. **Cobrar plano de automação com data e responsável:** a reunião definiu o caminho, mas não registrou prazo para eliminar a planilha manual.

## Alertas ao Sergio
- **Atenção imediata:** o risco principal é fiscal/compliance — guia emitida antes da conferência e nota cancelada tratada como ativa.
- O prazo mensal do dia 15 foi decidido, mas faltam evidência de controle, SLA de correção e prazo para a automação.
- A divergência de PIS/COFINS permanece sem causa raiz; acompanhar até haver diagnóstico documentado.
- **Camila:** não há necessidade de alinhamento imediato indicada nas notas. Vale envolver Camila apenas se a correção exigir mudança estrutural relevante, investimento ou alteração de governança.

## Fonte
- Granola, reunião `374200d8-ea1b-43d9-a889-e8d7b48f4d85`, 29/09/2026, 10:43 BRT.
- Base factual disponível: resumo estruturado e metadados; transcrição literal indisponível no plano atual.
