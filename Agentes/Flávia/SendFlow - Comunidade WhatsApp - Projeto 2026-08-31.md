# SendFlow — Comunidade WhatsApp (Projeto)

**Criado:** 31/08/2026 · Flávia (Marketing)
**Origem:** conversa Sérgio × ChatGPT ("Como funciona a Sendflow") — https://chatgpt.com/share/6a9657ef-b328-83e9-89d3-d56db1e23dcb
**Status:** em análise pré-decisão

---

## 🎯 Resumo executivo (1 minuto)

Proposta: trocar o **outbound 1:1 em massa** por uma **comunidade de WhatsApp opt-in** (SendFlow), com número dedicado, grupo fechado (só admin publica) e funil limpo:

```
Grupo (conteúdo em escala) → interesse → privado (Octadesk) → vendedor → pedido
```

**Achado-chave:** a API oficial do WhatsApp **não faz grupos** (limite de 8 participantes). Logo, o modelo de comunidade **só existe via API não oficial** — o risco de bloqueio é inerente ao caso de uso, não é "defeito" do SendFlow.

**Decisão real:** "aceitamos o risco de bloqueio (mitigado)?" — não "qual ferramenta?".

**Veredito da Flávia:** aceitar, com mitigação forte (número dedicado + cadência baixa + grupo fechado + co-admin de resgate). SendFlow tem **API completa + webhooks + MCP** e integra com Octadesk/RD de forma **100% automática**.

---

## 1. A estratégia (o que foi desenhado)

- **Entrada:** 100% voluntária (opt-in).
- **Grupo:** somente administradores publicam (fechado).
- **Frequência:** 2–3 posts/semana.
- **Mix de conteúdo:** ~70% valor / 20% produto / 10% oferta.
- **Separação de função:** SendFlow = mídia/comunidade; Octadesk = atendimento/venda.
- **Número:** dedicado ao SendFlow (nunca o do Octadesk).
- **Inversão de lógica:** de "achar quem quer comprar" para "criar ambiente onde o interessado levanta a mão".

**Benefícios:**
1. Opt-in real (filtra audiência, melhora base).
2. Cliente controla o incômodo (silencia quando quiser).
3. Conamore controla a pressão comercial (cadência centralizada).
4. **Remarketing orgânico**: mantém o gerente de hotel "quente" por meses até o momento da compra.

---

## 2. Comparativo de API (o achado-chave)

| Critério | SendFlow (não oficial) | API oficial (Zenvia/360dialog/Gupshup) |
|---|---|---|
| **Grupos/comunidade** | ✅ core do produto, ilimitado | ❌ 8 participantes/grupo (inviável) |
| **Canais/status** | ✅ | ❌ |
| **Custo** | Assinatura fixa (previsível) | Por mensagem (Meta) + taxa BSP |
| **Risco de bloqueio** | ⚠️ sim (não oficial) | ✅ baixo |
| **Responsabilidade por bloqueio** | ❌ SendFlow se exime (ToS §7.4) | — (oficial) |
| **Onboarding** | rápido | lento (verificação Meta) |
| **Melhor para** | comunidade/demanda | 1:1, transacional, broadcast |

**Nota:** a Groups API oficial (Cloud API, 2026) exige *Official Business Account*, limita a **8 participantes/grupo**, 10.000 grupos/número, sem endpoint de adicionar participante diretamente. Comunidades/canais/status não existem na API oficial.

## 3. Preços

**SendFlow (semestral):**
- **Lite** — R$ 1.500/semestre (~R$250/mês) · 1 número · grupos/mensagens ilimitados
- **Standard** — R$ 3.000/semestre (~R$500/mês) · 3 números · 2 acessos extras
- **Black** — R$ 5.000/semestre (~R$833/mês) · 5 números · 5 acessos extras

**API oficial:** sem mensalidade fixa; Meta cobra por conversa — marketing ~R$0,32 · utility ~R$0,04 · autenticação ~R$0,03 (+ taxa do provedor).

**Recomendação:** Lite para o piloto (~R$250/mês).

---

## 4. Capacidades técnicas (API / MCP / webhooks)

### SendFlow
- **Base URL:** `https://sendflow.pro/sendapi` · auth `Authorization: <API_KEY>`
- **Campanhas/grupos:** `POST/PUT/DELETE /releases/{id}` — config inclui `admins`, `onlyAdminsSpeak`, `limit` (350), `communityEnabled`.
- **Listar grupos:** `GET /releases/{id}/groups` (id, nome, gid/jid, inviteCode, participantsAmount, admins).
- **Opt-in:** `GET /releases/{id}/join-requests` + `POST .../join-requests` approve/reject (em lote).
- **Métricas/analytics** da campanha + **leadscoring** (gerar + baixar).
- **Link de redirect** da campanha: `PATCH .../redirect` (o link rastreável).
- **Webhooks:** `release.join-request.created`, entrada/saída de membros (tempo real).
- **MCP server (open-source):** `AllissonOliveira/sendflow-mcp` (base URL padrão = sendapi) → eu conecto igual ao MCP do RD.
- **Orquestração:** n8n (tutorial oficial "Sendflow API e N8N").

### Octadesk
- **API Key:** Configurações > API. **Base URL:** `https://<subdominio>.api001.octadesk.services`.
- Endpoints: criar contato/ticket/organização, `chat/send-template`, get chat by id.
- **Webhooks:** eventos de contato/ticket criado/alterado.
- **Bot:** "Conectar a outro sistema" (API síncrona) + "Aguardar Evento Externo" (webhook assíncrono).

### Integração automática SendFlow → Octadesk + RD
```
Grupo SendFlow → evento (entrada/clique/mensagem) → webhook SendFlow
  → Flávia (ou n8n) → Octadesk API: cria contato/ticket origem "sendflow_grupo"
  → RD Station: cria/atualiza lead com tag origem_sendflow_grupo
```

**Caso mais poderoso (resolve a atribuição):** `join-request.created` (opt-in) traz o telefone → aprovo via API → crio contato no Octadesk + tag no RD → lead já nasce rastreado, **sem depender do vendedor marcar origem**.

---

## 5. Atribuição (3 níveis)

```
GRUPO (post) → CLIQUE (link rastreável) → PRIVADO (Octadesk) → VENDEDOR → PEDIDO (ERP)
```

- **Nível 1 — Clique (auto, GA4+RD):** CTA = link rastreável → redirect (GA4 + tracking RD) → wa.me. UTM: `utm_source=sendflow` · `utm_medium=whatsapp_grupo` · `utm_campaign=comunidade_<segmento>` · `utm_content=<slug>`.
- **Nível 2 — Lead (RD):** wa.me com `?text=Olá! Vim pelo grupo [Comunidade Conamore]` (pré-preenchido) + tag `origem_sendflow_grupo`.
- **Nível 3 — Venda (ERP):** cruzar pedido (Oracle DEBX) com contato RD (tag de origem); mesmo cruzamento do webhook `compra_erp`.

**Painel:** topo = cliques/post (GA4) · meio = conversas origem grupo (Octadesk/RD) · fundo = vendas da comunidade (ERP×RD).

**Pegadinha:** o elo fraco era o vendedor marcar origem — resolvido com opt-in automatizado (webhook + API), que já cria o lead rastreado.

---

## 6. Mitigação de risco de bloqueio

1. **Isolamento:** número 100% dedicado (nunca Octadesk (19) 98211-7472). Chip novo.
2. **Aquecimento:** 2–4 semanas em volume baixo (1:1) antes de abrir grupo; crescer gradual.
3. **Audiência:** só opt-in (nunca adicionar manualmente); base limpa; exportar backup semanal.
4. **Cadência:** 2–3 posts/semana, máx 1/dia/grupo; 70/20/10; horário comercial.
5. **Técnica:** Spintax ativo; anti-spam/anti-hacker/blacklist; ~350 leads/grupo; monitorar delivery.
6. **Plano B:** co-admin de resgate dentro de cada grupo desde o dia 1 (Sérgio no piloto). Se o número principal cair → co-admin adiciona o número novo, promove a admin, reconecta no SendFlow. Membros NÃO precisam ser reconvidados.
7. **LGPD:** opt-in auditável (data+origem) no RD; dono da comunidade definido.

**🚫 Red lines:** usar número do Octadesk · adicionar membro sem consentimento · disparo em massa no 1º dia · >1 post/dia/grupo · texto idêntico sem Spintax.

**Detalhe de troca de número:** conectar número novo no SendFlow é simples, mas ele **não herda os grupos/membros** — por isso o co-admin é obrigatório, não opcional. Confirmar com o suporte se a troca de número no meio do plano é liberada.

---

## 7. Operação diária

**Ciclo:** post agendado → membros leem → clicam "fale no privado" → Octadesk → vendedor → venda (2–3x/semana).

| Dia | Ação | Quem | Automático? |
|---|---|---|---|
| Seg | Planejar/agendar posts da semana | Flávia (rascunho) + Sérgio (aprova) | agendamento sim |
| Ter | Post #1 (valor) 10h | agendado | ✅ |
| Qua | Monitorar cliques/entradas | Flávia (cron) | ✅ |
| Qui | Post #2 (produto/oferta) 10h | agendado | ✅ |
| Sex | Relatório do funil | Flávia (cron) | ✅ |
| Contínuo | Aprovar entradas, triagem, backup | Flávia (webhook) + vendedores | ✅ aprovação |

**Automatizado (Flávia + API/webhook):** aprovação de entrada + tag RD + contato Octadesk · agendamento/disparo (Spintax) · boas-vindas · anti-spam · monitoramento diário (cron) · relatório semanal (cron) · backup.

**Humano (mínimo):** conteúdo (eu rascunho, você aprova, ~1–2h/semana) · atendimento/venda (vendedores, já existente) · exceções (denúncia/bloqueio).

**Funções:**
- **Flávia:** conteúdo, automação, monitoramento, métricas (contínua).
- **Sérgio:** aprovar conteúdo/ações + co-admin de resgate (~30 min/semana).
- **Matias (TI):** setup inicial — API Keys, página de redirect, integração Octadesk (1x).
- **Vendedores:** atender no Octadesk + fechar pedido (diária, já existente).
- **Marketing (Camila/Jo/Junior):** alinhamento editorial + campanhas (semanal/quinzenal).

---

## 8. Pendências / próximos passos

- [ ] **Decisão:** aceitar o piloto (risco mitigado) — aguardando Sérgio.
- [ ] Obter **API Key SendFlow** (após assinatura) + confirmar endpoints/troca de número com suporte.
- [ ] Obter **API Key Octadesk** (verificar com Matias se já existe).
- [ ] Testar **MCP do SendFlow** localmente.
- [ ] **Matias:** página de redirect (GA4 + RD) + config integração Octadesk.
- [ ] **Flávia:** criar tag `origem_sendflow_grupo` no RD + template de link UTM.
- [ ] Comprar **número dedicado** + chip reserva (co-admin = Sérgio no piloto).
- [ ] Validar **LGPD** do opt-in com Adrian (Jurídico) — em paralelo ao consent mode em aberto.

---

## 📎 Referências
- Conversa ChatGPT: https://chatgpt.com/share/6a9657ef-b328-83e9-89d3-d56db1e23dcb
- SendFlow site/preços: https://sendflow.com.br / https://sendflow.pro
- SendFlow API docs: https://sendflow.pro/sendapi
- SendFlow MCP: github.com/AllissonOliveira/sendflow-mcp
- SendFlow ToS (exime de bloqueio, §7.4): https://sendflow.pro/termo-de-uso
- WhatsApp Group API (limite 8): unipile.com/br/whatsapp-group-api
- Octadesk API: developers.octadesk.com
