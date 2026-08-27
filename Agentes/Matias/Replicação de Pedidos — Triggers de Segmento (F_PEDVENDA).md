---
title: Replicação de Pedidos — Triggers de Segmento (F_PEDVENDA)
tags:
  - oracle
  - debx
  - triggers
  - pedidos
  - segmento
  - replicacao
  - matriz
---

# Replicação de Pedidos — Triggers de Segmento (F_PEDVENDA)

Como os pedidos da base central `TEST_PED` são distribuídos (replicados) para os schemas das lojas/matriz no Oracle DEBX, e onde a decisão de **segmento** é tomada.

## Resumo em uma frase

A decisão de **qual schema recebe o pedido** é feita na trigger `DEBI_PEDVENDA_INDICA_SEGMENTO` (BEFORE). A trigger `DEBI_PEDVENDA_REPLICA` (AFTER) só **lê** o `PDV_CODSEG` já gravado e o traduz para o schema destino.

## Sequência de execução

1. `DEB_PEDVENDA_ORCAME` — marca orçamento
2. `DEBI_PEDVENDA_INDICA_SEGMENTO` — **grava `PDV_CODSEG`** (BEFORE INSERT/UPDATE OF PDV_VALTOT)
3. `INSERT`/`UPDATE` efetivo na `F_PEDVENDA`
4. `DEBI_PEDVENDA_REPLICA` — replica para o schema do segmento (AFTER)

## Tabela de segmentos (`C_SEGMENTO`)

| SEG_CODIGO | SEG_DESCRI | SEG_USUIND (schema) |
|:---:|---|---|
| 0 | CONSOLIDADO PED | `NULL` |
| 100 | MATRIZ | `TEST_MATRIZ` |
| 200 | FILIAL | `TEST_FILIAL` |
| 300 | ACL | `TEST_ACL` |
| 400 | CHC | `TEST_CHC` |
| 500 | GCL | `TEST_GCL` |
| 600 | PEDIDOS (central) | `TEST_PED` |
| 700 | BRG | `TEST_BRG` |

- `SEG_CODIGO 0` e `600` são excluídos do roteamento (ficam na central).
- O trigger de replicação resolve o destino via `C_SEGMENTO.SEG_USUIND` a partir do `PDV_CODSEG`.

## Regra de decisão do segmento (`DEBI_PEDVENDA_INDICA_SEGMENTO`)

Três rotas, por origem (`PDV_ORIGEM`):

| Origem | Regra | Resultado |
|---|---|---|
| `MAG` (Magento) | Por **valor**: líquido (VALTOT−VALFRE−VLDESC) ≤ `I_PARAM_INTERFACE.IPI_VALPDV` → `IPI_CODSEG`; senão → `100` (Matriz) | 300 ou 100 |
| `GER` (gerencial) | Não altera segmento | mantém (600/NULL) |
| vazio / outra | Por **estado** do endereço **comercial** do cliente | ver abaixo |

**Rota por estado** (origem vazia): força `100` (Matriz) quando:

```
UF do cliente NÃO está em I_UFMAGENTO
  E (pagamento é cartão OU UF ∈ {SP, MG, SC, RS} OU cliente é contribuinte ICMS)
```

Parâmetros atuais relevantes:

| Tabela | Valor | Significado |
|---|---|---|
| `I_UFMAGENTO` | só `IUF_ESTADO = 7` (DF) | whitelist de UFs do Magento |
| `I_PARAM_INTERFACE` | `IPI_CODIGO=1`, `IPI_VALPDV=1600`, `IPI_CODSEG=300` | teto de valor p/ pedido Magento ir à ACL |
| `F_ESTADO` | `CUF_CODIGO 7=DF, 25=SP` | código interno → UF |

> ⚠️ O "estado" considerado é o **endereço comercial** (`END_TIPEND = ci_END_Comercial`), não o de entrega.

## Alteração em 2026-08-27 (Sérgio)

**Objetivo:** enviar também **MG, SC e RS** para a Matriz, mantendo a mesma regra condicionada (cartão OU estado OU contribuinte ICMS), apenas para origem vazia.

**O que mudou na `DEBI_PEDVENDA_INDICA_SEGMENTO`:**

1. Constantes novas: `csUF_MG`, `csUF_SC`, `csUF_RS`.
2. Renomeado `vCLIENTE_SP` → `vCLIENTE_UF`.
3. Condição `CUF_ESIGLA = csUF_SP` → `CUF_ESIGLA IN (csUF_SP, csUF_MG, csUF_SC, csUF_RS)`.

As rotas `MAG` (valor) e `GER` (não altera) ficaram intactas.

**Avisos:**
- Vale apenas para pedidos **novos/alterados** a partir da aplicação; não reclassifica pedidos antigos.
- Script completo salvo em `~/.hermes/profiles/matias/scripts/DEBI_PEDVENDA_INDICA_SEGMENTO_MG_SC_RS.sql`.

### Script final (CREATE OR REPLACE)

```sql
CREATE OR REPLACE TRIGGER DEBI_PEDVENDA_INDICA_SEGMENTO
  BEFORE INSERT OR UPDATE OF PDV_VALTOT ON F_PEDVENDA FOR EACH ROW
  FOLLOWS DEB_PEDVENDA_ORCAME -- FORÇAR A FUNCIONAR SOMENTE DEPOIS DESSA TRIGGER
DECLARE
  ciCON_PED           CONSTANT NUMBER := 600;
  ciCON_MATRIZ        CONSTANT NUMBER := 100;
  csUF_SP             CONSTANT VARCHAR2(2) := 'SP';
  csUF_MG             CONSTANT VARCHAR2(2) := 'MG';
  csUF_SC             CONSTANT VARCHAR2(2) := 'SC';
  csUF_RS             CONSTANT VARCHAR2(2) := 'RS';
  csStatus_Orcamento  CONSTANT VARCHAR2(1) := 'Z';
  cs_ORIGEM_GER       CONSTANT VARCHAR2(3) := 'GER';

  vCARTAO       NUMBER;
  vCLIENTE_UF   NUMBER;
  vCONTRIBUINTE NUMBER;
  vVALMIN       NUMBER;
  vCODSEG       NUMBER;
  vCOUNTUF      NUMBER;
BEGIN

  IF ((:NEW.PDV_STATUS = csStatus_Orcamento) AND (:NEW.PDV_ORCAME = CONS.cs_Sim)) OR (:NEW.PDV_VALTOT <= 0) THEN
    :NEW.PDV_CODSEG := NULL;
    RETURN;
  END IF;

  IF (:NEW.PDV_CODSEG = ciCON_PED) OR
     (:NEW.PDV_CODSEG IS NULL) OR
     (UPDATING AND (:OLD.PDV_STATUS = csStatus_Orcamento)) THEN

    IF (:NEW.PDV_ORIGEM = DEBMAGENTO2.cs_ORIGEM) THEN

      IF (NVL(:NEW.PDV_VALTOT, 0) > 0) THEN

        SELECT IPI_VALPDV, IPI_CODSEG
          INTO vVALMIN, vCODSEG
          FROM I_PARAM_INTERFACE
         WHERE IPI_CODIGO = 1;

        IF ((NVL(:NEW.PDV_VALTOT, 0) - NVL(:NEW.PDV_VALFRE, 0)) - (NVL(:NEW.PDV_VLDESC, 0)) ) <= vVALMIN THEN
          :NEW.PDV_CODSEG := vCODSEG;
        ELSE --ALTERADO DIA 18/01 PARA SE NAO ATENDER O VALOR DO PARAMETRO, FORÇAR MATRIZ (THIAGO ESTÁ CIENTE)
          :NEW.PDV_CODSEG := ciCON_MATRIZ;
        END IF;

      END IF;

      RETURN;
    END IF;

    IF (NVL(:NEW.PDV_ORIGEM, '-999') <> cs_ORIGEM_GER) THEN --ENTRA CASO A ORIGEM ESTEJA VAZIA OU QUE A ORIGEM NÃO SEJA "GER"

      SELECT COUNT(1)
        INTO vCOUNTUF
        FROM I_UFMAGENTO
       WHERE IUF_ESTADO IN (SELECT CID_ESTADO
                              FROM F_CIDADES, F_ENDERE
                             WHERE END_CODEMP = :NEW.PDV_CODEMP
                               AND END_TIPEND = CONS.ci_END_Comercial
                               AND CID_CODIGO = END_CODCID);

      IF vCOUNTUF = 0 THEN

        --É CARTÃO?
        SELECT COUNT(1)
          INTO vCARTAO
          FROM F_TIPOSCD
         WHERE TPG_TIPTEF IS NOT NULL
           AND TPG_CODIGO = :NEW.PDV_FRMPAG;

        --É DE UM DOS ESTADOS ATENDIDOS PELA MATRIZ?
        SELECT COUNT(1)
          INTO vCLIENTE_UF
          FROM F_ESTADO, F_CIDADES, F_ENDERE
         WHERE END_CODEMP = :NEW.PDV_CODEMP
           AND END_TIPEND = CONS.ci_END_Comercial
           AND CID_CODIGO = END_CODCID
           AND CUF_CODIGO = CID_ESTADO
           AND CUF_ESIGLA IN (csUF_SP, csUF_MG, csUF_SC, csUF_RS);

        --TEM IE E É CONTRIBUINTE DO ICMS?
        SELECT COUNT(1)
          INTO vCONTRIBUINTE
          FROM F_ENDERE
         WHERE END_CODEMP = :NEW.PDV_CODEMP
           AND END_TIPEND = CONS.ci_END_Comercial
           AND END_CONICM = CONS.cs_SIM
           AND END_INSEST IS NOT NULL;

        --FRMPAG = CARTAO OU CLIENTE DE SP/MG/SC/RS OU CONTRIBUINTE ICMS
        IF (vCARTAO > 0) OR (vCLIENTE_UF > 0) OR (vCONTRIBUINTE > 0) THEN
          :NEW.PDV_CODSEG := ciCON_MATRIZ;
        END IF;

      END IF;

      RETURN;
    END IF;

  END IF;
END;
/
```

## Notas sobre a trigger de replicação (`DEBI_PEDVENDA_REPLICA`)

- `AFTER INSERT/UPDATE/DELETE` com `WHEN (NEW.PDV_CODSEG IS NOT NULL)`.
- Resolve schema destino em `C_SEGMENTO.SEG_USUIND` (exclui `0` e `600`).
- `INSERT` com captura de `DUP_VAL_ON_INDEX` → `UPDATE` dos campos no destino.
- Status no destino: pagamento Increazy **ou** origem ≠ Magento → `Pendente`; senão `Aprovado`.
- Itens (`F_PEDITEM`) e programação (`F_PRGVEN`) replicam **somente em UPDATE**, nunca no INSERT.
- `PDV_IDIMAG` e `PDV_IDANOT` vão como `NULL` no destino.
- Proteções: `-20001` (valor total), `-20002` (troca de segmento), `-20003` (delete). ⚠️ O `-20003` é provavelmente **código morto** — a cláusula `WHEN` exige `NEW.PDV_CODSEG IS NOT NULL`, que é falso em `DELETE`.

## Relacionado

- [[Banco de Dados e Oracle]]
- [[DEBX — Conexão e Consultas Oracle]]
