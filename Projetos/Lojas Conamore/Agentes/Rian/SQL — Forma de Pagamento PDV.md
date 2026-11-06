# SQL — Forma de Pagamento do Pedido no PDV

Query para extrair a **forma de pagamento** de cada pedido no momento em que passou pelo PDV (caixa). Liga o pedido ao cupom fiscal e ao lançamento de caixa, traduzindo o código da forma via `F_TIPOSCD`.

## Query canônica

```sql
SELECT DISTINCT
       p.PDV_NUMPED      AS PEDIDO,
       m.MOV_NTFISC      AS CUPOM,
       m.MOV_NFSERI      AS SERIE,
       m.MOV_DATMOV      AS DATA_MOVIMENTO,
       cx.CAM_INDICE     AS ID_MOVIMENTO_CAIXA,
       cx.CAM_FORPAG     AS COD_FORMA,
       fp.TPG_DESCRI     AS FORMA_PAGAMENTO,
       cx.CAM_VALOR      AS VALOR,
       cx.CAM_CODSAI
FROM F_PEDVENDA p
JOIN F_MOVTO m
  ON TRIM(m.MOV_NUMPED) = TRIM(p.PDV_NUMPED)
JOIN F_CAIXA_MOV cx
  ON TRIM(cx.CAM_NONOTA) = TRIM(m.MOV_NTFISC)
 AND TRIM(cx.CAM_NFSERI) = TRIM(m.MOV_NFSERI)
 AND TRUNC(cx.CAM_DTHORA) = TRUNC(m.MOV_DATMOV)
 AND cx.CAM_TIPOES = 'E'
LEFT JOIN F_TIPOSCD fp
  ON TRIM(fp.TPG_CODIGO) = TRIM(cx.CAM_FORPAG)
WHERE m.MOV_NTFISC IS NOT NULL
  AND m.MOV_DATMOV >= TO_DATE(:n1,'DD/MM/YYYY')
  AND m.MOV_DATMOV <= TO_DATE(:n2,'DD/MM/YYYY')
ORDER BY PEDIDO, DATA_MOVIMENTO, CUPOM, ID_MOVIMENTO_CAIXA;
```

## Cadeia de relacionamento

```
F_PEDVENDA (pedido)
   └─ MOV_NUMPED = PDV_NUMPED ─▶ F_MOVTO (movimento / cupom fiscal)
        └─ MOV_NTFISC = CAM_NONOTA ─▶ F_CAIXA_MOV (lançamento de caixa no PDV)
             └─ CAM_FORPAG = TPG_CODIGO ─▶ F_TIPOSCD (descrição da forma de pagamento)
```

## Tabelas e colunas-chave

| Tabela | Papel | Colunas-chave |
|---|---|---|
| `F_PEDVENDA` | Pedido de venda | `PDV_NUMPED` |
| `F_MOVTO` | Movimento / cupom fiscal | `MOV_NUMPED`, `MOV_NTFISC` (cupom), `MOV_NFSERI` (série), `MOV_DATMOV` |
| `F_CAIXA_MOV` | Lançamento do caixa/PDV | `CAM_NONOTA` (cupom), `CAM_NFSERI`, `CAM_DTHORA`, `CAM_FORPAG` (forma), `CAM_TIPOES`, `CAM_VALOR`, `CAM_CODSAI` |
| `F_TIPOSCD` | Domínio das formas de pagamento | `TPG_CODIGO`, `TPG_DESCRI` |

## Regras de junção (validadas com o TI)

1. **`cx.CAM_TIPOES = 'E'`** — só lançamentos de **entrada** (cupom fiscal emitido). Evita pegar os lançamentos de fechamento/sangria (`CAM_TIPOES = 'S'`).
2. **`TRUNC(cx.CAM_DTHORA) = TRUNC(m.MOV_DATMOV)`** — igualdade de dia reduz associação indevida (mesmo cupom/série em datas diferentes).
3. **`TRIM(...)` em todas as chaves** — os campos de código/cupom têm espaços/zeros à esquerda; sem `TRIM` a junção falha.
4. **`JOIN` no caixa (não `LEFT JOIN`)** — lista apenas pedidos que **têm** forma registrada no caixa. Pedidos antigos sem correspondência no caixa não aparecem e **não** devem ser preenchidos com a condição do pedido (`PDV_FRMPAG` é default `'04'` e não reflete o pagamento real).
5. **`LEFT JOIN F_TIPOSCD`** — preserva formas sem descrição (não perde o lançamento).

## Formas de pagamento mais relevantes (ACL)

| Código | Descrição |
|---|---|
| `04` | DINHEIRO |
| `03` | PIX |
| `88` | LOJA - PIX A VISTA - POS |
| `71` | CARTÃO VISA - TEF |
| `72` | CARTÃO MASTER - TEF |
| `77` | DEBITO - CARTEIRA - LOJA - TEF |
| `87` | LOJA - DEBITO - POS |
| `81`–`86` | LOJA - CARTÃO (VISA/MASTER/ELO/AMEX/DISCOVERY/HIPERCARD) - POS |
| `16` | LOJA - DEPOSITO EM CONTA |
| `VC` | VALE CREDITO |

## Observações / cuidados

- `F_TIPOSCD` é um **SYNONYM** em `TEST_ACL` → tabela real `TEST_MATRIZ.F_TIPOSCD`. Também disponível em `TEST_GCL`.
- Um mesmo pedido/cupom pode ter **várias formas** (ex.: parte no débito, parte em dinheiro) — a query lista uma linha por forma.
- **`CAM_CODSAI` ainda não validado** para conciliação definitiva de histórico. Validar antes de tratar como chave de conciliação.
- `PDV_FRMPAG` (coluna do pedido) NÃO é confiável — fica `'04'` como default e não reflete o pagamento real do PDV.
