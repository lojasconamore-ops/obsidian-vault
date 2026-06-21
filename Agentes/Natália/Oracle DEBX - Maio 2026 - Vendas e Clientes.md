---
title: Oracle DEBX — Maio/2026 — Vendas e Clientes
tags:
  - oracle
  - debx
  - vendas
  - clientes
  - natalia
---

# Oracle DEBX — Maio/2026 — Vendas e Clientes

**Fonte:** Oracle `conamore` (`172.169.0.11:1521`) — schema `TEST_ACL`
**Usuário:** `TEST_PED`
**Janela:** 01/05/2026 a 31/05/2026
**Janela operacional do Oracle DEBX:** disponível diariamente das **08:00 às 18:00 (BRT)**

## Escopo e método
- Vendas analisadas pela tabela `TEST_ACL.F_PEDVENDA`
- Clientes analisados, no recorte com nome disponível, via `TEST_PED.FI_MAG_PEDIDOS`
- Considerei **pedidos com `PDV_STATUS = 'X'`** como vendas confirmadas no mês
- Não houve alteração de dados; consulta apenas leitura

## Resumo executivo
- **Pedidos confirmados:** 3.219
- **Faturamento total:** R$ 562.562,61
- **Ticket médio:** R$ 174,76
- **Maior pedido:** R$ 2.781,02
- **Menor pedido:** R$ 2,30
- **Desconto total informado:** R$ 4.595,15
- **Frete total informado:** R$ 23.099,64

## Leitura comercial
- O mês foi **fortemente concentrado em poucos dias de pico**, com melhor desempenho em 04/05, 05/05, 12/05, 07/05 e 13/05
- **LOADER** respondeu por **46,41%** do faturamento do mês, sugerindo um bucket operacional relevante, não necessariamente um vendedor individual
- A origem comercial ficou assim:
  - **nulo:** 2.645 pedidos / R$ 288.925,52
  - **MAG:** 554 pedidos / R$ 257.169,38
  - **GER:** 20 pedidos / R$ 16.467,71
- A condição de pagamento mais frequente foi **`000`** (2.864 pedidos / R$ 390.679,99)
- O código de forma de pagamento **`04`** concentrou o maior valor total entre as formas registradas

## Vendas por dia — destaque
- **04/05/2026:** 172 pedidos / R$ 32.735,22
- **05/05/2026:** 154 pedidos / R$ 31.035,10
- **12/05/2026:** 147 pedidos / R$ 27.115,86
- **07/05/2026:** 158 pedidos / R$ 25.154,90
- **13/05/2026:** 122 pedidos / R$ 25.118,64

## Clientes — recorte com nome disponível
- A base de clientes com nome disponível veio do cruzamento com `FI_MAG_PEDIDOS`
- **Pedidos linkados nesse recorte:** 557
- **Clientes distintos:** 535
- **Clientes com recompra no mês:** 20
- **Média de pedidos por cliente no recorte:** 1,04

### Top clientes do recorte MAG
- **guilherme beyrodt** — 3 pedidos / R$ 1.990,78
- **Ana Claudia Vicente** — 1 pedido / R$ 1.868,50
- **Daniela Silva** — 2 pedidos / R$ 1.824,84
- **FMNS Emprendimentos ltda Pousada Bicame de Pedra** — 1 pedido / R$ 1.646,41
- **Giselle Lopes** — 1 pedido / R$ 1.582,20
- **Thayany Brum** — 1 pedido / R$ 1.570,40
- **Centro de Procedimentos Hospitalar Dermac Ltda Dermac** — 1 pedido / R$ 1.560,00
- **Maria Araujo** — 2 pedidos / R$ 1.550,90
- **Marcelo Anderson de Sousa Barros** — 1 pedido / R$ 1.542,40
- **Braulio Diniz** — 1 pedido / R$ 1.534,00

## Geografia do recorte MAG
- **São Paulo/SP:** 138 pedidos / R$ 53.621,81
- **Rio de Janeiro/RJ:** 26 pedidos / R$ 13.245,14
- **Belo Horizonte/MG:** 22 pedidos / R$ 12.128,24
- **Brasília/DF:** 13 pedidos / R$ 7.708,92
- **Curitiba/PR:** 12 pedidos / R$ 7.393,06

## Observações
- A análise de clientes **não cobre todo o universo do mês**, porque o Oracle acessível nesta sessão não expõe um cadastro mestre de clientes facilmente rastreável para todos os pedidos; o nome do cliente ficou disponível sobretudo no recorte MAG
- Para um relatório comercial mais completo, o próximo passo é buscar a dimensão de cliente do ERP ou outra visão de integração que cubra os 3.219 pedidos confirmados
- Se você quiser, no próximo passo eu posso aprofundar em:
  - ranking de vendedores
  - mix de pagamento
  - curva diária de vendas
  - clientes recorrentes
  - clientes por UF/cidade
