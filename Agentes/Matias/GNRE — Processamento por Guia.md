# GNRE — Processamento por Guia

## Objetivo e corte

O job Hermes `13b0904ff094` executa `gnre_production_watchdog.py` a cada cinco minutos das 05:00 às 19:55 BRT. O watchdog seleciona `production_automatic.py` até 15/11/2026 23:59 BRT e `production_per_guide.py` a partir de 16/11/2026 00:00 BRT. Antes do primeiro disparo útil (05:00), confirmar teste e revisar este documento. Não executar o novo script sem `--dry-run` fora da janela de produção.

## Fluxo

1. Sincronizar XMLs do SMB para inbox local sem alterar originais. `--dry-run` só lê inbox local e histórico; não sincroniza nem envia.
2. Conferir no SQLite se o lote original ou um derivado legado já foi transmitido/reservado. Um histórico `SENDING`/`UNCERTAIN` bloqueia toda divisão dessa origem; não limpar reserva, nem dividir retroativamente o lote de 13/11.
3. Ignorar origens históricas anteriores a 16/11/2026 para novos envios. Dividir fonte elegível em um XML derivado determinístico por guia; validar cada um pelo XSD oficial separadamente e preservar fonte intacta. Falha de uma guia não impede as demais.
4. Preparar AL/BA/MS e normalizar espaços por guia. Para AL/100102, resolver chave NF-e no Oracle quando necessário; para BA, usar campo extra 86. Revisar novamente XSD, prazo e identidade de negócio.
5. Persistir identidade estável (emitente, UF, receita, tipo e documento de origem do guia original) e marcar `INCERTA` **antes** da chamada fiscal `send` do cliente assistido. Nunca repetir automaticamente `send`; máximo de dois por execução. O cliente assistido mantém a reserva por hash e chave semântica.
6. Com recibo fiscal, consultar no máximo um recibo por execução. `402` com único status `0` = `CONCLUIDA` (guia aprovada; pagamento não comprovado). Status provisório permanece `EM_PROCESSAMENTO`. Rejeição final requer ação humana, não retransmissão automática.
7. Sem recibo e envio incerto, consultar somente por documento de origem via `GnreLoteRecepcaoConsulta` e `GnreResultadoLoteConsulta`, com mTLS verificado. O recibo de **consulta** é guardado separadamente do recibo **fiscal**. Conferir UF, CNPJ do emitente, tipo e número do documento. Retorno `701`, timeout e ausência de guia são inconclusivos; não autorizam reenvio. No máximo uma consulta por execução.
8. Atualizar atomica e privadamente (`0600`) `runtime/production/guide-status.txt` a cada execução. Inclui UF, arquivo de origem, índice, etapa, estado e motivo sem documento fiscal integral. `PRONTA` significa validada para envio, `CONCLUIDA` significa aprovação GNRE e **não** pagamento. Lotes antigos incertos aparecem como legados bloqueados para conciliação humana; lotes antigos já resolvidos não poluem a lista. Alertas de transições novas são deduplicados em `runtime/production/per-guide-events.json`.

## Verificações e contenção

- Suíte offline: `TMPDIR=$HOME/.hermes/profiles/matias/cache/scratch /usr/bin/env -u PYTHONPATH .venv/bin/python -m unittest discover -s tests -q` no projeto GNRE. Testes usam SQLite e XML temporários; mocks nunca transmitem lotes reais.
- Simulação local de leitura: `TMPDIR=$HOME/.hermes/profiles/matias/cache/scratch /usr/bin/env -u PYTHONPATH .venv/bin/python scripts/production_per_guide.py --dry-run`. Não altera DB, XMLs derivados nem relatório de produção.
- A trava compartilhada é `runtime/production/automatic.lock`. O envio e consulta reais são delegados a `production_assisted.py` e só devem ser executados pelo agendador após o corte e os testes.
- Se houver problema na implantação, desativar o agendamento GNRE e avaliar antes de reverter: o fluxo antigo agrupa guias e pode reencaminhar um lote que já foi dividido. Não alterar transmissão `UNCERTAIN` para permitir reenvio. Qualquer alteração de produção deve ser comunicada.

## Validação antes da virada

Em 14/11/2026, o teste offline de divisão do XML histórico de cinco guias produziu cinco XMLs válidos (MG, BA, MG, SC, RS) no diretório temporário, sem transmissão. O guard de legado identificou o lote `UNCERTAIN` de 13/11 e proibiu retransmissão. O dry-run do inbox real mostrou 24 linhas de guias de lotes legados incertos e nenhum novo envio elegível. A suíte completa passou em 141 testes. Esses resultados são simulação e **não** comprovam execução real da primeira janela de segunda-feira nem pagamento fiscal.
