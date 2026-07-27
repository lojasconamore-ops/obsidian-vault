---
title: Oracle e DEBX — Treinamento de Agentes
aliases:
  - Oracle e DEBX - Treinamento de Agentes
tags:
  - debx
  - oracle
  - treinamento
  - agentes
  - conamore
---

# Oracle e DEBX — Treinamento de Agentes

Nota de ponte para o treinamento do Matias.

O documento oficial fica em:

[[Projetos/Lojas Conamore/Oracle e DEBX - Treinamento de Agentes|Oracle e DEBX - Treinamento de Agentes]]

Resumo operacional:
- Banco Oracle `conamore` em `172.169.0.11:1521/conamore`.
- Trabalhar em leitura primeiro; padrão seguro é `SELECT`.
- Validar sessão com `select 1 from dual` e `sys_context`.
- Não misturar PED com venda física.
- PED: pedidos/aprovação/vendas centralizadas.
- `F_MOVTO` + `MOV_NATIND = 100`: venda física.
- `v_estoq`: estoque disponível para venda.
- `ALMOX`: estoque local de loja física.

> Esta nota existe para manter compatibilidade com a ordem de leitura do perfil Matias; a fonte de verdade continua no documento oficial em Projetos/Lojas Conamore.
