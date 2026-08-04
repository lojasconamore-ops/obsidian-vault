# SEO — Conamore — “onde comprar lençol branco” — Search Console e Google Ads

**Data da consulta:** 04/08/2026 (BRT)  
**Property GSC:** `sc-domain:conamore.com.br`  
**Tipo de pesquisa:** web  
**Período comparável:** 04/04/2025 a 01/08/2026  

## Google Search Console

- Consulta exata aplicada: `onde comprar lençol branco`
- Total da property no período, sem filtro: **147.649 cliques**, **6.792.474 impressões**, **CTR 2,17%**, **posição média 9,27**.
- Com o filtro exato, a API retornou **nenhuma linha de consulta** e **nenhuma página atribuída**.
- A extração diária filtrada retornou 485 dias, todos com cliques e impressões iguais a zero.

### Limitação de interpretação
A ausência de linhas no Search Console significa que não houve dados retornados para a consulta exata no recorte/property consultado; não deve ser interpretada como prova de que a página não está indexada.

## Google Ads

Foram tentadas duas consultas na conta `customers/2335779078`:

1. `search_term_view` para o termo exato, com métricas de impressões, cliques, CTR, custo e conversões.
2. `keyword_view` para identificar keywords, tipos de correspondência e campanhas.

Ambas falharam por **quota do desenvolvedor esgotada (HTTP 429 / RESOURCE_EXHAUSTED)**. A API informou retry aproximado em **6.041–6.042 segundos**.

## Conclusão provisória

- **Orgânico:** não há evidência de presença mensurável para o termo exato no GSC no período consultado.
- **Pago:** não foi possível validar o termo de pesquisa nem a keyword acionadora devido ao bloqueio temporário de quota da API Google Ads.
- Não concluir ainda se existe ou não tráfego pago para esse termo.

## Próximo passo

Retentar a consulta do Google Ads após a janela de quota informada. Na análise final, manter a distinção entre **termo de pesquisa real** (`search_term_view`) e **keyword cadastrada** (`keyword_view`).
