# Consent Mode GA4 — Teste diário 2026-08-31

- **Horário:** 08:05 BRT
- **URL:** https://www.conamore.com.br/
- **GA4:** `properties/379729087` / `G-V0KMM7L6M6`
- **GTM:** `GTM-MMGX8ZL`

## Teste ao vivo

- Sessão limpa: `consent default` com `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization` e `personalization_storage` em `denied`; comportamento inicial esperado.
- Botão real acionado: **Aceitar Tudo**.
- Após escolha: `consent update` com os cinco campos em `granted`.
- Persistência: `cc_cookie_consent_status=true`; preferências `marketing=true` e `statistics=true`.
- Recarregamento após aceite: coleta confirmada em `gtmserver.conamore.com.br/g/collect`, `tid=G-V0KMM7L6M6`, evento `PageView`.
- `gtag` carregado e `dataLayer` ativo.
- Sem erros JavaScript não capturados. Falhas CORS de Reclame Aqui/Veels e aviso de moeda do Meta Pixel são terceiros, sem causalidade demonstrada com GA4.

## GA4 consolidado — D-3 (2026-08-28)

- Sessões: **1.865**
- Sessões engajadas: **1.008**
- Bounce rate: **45,95%**
- Duração média: **4m18,7s**
- Principais fontes: Google 1.334 sessões / 44,23% bounce; direto 252 / 59,92%; Instagram 100 / 54,00%.
- Não há queda sistêmica de engajamento nem bounce acima de 95% em todas as fontes. Buckets com 100% de bounce têm volume residual.

## Status

**Funcionando.** Fluxo pós-consentimento e coleta GA4 confirmados. Nenhuma anomalia sistêmica no D-3.
