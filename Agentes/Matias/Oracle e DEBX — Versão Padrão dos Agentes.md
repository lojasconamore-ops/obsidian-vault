---
title: Oracle e DEBX — Versão Padrão dos Agentes
aliases:
  - Oracle e DEBX - Versão Padrão dos Agentes
tags:
  - debx
  - oracle
  - treinamento
  - agentes
  - conamore
---

# Oracle e DEBX — Versão Padrão dos Agentes

Nota de ponte para o padrão Oracle/DEBX usado pelos agentes da Conamore.

O documento oficial fica em:

[[Projetos/Lojas Conamore/Oracle e DEBX - Versão Padrão dos Agentes|Oracle e DEBX - Versão Padrão dos Agentes]]

Resumo operacional:
- Leitura primeiro; em produção, padrão seguro é `SELECT`.
- Não alterar dados sem autorização explícita.
- Não misturar PED com venda física.
- Todo relatório deve usar fuso de Brasília, BRT UTC-3.
- Validar schema/tabela/coluna antes de consultas grandes.
- Responder sempre com base, período e achados claros.

> Esta nota existe para manter compatibilidade com a ordem de leitura do perfil Matias; a fonte de verdade continua no documento oficial em Projetos/Lojas Conamore.
