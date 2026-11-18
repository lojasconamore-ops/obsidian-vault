# Rotina diária de logística — 2026-11-18

## Execução
- Referência: NFs emitidas em 17/11/2026; horários BRT.
- Oracle: sessão validada em `conamore`, usuário `TEST_PED`, 08:02 BRT.
- Regra aplicada: `PDV_STATUS = 'X'` interpretado como EXPEDIDO; não como cancelamento.

## Intelipost
- API online; 9/15 transportadoras ativas.
- Ativas: Via Pajuçara (30), Pacífico (75), Rápido Figueiredo (17767), Dia e Noite (3752), Frota Interna (138), Jamef (23), Rodonaves (41), Favorita (278), Correios Sedex (2).
- Contraprovas de tracking/shipment em 18/11:
  - `300-0006047-2` (Correios): Criado na transportadora; ETA 23/11; emissão DC-e com sucesso.
  - `500-0002824-2` (Via Pajuçara): em trânsito, saída de Campinas às 02:30 de 18/11; ETA 19/11.
  - `100-0014420-2` (Jamef): em trânsito, transferência às 04:53 de 18/11; ETA 26/11; 2 volumes, ambos em trânsito.
- Não houve atraso aberto, extravio, avaria ou falha de entrega comprovados nos shipments verificados.

## Oracle/DEBX — consolidação
- 89 NFs, faturamento R$ 238.300,54, frete R$ 2.194,34, 4/5 unidades ativas.
- 76/89 NFs com cotação; CIF 67, custo real de frete R$ 3.253,71, 5,1% do faturamento CIF (meta <5%).
- Fila `TEST_PED.I_FILA_INTELIPOST`: 0 registros desde 10/11 e nenhum em 17/11; silêncio isolado não foi tratado como integração parada porque os shipments atuais foram criados e possuem eventos.
- ACL statuses desde 10/11: A=23, D=1, F=6, L=1, P=1, X=885. O D (`PDV 0130246`) usa CODTRA 29205 (Frota Interna), portanto não é rastreável via Intelipost e não é extravio automático. O L (`129941A`) não tem transportadora; requer auditoria operacional, mas não foi classificado como criticidade Intelipost.

## Recomendações
- Monitorar o custo de frete CIF de 5,1%, acima da meta em 0,1 p.p.; revisar as 42 NFs CIF acima de 5%.
- Manter acompanhamento de `300-0006047-2` até surgir primeiro evento postal; ETA ainda dentro do prazo.
- Não abrir incidente de integração nem repetir alertas históricos: fila zerada, mas houve geração recente de shipments e eventos válidos.
