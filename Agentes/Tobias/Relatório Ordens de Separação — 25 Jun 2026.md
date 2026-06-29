---
title: Relatório de Ordens de Separação — 25 Jun 2026
tags:
  - logistica
  - debx
  - ordem-separacao
  - cron
date: 2026-06-25
---

# Relatório de Ordens de Separação (OS) — 25/06/2026

## Contexto
Consulta executada no Oracle DEBX para apurar a produtividade da matriz por separador no dia **25/06/2026**.

## Base usada
- `TEST_MATRIZ.F_CABORDSEP`
- `TEST_MATRIZ.F_ORDEMSEP`
- `TEST_MATRIZ.F_VOLUME` com **agregação prévia** antes do join
- `TEST_PED.F_ORDCOLAB`
- `TEST_PED.F_COLAB`

## Resultado encontrado
- **OS:** 7
- **Itens:** 36
- **Qtde enviada:** 162
- **Valor separado:** R$ 8.725,68
- **Volume:** 6
- **Peso bruto:** 98,3
- **Peso líquido:** 98,3
- **Cubagem:** 0

## Limitação operacional
No ambiente consultado, **não havia vínculo vivo de separador humano** para essas OSs:
- `TEST_PED.F_ORDCOLAB` = 0 linhas
- `TEST_PED.F_OSEXEC` = 0 linhas
- `TEST_PED.F_OSAPONT_EXEC` = 0 linhas
- `TEST_PED.C_CONFIG_WMS` = 0 linhas

Conclusão: a produtividade pôde ser medida, mas **não foi possível atribuir por nome/código de separador**. Todo o volume do dia caiu em **SEM VÍNCULO DE SEPARADOR**.

## Observação técnica
A consulta foi reescrita com `F_VOLUME` agregado em CTE antes do join, para evitar duplicação de métricas de volume/peso/cubagem.
