# Conciliação Mercado Livre × DEBX/PED — 27/10/2026 07:10 BRT

Consulta em leitura à API da conta `CONAMORE_HOTELARIA`, `GET /orders/search?order.status=paid`, 22 pedidos pagos (11–26/10/2026 BRT), 14 packs/vendas; dois pedidos cancelados excluídos. Oracle `TEST_PED.F_PEDVENDA` e `F_PEDITEM`, clientes `TEST_MATRIZ.F_CDEMP`. Sessão `TEST_PED` validada. Conferidos documento/nome fiscal do comprador, valor, SKU base, quantidade física do kit e, quando presente, ID externo nas observações. Arquivo de trabalho privado: `~/.hermes/profiles/melia/cache/scratch/ml_debx_reconciliation_20261027.json`.

**Resultado:** 22 pedidos ML pagos estão representados em 13 pedidos PED (dois packs de Maria José foram digitados juntos). Valor ML de R$ 3.732,80 = valor dos 13 PED de R$ 3.732,80. Em registros sem ID externo, a correspondência é baseada em cliente, preço, produtos e quantidades — não existe chave automática garantida. PED não é venda física/faturamento/entrega.

- `0125325` ← pedido ML `2000018920797882`, R$ 101,80, lençol Solteiro.
- `0125323` ← pack `2000015484617239`, R$ 387,20, rosto e piso.
- `0125324` ← pack `2000015484617243`, R$ 686,40, banho e piso.
- `0125739` ← pack `2000015532446181`, R$ 440,00, banho, rosto e piso.
- `0125744` ← pedido `2000018995714146`, R$ 149,80, lençol Queen.
- `0126594` ← pack `2000015636763939`, R$ 149,80, lençol King com elástico.
- `0126830` ← packs `2000015659275625` e `2000015659241785`, total R$ 208,40, cliente Maria José Rêgo Caldas, toalha banho 4 peças + rosto 4 peças. Os dois IDs externos estão na observação do PED.
- `0127187` ← pack `2000015676606833`, R$ 71,60, piso 4 peças.
- `0127110` ← pack `2000015687837577`, R$ 151,80, protetor Casal 2 peças.
- `0127181` ← pack `2000015697098287`, R$ 303,20, 8 toalhas banho; faturamento fiscal do ML em nome Vinicius Pereira Caetano, mesmo nome do cadastro Oracle (o perfil ML é Villa Sabiá).
- `0127176` ← pack `2000015702461467`, R$ 799,20, cinco pedidos da TINY HOUSE PASSAUNA LTDA; 2+2+20+2+2 peças dos SKUs 19348, 17689, 16446, 19356 e 16429. Cliente **existe no Oracle** sob `07605`, embora o monitor do espelho SQL o tenha marcado não localizado (defasagem de sincronização provável; verificar).
- `0127172` ← pack `2000015710755391`, R$ 131,80, lençol Queen com elástico.
- `0127169` ← pack `2000015712895809`, R$ 151,80, protetor Casal.

**Esclarecimento do Sérgio:** os dois pacotes ML de Maria José foram inicialmente digitados juntos no PED `0126830`; depois houve uma entrada na parte errada da operação e foi feito outro pedido PED `0126879` para separá-los. **Não classificar automaticamente `0126879` como venda duplicada nem pedir seu cancelamento.** Em releitura, o cabeçalho e os itens do PED `0126830` ainda mostram as quatro toalhas de rosto SKU `18090` além das quatro de banho, e o `0126879` também mostra quatro toalhas de rosto. Portanto, para somas brutas de PED, não incluir os dois sem entender a correção contábil/operacional; confirmar com faturamento qual entrada gera NF, baixa e expedição. Os 22 pedidos ML pagos somam R$ 3.732,80; a soma bruta dos registros PED `0126830` e `0126879` adicionaria R$ 56,80 se não houver compensação em outra etapa. Nenhum registro foi modificado pela Melia.

PED `P` em alguns recentes é apenas status registrado; não afirmar faturamento ou entrega. Não houve baixa de estoque, correção de pedido nem ação no ML/DEBX durante a consulta.
