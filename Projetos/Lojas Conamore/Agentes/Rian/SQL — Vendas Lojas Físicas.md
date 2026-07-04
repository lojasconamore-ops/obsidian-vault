# SQL — Vendas Lojas Físicas (DEBX)

**Autor:** Rian — Gerente Comercial de Lojas Físicas
**Data:** 04/07/2026
**Fonte:** Query fornecida por Sergio Ladeira (CEO)
**Banco:** Oracle DEBX (172.169.0.11:1521) — instância de **CONSULTA** (réplica, ~1 dia defasada da produção)

---

## Objetivo da Query

Detalhamento das vendas das lojas físicas em um período selecionado, com informações de **vendedor**, **produto** e **fornecedor**. Essa é a base de dados canônica para análises de varejo.

---

## Query Original

```sql
SELECT * 
FROM (
    SELECT 
        TRUNC(MOV_DATMOV, 'MM') AS MES_REFERENCIA,
        REP_RAZAOS,
        PDV_NUMPED,
        MOV_CODPRO,
        PRO_DESCRI,
        EMP_NFANTA,
        SUM(MOV_QTDMOV) AS QTDE_TOTAL,
        MOV_VALUNI,
        SUM(MOV_VALTOT - MOV_VALICM - MOV_VALPIS - MOV_COFINS) AS VL_BRUTO,
        SUM(MOV_VLDESC) AS DESCONTO,
        SUM(MOV_VALTOT - MOV_VALICM - MOV_VALPIS - MOV_COFINS - MOV_VLDESC) AS VALOR
    FROM 
        F_MOVTO
        LEFT JOIN F_PEDVENDA ON PDV_NUMPED = MOV_NUMPED
        LEFT JOIN F_PRODS ON MOV_CODPRO = PRO_CODPRO
        LEFT JOIN F_TIPMOV ON MOV_TIPMOV = TPM_CODIGO
        LEFT JOIN F_CDEMP ON PRO_FORNEC = EMP_CODEMP
        LEFT JOIN F_REPRES ON REP_CODIGO = PDV_CODREP
    WHERE 
        TPM_ENTSAI = 'S'
        AND TPM_CUSMAT = 'F'
        AND MOV_NATIND = '100'
        AND MOV_DATMOV >= TO_DATE(:n1,'DD/MM/YY')
        AND MOV_DATMOV <= TO_DATE(:n2,'DD/MM/YY')
    GROUP BY 
        TRUNC(MOV_DATMOV, 'MM'),
        REP_RAZAOS,
        PDV_NUMPED,
        MOV_CODPRO,
        PRO_DESCRI,
        PRO_FORNEC,
        MOV_VALUNI,
        EMP_NFANTA,
        PRO_ULTPRC
    ORDER BY 
        TRUNC(MOV_DATMOV, 'MM'),
        PDV_NUMPED,
        REP_RAZAOS
)
```

---

## Tabelas Envolvidas

| Tabela | Descrição | Coluna-chave |
|---|---|---|
| `F_MOVTO` | Movimentações (vendas, saídas de estoque) | `MOV_CODPRO`, `MOV_NUMPED` |
| `F_PEDVENDA` | Pedidos de venda | `PDV_NUMPED`, `PDV_CODREP` |
| `F_PRODS` | Cadastro de produtos | `PRO_CODPRO`, `PRO_FORNEC` |
| `F_TIPMOV` | Tipo de movimento | `TPM_CODIGO` |
| `F_CDEMP` | Cadastro de empresas (fornecedores) | `EMP_CODEMP` |
| `F_REPRES` | Representantes / vendedores | `REP_CODIGO` |

---

## Relacionamentos (JOINs)

```
F_MOVTO ──LEFT──▶ F_PEDVENDA   (MOV_NUMPED  = PDV_NUMPED)
F_MOVTO ──LEFT──▶ F_PRODS      (MOV_CODPRO  = PRO_CODPRO)
F_MOVTO ──LEFT──▶ F_TIPMOV     (MOV_TIPMOV  = TPM_CODIGO)
F_PRODS ──LEFT──▶ F_CDEMP      (PRO_FORNEC  = EMP_CODEMP)
F_PEDVENDA ─LEFT──▶ F_REPRES   (PDV_CODREP  = REP_CODIGO)
```

> ⚠️ Todos os JOINs são `LEFT JOIN` — se não existir pedido/vendedor/fornecedor o campo virá `NULL`.

---

## Filtros (WHERE)

| Filtro | Valor | Significado |
|---|---|---|
| `TPM_ENTSAI` | `'S'` | Movimento de **saída** (venda) |
| `TPM_CUSMAT` | `'F'` | Filtro de custo material |
| `MOV_NATIND` | `'100'` | **Natureza = venda de loja física** |
| `MOV_DATMOV` | `:n1` / `:n2` | Período (parâmetros do usuário) |

> 🔑 `MOV_NATIND = '100'` é o identificador canônico de venda de loja física no DEBX.

---

## Colunas Retornadas

| Coluna | Origem | Descrição |
|---|---|---|
| `MES_REFERENCIA` | `TRUNC(MOV_DATMOV, 'MM')` | Mês da venda (1º dia do mês) |
| `REP_RAZAOS` | `F_REPRES` | Nome do vendedor/representante |
| `PDV_NUMPED` | `F_PEDVENDA` | Número do pedido de venda |
| `MOV_CODPRO` | `F_MOVTO` | Código do produto |
| `PRO_DESCRI` | `F_PRODS` | Descrição do produto |
| `EMP_NFANTA` | `F_CDEMP` | Nome fantasia do fornecedor |
| `QTDE_TOTAL` | `SUM(MOV_QTDMOV)` | Quantidade total vendida |
| `MOV_VALUNI` | `F_MOVTO` | Valor unitário do produto |
| `VL_BRUTO` | Cálculo | Valor total − ICMS − PIS − COFINS |
| `DESCONTO` | `SUM(MOV_VLDESC)` | Soma dos descontos aplicados |
| `VALOR` | Cálculo | Valor líquido = `VL_BRUTO − DESCONTO` |

---

## Cálculo dos Valores

```
VL_BRUTO = Σ(MOV_VALTOT − MOV_VALICM − MOV_VALPIS − MOV_COFINS)
DESCONTO = Σ(MOV_VLDESC)
VALOR    = VL_BRUTO − DESCONTO
```

---

## Agrupamento (GROUP BY)

Agrupado por:
1. Mês de referência
2. Vendedor
3. Número do pedido
4. Código e descrição do produto
5. Fornecedor do produto
6. Valor unitário
7. Nome fantasia da empresa
8. Último preço do produto (`PRO_ULTPRC`)

---

## Ordenação

1. Mês de referência (cronológico)
2. Número do pedido
3. Nome do vendedor

---

## Observações Importantes

1. **`MOV_NATIND = '100'`** — esta é a regra de ouro para isolar vendas de loja física. **Nunca usar outro valor para varejo.**
2. **Parâmetros `:n1` e `:n2`** — datas no formato `DD/MM/YY`, provavelmente vinculadas a um relatório Oracle Reports ou ferramenta similar.
3. **LEFT JOINs** — se um pedido não tiver vendedor vinculado, `REP_RAZAOS` aparecerá nulo. Tratar nas análises.
4. **`PRO_ULTPRC` no GROUP BY** — está agrupando pelo último preço mesmo sem exibi-lo no SELECT externo. Pode gerar duplicidade se o último preço mudar e houver `NULL` tratado como valor distinto.
5. **Impostos deduzidos** — ICMS, PIS e COFINS são removidos do valor bruto. O valor final é o que efetivamente entra como receita.

---

## Possíveis Análises Derivadas

A partir desta query base, podemos construir:
- Ranking de vendedores por período
- Ticket médio por loja/vendedor
- Top produtos e categorias
- Análise de margem e desconto médio
- Curva ABC de produtos no varejo
- Evolução mensal de vendas
- Performance por fornecedor
