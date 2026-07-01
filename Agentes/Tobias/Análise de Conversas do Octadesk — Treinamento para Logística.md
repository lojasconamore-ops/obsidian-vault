# Análise de Conversas do Octadesk — Treinamento para Logística

> **Autora:** Natália — Gerente Comercial
> **Público:** Tobias — Logística
> **Objetivo:** Capacitar o Tobias a extrair, analisar e interpretar as conversas do Octadesk do setor de Logística (Eduardo), gerando relatórios diários de atendimento — de forma semelhante ao que a Natália faz para o relatório da Casa (Joana + Fabiana).

- [[Agentes/Tobias/Rotina Operacional|Rotina operacional]]
- [[Agentes/Matias/Integração Octadesk|Integração Octadesk]]

---

## 1. Por que analisar conversas do Octadesk?

O Octadesk é o canal de WhatsApp da Conamore. **Toda interação com clientes** — vendas, pós-venda, logística — passa por ele. Analisar essas conversas permite:

- **Medir volume e qualidade do atendimento** do Eduardo (Logística)
- **Identificar gargalos** recorrentes (entregas atrasadas, falta de rastreio, erros de endereço)
- **Detectar tensões e insatisfações** antes que escalem para reclamação formal
- **Criar base de conhecimento** para respostas padronizadas (ex: prazos por região, como rastrear)
- **Gerar relatórios diários** para a gestão (Sergio, DigitalCEO)

---

## 2. Acesso ao Banco de Dados

As conversas do Octadesk ficam no **SQL Server `hotel-finder`**, schema `octa`.

### Conexão (Python + pymssql)

```python
import pymssql

conn = pymssql.connect(
    server='40.125.121.83',
    user='hotelfinder',
    password='saoroque2024!',
    database='hotel-finder'
)
cursor = conn.cursor()
```

> ⚠️ **Apenas `pymssql` funciona.** `sqlcmd` não está instalado no ambiente.

---

## 3. Schema `octa` — Tabelas Relevantes

| Tabela/View | Conteúdo | Colunas-chave |
|---|---|---|
| `octa.chats` | Mensagens individuais (WhatsApp) | `chat_id`, `agent`, `contact_name`, `msg_time_sent`, `sender_type`, `content`, `group_name`, `sender` |
| `octa.conversations` | Metadados dos chats | `chat_id`, `status` (talking/closed/waiting), `opened_at`, `closed_at` |
| `octa.customers` | Contatos/clientes | `id`, `name`, `email`, `phone`, `CNPJ_CPF`, `cod_cliente_debx` |
| `octa.mensagens_dia` | View agregada diária por agente | `data`, `agent`, `sender_type`, `total_messages` |
| `octa.v_conversas_no_dia` | View agregada: conversas/dia por vendedor | `data`, `vendedor`, `conversas_no_dia` |

### Colunas críticas de `octa.chats`

| Coluna | Tipo | Descrição |
|---|---|---|
| `chat_id` | nvarchar | ID único da conversa |
| `agent` | nvarchar | Nome do atendente (pode ser NULL → usar `ISNULL(agent, 'N/A')`) |
| `contact_name` | nvarchar | Nome do contato, formato `"Nome Cliente (Vendedor)"` |
| `msg_time_sent` | datetime2 | **UTC** — sempre converter para BRT (subtrair 3h) |
| `sender_type` | varchar | `'agent'` (Eduardo) ou `'contact'` (cliente) |
| `content` | nvarchar | Corpo da mensagem (pode conter HTML: `<p>`, `<br>`, `<span>`) |

### Agentes do setor de Logística

| Agente | Nome no Octadesk |
|---|---|
| Eduardo | `Eduardo` |

> 📦 **Logística** tem apenas 1 atendente: **Eduardo**. Ele cuida de consultas de entrega, prazos, rastreio, SLA e problemas de frete.

---

## 4. ⚠️ Fuso Horário — Regra de Ouro

O SQL Server armazena **TUDO em UTC**. Para exibir em horário de Brasília:

```
DB_time - 3h = BRT
```

**Exemplo:** `14:00 UTC = 11:00 BRT`

### Filtro de data correto

Para pegar o **dia de ontem** em BRT, o filtro em UTC é:

```sql
-- Ontem em BRT = msg_time_sent entre ontem 03:00 e hoje 03:00 (UTC)
WHERE msg_time_sent >= '2026-06-29 03:00:00'
  AND msg_time_sent <  '2026-06-30 03:00:00'
```

**Por quê?** Meia-noite BRT = 03:00 UTC. Se usar `CAST(msg_time_sent AS DATE)`, os registros entre 00:00-02:59 UTC do dia D+1 vão parar no dia errado.

### Conversão no Python

```python
from datetime import timedelta

def to_brt(db_timestamp):
    """Converte timestamp UTC do banco para BRT (UTC-3)."""
    return db_timestamp - timedelta(hours=3)
```

---

## 5. Queries para Logística

### 5.1 Verificar nome exato do agente

```sql
SELECT DISTINCT agent FROM octa.chats WHERE agent LIKE '%Eduardo%' ORDER BY agent;
```

### 5.2 Resumo do dia — Eduardo

```sql
SELECT
    COUNT(*) as total_msgs,
    COUNT(DISTINCT chat_id) as total_chats,
    COUNT(DISTINCT contact_id) as total_contacts,
    SUM(CASE WHEN sender_type = 'agent' THEN 1 ELSE 0 END) as msgs_agente,
    SUM(CASE WHEN sender_type = 'contact' THEN 1 ELSE 0 END) as msgs_cliente,
    MIN(msg_time_sent) as primeira_msg,
    MAX(msg_time_sent) as ultima_msg
FROM octa.chats
WHERE agent = 'Eduardo'
  AND msg_time_sent >= '2026-06-29 03:00:00'
  AND msg_time_sent <  '2026-06-30 03:00:00';
```

### 5.3 Status das conversas (talking vs closed)

```sql
SELECT
    conv.status,
    COUNT(DISTINCT c.chat_id) as chats
FROM octa.chats c
JOIN octa.conversations conv ON c.chat_id = conv.chat_id
WHERE c.agent = 'Eduardo'
  AND c.msg_time_sent >= '2026-06-29 03:00:00'
  AND c.msg_time_sent <  '2026-06-30 03:00:00'
GROUP BY conv.status
ORDER BY chats DESC;
```

### 5.4 Engajamento por conversa (alta/média/toque)

```sql
SELECT
    COUNT(*) as total_chats,
    SUM(CASE WHEN msgs >= 8 THEN 1 ELSE 0 END) as alta,
    SUM(CASE WHEN msgs BETWEEN 3 AND 7 THEN 1 ELSE 0 END) as media,
    SUM(CASE WHEN msgs <= 2 THEN 1 ELSE 0 END) as toque_unico
FROM (
    SELECT chat_id, COUNT(*) as msgs
    FROM octa.chats
    WHERE agent = 'Eduardo'
      AND msg_time_sent >= '2026-06-29 03:00:00'
      AND msg_time_sent <  '2026-06-30 03:00:00'
    GROUP BY chat_id
) sub;
```

### 5.5 Detalhamento: top conversas do Eduardo

```sql
SELECT
    c.chat_id,
    MIN(c.contact_name) as cliente,
    COUNT(*) as msgs,
    SUM(CASE WHEN c.sender_type = 'agent' THEN 1 ELSE 0 END) as msgs_agente,
    SUM(CASE WHEN c.sender_type = 'contact' THEN 1 ELSE 0 END) as msgs_cliente,
    MIN(c.msg_time_sent) as inicio,
    MAX(c.msg_time_sent) as fim,
    MAX(CASE WHEN conv.status IS NOT NULL THEN conv.status END) as status
FROM octa.chats c
LEFT JOIN octa.conversations conv ON c.chat_id = conv.chat_id
WHERE c.agent = 'Eduardo'
  AND c.msg_time_sent >= '2026-06-29 03:00:00'
  AND c.msg_time_sent <  '2026-06-30 03:00:00'
GROUP BY c.chat_id
ORDER BY msgs DESC;
```

### 5.6 Curva horária de atividade

```sql
SELECT
    DATEPART(HOUR, msg_time_sent) as hora_utc,
    COUNT(*) as mensagens
FROM octa.chats
WHERE agent = 'Eduardo'
  AND msg_time_sent >= '2026-06-29 03:00:00'
  AND msg_time_sent <  '2026-06-30 03:00:00'
GROUP BY DATEPART(HOUR, msg_time_sent)
ORDER BY hora_utc;
```

> ⚠️ A hora retornada é **UTC**. Subtraia 3 para obter BRT. Ex: `hora_utc=14` → `11h BRT`.

### 5.7 Buscar palavras-chave logísticas

```sql
SELECT contact_name, msg_time_sent, sender_type,
       LEFT(content, 300) as trecho
FROM octa.chats
WHERE agent = 'Eduardo'
  AND msg_time_sent >= '2026-06-29 03:00:00'
  AND msg_time_sent <  '2026-06-30 03:00:00'
  AND (content LIKE '%rastreio%'
    OR content LIKE '%entrega%'
    OR content LIKE '%prazo%'
    OR content LIKE '%frete%'
    OR content LIKE '%atraso%'
    OR content LIKE '%endereço%'
    OR content LIKE '%endereco%'
    OR content LIKE '%transportadora%'
    OR content LIKE '%SLA%'
    OR content LIKE '%não chegou%'
    OR content LIKE '%nao chegou%'
    OR content LIKE '%devolução%'
    OR content LIKE '%devolucao%')
ORDER BY msg_time_sent;
```

### 5.8 Buscar sinais de tensão/insatisfação

```sql
SELECT contact_name, chat_id, msg_time_sent, sender_type,
       LEFT(content, 400) as trecho
FROM octa.chats
WHERE agent = 'Eduardo'
  AND msg_time_sent >= '2026-06-29 03:00:00'
  AND msg_time_sent <  '2026-06-30 03:00:00'
  AND sender_type = 'contact'
  AND (content LIKE '%urgente%'
    OR content LIKE '%absurdo%'
    OR content LIKE '%reclama%'
    OR content LIKE '%cobrando%'
    OR content LIKE '%já faz%'
    OR content LIKE '%ja faz%'
    OR content LIKE '%sem resposta%'
    OR content LIKE '%cancelar%'
    OR content LIKE '%resolver%'
    OR content LIKE '%satisfeito%'
    OR content LIKE '%decepcionado%')
ORDER BY msg_time_sent;
```

### 5.9 Conteúdo completo de um chat específico

```sql
SELECT msg_time_sent, sender_type, content
FROM octa.chats
WHERE chat_id = '<CHAT_ID>'
ORDER BY msg_time_sent ASC;
```

---

## 6. Limpeza de Conteúdo HTML

As mensagens frequentemente vêm com HTML (`<p>`, `<br>`, `<span>`). Limpe antes de exibir:

```python
import re

def clean_content(text):
    if not text:
        return ''
    text = re.sub(r'<[^>]+>', '', text)
    text = text.replace('&nbsp;', ' ').replace('&lt;', '<').replace('&gt;', '>')
    return text.strip()
```

---

## 7. Classificações e Interpretações para Logística

### Engajamento

| Classificação | Critério | Significado para Logística |
|---|---|---|
| **Alta** | 8+ msg/chat | Caso complexo: rastreio de extravio, disputa de frete, múltiplas tentativas de entrega |
| **Média** | 3-7 msg/chat | Consulta padrão: prazo, código de rastreio, confirmação de endereço |
| **Toque único** | 1-2 msg/chat | Cliente pediu rastreio e recebeu (resolvido rápido) OU cliente não respondeu |

### Métrica-chave para Logística

| Métrica | Referência | Alerta |
|---|---|---|
| **% Alta (8+)** | Esperado > 60% dos chats | < 40% = Eduardo pode estar resolvendo muito rápido ou evitando casos complexos |
| **% Toque único** | Esperado < 25% | > 40% = cliente abandonou sem solução |
| **Chats fechados** | Esperado > 70% | < 50% = muitos casos abertos, risco de SLA estourado |
| **Média msg/chat** | Esperado > 8 | < 5 = atendimento muito superficial |

### Sinais de alerta na Logística

| Tema | Exemplos de palavras | Gravidade |
|---|---|---|
| Atraso na entrega | `"atrasado"`, `"não chegou"`, `"já faz X dias"` | 🔴 Alta |
| Falta de rastreio | `"não consigo rastrear"`, `"código não funciona"` | 🟡 Média |
| Erro de endereço | `"endereço errado"`, `"entregou no lugar errado"` | 🔴 Alta |
| Transportadora | `"transportadora não atende"`, `"não recebi ligação"` | 🟡 Média |
| Frete divergente | `"frete mais caro que o combinado"`, `"cobrança indevida"` | 🔴 Alta |
| Ameaça de cancelamento | `"cancelar pedido"`, `"devolver"`, `"quero reembolso"` | 🔴 Crítica |
| Reclamação explícita | `"absurdo"`, `"reclamação"`, `"insatisfeito"`, `"decepcionado"` | 🔴 Crítica |

---

## 8. Estrutura do Relatório Diário — Logística

O relatório deve seguir este formato:

```
📦 RELATÓRIO DIÁRIO DE ATENDIMENTO — LOGÍSTICA
   Data: DD/MM/AAAA (referente a DD/MM/AAAA)
   Atendente: Eduardo
   Fonte: Octadesk (SQL Server hotel-finder / schema octa)
   ⏰ Todos os horários em BRT (UTC-3)

1. RESUMO EXECUTIVO
   - Total de mensagens, chats, clientes
   - Proporção agente/cliente
   - Status: talking vs closed
   - ⚠️ Se houver tensões críticas, DESTACAR AQUI NO TOPO

2. ⚠️ ATENÇÃO CRÍTICA — TENSÕES E INSATISFAÇÕES (se houver)
   Para cada caso crítico:
   - Cliente/contato
   - Sinais objetivos observados
   - Motivo provável
   - Prioridade de tratamento (Imediata / Hoje / Esta semana)

3. MÉTRICAS DE ATENDIMENTO
   - Tabela: total msgs, chats, média msg/chat, alta, média, toque único
   - Status: talking, closed, waiting
   - Jornada: primeira e última mensagem do dia
   - Tempo médio de resposta (se disponível)

4. TOP CONVERSAS DO DIA
   - Tabela: # | cliente | msgs | tema principal | status
   - Destaque para os 3 casos mais relevantes com contexto

5. CURVA HORÁRIA
   - Tabela com hora (BRT) e intensidade
   - Identificar picos (ex: manhã 9-11h, tarde 14-16h)

6. TEMAS RECORRENTES
   - Rastreio: X consultas
   - Prazo de entrega: X consultas
   - Problema com transportadora: X casos
   - Erro de endereço: X casos
   - Outros

7. O QUE ACERTOU
   - Casos resolvidos rapidamente
   - Feedbacks positivos de clientes
   - Boas práticas observadas

8. PONTOS A MELHORAR
   - Oportunidades de agilizar resposta
   - Padronização de respostas
   - Follow-ups pendentes

9. PLANO DE AÇÃO
   - Prioridades para hoje
   - Casos que precisam de follow-up
   - Melhorias de processo sugeridas

10. CHECKLIST DE QUALIDADE
    - [ ] Todos os rastreios foram enviados?
    - [ ] Casos urgentes foram escalados?
    - [ ] Transportadoras notificadas sobre atrasos?
    - [ ] Clientes com problema receberam retorno?
```

---

## 9. Dicas de Análise Qualitativa

Além dos números, **leia algumas conversas** para entender o contexto real:

1. **Pegue os 3 chats com mais mensagens** — leia a conversa completa. O que o cliente queria? Foi resolvido? Quanto tempo levou?

2. **Pegue os 3 chats fechados mais recentes** — o fechamento foi satisfatório? O cliente saiu feliz?

3. **Varra menções a palavras de insatisfação** — `urgente`, `reclamação`, `absurdo`, `cancelar`, `não chegou`. Esses casos exigem atenção imediata.

4. **Compare dias consecutivos** — o volume está subindo? As reclamações estão aumentando?

5. **Identifique padrões** — se 5 clientes diferentes reclamam da mesma transportadora, é um problema estrutural (não do Eduardo).

---

## 10. Pitfalls Específicos

| # | Pitfall | Solução |
|---|---|---|
| 1 | **Fuso horário:** esquecer de converter UTC → BRT | Subtrair 3h de TODOS os timestamps. Usar `to_brt()` no Python. |
| 2 | **Filtro de data errado:** `CAST(msg_time_sent AS DATE)` quebra na madrugada | Usar o padrão `>= 'D-1 03:00' AND < 'D 03:00'` (UTC) |
| 3 | **Timeout em queries complexas:** JOINs aninhados podem estourar 30s | Prefira 3 queries simples a 1 complexa. Não aninhe subqueries desnecessárias. |
| 4 | **`agent IS NULL` vs `agent = 'N/A'`** | Sempre usar `ISNULL(agent, 'N/A')` para unificar |
| 5 | **Conteúdo vazio:** mensagens sem texto (imagens/anexos) | Normal — não é erro. Apenas marque como `(anexo/mídia)`. |
| 6 | **`contact_name` inclui o agente:** ex: `"Joicimeire Cruz  (Joana)"` | Sempre use `LIKE '%parte%'`, nunca `=`. |
| 7 | **SQL cobre APENAS WhatsApp:** chats internos do Octadesk não estão no banco | Para chats internos (gerentes ↔ agentes Hermes), use a API REST do Octadesk. |
| 8 | **Suposição sem evidência:** "cliente parecia irritado" sem trecho comprovando | Sempre cite trecho real. Se não houver evidência objetiva, não classifique como tensão. |
| 9 | **Ignorar o follow-up:** relatório sem plano de ação é só diagnóstico | Sempre inclua próximos passos concretos. |

---

## 11. Script Base (Python + pymssql)

```python
import pymssql
import re
from datetime import date, datetime, timedelta
from collections import defaultdict

# ── Config ──────────────────────────────────────────────────
DB = {
    'server': '40.125.121.83',
    'user': 'hotelfinder',
    'password': 'saoroque2024!',
    'database': 'hotel-finder'
}
AGENTE = 'Eduardo'
TODAY = date.today()
TARGET_DATE = TODAY - timedelta(days=1)  # Ontem

# Datas em UTC para o filtro correto
data_inicio_utc = f"{TARGET_DATE.isoformat()} 03:00:00"
data_fim_utc = f"{TODAY.isoformat()} 03:00:00"

# ── Conexão ─────────────────────────────────────────────────
conn = pymssql.connect(**DB)
cur = conn.cursor()

# ── Helpers ─────────────────────────────────────────────────
def to_brt(ts):
    if ts is None:
        return None
    return ts - timedelta(hours=3)

def clean(text):
    if not text:
        return ''
    text = re.sub(r'<[^>]+>', '', text)
    return text.replace('&nbsp;', ' ').strip()

# ── Q1: Resumo ──────────────────────────────────────────────
cur.execute(f"""
    SELECT
        COUNT(*) as total_msgs,
        COUNT(DISTINCT chat_id) as total_chats,
        COUNT(DISTINCT contact_id) as total_clients,
        SUM(CASE WHEN sender_type='agent' THEN 1 ELSE 0 END) as a_msgs,
        SUM(CASE WHEN sender_type='contact' THEN 1 ELSE 0 END) as c_msgs,
        MIN(msg_time_sent) as first,
        MAX(msg_time_sent) as last
    FROM octa.chats
    WHERE agent = '{AGENTE}'
      AND msg_time_sent >= '{data_inicio_utc}'
      AND msg_time_sent <  '{data_fim_utc}'
""")
total_msgs, total_chats, total_clients, a_msgs, c_msgs, first, last = cur.fetchone()

print(f"📦 Logística — {TARGET_DATE.strftime('%d/%m/%Y')} (Eduardo)")
print(f"   Mensagens: {total_msgs} | Chats: {total_chats} | Clientes: {total_clients}")
print(f"   Agente: {a_msgs} msg | Clientes: {c_msgs} msg")
if first and last:
    print(f"   Jornada: {to_brt(first).strftime('%H:%M')} → {to_brt(last).strftime('%H:%M')} BRT")

# ── Q2: Status ──────────────────────────────────────────────
cur.execute(f"""
    SELECT conv.status, COUNT(DISTINCT c.chat_id)
    FROM octa.chats c
    JOIN octa.conversations conv ON c.chat_id = conv.chat_id
    WHERE c.agent = '{AGENTE}'
      AND c.msg_time_sent >= '{data_inicio_utc}'
      AND c.msg_time_sent <  '{data_fim_utc}'
    GROUP BY conv.status
""")
print("\n   Status:", dict(cur.fetchall()))

# ── Q3: Engajamento ─────────────────────────────────────────
cur.execute(f"""
    SELECT
        COUNT(*) as chats,
        SUM(CASE WHEN msgs >= 8 THEN 1 ELSE 0 END) as alta,
        SUM(CASE WHEN msgs BETWEEN 3 AND 7 THEN 1 ELSE 0 END) as media,
        SUM(CASE WHEN msgs <= 2 THEN 1 ELSE 0 END) as toque
    FROM (
        SELECT chat_id, COUNT(*) as msgs
        FROM octa.chats
        WHERE agent = '{AGENTE}'
          AND msg_time_sent >= '{data_inicio_utc}'
          AND msg_time_sent <  '{data_fim_utc}'
        GROUP BY chat_id
    ) sub
""")
chats, alta, media, toque = cur.fetchone()
print(f"   Engajamento: alta={alta} ({100*alta//max(chats,1)}%) | média={media} | toque={toque}")

# ── Q4: Top conversas ───────────────────────────────────────
cur.execute(f"""
    SELECT TOP 10
        c.chat_id,
        MIN(c.contact_name) as cliente,
        COUNT(*) as msgs,
        MIN(c.msg_time_sent) as inicio,
        MAX(c.msg_time_sent) as fim,
        MAX(CASE WHEN conv.status IS NOT NULL THEN conv.status END) as status
    FROM octa.chats c
    LEFT JOIN octa.conversations conv ON c.chat_id = conv.chat_id
    WHERE c.agent = '{AGENTE}'
      AND c.msg_time_sent >= '{data_inicio_utc}'
      AND c.msg_time_sent <  '{data_fim_utc}'
    GROUP BY c.chat_id
    ORDER BY msgs DESC
""")
print("\n   Top conversas:")
for i, (chat_id, cliente, msgs, ini, fim, status) in enumerate(cur.fetchall(), 1):
    ini_brt = to_brt(ini).strftime('%H:%M') if ini else '?'
    print(f"   {i}. {cliente[:40] if cliente else '(sem nome)':40s} | {msgs:3d} msg | {ini_brt} | {status or '?'}")

# ── Q5: Palavras de tensão ──────────────────────────────────
cur.execute(f"""
    SELECT contact_name, LEFT(content, 200) as trecho
    FROM octa.chats
    WHERE agent = '{AGENTE}'
      AND msg_time_sent >= '{data_inicio_utc}'
      AND msg_time_sent <  '{data_fim_utc}'
      AND sender_type = 'contact'
      AND (content LIKE '%urgente%' OR content LIKE '%reclama%'
        OR content LIKE '%absurdo%' OR content LIKE '%cancelar%'
        OR content LIKE '%não chegou%' OR content LIKE '%nao chegou%'
        OR content LIKE '%insatisf%' OR content LIKE '%decepcion%')
""")
tensoes = cur.fetchall()
if tensoes:
    print(f"\n   ⚠️  ALERTAS DE TENSÃO ({len(tensoes)} ocorrências):")
    for nome, trecho in tensoes:
        print(f"   • {nome}: \"{clean(trecho)[:100]}...\"")
else:
    print("\n   ✅ Nenhum sinal de tensão detectado.")

# ── Cleanup ─────────────────────────────────────────────────
conn.close()
```

---

## 12. Checklist de Execução Diária

- [ ] Conectar ao `hotel-finder`
- [ ] Rodar query de resumo (Q1)
- [ ] Rodar query de status (Q2)
- [ ] Rodar query de engajamento (Q3)
- [ ] Rodar top conversas (Q4) e ler as 3 principais
- [ ] Rodar busca de tensões (Q5)
- [ ] Verificar curva horária (Q6)
- [ ] Cruzar com dados de vendas/entregas se necessário
- [ ] Escrever relatório seguindo a estrutura da seção 8
- [ ] Se houver tensão crítica, destacar no topo com ⚠️
- [ ] Salvar em `Agentes/Tobias/Relatórios/Octadesk-Logistica-YYYY-MM-DD.md`

---

> *"Logística não é só entregar caixa. É entregar confiança."*

---

## Apêndice A: Referência Rápida de Queries

```sql
-- Vendedores ativos no Octadesk (todos)
SELECT agent, COUNT(*) as msgs
FROM octa.chats
WHERE msg_time_sent >= DATEADD(DAY, -7, GETDATE())
GROUP BY agent ORDER BY msgs DESC;

-- Clientes do Eduardo (últimos 30 dias)
SELECT DISTINCT contact_name, contact_id
FROM octa.chats
WHERE agent = 'Eduardo'
  AND msg_time_sent >= DATEADD(DAY, -30, GETDATE())
ORDER BY contact_name;

-- Média de mensagens por chat do Eduardo (últimos 7 dias)
SELECT AVG(msgs * 1.0) as media_msg_por_chat
FROM (
    SELECT chat_id, COUNT(*) as msgs
    FROM octa.chats
    WHERE agent = 'Eduardo'
      AND msg_time_sent >= DATEADD(DAY, -7, GETDATE())
    GROUP BY chat_id
) sub;

-- Temas mais mencionados pelos clientes (últimos 7 dias)
SELECT
    SUM(CASE WHEN content LIKE '%rastreio%' THEN 1 ELSE 0 END) as rastreio,
    SUM(CASE WHEN content LIKE '%entrega%' THEN 1 ELSE 0 END) as entrega,
    SUM(CASE WHEN content LIKE '%prazo%' THEN 1 ELSE 0 END) as prazo,
    SUM(CASE WHEN content LIKE '%frete%' THEN 1 ELSE 0 END) as frete,
    SUM(CASE WHEN content LIKE '%atraso%' OR content LIKE '%atrasad%' THEN 1 ELSE 0 END) as atraso
FROM octa.chats
WHERE agent = 'Eduardo'
  AND msg_time_sent >= DATEADD(DAY, -7, GETDATE())
  AND sender_type = 'contact';
```

## Apêndice B: Conversão para PDF

Para gerar PDF a partir do markdown:

```bash
pip install weasyprint markdown
```

```python
import markdown
from weasyprint import HTML

with open('relatorio.md', 'r') as f:
    md = f.read()

html_body = markdown.markdown(md, extensions=['tables', 'fenced_code'])
html = f"""<!DOCTYPE html>
<html lang="pt-BR">
<head><meta charset="utf-8">
<style>
  @page {{ size: A4; margin: 2cm 2.2cm; }}
  body {{ font-family: Arial, sans-serif; font-size: 10.5pt; line-height: 1.5; color: #1a1a1a; }}
  h1 {{ color: #2563eb; font-size: 18pt; border-bottom: 2px solid #2563eb; }}
  h2 {{ color: #2563eb; font-size: 13pt; border-bottom: 1px solid #e0e0e0; }}
  th {{ background-color: #2563eb; color: white; padding: 6px 8px; }}
  td {{ padding: 5px 8px; border: 1px solid #ddd; }}
  tr:nth-child(even) td {{ background-color: #f8f9fa; }}
  blockquote {{ border-left: 3px solid #2563eb; padding: 8px 14px; background: #f0f4ff; }}
</style></head><body>{html_body}</body></html>"""

HTML(string=html).write_pdf('relatorio.pdf')
```
