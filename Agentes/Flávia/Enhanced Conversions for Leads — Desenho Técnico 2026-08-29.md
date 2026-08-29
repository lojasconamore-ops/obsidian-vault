# Enhanced Conversions for Leads — Desenho Técnico (Conamore)

**Gerado em:** 29/08/2026 · Flávia (Marketing)
**Conta:** Google Ads `AW-1041572367` · customer_id `2335779078`

## Objetivo
Restabelecer a atribuição de vendas off-line B2B no Google Ads usando first-party data (e-mail/telefone dos leads), em vez do GCLID — que a Conamore não está capturando (verificado no RD Station em 29/08).

## Por que Enhanced Conversions for Leads (ECL)
- A venda B2B fecha off-line (anúncio → contato → atendimento → orçamento → link de pagamento).
- O GCLID não está sendo capturado em lugar nenhum (RD Station grava só `utm`, `extra_params` vazio).
- O ECL faz match por **e-mail/telefone (hash SHA-256)**, dado que o RD Station **já tem** — funciona mesmo sem GCLID.
- Bônus: se também capturar o GCLID, o match rate sobe ainda mais.

## Fluxo end-to-end

```
[1] Clique no anúncio → Google gera GCLID
        ↓
[2] Lead converte no site → form RD Station captura e-mail/telefone (+ GCLID se configurado)
        ↓
[3] RD Station guarda o lead (e-mail/telefone/utm)  ← já funciona hoje
        ↓
[4] Venda fecha off-line → Oracle DEBX registra pedido + Pagar.me confirma pagamento
        ↓
[5] Middleware detecta o fechamento:
      · busca o lead (e-mail/telefone) no RD Station
      · normaliza + hash SHA-256
      · chama Google Ads Data Manager API (upload com user_identifiers)
        ↓
[6] Google faz match (hash → usuário logado Google + GCLID se houver) → atribui a conversão
```

## Componentes e responsabilidades

| # | Componente | Dono | O que faz |
|---|---|---|---|
| 1 | Ação de conversão no Ads | Flávia | Criar/ajustar ação "Compra Offline B2B" (PURCHASE) com ECL ativado |
| 2 | Captura do lead | Site/RD Station | Form já captura e-mail/telefone. Opcional: adicionar GCLID |
| 3 | Middleware de upload | Increazy ou Matias | Job que lê pedido fechado → normaliza/hash → upload |
| 4 | Fonte de verdade do fechamento | Oracle DEBX + Pagar.me | Gatilho do upload (pedido fechado + pagamento confirmado) |
| 5 | LGPD | Adrian | Base legal + política de privacidade |

## Regras de normalização + hash (CRÍTICO)

**E-mail**
1. `trim` (remover espaços início/fim)
2. `lowercase`
3. SHA-256 → hexadecimal

**Telefone**
1. Formato E.164: `+55` + DDD + número (ex.: `+5519982117472`)
2. Remover espaços, traços e parênteses
3. SHA-256 → hexadecimal

Exemplos:
- `"  Joao.Silva@GMAIL.com  "` → `joao.silva@gmail.com` → sha256 → `9c3b…`
- `"(19) 98211-7472"` → `+5519982117472` → sha256 → `a1f2…`

## Payload do upload (Data Manager API / ConversionUploadService)

```json
{
  "conversion_action": "customers/2335779078/conversionActions/<ID>",
  "gclid": "TeQ6aR... (opcional, mas recomendado)",
  "conversion_value": 8500.00,
  "conversion_date_time": "2026-08-26 14:30:00-03:00",
  "currency_code": "BRL",
  "order_id": "PED-12345",
  "user_identifiers": [
    { "hashed_email": "<sha256 do e-mail>" },
    { "hashed_phone_number": "<sha256 do telefone E.164>" }
  ]
}
```

## Checklist de implementação

1. **Ads:** criar/ajustar ação de conversão "Compra Offline B2B" (categoria PURCHASE), ativar Enhanced Conversions for Leads, janela de 90 dias.
2. **Captura (opcional):** cookie `_gclid` + campo oculto no form + campo customizado `gclid` no RD Station.
3. **Middleware (server-side):** job que lê pedidos fechados do Oracle DEBX, cruza com RD Station (e-mail/telefone), normaliza + hash, envia via Data Manager API e loga sucesso/erro (com `order_id` para idempotência).
4. **LGPD:** validar base legal com Adrian + atualizar política de privacidade.
5. **Validação:** 1 pedido de teste → conferir match no Ads → escalar.

## Pontos de atenção
- **Hash errado = match zero.** Testar com os vetores oficiais do Google antes de produção.
- **Idempotência:** guardar `order_id` para não re-enviar o mesmo pedido (evita conversão duplicada).
- **Janela:** conversões além de 90 dias do clique não contam (configurável).
- **GCLID é bônus:** sem ele o ECL funciona por e-mail/telefone hash; com ele, o match rate sobe.
- **Quota:** developer token tem limite (vimos 429) → middleware precisa de backoff/retry.
- **Consentimento:** leads já têm consentimento `communications` no RD Station; validar interesse legítimo para medição.
