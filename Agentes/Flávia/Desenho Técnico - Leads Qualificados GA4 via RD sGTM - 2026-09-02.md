---
tags: [ga4, rd-station, crm, conversao-offline, server-side, projeto, desenho-tecnico]
fonte: "Live 109 Celso Cestaro — Leads Qualificados GA4 x CRM"
gerado: 2026-09-02
status: rascunho-para-avaliacao
---

# Desenho Técnico — Leads Qualificados GA4 (qualify_lead / working_lead / close_convert_lead) via RD Station + sGTM

> Complemento de pipeline ao [[Enhanced Conversions for Leads — Desenho Técnico 2026-08-29]] (que cobre o FECHAMENTO/first-party para Google Ads).
> Aqui cobrimos a EVOLUÇÃO DO LEAD dentro do funil RD → eventos recomendados do GA4.

## Objetivo
Popular no GA4 os eventos de "gerar leads" (`qualify_lead`, `working_lead`, `close_convert_lead`, `close_unconvert_lead`) a partir das **mudanças de etapa no funil do RD Station**, ganhando relatórios "Gerar Leads" (novos/qualificados/convertidos × origem/campanha) e alimentando a atribuição server-side.

## Por que vale a pena (nosso caso)
- Conamore é B2B hotelaria com venda consultiva (SDR/comercial), pipeline no RD → é exatamente o cenário da live.
- Hoje medimos só o `generate_lead` (form) e a venda final (`compra_erp`). O **meio do funil é uma caixa-preta**: não sabemos qual campanha gera lead que AVANÇA.
- Decisões de investimento (Meta vs Google Ads vs orgânico) hoje são feitas às cegas no meio da jornada.

## Ativos que JÁ temos (reduz muito o esforço)
| Ativo | Estado |
|---|---|
| sGTM Stape `GTM-N7Z62R96` | ✅ ativo |
| GTM web `GTM-MMGX8ZL` | ✅ ativo |
| Webhook receptor server-side | ✅ precedente: `/purchase_erp` (Increazy) e webhook "Oportunidade" Nexopath |
| RD captura `client_id` + `utm_*` + email/telefone no contato | ✅ (form já tem campo `client_id`) |
| Funil/etapas no RD (contact_funnel_stage) | ✅ existe (MCP) |
| `compra_erp` = venda B2B no Ads | ✅ |

## Gap de infra (o que falta)
1. **Webhook no RD** disparando quando o contato **muda de etapa no funil** (RD Station Marketing tem automação/webhook → validar endpoint exato e payload).
2. **Cliente "webhook" no sGTM** recebendo esse evento (analogia do que já fazemos com `purchase_erp`).
3. **Mapeamento etapa→evento** + **value** + envio via Measurement Protocol (client_id do contato + API secret).

> Diferente da live do Celso, NÃO precisamos de Firebase/Supabase de cross-reference: o RD já guarda `client_id` + `utm_*` no próprio contato. Cruzamento por e-mail é interno ao RD.

## Mapeamento etapa RD → evento GA4 (a validar etapas reais)
| Etapa do funil RD (proposta) | Evento GA4 | Params |
|---|---|---|
| Lead novo (form preenchido) | `generate_lead` | (já existe) |
| Qualificado / MQL | `qualify_lead` | `value` + `currency=BRL` |
| Em atendimento (SDR/comercial) | `working_lead` | `lead_status` (+ `item_name` opcional) |
| Oportunidade ganha (venda) | `close_convert_lead` | `value` (ticket real) + `currency` |
| Oportunidade perdida | `close_unconvert_lead` | `lead_status` + motivo |

### Estimativa de `value` (qualify_lead)
`value = taxa_aproveitamento × ticket_médio_B2B`
- taxa_aproveitamento: 10–20% (calibrar com Comercial/DEBX)
- ticket_médio: usar dado real do DEBX (não chutar)

## Fluxo end-to-end
```
Contato muda etapa no RD (ex.: → "Qualificado")
  → Webhook RD dispara (evento etapa + email/client_id)
  → sGTM (cliente webhook) recebe
      → mapeia etapa → evento recomendado
      → monta payload MP: client_id (do contato) + event params + SECRET TOKEN
      → POST https://www.google-analytics.com/mp/collect?measurement_id=...&api_secret=...
  → GA4 registra qualify_lead (com client_id → cruza com sessão/UTM original)
```

## Configuração crítica (Measurement Protocol)
- **API Secret**: Admin → Fluxo de dados (GA4 Hotelaria `379729087`) → Measurement Protocol API secrets → gerar token.
- **client_id**: vem do campo `client_id` que o RD já captura (senão o MP não associa à sessão/atribuição e o evento fica "órfão").
- Dedup: usar event id/idempotência para não duplicar em reenvio de webhook.

## Fases de implementação
| Fase | O quê | Dono | Esforço |
|---|---|---|---|
| F1 — Mapear etapas reais do funil RD | Listar etapas + nomes exatos via MCP/Comercial | Flávia | baixo |
| F2 — Webhook RD (mudança de etapa) | Configurar automação/webhook p/ endpoint sGTM | Flávia + Matias | médio |
| F3 — Cliente sGTM + mapeamento + MP | endpoint receptor, map etapa→evento, MP c/ secret | Matias (TI) | médio |
| F4 — Value/calibragem | definir ticket médio + taxa aproveitamento (DEBX) | Flávia + Comercial | baixo |
| F5 — Validação | 1 lead teste por etapa → conferir no GA4 DebugView | Flávia | baixo |
| F6 — Monitoramento 7d | relatórios "Gerar Leads" × atribuição | Flávia | — |

## Decisões a escalar (DigitalCEO / Sérgio)
1. **Autorizar o projeto** (F1–F2 já são baratos e reversíveis; F3 envolve TI/Matias).
2. **API Secret novo no GA4** — criação de chave de medição (ação com impacto em dados de medição).
3. **Ticket médio + taxa de aproveitamento** — precisa de dado do DEBX/Comercial para o `value` (não inventar).
4. **Prioridade**: isso vs. terminar ECL (fechamento) vs. corrigir cf_gclid Nexopath (topo). Sugiro sequência: terminamos o que está pendente primeiro (cf_gclid + ECL), e damos início a F1 em paralelo (mapear etapas é leitura pura).

## Riscos / atenção
- **Etapas do funil RD bagunçadas** → mapeamento errado contamina todo o relatório. Validar antes.
- **Consent Mode**: cf_gclid/tag bloqueada por consent pode afetar também o MP server-side → alinhar com Matias (consent ainda quebrado desde 29/08).
- **client_id ausente** em alguns contatos antigos → evento "órfão" sem atribuição (não quebra, mas não agrega).
- **Quota/limite MP**: backoff em rajada de webhooks.
- **LGPD**: eventos de medição com first-party, base legal a validar com Adrian.

## Status
- [ ] F1 mapear etapas (pode iniciar já — leitura pura)
- [ ] Aguardando autorização DigitalCEO p/ F2–F3
