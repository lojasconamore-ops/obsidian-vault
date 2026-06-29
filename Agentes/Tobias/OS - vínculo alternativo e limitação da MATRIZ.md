---
title: OS — vínculo alternativo e limitação da MATRIZ
date: 2026-06-29
status: concluido
tags:
  - debx
  - oracle
  - ordem-separacao
  - separador
  - wms
---

# OS — vínculo alternativo e limitação da MATRIZ

## Descoberta
Ao tentar substituir `F_ORDCOLAB` na produtividade por separador da MATRIZ, o dicionário do Oracle mostrou candidatos de vínculo em `TEST_PED`:

- `F_ORDEXE` — colunas `ORE_ORDSER`, `ORE_ATIVID`, `ORE_EXECUT`, `ORE_FUNCAO`, `ORE_LIDER`
- `F_OSPJEX` — colunas `OPE_ORDSER`, `OPE_ATIVID`, `OPE_EXECUT`, `OPE_FUNCAO`, `OPE_LIDER`, `OPE_GRPATV`, `OPE_RESPON`
- `F_APONOS`
- `F_APOSPJ`
- `F_OSEXEC`
- `F_OSAPONT_EXEC`

## O que foi confirmado
### Estrutura de relacionamento
- `F_OSEXEC.OSE_EXECUT -> F_COLAB.CLB_CODIGO`
- `F_OSAPONT_EXEC.OAE_EXECUT -> F_COLAB.CLB_CODIGO`
- `F_ORDEXE.ORE_EXECUT -> PK_EMPREG`
- `F_OSPJEX.OPE_EXECUT -> PK_EMPREG`
- `F_APONOS.APO_EXECUT -> PK_EMPREG`
- `F_APOSPJ.AOP_EXECUT -> PK_EMPREG`
- `F_EXEC_ATOS.EAO_CODCLB -> PK_COLAB`

### Situação dos dados consultados
No ambiente acessado nesta rodada, todas as tabelas acima estavam **zeradas**:
- `F_ORDCOLAB = 0`
- `F_OSEXEC = 0`
- `F_OSAPONT_EXEC = 0`
- `F_ORDEXE = 0`
- `F_OSPJEX = 0`
- `F_APONOS = 0`
- `F_APOSPJ = 0`
- `F_APDSPJ = 0`
- `F_APMTPJ = 0`

## Conclusão operacional
- **Não existe substituto populado e confiável para `F_ORDCOLAB` no recorte da MATRIZ consultado.**
- `TEST_MATRIZ` guarda a OS e os volumes, mas **não guarda o separador nominal**.
- Os elos de executor ficam em `TEST_PED`, porém o ambiente consultado estava sem linhas vivas para fechar o vínculo OS → separador.

## Recomendação
Para produtividade por separador da MATRIZ:
1. manter `F_CABORDSEP` + `F_ORDEMSEP` em `TEST_MATRIZ`
2. usar `F_ORDCOLAB` / `F_COLAB` quando houver carga viva
3. se `F_ORDCOLAB` estiver vazia, reportar **SEM VÍNCULO DE SEPARADOR** em vez de forçar join alternativo

## Nota
`F_ORDEXE` e `F_OSPJEX` parecem ser vínculos de outros fluxos de OS/ordem, não o elo da separação da MATRIZ.
