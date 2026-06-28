# OS — separador humano no Oracle DEBX

**Data da apuração:** 2026-06-28
**Fuso:** Brasília (BRT, UTC-3)

## Conclusão objetiva
- A tabela de cadastro de separadores encontrada é **`TEST_PED.F_COLAB`**.
- O vínculo entre OS/apontamento e separador humano passa por **`F_OSEXEC`** e **`F_OSAPONT_EXEC`**, ambos apontando para `F_COLAB.CLB_CODIGO`.
- **Não encontrei evidência de que a OS registre exatamente 2 separadores por ordem.** No desenho do banco, a cardinalidade é **N executantes por atividade/OS**.
- No ambiente consultado, as tabelas de apontamento/executantes estavam **sem linhas** (`F_APONOS`, `F_APOSPJ`, `F_OSEXEC`, `F_OSAPONT_EXEC`), então não deu para validar “2 por OS” com dados vivos.

## Tabela mestre de separadores
### `TEST_PED.F_COLAB`
Campos relevantes:
- `CLB_CODIGO` → código do colaborador/separador
- `CLB_NOMECB` → nome humano
- `CLB_TPSEPA` → indica separador (`'S'`)
- `CLB_STATUS` → status ativo/inativo

Exemplos encontrados:
- `0001` — **FREDSON JOSE VENANCIO**
- `0003` — **KAIQUE DOS SANTOS PAES**
- `0002` — **JOSE EDUARDO CAVALCANTE**

## Como ligar OS -> separador
### Caminho confirmado no código
- `MANUTENCAO.OSEXECUT` faz:
  - `FROM F_OSEXEC, F_COLAB`
  - `WHERE OSE_EXECUT = CLB_CODIGO`
  - retorna `CLB_NOMECB`
- `MANUTENCAO.CALCCUSOS` faz:
  - `FROM F_OSAPONT_EXEC`
  - `WHERE OAE_EXECUT = CLB_CODIGO`
  - usa o valor/hora do colaborador

### Estrutura de chave
- `F_OSEXEC`:
  - `OSE_MANUTE`, `OSE_CODATV`, `OSE_SEQITE`, `OSE_EXECUT`
  - PK inclui o executor: `OSE_MANUTE, OSE_CODATV, OSE_SEQITE, OSE_EXECUT`
- `F_OSAPONT_EXEC`:
  - `OAE_MANUTE`, `OAE_ATIVID`, `OAE_SEQUEN`, `OAE_SEQITE`, `OAE_EXECUT`
  - PK inclui o executor: `OAE_MANUTE, OAE_ATIVID, OAE_SEQUEN, OAE_EXECUT, OAE_SEQITE`

## Evidências de OS base
- `TEST_PED.F_CABORDSEP`
  - 1 OS encontrada no ambiente de teste consultado
  - `COS_CODIGO = 1`, `COS_NUMPED = 0081982`
- `TEST_PED.F_ORDEMSEP`
  - 4 itens ligados à OS `1`
  - vínculo direto: `ORD_CODIGO = COS_CODIGO`

## Leitura final
- **Tabela do separador:** `F_COLAB`
- **Chave do separador:** `CLB_CODIGO`
- **Nome humano:** `CLB_NOMECB`
- **Ligação operacional:** `F_OSEXEC` / `F_OSAPONT_EXEC` → `F_COLAB`
- **2 separadores por OS?** **Não validado; a estrutura permite múltiplos executantes e não força exatamente 2.**
