---
title: Oracle e DEBX — Treinamento de Agentes
tags:
  - debx
  - oracle
  - treinamento
  - agentes
  - conamore
---

# Oracle e DEBX — Guia Único Operacional

Este é o **documento único e oficial** para qualquer agente que precise conectar no Oracle do DEBX e trabalhar com consultas operacionais da Conamore.

## Objetivo

Dar um caminho rápido para:

- conectar no banco com segurança;
- validar a sessão;
- entender onde estão os dados certos;
- consultar em modo somente leitura;
- interpretar o resultado sem misturar loja física, PED e estoque disponível.

## Regra principal

- **Leitura primeiro.** Em produção, o padrão é `SELECT`.
- Não alterar dados sem autorização explícita.
- Se houver dúvida de schema, coluna, relacionamento ou regra de negócio, chame o **Matias**.
- Se a consulta puder ser menor e mais objetiva, faça menor.

## Ambiente de conexão

- **Banco:** Oracle `conamore`
- **Host:** `172.169.0.11`
- **Porta:** `1521`
- **Contexto:** DEBX / Conamore

Exemplo de string:

```text
//172.169.0.11:1521/conamore
```

Se a ferramenta pedir SID/service name, use o nome do ambiente informado para aquela sessão.

## Validação mínima da sessão

Sempre comece com consultas inocentes:

```sql
select 1 as ok from dual;
```

```sql
select
  sys_context('USERENV','DB_NAME') as db_name,
  sys_context('USERENV','SERVICE_NAME') as service_name,
  sys_context('USERENV','SESSION_USER') as session_user
from dual;
```

Se isso falhar, o problema é de conexão/credencial/sessão — não de negócio.

## Como o DEBX funciona na prática

### 1) PED é o centro do negócio

- A **PED** concentra pedidos e vendas.
- `I_PDVAPROV` marca a **data de aprovação**.
- Antes da aprovação, o registro tende a estar como orçamento/editável.
- Depois da aprovação, vira pedido travado para separação, faturamento e envio.

### 2) Estoque e loja física não são a mesma coisa

- `v_estoq` representa o **estoque disponível para venda**.
- Ele consolida saldos e desconta reservas de pedidos aprovados ainda sem NF.
- Lojas físicas usam o estoque local `ALMOX`.
- Se a pergunta for **venda da loja física**, o caminho validado é `F_MOVTO` com `MOV_NATIND = 100`.

### 3) Intelipost pode estar separado por operação

- Dados de rastreio e frete podem ficar por loja/schema.
- Não assuma que a operação central responde por tudo.
- Consulte a operação onde a NF foi emitida quando o tema for rastreamento/logística.

## Tabelas e campos que mais aparecem

### PED / venda central

- `TEST_ACL.F_PEDVENDA` — cabeçalho do pedido
- `TEST_ACL.F_PEDITEM` — itens do pedido
- `TEST_ACL.F_PRODS` — descrição e classificação do produto

Campos úteis:

- `PDV_NUMPED`
- `PDV_DATPED`
- `PDV_STATUS`
- `PDV_VALTOT`
- `ITV_CODPRO`
- `ITV_QTDITE`
- `ITV_VALITE`

### Loja física / movimentação

- `TEST_ACL.F_MOVTO` — movimentos operacionais da loja

Campos úteis:

- `MOV_DATMOV`
- `MOV_NATIND`
- `MOV_CODPRO`
- `MOV_QTDMOV`
- `MOV_VALTOT`
- `MOV_TIPMOV`

## Padrões de consulta que funcionam

### A. Vendas da PED por período

Use quando a pergunta for pedido/aprovação/venda central.

```sql
select
  trunc(p.pdv_datped, 'MM') as mes,
  i.itv_codpro as sku,
  max(pr.pro_descri) as descricao,
  sum(i.itv_qtdite) as qtd,
  round(sum(i.itv_valite), 2) as valor
from test_acl.f_pedvenda p
join test_acl.f_peditem i on i.itv_numped = p.pdv_numped
join test_acl.f_prods pr on pr.pro_codpro = i.itv_codpro
where p.pdv_datped >= date '2026-01-01'
  and p.pdv_status = 'X'
group by trunc(p.pdv_datped, 'MM'), i.itv_codpro
order by mes, sku;
```

### B. Venda da loja física por período

Use quando a pergunta for **loja física**.

```sql
select
  trunc(m.mov_datmov, 'MM') as mes,
  m.mov_codpro as sku,
  max(pr.pro_descri) as descricao,
  sum(m.mov_qtdmov) as qtd,
  round(sum(m.mov_valtot), 2) as valor
from test_acl.f_movto m
join test_acl.f_prods pr on pr.pro_codpro = m.mov_codpro
where m.mov_natind = 100
  and m.mov_datmov >= date '2026-01-01'
  and upper(pr.pro_descri) like '%EDREDOM%'
group by trunc(m.mov_datmov, 'MM'), m.mov_codpro
order by mes, sku;
```

### C. Consulta inicial para descobrir objetos

Quando não souber onde está o dado:

```sql
select owner, table_name
from all_tables
where owner in ('TEST_ACL','TEST_PED')
order by owner, table_name;
```

```sql
select column_name, data_type
from all_tab_columns
where owner = 'TEST_ACL'
  and table_name = 'F_MOVTO'
order by column_id;
```

## Regras de leitura segura

- Comece com poucos registros.
- Confirme nomes de coluna antes de montar joins grandes.
- Não suponha que coluna com nome parecido existe em outra tabela.
- Valide o filtro de data antes de fechar o relatório.
- Se o total parecer estranho, compare com outra visão antes de concluir.

## Quando usar qual base

- **PED / aprovação / pedido comercial** → `F_PEDVENDA` + `F_PEDITEM`
- **Venda da loja física** → `F_MOVTO` com `MOV_NATIND = 100`
- **Estoques para venda** → `v_estoq`
- **Estoque local da loja** → `ALMOX`
- **Rastreio / transporte** → schema operacional da loja da NF

## Erros comuns

- Confundir venda da PED com venda da loja física.
- Usar tabela errada e perder registros válidos.
- Misturar estoque físico com disponível para venda.
- Consultar loja central quando o dado é de uma operação específica.
- Fazer join desnecessário e derrubar linhas.

## Checklist rápido para qualquer agente

1. Entenda a pergunta de negócio.
2. Escolha a base correta: PED ou loja física.
3. Valide a sessão no Oracle.
4. Faça a menor consulta que responda a pergunta.
5. Agrupe por mês/SKU quando houver volume.
6. Confira total mensal e total geral.
7. Registre a conclusão de forma clara.

## Regra de trabalho

Se a pergunta for sobre **venda da loja física**, o filtro base é:

- `MOV_NATIND = 100`

Se a pergunta for sobre **pedido comercial**, o caminho é a **PED**.

## Referências relacionadas

- [[Agentes/Matias/Banco de Dados e Oracle]]
- [[Agentes/Matias/DEBX — Conexão e Consultas Oracle]]

> Observação: este é o documento compartilhado que deve ser usado por todos os agentes. Os demais podem servir como apoio, mas esta é a referência operacional principal.
