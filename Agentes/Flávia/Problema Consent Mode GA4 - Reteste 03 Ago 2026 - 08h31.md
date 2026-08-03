# Reteste de Consent Mode e disparo de tags — 03/08/2026

**Horário:** 08:31 BRT  
**URL:** https://www.conamore.com.br/  
**GA4:** `G-V0KMM7L6M6`  
**GTM:** `GTM-MMGX8ZL`

## Estado inicial

- Sessão limpa: `cc_cookie_consent_status` e `cc_cookie_preferences` ausentes.
- Banner de privacidade visível.
- `gtag`: function.
- `dataLayer`: disponível, 10 entradas.
- Consent Mode inicial:
  - `analytics_storage: denied`;
  - `ad_storage: denied`;
  - `ad_user_data: denied`;
  - `ad_personalization: denied`;
  - `personalization_storage: denied`;
  - `functionality_storage` e `security_storage`: granted.

## Após “Aceitar Tudo”

- Banner ocultado.
- `consent update` disparado.
- `analytics_storage`: `granted`.
- Categorias de marketing: `granted`.
- Evento customizado: `cc_consent_update`.
- Preferências persistidas:
  - `cc_cookie_consent_status: true`;
  - `cc_cookie_preferences: {marketing:true, statistics:true}`.
- Cookies GA4 presentes:
  - `_ga`;
  - `_ga_V0KMM7L6M6`;
  - `_ga_CDCKFVTR5M`.

## Evidência de disparo

Foram observadas requisições após o consentimento para:

- `gtmserver.conamore.com.br/g/collect` com `tid=G-V0KMM7L6M6` e `en=PageView`;
- `stats.g.doubleclick.net/g/collect`;
- `analytics.google.com/g/s/collect`;
- `google-analytics.com/g/s/collect`;
- script `googletagmanager.com/gtag/js?id=G-V0KMM7L6M6`.

## Console

- Erros JavaScript não capturados: **nenhum**.
- Avisos/erros de terceiros observados:
  - resposta indisponível da API do Reclame Aqui;
  - aviso do Meta Pixel sobre formato de moeda inválido.
- Esses dois pontos não impediram o disparo observado do GA4/GTM.

## Conclusão

O fluxo de Consent Mode está funcionando no teste:

1. inicia negando analytics antes da escolha;
2. aguarda a decisão do visitante;
3. atualiza para `granted` após “Aceitar Tudo`;
4. dispara o evento de consentimento;
5. envia a coleta do GA4 após o aceite.

O estado inicial `denied` é compatível com o fluxo de privacidade. A limitação permanece para visitantes que não concedem consentimento analítico: esses usuários podem gerar medição reduzida.
