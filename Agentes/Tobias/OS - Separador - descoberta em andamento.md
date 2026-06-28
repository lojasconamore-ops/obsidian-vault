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
- A MATRIZ entrega com segurança **OS, volumes, valor, pedidos e status** em `TEST_MATRIZ.F_CABORDSEP` + `TEST_MATRIZ.F_ORDEMSEP`.
- A correlação nominal do separador **não está na MATRIZ**.
- O vínculo operacional existe no WMS/abertura de OS:
  - `TEST_PED.CONFIRM_PICKING` grava `F_ORDCOLAB (ODC_CODORD, ODC_CODCLB)` usando `C_CONFIG_WMS.CWM_COLABP`.
  - `TEST_PED.MANUTENCAO.OSEXECUT` resolve o nome humano com `F_OSEXEC.OSE_EXECUT -> F_COLAB.CLB_CODIGO`.
  - `TEST_PED.MANUTENCAO.CALCCUSOS` cruza `F_OSAPONT_EXEC.OAE_EXECUT -> F_COLAB.CLB_CODIGO`.
- Porém, no banco consultado nesta execução, as tabelas de vínculo estão **zeradas**:
  - `TEST_PED.F_ORDCOLAB = 0`
  - `TEST_PED.F_OSEXEC = 0`
  - `TEST_PED.F_OSAPONT_EXEC = 0`
  - `TEST_PED.C_CONFIG_WMS = 0`
- Conclusão: há prova do caminho técnico, mas **não há linhas vivas suficientes para atribuir as OSs de 26/06 aos nomes FREDSON/KAIQUE com evidência direta**.

## Bloqueio atual
O Oracle estava acessível nesta rodada, mas o elo OS → separador ficou bloqueado por ausência de registros nas tabelas de integração/WMS. A janela operacional não foi o problema desta vez.

## Próximo passo
Se aparecer uma carga com dados vivos de WMS/integração, repetir a busca em ordem:
1. `F_ORDCOLAB` + `F_COLAB`
2. `F_OSEXEC` + `F_OSAPONT_EXEC` + `F_COLAB`
3. `C_INTEGRAWMS` + `C_CABOSWMS` + `C_CONFIG_WMS`
4. cruzar com `TEST_MATRIZ.F_CABORDSEP` e `TEST_MATRIZ.F_ORDEMSEP`
