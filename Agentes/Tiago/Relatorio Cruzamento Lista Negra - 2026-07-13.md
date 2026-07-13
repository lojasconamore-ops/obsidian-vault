# 📊 Cruzamento Semanal — Lista Negra × Oracle TEST_MATRIZ

**Data:** 13/07/2026 (Segunda-feira) 08:05 BRT
**Executor:** Tiago — Gerente Financeiro

---

## 🔢 Resumo

| Métrica | Qtd |
|---|---|
| Lista Negra Conamore | 90 |
| Inativas Oracle (STATUS≠0) | 172 |
| Consistentes (bloqueadas E inativas) | **90 (100%)** |
| Sugestão INCLUIR (STATUS=1) | **0** |
| Sugestão INCLUIR (STATUS=3) | **0** |
| Avaliar (STATUS=2) | 82 |
| Revisar (bloqueadas mas ATIVAS) | **0** |

---

## Lista Negra 100% Validada

**Todos os 90 clientes da Lista Negra Conamore estao confirmados como inativos no Oracle TEST_MATRIZ.** Nenhuma entrada bloqueada foi encontrada como ativa (EMP_STATUS='0') no Oracle — o que confirma que a lista esta atualizada e consistente.

- **28 empresas com STATUS=1 (Bloqueado)** — Oracle ja bloqueou. Exemplos: SHINKAI E MAXIMO, PASSOS E SANTOS, LD CONEXOES, GRAN CHEVALIER HOTEL, KAUAI SPA.
- **60 empresas com STATUS=3 (Encerrado)** — Baixadas/encerradas. Exemplos: POLARI FLATS, HOTEL CITY CALIFORNIA, MONTANARI POUSADA, SAAM TOWAGE (13 filiais).
- **2 empresas com outros status** — variacoes de codigo.

---

## Sugestoes de INCLUSAO — STATUS=1 (Bloqueado Oracle)

**Nenhuma.** Todos os 28 STATUS=1 do Oracle ja estao na Lista Negra.

---

## Sugestoes de INCLUSAO — STATUS=3 (Encerrado Oracle)

**Nenhuma.** A unica candidata aparente (codigo `01077` — RAFAEL LIMA VIANA, CNPJ/CPF `5559958360`, Encerrado em 08/12/2025) e um **duplicado** do codigo `1077` da Lista Negra (CPF `055.599.583-60`). Trata-se do classico caso de *CPF masking* do Oracle (padding com zero a esquerda: `01077` vs `1077`). Ja esta bloqueado — nao requer acao.

---

## Para AVALIACAO — STATUS=2 (Cancelado Oracle)

**82 empresas** estao com STATUS=2 (Cancelado) no Oracle e **nao** constam na Lista Negra.

Dentre elas:

| Perfil | Qtd | Recomendacao |
|---|---|---|
| TOP SERVICE (multiplas filiais) | 10 | Empresa grande, varios CNPJs cancelados — provavelmente reorganizacao societaria |
| CPFs de pessoas fisicas | ~30 | Cadastros de teste, funcionarios ou compradores eventuais — baixo risco |
| Hoteis/Pousadas (cancelados) | 5 | HOTEL DAN INN, ARGENTIN PALACE, WORK HOTEL, HOSTEL CANTINHO DO CUNTA, STAY COZY |
| Orgaos publicos/entidades | 5 | SESC, SENAC, MUNICIPIO, SANTA CASA, DIOCESE — cadastros institucionais |
| Testes internos | 1 | "SERGIO TESTE 2" — claramente cadastro de teste |
| Outros | ~31 | Empresas diversas sem historico de compra |

**Recomendacao:** Por padrao, STATUS=2 (Cancelado) **nao requer inclusao automatica na Lista Negra**. A maioria sao cadastros de teste, registros de orcamento nunca convertidos, ou empresas que apenas consultaram precos. Excecoes pontuais (se houver divida ativa ou protestos) devem ser avaliadas individualmente pelo Sergio.

---

## Para REVISAO — Bloqueadas mas ATIVAS no Oracle

**Nenhuma.** Zero empresas da Lista Negra estao ativas no Oracle. Nao ha sugestoes de remocao esta semana.

---

## Totalizacao para Aprovacao

| Acao | Qtd |
|---|---|
| Incluir (STATUS=1) | 0 |
| Incluir (STATUS=3) | 0 |
| Remover (ativos sem divida) | 0 |

**Status: Sem alteracoes pendentes esta semana**

---

## Notas Tecnicas

1. **CPF masking (Oracle):** O codigo `1077` (RAFAEL LIMA VIANA) aparece na Lista Negra e no Oracle como `01077` — padding com zero a esquerda tipico de CPFs. Confirmado como duplicado. O CPF esta mascarado: Blacklist usa `055.599.583-60` (11 digitos com zero) e Oracle armazena `5559958360` (10 digitos sem zero). A deteccao foi feita comparando os ultimos 9 digitos de ambos.

2. **SAAM TOWAGE BRASIL S.A.:** 13 filiais bloqueadas, todas confirmadas como STATUS=3 (Encerrado) no Oracle. Consistente.

3. **DECORACAO E CIA / CIA E ARTE:** Codigos `88839` e `90150` na Lista Negra — mesmo CNPJ `14.627.870/0001-08`. Ambos confirmados como STATUS=1 no Oracle via correspondencia por CNPJ. Duplicata intencional (dois codigos DEBX diferentes para o mesmo CNPJ).

4. **Horario da consulta:** 08:05 BRT — Oracle disponivel, primeira tentativa bem-sucedida.

---

## Conclusao

**Lista Negra Conamore esta 100% alinhada com Oracle TEST_MATRIZ.** Todos os 90 bloqueios sao suportados por inativacao no ERP. Nenhuma acao de inclusao ou remocao e necessaria esta semana.

Aguardando validacao do Sergio.

---

*Relatorio gerado automaticamente pelo Tiago (Gerente Financeiro) via cron job semanal.*
