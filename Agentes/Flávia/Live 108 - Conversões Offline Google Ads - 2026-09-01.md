---
tags: [google-ads, conversao-offline, ecl, crm, attribution, aprendizado]
fonte: "https://www.youtube.com/watch?v=URxX9Z5PGGA"
autor: "Celso Cestaro + Marco Lambert (Data Growth) — LIVE 108"
assistido: 2026-09-01
relacionado: "[[Live 109 - Leads Qualificados GA4 x CRM (RD Station) - 2026-09-01]], [[Enhanced Conversions for Leads — Desenho Técnico 2026-08-29]], [[Diagnóstico compra_erp vs DEBX — schemas não mapeados 2026-08-29]]"
---

# Live 108 — Conversões Offline do Google Ads (celso + marco lambert)

> Precursora da Live 109. Aqui o foco é **Google Ads** (não GA4); a 109 foca GA4. As duas compõem a mesma tese: parar de otimizar para "lead" e passar a otimizar para o que gera receita.

> ⚠️ Nota de extração: peguei a descrição completa + a abertura da live (~5 min). A transcrição completa ficou bloqueada (bot-wall do YouTube no painel de transcrição + IP cloud bloqueado no youtube-transcript-api). O que segue combina isso com o contexto técnico que já tenho documentado (ECL / compra_erp / Nexopath).

## Ideia central
Uma mudança recente (17/08) nos **lances smart bidding (CPA desejado / ROAS desejado)** do Google Ads tornou ainda mais crítico o dado que você entrega ao algoritmo. Se você otimiza para `lead` (conversão do site), o Google aprende a trazer **lead**, não **venda**. A solução é mandar a **Conversão Offline** — o que acontece no CRM depois do clique.

## Contexto — a mudança nos lances (17/08)
- Lances `CPA desejado` / `ROAS desejado` passaram a impactar mais diretamente **como** o Google trabalha as campanhas.
- Resultado: otimizar para uma conversão que **não representa receita** fica ainda mais caro/errado.

## O problema central (por que o lead é insuficiente)
| O Google vê | O seu negócio vê |
|---|---|
| Lead (formulário) | Lead qualificado (MQL) |
| — | Oportunidade (SQL) |
| — | Venda / Receita |

Se o algoritmo só recebe `lead`, ele otimiza pra quem levanta a mão — não pra quem **fecha**.

## O que é Conversão Offline
Tudo que acontece **fora do site** e fica registrado no CRM (HubSpot, RD Station, Pipedrive...):
- Test drive agendado (concessionária)
- Consulta realizada (clínica)
- **Venda B2B fechada** (nosso caso, hotelaria)
- Case da live: **clínica** — o que mexe ponteiro é cirurgia/consulta, não o lead do formulário.

## A solução — Enhanced Conversions for Leads + upload offline
1. Lead converte no site (form → CRM já captura email/telefone).
2. Venda/qualificação acontece **offline** no CRM.
3. Envia-se essa conversão de volta ao Google Ads por **first-party data (email/telefone com hash SHA-256)** — funciona mesmo sem GCLID.
4. O algoritmo passa a otimizar para o dado **mais próximo do resultado real**.

## Arquitetura (igual à que já desenhamos)
```
Contato avança/qualifica/fecha no CRM (RD Station)
  → webhook dispara
  → orquestrador (n8n / GTM server-side) recebe
  → normaliza + hash (email/telefone)
  → upload via Click Conversions API / Data Manager → Google Ads
```
Marco Lambert (convidado) opera a frente de `n8n` + códigos que une online↔offline na Data Growth.

## Tópicos que a live promete cobrir (da descrição)
- O que muda no CPA/ROAS desejado
- Por que depender só de conversões do site prejudica a otimização
- Como funcionam as Conversões Offline no Google Ads
- Como as Conversões para Leads alimentam o algoritmo com dado real
- Dicas de conexão CRM + Tracking + Google Ads
- Como fazer o Google entender quais leads têm valor

## Relação direta com a Conamore
- Temos exatamente o caso da live: B2B hotelaria, pipeline no RD Station, venda consultiva, `compra_erp` (nossa conversão B2B no Ads).
- **Problema espelhado:** nossa `compra_erp` captura só ~17% do faturamento (R$530k vs R$3,14M real) — o algoritmo está aprendendo com dado **incompleto e enviesado**, exatamente o alerta do Celso/Marco.
- **Já em andamento:** [[Enhanced Conversions for Leads — Desenho Técnico 2026-08-29]] (upload first-party por email/telefone para fechar a atribuição sem GCLID) e a correção do cf_gclid Nexopath (topo).
- A Live 109 (GA4) é o **complemento de pipeline**; esta 108 é o **complemento de fechamento** — juntas formam o funil completo (gerar → qualificar → converter) para alimentar Ads + GA4.

## Status
- [x] Conteúdo entendido e organizado
- [ ] ECL (fechamento) — desenho pronto, aguardando execução
- [ ] Leads Qualificados GA4 (pipeline) — desenho pronto, aguardando autorização
