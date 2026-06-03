---
title: Oracle e DEBX — Versão Padrão dos Agentes
tags:
  - debx
  - oracle
  - treinamento
  - agentes
  - conamore
---

# Oracle e DEBX — Padrão para todos os agentes

Este texto é a versão padrão para copiar em todos os perfis que precisem consultar o Oracle do DEBX.

## Objetivo

Usar o Oracle do DEBX com segurança, clareza e foco em leitura, sempre respondendo perguntas operacionais da Conamore sem misturar bases ou inventar interpretação.

## Regra principal

- Leitura primeiro.
- Em produção, o padrão é `SELECT`.
- Não alterar dados sem autorização explícita.
- Não misturar PED com venda física.
- Se houver dúvida de schema, tabela ou coluna, confirmar antes de rodar consulta grande.

## Quando usar cada base

- PED: pedidos comerciais, aprovação, faturamento, análise de vendas central e itens do pedido.
- F_MOVTO + `MOV_NATIND = 100`: venda da loja física.
- `v_estoq`: estoque disponível para venda.
- `ALMOX`: estoque local da loja física.
- Dúvida de estrutura: validar schema/tabela/coluna antes do relatório.

## Fluxo padrão

1. Entender a pergunta de negócio.
2. Escolher a base correta.
3. Validar a sessão no Oracle.
4. Confirmar schema, tabela e coluna se houver dúvida.
5. Rodar a menor consulta possível.
6. Conferir totais e consistência.
7. Comparar com outra visão se necessário.
8. Responder com resumo claro.

## Conexão

- Banco: Oracle `conamore`
- Host: `172.169.0.11`
- Porta: `1521`
- String exemplo: `//172.169.0.11:1521/conamore`

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

Se isso falhar, o problema é de conexão, credencial ou sessão.

## Tabelas mais usadas

### PED
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

### Venda física
- `TEST_ACL.F_MOVTO`

Campos úteis:
- `MOV_DATMOV`
- `MOV_NATIND`
- `MOV_CODPRO`
- `MOV_QTDMOV`
- `MOV_VALTOT`
- `MOV_TIPMOV`

## Padrões de consulta

### Venda física por mês e SKU

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

### PED por mês e SKU

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
- Use agregação em vez de `SELECT *`.
- Se o total parecer estranho, compare com outra visão.

## Erros comuns

- Conectar no host ou porta errados.
- Informar service name incorreto.
- Usar schema ou tabela sem prefixo quando a visão não é a padrão.
- Misturar PED com venda física.
- Rodar consulta grande sem filtro de data.
- Assumir coluna sem validar o nome real.

## Como o agente deve responder

Sempre devolver:
- resumo curto da resposta de negócio
- base usada
- período consultado
- lógica usada, em alto nível
- totais principais
- observações se houver inconsistência ou limitação

## Exemplo de resposta

"Usei a base PED para analisar janeiro/2026. O total de pedidos aprovados foi X, com valor total Y. A consulta foi feita com filtro por data e status, sem alteração de dados."

## Quando chamar o Matias

- Dúvida de schema, tabela ou coluna.
- Dúvida sobre regra de negócio do DEBX.
- Resultado inconsistente ou impossível de validar.
- Necessidade de confirmar a fonte correta antes do relatório.

> Este texto pode ser copiado para qualquer perfil que precise operar o Oracle do DEBX. A ideia é manter o comportamento consistente entre agentes.
