# 📊 Relatório Cruzamento Lista Negra — 19/06/2026

**Data:** 19/06/2026 08:41 BRT
**Executor:** Tiago — Gerente Financeiro
**Fontes:** Oracle TEST_MATRIZ (F_CDEMP) + Lista Negra Conamore (Obsidian)

---

## 🔢 Resumo

| Métrica | Qtd |
|---|---|
| Lista Negra Conamore | 89 |
| Inativas Oracle (STATUS≠0) | 168 |
| ✅ Consistentes (bloqueadas E inativas) | 87 |
| 🔴 Sugestão INCLUIR (STATUS=3) | 2 |
| 🟠 Avaliar (STATUS=2) | 79 |
| ⚠️ Revisar (bloqueadas mas ATIVAS) | 2 |

---

## 🔴 Sugestões de INCLUSÃO — STATUS=3 (Encerrado Oracle)

| Código | Razão Social | CNPJ | Observação |
|---|---|---|---|
| `01077` | RAFAEL LIMA VIANA | 00005559958360 | CPF mascarado — mesmo CPF de `1077` já na LN |
| `02064` | JESSE TEIXEIRA | 00027624027860 | CPF mascarado — mesmo CPF de `2064` já na LN |

> **Nota:** São duplicatas de cadastro (CPF com zeros à esquerda). `1077` e `2064` já estão na Lista Negra — estes são os mesmos clientes com código diferente. **Não requer ação.**

---

## ⚠️ Para REVISÃO — Bloqueadas mas ATIVAS no Oracle

| Código LN | Razão Social | CNPJ | Observação |
|---|---|---|---|
| `1077` | RAFAEL LIMA VIANA | 055.599.583-60 | Versão ATIVA no Oracle. Inativa sob código `01077` |
| `2064` | JESSE TEIXEIRA | 276.240.278-60 | Versão ATIVA no Oracle. Inativa sob código `02064` |

> **Nota:** Ambos têm duplicata inativa (STATUS=3) no Oracle. São casos de duplicidade de cadastro, não de desbloqueio indevido. **Não requer ação.**

---

## 🟠 Para AVALIAÇÃO — STATUS=2 (Cancelado Oracle)

**79 empresas.** Destaques:

| Código | Razão Social | CNPJ |
|---|---|---|
| `00731` | HOSTEL CANTINHO DO CUNTA LTDA | 12.100.430/0001-64 |
| `01455` | AQUARIOS ALIMENTAÇOES LTDA EPP | 05.806.850/0001-03 |
| `02148` | SERVICO SOCIAL DO COMERCIO SESC | 03.482.931/0001-61 |
| `02399` | UNITED LAB MEDICINA E FERTILIDADE LTDA | 58.251.793/0001-00 |
| `03006` | SANTA CASA DE MISERICORDIA DE RIBEIRAO CLARO | 80.724.586/0001-76 |
| `04727` | HOTEL DAN INN SÃO CARLOS | 04.192.534/0003-80 |
| `04764` | ARGENTIN PALACE HOTEL LTDA | 65.580.517/0001-42 |
| `36727` | SENAC | 03.709.814/0057-42 |
| `89471` | IRMANDADE DA SANTA CASA DE MISERICORDIA DE SAO CARLOS | 59.610.394/0001-42 |
| `01093~01171` | **TOP SERVICE** (10 filiais) | 00.973.749/xxxx-xx |

Lista completa disponível na execução do job semanal.

---

## 📈 Totalização para Aprovação

| Ação | Qtd | Status |
|---|---|---|
| 🔴 Incluir (STATUS=3) | 2 | ⚠️ Duplicatas — sem ação necessária |
| 🟠 Avaliar (STATUS=2) | 79 | A definir |
| ⚠️ Revisar/remover | 2 | ⚠️ Duplicatas — sem ação necessária |

---

**✅ Status:** Nenhuma alteração urgente pendente. Lista Negra está consistente com Oracle em 87/89 (97,8%).

*Próxima execução automática: segunda-feira 22/06/2026 às 08:05 BRT.*
