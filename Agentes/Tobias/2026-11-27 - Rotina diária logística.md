# Rotina diária logística — 27/11/2026

## Status da API
- Intelipost online, 0,3 ms.
- 9/15 transportadoras ativas.
- Transportadoras ativas: Via Pajuçara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita e Correios Sedex.

## Oracle/DEBX
- Sessão validada no serviço `conamore`, usuário `TEST_PED`; consultas somente leitura.
- Relatório gerencial de 26/11: 73 NFs, R$ 161.091,58, frete R$ 1.295,08.
- Regra aplicada: `PDV_STATUS = 'X'` significa EXPEDIDO; não foi usado como cancelamento.
- Fila `TEST_PED.I_FILA_INTELIPOST`: 0 registros nos últimos 3 dias.
- ACL últimos 7 dias: 603 X, 18 A, 3 F, 2 D e 2 G. Os quatro D/G têm `PDV_CODTRA=29205` (frota interna), portanto não são rastreáveis via Intelipost; não há evidência de extravio.
- NFs recentes com transportadoras existem nos schemas MATRIZ, ACL, GCL e BRG; ausência de `SAI_DATSAI` nas linhas consultadas não foi usada isoladamente para classificar criticidade.

## Alertas confirmados
1. **🔴 NF 0014318 — shipment `100-0014318-2` — Via Pajuçara — Ipanema/MG**
   - Despacho: 12/11 às 10:00 BRT.
   - Previsão: 25/11 às 23:59 BRT.
   - Status atual: `Label Created`, 0/1 entregues.
   - Último evento: etiqueta criada em 12/11 às 10:04; sem trânsito posterior.
   - Classificação: pendência crítica de expedição/coleta, atraso aberto de 2 dias.

2. **🔴 NF 0006002 — shipment `300-0006002-2` — Via Pajuçara — Palmas/PR**
   - Despacho: 12/11 às 12:30 BRT.
   - Previsão: 23/11 às 23:59 BRT.
   - Status atual: `To Be Delivered`, 0/1 entregues.
   - Último evento: saiu para entrega em 24/11 às 07:57; sem confirmação de entrega até 27/11 08:01 BRT.
   - Classificação: atraso aberto / falha de última milha; não é extravio confirmado.

## Amostras sem alerta
- `500-0002798-2`: 2/2 entregues em 16/11.
- `700-0000722-2`: entregue em 14/11.
- `100-0014307-2`: Correios entregue em 16/11 antes da previsão.
- `300-0006006-2`: Correios entregue em 14/11 antes da previsão.
- `300-0006092-2`, `100-0014575-2`, `500-0002872-2` e `700-0001031-2`: despachados em 26/11, dentro da janela prevista.

## Recomendações
- Acionar imediatamente a Via Pajuçara para localizar e concluir as NFs 0014318 e 0006002; registrar protocolo.
- Não abrir sinistro de extravio sem evento objetivo.
- Manter monitoramento da fila Intelipost: silêncio de 3 dias é alerta de integração, mas não prova falha; correlacionar com os shipments atuais.
