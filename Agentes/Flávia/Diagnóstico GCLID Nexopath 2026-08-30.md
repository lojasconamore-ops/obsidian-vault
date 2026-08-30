# Diagnóstico — Captura de GCLID (Nexopath rd-click-id.js) — 30/08/2026

**Autor:** Flávia (Marketing)
**Contexto:** leads do RD Station com `cf_gclid` vazio (0/13 amostrados em 29/08).

## Conclusão

O script `rd-click-id.js` da Nexopath **ESTÁ disparando e capturando o gclid no navegador**, mas o dado **não chega ao RD Station** por **dois defeitos distintos**.

## Evidência de que a captura client-side funciona

Teste em `https://www.conamore.com.br/?gclid=teste123abc`:

| Sinal | Valor observado |
|---|---|
| `localStorage.nexopath_rd_click_id_gclid` | `{"value":"teste123abc", ...}` ✅ |
| Cookie `_gcl_aw` | `GCL.1788086771.teste123abc` ✅ |
| Cookie RD `__trf.src` | `current_session.value = "gclid=teste123abc"` ✅ |

## Causa raiz 1 — Token `t` malformado (quebra o beacon ECL)

A tag carrega:
`https://nexopath.com/rd-click-id.js?t=822d2690-5b46-440-953-cfb1d93702ea`

- O token `822d2690-5b46-440-953-cfb1d93702ea` tem **34 caracteres** (segmentos 8-4-3-3-12).
- Um UUID válido tem **36** (8-4-4-4-12). Os grupos 3 e 4 estão com 3 chars em vez de 4.
- O script valida `token()` com regex `/^[0-9a-f-]{36}$/i` → **rejeita** → retorna `''`.
- Consequência: a função `send()` (hash SHA-256 do email + gclid → `POST https://nexopath.com/api/track/{token}` → Google Ads ECL) **nunca dispara** (`if (!publicToken || ...) return`).

Ou seja: a "Conversões Otimizadas no Google Ads" via Nexopath está **inerte por token truncado**.

## Causa raiz 2 — Formulário sem campo `cf_gclid`

A função `fill()` do script só preenche `input[name="gclid"]` ou `input[name="cf_gclid"]`.

O form do RD Station (action `cta-redirect.rdstation.com/v2/conversions`) NÃO tem nenhum desses campos. Campos presentes: `token_rdstation`, `conversion_identifier`, `internal_source`, `c_utmz`, `traffic_source`, `client_id`, `_doe`, `privacy_data[browser]`, `name`, `email`, `personal_phone`, consent.

Consequência: mesmo capturando o gclid, não há campo de destino → o campo customizado `cf_gclid` fica vazio.

## Onde corrigir

1. **Token:** no container GTM `GTM-MMGX8ZL` (a tag Nexopath é injetada via GTM — não está no HTML cru; o GTM carrega via `/metrics/?id=GTM-MMGX8ZL`). Corrigir o `t` para o UUID válido de 36 chars do painel Nexopath.
2. **Campo `cf_gclid`:** adicionar campo oculto `cf_gclid` ao formulário RD Station (mapeado ao custom field), OU injetar via GTM um input oculto `cf_gclid` no form (o `fill()` do script, via MutationObserver, preenche quando o campo aparecer).

## Pendências

- Token correto da Nexopath (painel) — precisa do valor de 36 chars.
- Decisão: priorizar ECL (token) vs. campo `cf_gclid` (form), ou ambos.
