# 📊 Cruzamento Semanal — Lista Negra × Oracle TEST_MATRIZ

**Data:** 19/06/2026 (sexta-feira) BRT
**Executor:** Tiago — Gerente Financeiro
**Fonte Oracle:** `TEST_MATRIZ.F_CDEMP` @ `172.169.0.11:1521/conamore`
**Fonte Lista Negra:** `Agentes/Tiago/Lista Negra.md` (89 clientes)

---

## 🔢 Resumo

| Métrica | Qtd |
|---|---|
| Lista Negra Conamore | 89 |
| Inativas Oracle (STATUS≠0) | 168 |
| STATUS=1 (Bloqueado) Oracle | 27 |
| STATUS=2 (Cancelado) Oracle | 79 |
| STATUS=3 (Encerrado) Oracle | 62 |
| ✅ Consistentes (LN ∩ Inativas Oracle) | **89** (100% da LN) |
| 🔴 Sugestão INCLUIR (STATUS=1) | 0 |
| 🟡 Sugestão INCLUIR (STATUS=3) | 0 |
| 🟠 Avaliar (STATUS=2) | 79 |
| ⚠️ Revisar (LN mas ATIVAS Oracle) | 0 |

---

## ✅ Situação Geral

**Lista Negra 100% consistente com Oracle.** Todos os 89 clientes bloqueados na Lista Negra Conamore estão confirmados como inativos no Oracle TEST_MATRIZ:
- 27 com STATUS=1 (Bloqueado)
- 62 com STATUS=3 (Encerrado)

**Nenhuma empresa bloqueada está ativa** no Oracle — zero recomendações de remoção.

**Sem novas inclusões urgentes** — todos os STATUS=1 e STATUS=3 do Oracle já constam na Lista Negra.

---

## 🔴 Sugestões de INCLUSÃO — STATUS=1 (Bloqueado Oracle)

**Nenhuma.** Todos os 27 registros com STATUS=1 no Oracle já estão na Lista Negra.

---

## 🟡 Sugestões de INCLUSÃO — STATUS=3 (Encerrado Oracle)

**Nenhuma.** Todos os 62 registros com STATUS=3 no Oracle já estão na Lista Negra.

---

## 🟠 Para AVALIAÇÃO — STATUS=2 (Cancelado Oracle)

**79 empresas** com STATUS=2 no Oracle **não constam** na Lista Negra. São empresas canceladas que merecem avaliação caso a caso para possível inclusão.

### Amostra (primeiras 20 de 79):

| Código Oracle | Razão Social | CNPJ | Cadastro | Últ. Mov |
|---|---|---|---|---|
| 00214 | MIRIAN MORAIS | 80006124534 | 2025-10-28 | — |
| 00731 | HOSTEL CANTINHO DO CUNTA LTDA | 12100430000164 | 2025-11-21 | 2025-11-25 |
| 00739 | MARIZETE LOBO FERREIRA YOSHINISHI | 4801657850 | 2025-11-21 | — |
| 00748 | ANDRE LUIS ANDRADE DUQUE ESTRADA | 46735306830 | 2025-11-21 | — |
| 01093 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749002320 | 2025-12-05 | — |
| 01163 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749003564 | 2025-12-09 | — |
| 01164 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749003050 | 2025-12-09 | — |
| 01165 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749002754 | 2025-12-09 | — |
| 01166 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749001782 | 2025-12-09 | — |
| 01167 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749002088 | 2025-12-09 | — |
| 01168 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749002673 | 2025-12-09 | — |
| 01169 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749002835 | 2025-12-09 | — |
| 01170 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749002401 | 2025-12-09 | — |
| 01171 | TOP SERVICE SERVICOS E SISTEMAS S/A | 973749002240 | 2025-12-09 | — |
| ... | *(mais 65 registros)* | | | |

> **Nota:** A lista completa dos 79 registros está disponível no JSON de cruzamento (`/tmp/cruzamento_result.json`) e pode ser consultada sob demanda. A TOP SERVICE aparece com múltiplas filiais (cada CNPJ diferente).

---

## ⚠️ Para REVISÃO — Bloqueadas mas ATIVAS no Oracle

**Nenhuma.** Zero empresas da Lista Negra estão com STATUS='0' (Ativo) no Oracle. Nenhuma remoção sugerida.

---

## 📈 Totalização para Aprovação

| Ação | Qtd |
|---|---|
| 🔴 Incluir (STATUS=1 — Bloqueado) | 0 |
| 🟡 Incluir (STATUS=3 — Encerrado) | 0 |
| 🟠 Avaliar (STATUS=2 — Cancelado) | 79 |
| ⚠️ Remover (ativos sem dívida) | 0 |

**Sem alterações pendentes esta semana.** A Lista Negra está plenamente alinhada com o Oracle TEST_MATRIZ.

### Recomendação
- **Manter Lista Negra como está** — todos os 89 bloqueios são corroborados pelo Oracle.
- **Avaliar os 79 STATUS=2 (Cancelados)** — Sérgio pode decidir se algum deles deve ser incluído na Lista Negra. Recomendo priorizar os que tiveram movimentação recente (ex: HOSTEL CANTINHO DO CUNTA, última movimentação 2025-11-25) e os que aparecem em múltiplos CNPJs (TOP SERVICE).
- **Próximo cruzamento:** Segunda-feira, 23/06/2026.

---

Aguardando validação do Sérgio. ✅
