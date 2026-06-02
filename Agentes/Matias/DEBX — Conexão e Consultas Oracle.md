---
title: DEBX — Conexão e Consultas Oracle
tags:
  - debx
  - oracle
  - matias
  - conamore
---

# DEBX — Conexão e Consultas Oracle

## Objetivo

Este documento ensina outros agentes a:

- conectar no banco Oracle do **DEBX / Conamore**;
- validar que a conexão está correta;
- fazer consultas **seguras, somente leitura**;
- entender o mínimo do contexto de negócio para não interpretar o banco errado.

> Regra principal: **consultar é permitido; alterar em produção não é padrão**. Se houver dúvida, pare e peça validação.

---

## Visão rápida do ambiente

- **Banco:** Oracle `conamore`
- **Host:** `172.169.0.11`
- **Porta:** `1521`
- **Natureza:** ambiente operacional da Conamore / DEBX
- **Janela conhecida de consulta:** horário de Brasília das **08:00 às 12:59** e das **14:01 às 17:59**

### Contexto de negócio que importa

- A **PED** é o hub central dos pedidos e vendas.
- `I_PDVAPROV` indica a **data de aprovação**:
  - antes disso, o registro tende a estar em modo **orçamento/editável**;
  - depois disso, vira **pedido travado** para separação, faturamento e envio.
- `v_estoq` é o **estoque disponível para venda**:
  - soma estoques dos CDs/unidades;
  - desconta reservas de pedidos aprovados ainda sem NF.
- As lojas físicas usam o estoque local `ALMOX`.
- O Intelipost costuma ficar separado por operação/schema da loja onde a NF foi emitida.

---

## Como conectar

### 1) Informações necessárias

Antes de conectar, confirme:

- usuário Oracle
- senha
- service name ou SID correto
- ferramenta usada: SQL Developer, TOAD, DBeaver, `sqlplus`, etc.

> Não grave senha em nota. Use cofre, variável temporária ou conexão salva na ferramenta.

### 2) String de conexão básica

Exemplo de rede:

```text
HOST=172.169.0.11
PORT=1521
DB=conamore
```

Se a ferramenta pedir formato TNS:

```text
(conecte com o service name ou SID informado para o ambiente)
```

Se estiver em linha de comando com `sqlplus`, o padrão costuma ser:

```bash
sqlplus usuario@//172.169.0.11:1521/conamore
```

> Se o service name não responder, testar SID só quando isso fizer sentido para o ambiente e com autorização.

---

## Validação mínima da conexão

Após logar, rode primeiro consultas inocentes.

### Identidade da sessão

```sql
select
  sys_context('USERENV','DB_NAME') as db_name,
  sys_context('USERENV','SERVICE_NAME') as service_name,
  sys_context('USERENV','SESSION_USER') as session_user
from dual;
```

### Timezone e horário da sessão

```sql
select
  systimestamp,
  current_timestamp,
  sessiontimezone
from dual;
```

### Confirmação de leitura

```sql
select 1 as ok from dual;
```

Se essas consultas falharem, o problema é de conexão, credencial ou contexto de sessão — não de negócio.

---

## Como consultar com segurança

### Regras práticas

- Prefira `SELECT`.
- Use `ROWNUM` ou `FETCH FIRST` para limitar resultados.
- Sempre qualifique o schema quando possível.
- Evite queries amplas sem filtro em produção.
- Não execute `DELETE`, `UPDATE`, `INSERT`, `MERGE`, `DROP` ou `ALTER` sem aprovação explícita.
- Não exponha credenciais em logs, prints ou respostas.

### Padrão de consulta recomendado

1. descobrir a tabela/view correta;
2. entender as colunas;
3. testar com poucas linhas;
4. só depois ampliar o recorte.

---

## Consultas úteis para reconhecimento

### Ver objetos do usuário

```sql
select object_type, count(*)
from user_objects
group by object_type
order by object_type;
```

### Ver tabelas e views acessíveis

```sql
select owner, object_name, object_type
from all_objects
where object_type in ('TABLE','VIEW')
order by owner, object_name;
```

### Ver colunas de uma tabela

```sql
select column_name, data_type, data_length, nullable
from all_tab_columns
where owner = 'SCHEMA_AQUI'
  and table_name = 'TABELA_AQUI'
order by column_id;
```

### Amostrar linhas sem pesar demais

```sql
select *
from SCHEMA_AQUI.TABELA_AQUI
where rownum <= 10;
```

Se a ferramenta suportar, prefira ordenar por data/chave de negócio para capturar dados mais recentes.

---

## Consultas que ajudam a entender o DEBX

### PED e ciclo do pedido

Use a PED para entender:

- pedido em orçamento;
- pedido aprovado;
- pedido travado;
- separação/faturamento/envio.

Exemplo de exploração:

```sql
select *
from PED
where rownum <= 10;
```

Depois, procure campos como:

- status;
- aprovação;
- data de aprovação;
- empresa/loja;
- produto;
- quantidade;
- faturamento.

### Aprovação do pedido

A lógica de negócio mais importante é a diferença entre **antes** e **depois** de `I_PDVAPROV`.

- antes: orçamento editável;
- depois: pedido efetivado para a operação.

### Estoque disponível

Quando o objetivo for entender saldo vendável, consulte `v_estoq` primeiro.

```sql
select *
from v_estoq
where rownum <= 20;
```

Interpretação:

- não confundir **estoque físico** com **estoque vendável**;
- `v_estoq` já considera reservas relevantes;
- estoque de loja física pode estar em `ALMOX`.

### Estoque de loja física

```sql
select *
from ALMOX
where rownum <= 20;
```

Use isso para entender o estoque real da loja, não o saldo central de venda.

---

## Como interpretar schemas e operações

O DEBX não deve ser lido como um banco único “genérico”. Ele é dividido por operação/loja.

### Padrões comuns

- schemas por operação: `ACL`, `BRG`, `GCL`, `CHC`, `Matriz`, `Filial`;
- rastreamento do Intelipost separado por loja/schema;
- tabelas de negócio centralizadas na PED;
- visão consolidada em views calculadas, não em tabela bruta.

### Regra de interpretação

- se a consulta for de **pedido/venda central**, comece pela PED;
- se for **estoque vendável**, use `v_estoq`;
- se for **estoque físico de loja**, use `ALMOX`;
- se for **logística/Intelipost**, consulte o schema da operação onde a NF foi emitida.

---

## Padrão de consulta para outros agentes

Quando outro agente precisar consultar o DEBX, siga esta ordem:

1. confirmar conexão com `DB_NAME`, `SERVICE_NAME` e `SESSION_USER`;
2. identificar a entidade de negócio: pedido, estoque, nota, logística, cliente, produto;
3. localizar a tabela/view adequada;
4. fazer amostra pequena;
5. interpretar com a regra de negócio correta;
6. registrar a descoberta no Obsidian.

---

## Erros comuns e como agir

### `ORA-12154`

- normalmente problema de alias/TNS/DSN;
- revisar service name, tnsnames ou string de conexão.

### `ORA-12514`

- o listener não reconhece o service informado;
- tentar o service correto ou confirmar configuração do listener.

### `ORA-28000` / `ORA-28001`

- conta bloqueada ou senha expirada;
- acionar o responsável pelo banco.

### Query lenta

- limitar linhas;
- filtrar por data/chave;
- evitar `SELECT *` em tabelas muito grandes;
- avaliar índice/partição se a consulta for recorrente.

---

## O que nunca fazer

- não testar `UPDATE`/`DELETE` em produção “só para ver”;
- não rodar query sem filtro em tabela grande se não houver necessidade;
- não assumir que `v_estoq` é estoque físico;
- não confundir orçamento com pedido aprovado;
- não divulgar credenciais em documento compartilhado.

---

## Checklist rápido para um novo agente

- [ ] Sei o host/porta do Oracle
- [ ] Sei qual usuário e service name usar
- [ ] Consegui validar a sessão com `DB_NAME` e `SERVICE_NAME`
- [ ] Entendi se estou olhando PED, `v_estoq` ou `ALMOX`
- [ ] Minhas consultas estão limitadas e são só leitura
- [ ] Anotei qualquer descoberta relevante no Obsidian

---

## Resumo executivo

**DEBX = Oracle operacional da Conamore.**

Se o agente quiser responder com precisão, precisa lembrar destas três coisas:

- **PED** = centro do pedido e do ciclo comercial;
- **I_PDVAPROV** = linha entre orçamento e pedido efetivado;
- **v_estoq** = saldo vendável; **ALMOX** = estoque físico da loja.

