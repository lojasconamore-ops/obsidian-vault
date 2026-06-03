---
title: Oracle e DEBX — Treinamento de Agentes
tags:
  - debx
  - oracle
  - treinamento
  - agentes
  - conamore
---

# Oracle e DEBX — Guia Rápido para Agentes

Este é o **guia único e oficial** para qualquer agente que precise conectar no Oracle do DEBX e trabalhar com consultas operacionais da Conamore.

## Uso em 30 segundos

1. **Conecte no Oracle** `conamore` em `172.169.0.11:1521`.
2. **Valide a sessão** com `select 1 from dual` e `sys_context`.
3. **Escolha a base certa**:
   - **PED** = pedidos / aprovação / venda central
   - **F_MOVTO + MOV_NATIND = 100** = venda da loja física
   - **v_estoq** = estoque disponível para venda
   - **ALMOX** = estoque local da loja
4. **Consulte em leitura** (`SELECT`) e filtre o máximo possível.
5. Se tiver dúvida de schema, coluna ou regra, chame o **Matias**.

## Regra principal

- **Leitura primeiro.** Em produção, o padrão é `SELECT`.
- Não alterar dados sem autorização explícita.
- Se a consulta puder ser menor e mais objetiva, faça menor.
- Não misture **venda da PED** com **venda física**.

## Conexão

- **Banco:** Oracle `conamore`
- **Host:** `172.169.0.11`
- **Porta:** `1521`
- **Exemplo de string:** `//172.169.0.11:1521/conamore`

## Validação mínima da sessão

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

Se isso falhar, o problema é de conexão/credencial/sessão.

## Como o DEBX funciona

### PED
- A **PED** concentra pedidos e vendas.
- `I_PDVAPROV` marca a data de aprovação.
- Antes da aprovação, tende a estar editável/orçamento.
- Depois da aprovação, vira pedido travado para separação, faturamento e envio.

### Estoque
- `v_estoq` = estoque disponível para venda.
- Ele consolida saldos e desconta reservas de pedidos aprovados sem NF.
- `ALMOX` = estoque local da loja física.

### Loja física
- Para vender da **loja física**, use `F_MOVTO` com:
  - `MOV_NATIND = 100`
- Esse é o filtro validado para venda física da ACL.

## Tabelas mais usadas

### Venda central / PED
- `TEST_ACL.F_PEDVENDA` — cabeçalho do pedido
- `TEST_ACL.F_PEDITEM` — itens
- `TEST_ACL.F_PRODS` — produtos

Campos úteis:
- `PDV_NUMPED`
- `PDV_DATPED`
- `PDV_STATUS`
- `PDV_VALTOT`
- `ITV_CODPRO`
- `ITV_QTDITE`
- `ITV_VALITE`

### Venda física / movimentação
- `TEST_ACL.F_MOVTO`

Campos úteis:
- `MOV_DATMOV`
- `MOV_NATIND`
- `MOV_CODPRO`
- `MOV_QTDMOV`
- `MOV_VALTOT`
- `MOV_TIPMOV`

## Padrões de consulta

### 1) Venda física por mês e SKU

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
group by trunc(m.mov_datmov, 'MM'), m.mov_codpro
order by mes, sku;
```

### 2) PED por mês e SKU

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

## Regras práticas

- Comece com poucos registros.
- Confirme nomes de coluna antes de joins grandes.
- Valide o filtro de data antes de fechar relatório.
- Se o total parecer estranho, compare com outra visão.
- Consulte a operação certa quando o dado for de loja, frete ou rastreio.

## Checklist rápido

1. Entenda a pergunta de negócio.
2. Escolha a base correta: PED ou loja física.
3. Valide a sessão.
4. Faça a menor consulta que responda à pergunta.
5. Agrupe por mês e SKU quando houver volume.
6. Confira total mensal e total geral.
7. Registre a conclusão de forma clara.

## Referências

- [[Agentes/Matias/Banco de Dados e Oracle]]
- [[Agentes/Matias/DEBX — Conexão e Consultas Oracle]]

> Este documento deve ser a referência principal para todos os agentes. Os demais servem como apoio ou histórico.
