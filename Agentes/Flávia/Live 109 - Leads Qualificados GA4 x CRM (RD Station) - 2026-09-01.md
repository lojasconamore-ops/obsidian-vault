---
tags: [ga4, rd-station, crm, conversao-offline, server-side, aprendizado]
fonte: "https://www.youtube.com/watch?v=uLgRHx8FNf0"
autor: "Celso Cestaro (Data Growth) — LIVE 109"
assistido: 2026-09-01
---

# Live 109 — Como medir Leads Qualificados no GA4 integrando c/ CRM (RD Station, Salesforce, etc)

> Fonte: Celso Cestaro (consultoria Data Growth), live semanal sobre GA4/GTM/tracking/atribuição.
> Semana anterior: "Conversões Offline do Google Ads" (com Marco Lambert) — continuação lógica desta live.

## Ideia central (1 frase)
O GA4 lançou (jul/2025) relatórios de **leads** que mostram a evolução do lead **além do formulário** (MQL → SQL → fechado/perdido), mas isso **só funciona com tracking server-side + integração própria via webhook**, NÃO com a integração nativa do CRM (RD Station nativo "não traz a realidade dos dados").

## O problema que resolve
- Antes: só se media o `generate_lead` (formulário preenchido).
- Nada sobre o que acontece DEPOIS: quem qualificou, quem foi trabalhado, quem fechou.
- Empresas com venda consultiva (B2B, imobiliária, clínica, hotelaria) precisam saber qual campanha/canal avança de verdade na pipeline — não só quem levantou a mão.

## Os eventos recomendados do GA4 (categoria "gerar leads")
| Evento | Significado |
|---|---|
| `generate_lead` | Formulário preenchido (o que todo mundo já mede) |
| `qualify_lead` | Lead **qualificado** (MQL — critério do marketing) |
| `working_lead` | SDR/closer **trabalhando** o lead (status) |
| `close_convert_lead` | Lead **convertido** (venda fechada) |
| `close_unconvert_lead` | Lead **não convertido** (perdido) |

Cada evento com nome "recomendado" **destrava relatórios prontos** no GA4 (tipo `purchase`/`checkout` destravam relatórios de e-commerce).

## Relatório "Gerar Leads" no GA4 (3 divisões)
1. **Novos leads** → todos os leads gerados
2. **Leads qualificados** → momento em que avançou no CRM (HubSpot/RD/Salesforce/Pipedrive)
3. **Leads convertidos** → os que geraram venda

Permite quebrar por **primeira origem/mídia, campanha, termo, conjunto de anúncio** → ver qual canal traz mais PIPELINE AVANÇADA (não só lead cru).

## Parâmetros exigidos por evento (Measurement Protocol)
- `qualify_lead` → **value + currency** (R$). Por que? Para monetizar o pipeline.
- `working_lead` → **lead_status** (obrigatório) + `item name` (opcional, o que o lead queria).
- Motivos de perda/desqualificação também são parâmetros → populam relatório de **motivo da perda do lead** e **motivo de desqualificação**.

### Como estimar o value do lead
- Taxa de aproveitamento (lead → fechado) costuma ser 10–20%.
- `value_lead = taxa_aproveitamento × ticket_médio`.
- Um MQL vale menos que um lead fechado (fica explícito no cálculo).

## Arquitetura obrigatória (o "como faz")
```
Formulário (site)
  → grava lead em BASE DE DADOS (Firebase/Supabase) com UTM/campanha/origem/cookie de sessão
CRM (RD Station etc) [avancou de etapa]
  → dispara WEBHOOK (muda status do lead)
  → GTM SERVER-SIDE (cliente webhook) recebe o evento (lado web NÃO recebe evento offline)
      → consulta a BASE e cruza por e-mail → recupera UTM/atribuição original
      → envia via Measurement Protocol p/ GA4 (client_id + dados do evento + SECRET TOKEN)
```

Pontos-chave:
- **Server-side é obrigatório** — evento de CRM é offline, não chega pelo navegador.
- **Token/API Secret**: fica em Admin → Fluxo de dados → "Measurement Protocol API secrets". Sem token o GA4 não aceita.
- Webhook = comunicação sistema→URL. **Praticamente todo CRM tem webhook** (RD, HubSpot, Pipedrive, Manychat...). Testar o payload do lado do GTM Server.

## Pegadinha #1 — Integração NATIVA não serve
A integração nativa RD↔GA4 **não traz atribuição correta** (perde UTM/origem/campanha). Só vai levar "lead gerado", sem a qualificação. Por isso a base de dados própria (gravar UTM no momento do form) + cross-reference por e-mail é o padrão recomendado.

## Pegadinha #2 — Análise enviesada (atribuição)
- Não olhar só "leads qualificados/convertidos" de forma isolada.
- Canal pode **não converter em último clique** mas ser o **primeiro contato** (topo do funil) — tirá-lo do ar derruba todo o mix.
- Sempre cruzar com **relatórios de Publicidade do GA4** (modelos de atribuição, caminhos de conversão) antes de cortar investimento.

## Pegadinha #3 — UTM dentro do site
Nunca colocar UTM em banner/link interno do próprio site (sobrescreve a origem real da campanha de Ads). Para medir clique interno, usar **evento customizado** com parâmetros (texto/ID do clique), não URL parametrizada.

## Q&A relevantes
- **"A integração do RD Station já deixa tudo configurado?"** → Não. É preciso estrutura extra (base + webhook + sGTM).
- **"Manychat tem webhook?"** → Sim (procurar "webhook" na automação/API da plataforma; quase todo CRM tem).

## Aplicação na Conamore (Flávia)
- Conamore é B2B hotelaria com **RD Station** e pipeline consultiva → caso clássico desta live.
- Ponto de atenção: já temos `compra_erp`/webhook `/purchase_erp` (venda B2B) e estudo de Enhanced Conversions for Leads (nota [[Drinks/Enhanced Conversions for Leads — Desenho Técnico 2026-08-29]]) — este framework dos eventos `qualify_lead`/`working_lead`/`close_convert_lead` é o complemento "pipeline", enquanto o de hoje foca na "nível acima do formulário".
- Consolida a tese do meu memory: integração nativa RD não basta; Nexopath GCLID (cf_gclid vazio por Consent Mode) reforça que a atribuição server-side é o caminho.

## Status
- [x] Conteúdo entendido e organizado
- [ ] Avaliar implementação de `qualify_lead`/`working_lead` no RD + sGTM Conamore (pedir autorização DigitalCEO)
