# Rotina diária logística — 31/10/2026

- Execução: 08:00–08:02 BRT.
- Intelipost: API online; 9/15 transportadoras ativas.
- Transportadoras ativas: Via Pajucara, Pacífico, Rápido Figueiredo, Dia e Noite, Frota Interna, Jamef, Rodonaves, Favorita e Correios Sedex.
- Oracle DEBX: sessão validada em `conamore`, usuário `TEST_PED`; consultas somente leitura. Schemas/tabelas e colunas foram descobertos antes das consultas focadas.
- Fechamento de 30/10/2026 pelo wrapper canônico: 10 NFs série 2, R$ 58.906,94, 3 unidades ativas.
- Distribuição logística do resumo: 8 Retirada/Balcão, 1 Correios, 1 Frete Valor Fixo/Frota Interna.
- NF 0014073 série 2 / shipment `100-0014073-2`: Correios, `In Transit`, 0/1 entregue, ETA 03/11/2026 23:59, último evento em 30/10 às 22:02 em transferência de Indaiatuba/SP. Sem atraso ou falta de progresso.
- NF 0014075 série 2 / shipment `100-0014075-2`: CODTRA 29205/Frota Interna; Intelipost retornou pedido desconhecido. Tratado como não rastreável pela regra da frota interna, sem classificar como extravio.
- Fila `TEST_PED.I_FILA_INTELIPOST`: 2 registros nos últimos 7 dias, ambos em 28/10, mensagem de falha de cotação. Não há erro novo em 30/10–31/10.
- Criticidade real nova: zero.
- Regra aplicada: `PDV_STATUS='X'` foi interpretado como expedido; não usado como cancelamento nem como explicação para ausência de shipment order.
- Conclusão: operação normal; monitorar NF 0014073 até ETA e a Frota Interna fora do tracking Intelipost.
