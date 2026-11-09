# Monitoramento do clone radiotuzla.com

- Clone: https://conamore.com.br.radiotuzla.com/ — ativo desde pelo menos 17/06/2026; disavow enviado ao Google em 08/08/2026.
- Propriedade GSC: `sc-domain:conamore.com.br` (acesso `siteOwner` via Composio). A API pública do Search Console/Composio não expõe relatório de domínios de referência/links; não interpretar ausência de dado como ausência de backlinks.

## 02/11/2026, 09:00 BRT — 🔴 ativo

- Composio `COMPOSIO_SEARCH_WEB`: buscas `"conamore.com.br.radiotuzla.com"` e `site:conamore.com.br.radiotuzla.com` retornaram citação para https://conamore.com.br.radiotuzla.com/ com título que reproduz CONAMORE Hotelaria. É evidência de presença no índice do provedor de busca Exa, **não prova direta do índice do Google**.
- DNS `dig +short conamore.com.br.radiotuzla.com`: `94.72.141.240`.
- HTTP `curl -sSI --max-time 15 https://conamore.com.br.radiotuzla.com/`: timeout (28), sem cabeçalhos; HTTP em porta 80: conexão resetada (56). A resposta do site não foi confirmada.
- GSC: propriedade confirmada no `GOOGLE_SEARCH_CONSOLE_LIST_SITES`; nenhuma ferramenta de backlinks/referring domains disponível. Contagem de links não verificada.
- Conclusão: não resolvido, pois DNS persiste e a busca Composio ainda cita o clone. Não declarar que responde em HTTP ou que permanece no índice do Google sem verificação específica.

## 09/11/2026, 09:00 BRT — 🔴 ainda presente (indexação Google não confirmada)

- `COMPOSIO_SEARCH_WEB` com `"conamore.com.br.radiotuzla.com"` e `site:conamore.com.br.radiotuzla.com` continua citando [o clone](https://conamore.com.br.radiotuzla.com/) com título da CONAMORE Hotelaria. Isso comprova presença no índice Exa, não no Google.
- DNS `dig +short`: `94.72.141.240` (inalterado desde 02/11). HTTPS e HTTP `curl -sSI --connect-timeout 8 --max-time 15`: timeout (28), sem resposta/cabeçalho.
- GSC conectado à propriedade `sc-domain:conamore.com.br` com permissão `siteOwner`, porém ferramentas Composio disponíveis não incluem relatório de links/domínios de referência, logo contagem e presença do radiotuzla no GSC não verificadas.
- Busca direta ao Google via HTTP respondeu página intermediária sem resultados legíveis; navegador não pôde extrair página. Indexação Google permanece inconclusiva. Sem evidência de redução em relação a 02/11; ainda não resolvido.
