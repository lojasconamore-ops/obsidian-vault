# Intelipost no Oracle — consulta de clientes e transportadoras

## Contexto
Consulta aplicada no Oracle DEBX para cruzar pedidos com cliente e transportadora, usando a lógica já apresentada ao usuário.

## Base usada
- `TEST_PED.F_PEDVENDA`
- `TEST_PED.FI_MAG_PEDIDOS`
- `TEST_PED.SSL_CAIXA_DETALHADO_MATERIAL`

## Observações importantes
- `FI_MAG_PEDIDOS` trouxe dados de cliente/transportadora para parte dos pedidos.
- `F_PEDVENDA` contém o pedido completo, inclusive casos que não aparecem em `FI_MAG_PEDIDOS`.
- `SSL_CAIXA_DETALHADO_MATERIAL` ajudou a confirmar o cliente final e o representante/origem.
- O pedido `0106173` aparece como `TROCA - HOTELARIA` em parte do cruzamento.
- O código `29205` aparece no banco como caso problemático de integração/mapeamento e não deve ser tratado como transportadora “bonita” sem validação.

## Resultado operacional
- Pedido `0096811`:
  - cliente confirmado em `SSL_CAIXA_DETALHADO_MATERIAL`
  - transportadora não ficou consistente no cruzamento atual
- Pedidos `0102553`, `0102988`, `0103871`, `0105499`, `0106072`:
  - cliente confirmado
  - transportadora veio pelo `FI_MAG_PEDIDOS`
- Pedido `0106173`:
  - cliente confirmado
  - tratado como troca; sem transportadora confiável na visão atual

## Nota
Na próxima vez que o usuário pedir esse recorte, vale usar uma consulta que priorize:
1. `F_PEDVENDA`
2. `FI_MAG_PEDIDOS`
3. `SSL_CAIXA_DETALHADO_MATERIAL`
4. fallback explícito para `TRANSPORTADORA NÃO IDENTIFICADA`
