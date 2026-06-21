# Oracle DEBX — Análise Operacional — 04/06/2026

> Janela operacional do Oracle DEBX: disponível diariamente das **08:00 às 18:00 (BRT)**; fora disso a conexão pode retornar `ORA-01033`.

## Conexão validada
- Banco: Oracle `conamore`
- Host: `172.169.0.11:1521`
- Usuário: `TEST_PED`
- Schema principal para PED: `TEST_ACL`
- View de estoque: `TEST_PED.V_ESTOQ`

## Validação mínima
```sql
select 1 from dual;
```

Retorno confirmado:
- `DB_NAME = conamore`
- `SERVICE_NAME = conamore`
- `SESSION_USER = TEST_PED`

## Leitura de pedidos — últimos 60 dias
Período analisado: 05/04/2026 a 04/06/2026

- Pedidos: 6.547
- Receita: R$ 1.207.476,89
- Frete monetário: R$ 48.226,70
- Frete médio: R$ 7,37

### Status dos pedidos
- `X`: 6.460 pedidos | R$ 1.159.104,26 | frete R$ 44.626,08
- `A`: 73 pedidos | R$ 37.047,94 | frete R$ 3.111,64
- `D`: 8 pedidos | R$ 3.713,59 | frete R$ 363,98
- `G`: 2 pedidos | R$ 6.499,10 | frete R$ 100,00
- `L`: 2 pedidos | R$ 338,60 | frete R$ 0,00
- `F`: 1 pedido | R$ 564,40 | frete R$ 25,00
- `Z`: 1 pedido | R$ 209,00 | frete R$ 0,00

### Origem comercial
- Sem origem informada: 5.350 pedidos
- `MAG`: 1.153 pedidos
- `GER`: 44 pedidos

## Frete — pedidos mais caros
- `0103018` — frete R$ 245,82 — valor R$ 1.646,41 — status `X`
- `0101237` — frete R$ 242,20 — valor R$ 642,40 — status `X`
- `0102768` — frete R$ 236,93 — valor R$ 949,53 — status `X`
- `0099748` — frete R$ 188,55 — valor R$ 1.759,85 — status `X`
- `0103430` — frete R$ 178,43 — valor R$ 858,53 — status `X`

## Estoque — risco operacional
View analisada: `TEST_PED.V_ESTOQ`

- Itens totais: 5.361
- Itens zerados: 4.425
- Itens abaixo do mínimo: 82
- Itens abaixo da prateleira: 289

### Maiores faltas de estoque
- `113205005` — PERSONALIZACAO BORDADO/SILK - R$ 08,00 — saldo -700 | mínimo 0 | falta 700
- `113205006` — PERSONALIZACAO BORDADO/SILK - R$ 09,00 — saldo -680 | mínimo 0 | falta 680
- `ENC-1080001` — PROTETOR DE COLCHÃO IMPERMEÁVEL ... — saldo -630 | mínimo 0 | falta 630
- `ENC-15709` — PROTETOR TRAVESSEIRO IMPERMEÁVEL ... — saldo -630 | mínimo 0 | falta 630
- `113205004` — PERSONALIZACAO BORDADO/SILK - R$ 07,00 — saldo -619 | mínimo 0 | falta 619

## Movimentação — últimos 60 dias
- `SFC`: 11.511 linhas | 34.081 unidades | R$ 558.072,83
- `SFX`: 3.965 linhas | 12.615 unidades | R$ 547.015,38
- `EC`: 1.225 linhas | 33.623 unidades | R$ 415.855,87
- `S95`: 553 linhas | 3.546 unidades | R$ 47.173,66
- `SFZ`: 380 linhas | 3.372 unidades | R$ 90.779,87

## Leitura executiva
- O Oracle já está acessível e validado para consulta.
- Em PED, o volume está concentrado em status `X`.
- O campo de frete monetário é `PDV_VALFRE`.
- O maior alerta operacional hoje é **estoque**: há muito item zerado e 82 abaixo do mínimo.
- Os maiores buracos estão em itens de personalização e alguns itens de enxoval/protetores.

## Próximo passo recomendado
- Cruzar os itens abaixo do mínimo com a curva de venda para priorizar ressuprimento.
- Mapear os códigos de movimento (`SFC`, `SFX`, `EC`, etc.) com o time de TI/ERP para leitura operacional fechada.
