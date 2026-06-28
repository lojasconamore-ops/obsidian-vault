---
title: OS — Separador — descoberta em andamento
date: 2026-06-28
status: em_andamento
tags:
  - debx
  - oracle
  - ordem-separacao
  - separador
  - wms
---

# OS — Separador — descoberta em andamento

## Objetivo
Encontrar a tabela no Oracle DEBX que guarda o **código + nome do separador** das ordens de separação, e identificar como a OS registra os **2 separadores** que atuam na separação.

## O que já foi confirmado

### Base da OS na MATRIZ
- `TEST_MATRIZ.F_CABORDSEP`
  - `COS_CODIGO` = código da OS/cabeçalho
  - `COS_NUMPED` = pedido
  - `COS_DTEMIS` = data/hora do cabeçalho
  - `COS_STATUS` = status
- `TEST_MATRIZ.F_ORDEMSEP`
  - `ORD_CODIGO` = vínculo com o cabeçalho
  - `ORD_INDPRV` = índice do item
  - `ORD_CODPRO` = produto
  - `ORD_QTDENV` = volume/quantidade
  - `ORD_VALSEP` = valor separado
  - `ORD_STATUS` = status do item
  - `ORD_DTEMIS` = data/hora do item

### Índices / gatilhos úteis
- `TEST_MATRIZ` tem triggers ligadas a OS/WMS:
  - `DEB_CABORDSEP_WMS`
  - `DEB_ORDEMSEP_CAGITEM`
  - `DEB_ORDEMSEP_STATUS_FATANT`
- O trigger `DEB_ORDEMSEP_CAGITEM` chama `RETUSUSESS`, indicando que há trilha de usuário/sessão em rotinas de OS/WMS.

## Tentativas feitas hoje
- Consulta direta na MATRIZ para OS de `26/06/2026`
- Procura por tabela/coluna com termo de separador em `TEST_MATRIZ`
- Procura por tabelas com `USU`, `FUNC`, `COLAB`, `EMP`

## Resultado parcial
- A MATRIZ continua entregando **OS, volumes, valor e status**.
- **Ainda não foi encontrada** a tabela definitiva com **código + nome do separador**.
- Há forte indício de que isso esteja em **WMS / auditoria / cadastro de usuários** fora das tabelas-base da OS.

## Bloqueio atual
Às `07:06 BRT`, o Oracle DEBX respondeu `ORA-01033` na tentativa de conexão. A janela operacional documentada é **08:00–18:00 BRT**.

## Próximo passo
Quando o banco estiver disponível:
1. procurar tabelas com `USU`, `LOGIN`, `FUNC`, `OPER`, `RESP`, `SEPAR`
2. cruzar a OS com a trilha de apontamento/execução
3. validar se a OS grava **dois separadores por ordem**
4. trazer o resultado com nome humano, não só código
