# 📊 Cruzamento Semanal — Lista Negra × Oracle TEST_MATRIZ

**Data:** 22 Jun 2026 (segunda-feira) 08:08 BRT
**Executor:** Tiago — Gerente Financeiro
**Oracle:** `TEST_MATRIZ.F_CDEMP` @ 172.169.0.11 — 168 inativas (STATUS≠0)

---

## 🔢 Resumo

| Métrica | Qtd |
|---|---|
| Lista Negra Conamore | 89 |
| Inativas Oracle (STATUS≠0) | 168 |
| ✅ Consistentes (bloqueadas E inativas) | 89 |
| 🔴 Sugestão INCLUIR (STATUS=1 — Bloqueado) | 0 |
| 🟡 Sugestão INCLUIR (STATUS=3 — Encerrado) | 0 |
| 🟠 Avaliar (STATUS=2 — Cancelado) | 79 |
| ⚠️ Revisar (bloqueadas mas ATIVAS) | 0 |

---

## ✅ Status Geral: **Lista Negra 100% consistente com Oracle**

Todas as 89 empresas da Lista Negra Conamore estão com status **inativo** no Oracle TEST_MATRIZ. Não foi identificada nenhuma empresa bloqueada na Lista Negra que esteja ATIVA no Oracle — zero divergências.

**Distribuição dos status Oracle das 89 empresas da LN:**

| Status Oracle | Significado | Qtd LN |
|---|---|---|
| `1` | Bloqueado | 27 |
| `3` | Encerrado | 62 |
| **Total** | | **89** |

---

## 🔴 Sugestões de INCLUSÃO — STATUS=1 (Bloqueado Oracle)

**Nenhuma.** Todas as 27 empresas com STATUS='1' no Oracle já estão na Lista Negra.

---

## 🟡 Sugestões de INCLUSÃO — STATUS=3 (Encerrado Oracle)

**Nenhuma.** Todas as 62 empresas com STATUS='3' no Oracle já estão na Lista Negra.

---

## 🟠 Para AVALIAÇÃO — STATUS=2 (Cancelado Oracle)

**79 empresas** estão com STATUS='2' (Cancelado) no Oracle e NÃO constam na Lista Negra. Muitas são registros de teste, cadastros CPF com padding de zeros, ou empresas que nunca efetivaram compra.

### Destaques (não exaustivo):

| Código | Razão Social | CNPJ | Cadastro |
|---|---|---|---|
| 01093–01171 | TOP SERVICE SERVICOS E SISTEMAS S/A (10 filiais) | 00.973.749/xxxx-xx | Dez/2025 |
| 02148 | SERVICO SOCIAL DO COMERCIO SESC | 03.482.931/0001-61 | Fev/2026 |
| 02793 | INSTITUTO NACIONAL DE DESENVOLVIMENTO SOCIAL E HUMANO | 23.453.830/0004-12 | Mar/2026 |
| 03006 | SANTA CASA DE MISERICORDIA DE RIBEIRAO CLARO | 80.724.586/0001-76 | Mar/2026 |
| 04727 | HOTEL DAN INN SÃO CARLOS | 04.192.534/0003-80 | Mai/2026 |
| 04764 | ARGENTIN PALACE HOTEL LTDA | 65.580.517/0001-42 | Jun/2026 |
| 05106 | MUNICIPIO DE SAO SEBASTIAO DO PARAISO | 18.241.349/0001-80 | Jun/2026 |
| 36727 | SENAC CAMPINAS | 03.709.814/0057-42 | Nov/2024 |
| 89471 | SANTA CASA DE MISERICORDIA DE SAO CARLOS | 59.610.394/0001-42 | Mar/2025 |

**Recomendação:** STATUS='2' representa cancelamento (não bloqueio nem encerramento). Muitos são cadastros de proposta que não avançaram. **Nenhuma ação sugerida esta semana** — manter em observação. Se algum desses CNPJs aparecer em uma análise de crédito futura, o histórico de cancelamento no Oracle será um sinal de alerta.

---

## ⚠️ Para REVISÃO — Bloqueadas mas ATIVAS no Oracle

**Nenhuma.** Todas as 89 empresas da Lista Negra estão com STATUS≠0 no Oracle — ou seja, nenhuma está ATIVA.

---

## 📈 Totalização para Aprovação

| Ação | Qtd |
|---|---|
| 🔴 Incluir (STATUS=1) | **0** |
| 🟡 Incluir (STATUS=3) | **0** |
| ⚠️ Remover (ativos sem dívida) | **0** |

**Sem alterações pendentes esta semana ✅**

---

## 🔍 Observações Técnicas

### CPF Masking
- **Código 1077** (RAFAEL LIMA VIANA, CPF 055.599.583-60) — corresponde ao código Oracle `01077` (CNPJ 00005559958360, STATUS=3). CPF com padding de zeros — mesma pessoa, não duplicata.
- **Código 2064** (JESSE TEIXEIRA) — corresponde ao código Oracle `02064`. Padrão de padding similar.

### CNPJ Duplicado
- **Código 88839** (DECORACAO E CIA LTDA) e **Código 90150** (CIA E ARTE DECORACAO E CIA) — **mesmo CNPJ** 14.627.870/0001-08. Ambos constam como STATUS='1' no Oracle. Possível duplicata na Lista Negra.

### SAAM TOWAGE BRASIL S.A.
- **10 filiais** diferentes (CNPJs distintos) na Lista Negra — todas confirmadas como STATUS='3' no Oracle. Consistente.

---

## 📋 Metodologia

1. Lista Negra lida de `~/Documents/Obsidian Vault/Agentes/Tiago/Lista Negra.md` (89 entradas)
2. Oracle consultado via `oracledb` — query em `TEST_MATRIZ.F_CDEMP WHERE EMP_STATUS != '0'` (168 registros)
3. Cruzamento por código normalizado (sem prefixo 'A') e por CNPJ (apenas dígitos)
4. Classificação conforme workflow padrão de reconciliação

**Conexão Oracle:** ✅ Disponível. Sem retentativas necessárias.

---

Aguardando validação do Sérgio. Nenhuma alteração sugerida para a Lista Negra esta semana.
