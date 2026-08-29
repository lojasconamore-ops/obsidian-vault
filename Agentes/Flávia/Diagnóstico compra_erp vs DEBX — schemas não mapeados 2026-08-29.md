# Diagnóstico — compra_erp vs Oracle DEBX (schemas não mapeados)

**Data:** 29/08/2026 · Flávia (Marketing)
**Objetivo:** verificar a hipótese do Sérgio de que a integração da Increazy (que alimenta a conversão `compra_erp` no Google Ads) não mapeia todos os schemas do Oracle DEBX.

## Schemas de negócio do DEBX (empresas do grupo)

| Schema | Tabelas | Papel |
|---|---|---|
| `TEST_MATRIZ` | 70 | Matriz |
| `TEST_ACL` | 27 | Loja 03 (tem `SSL_CAIXAS_LOJA03`) |
| `TEST_BRG` | 27 | Loja 02 (tem `SSL_CAIXAS_LOJA02`) |
| `TEST_CHC` | 27 | Loja CHC |
| `TEST_GCL` | 27 | Loja GCL |
| `TEST_FILIAL` | 13 | Filial |
| `TEST_PED` | 3165 | Schema central (views consolidadas + interfaces Increazy/Magento) |

Cada schema tem `F_PEDVENDA`, `F_PEDITEM`, `F_MOVTO`, `F_PRODS` próprios.

## Interfaces da Increazy (em TEST_PED)

- `I_PEDVENDA_INTERFACE` — ponte de pedidos (10.229 registros; `IPV_CODMAG`=Magento em 644, `IPV_CODINC`=Increazy nos demais). 410 novos nos últimos 30 dias.
- `I_PEDINCREAZY` — pagamentos (10.517 registros; status: success 9.350, canceled 968, waiting 199).

## Vendas por schema — últimos 30 dias (29/07 → 27/08)

| Schema | F_PEDVENDA qtd | valor (R$) | F_MOVTO qtd | valor (R$) |
|---|---:|---:|---:|---:|
| TEST_MATRIZ | 377 | 1.257.855,56 | 0 | 0,00 |
| TEST_ACL | 3.229 | 652.691,45 | 5.636 | 282.756,61 |
| TEST_BRG | 52 | 248.489,51 | 0 | 0,00 |
| TEST_CHC | 1 | 95,80 | 0 | 0,00 |
| TEST_GCL | 858 | 513.793,27 | 1.507 | 67.504,92 |
| TEST_FILIAL | 25 | 119.772,24 | 0 | 0,00 |
| **TOTAL** | | **2.792.697,83** | | **350.261,53** |

**GRAND TOTAL (PED + venda física): R$ 3.142.959,36**

View consolidada `SSL_CAIXA_PERIODO_COM_ORIGEM` (por `IPA_DTAPRV`): **R$ 2.236.084,31** (origem: MAG R$484.612, GER R$92.899, NULL R$1.658.574).

## Referência — compra_erp no Google Ads (30 dias)

**R$ 530.895,01** (143,10 conversões, ~4,93/dia).

## Conclusão

A integração `compra_erp` captura apenas **~17% do faturamento** (R$530k vs R$3,14M real). Hipótese do Sérgio confirmada: **não mapeia todos os schemas**.

Duas causas prováveis:
1. **Schemas não mapeados** — a integração provavelmente lê apenas um schema (ou um subconjunto), deixando as demais empresas de fora.
2. **Escopo/critério** — venda física (`F_MOVTO`, R$350k) e pedidos com outras formas de pagamento (boleto/faturamento) não entram na `compra_erp`, que só conta pagamento confirmado via link Increazy.

## Próximo passo

Confirmar com a Increazy **qual schema/empresa (ou view/query)** a integração lê para disparar a `compra_erp`, e então especificar a correção para cobrir todas as empresas.
