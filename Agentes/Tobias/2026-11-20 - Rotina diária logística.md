# Rotina diária de logística — 20/11/2026

## Execução
- Horário: 08:01–08:06 BRT.
- Intelipost: API online; 9/15 transportadoras ativas.
- Oracle/DEBX: leitura dos treinamentos obrigatórios realizada antes da tentativa de consulta.
- Wrapper `daily-order-check.sh --yesterday --summary`: bloqueado porque o `python3` padrão não possui `oracledb`.
- Fallback com ambiente Python que possui `oracledb`: conexão recusada pelo Oracle (`DPY-6005`, `[Errno 111] Connection refused`). Não houve consulta de dados no DEBX nesta execução; não extrapolar números.
- Regra aplicada: `PDV_STATUS='X'` significa EXPEDIDO; não foi usado para inferir cancelamento ou criticidade.

## Intelipost
- Transportadoras ativas: Via Pajuçara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita e Correios Sedex.
- Contraprovas de tracking atuais:
  - `100-0014437-2` (Correios): entregue em 19/11 às 14:18; ETA 19/11.
  - `100-0014438-2` (Correios): entregue em 19/11 às 15:22; ETA 19/11.
  - `500-0002824-2` (Via Pajuçara): entregue em 19/11 às 17:55; ETA 19/11.
  - `100-0014428-2` (Correios): em trânsito, 0/1, último evento em 19/11 às 22:28 em transferência de Indaiatuba/SP; ETA 25/11. Dentro do prazo, sem criticidade.
  - `100-0014420-2` (Jamef): 0/2 volumes entregues, último evento em 18/11 às 04:53; ETA 26/11. Sem atraso pelo prazo, mas manter acompanhamento por ausência de novo evento.
- Rechecados sem reconhecimento: `100-0014429-2`, `100-0014448-2`, `100-0014443-2`, `100-0014446-2`, `100-0014447-2`. Sem Oracle disponível, não foi possível validar SAI_DATSAI, CODTRA, fila ou expedição; não classificar como atraso/extravio.

## Conclusão
- Nenhum atraso aberto, extravio, avaria ou falha de entrega comprovado nos shipments rechecados.
- A operação rastreada está normal. O Oracle permanece bloqueado por indisponibilidade de rede/conexão; fica pendente a consolidação de NFs e da fila de integração quando o DEBX voltar.

## Recomendações
- Reexecutar a validação Oracle/DEBX e consultar `I_FILA_INTELIPOST` quando a conexão estiver disponível.
- Acompanhar `100-0014420-2` até novo evento, sem abrir incidente neste momento; ETA ainda em 26/11.
- Para NFs sem shipment order, validar separadamente SAI_DATSAI, CODTRA e fila; não usar `PDV_STATUS='X'` como explicação.
