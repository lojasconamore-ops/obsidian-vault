# Ecommerce Hotelaria — comparação staging Increazy × produção — 08/11/2026

**Coleta:** 08/11/2026, a partir de 16h23 BRT. **Ambientes:** [staging](https://www_conamore_com_br.lab.increazy.com/) e [produção](https://www.conamore.com.br/). Escopo amostral: home desktop e mobile (390 px), categoria `/lencol-para-hotelaria`, PDP do SKU 19356 e carrinho em staging. Não é aprovação de lançamento, nem auditoria de todos os 15 itens da Fase 1. Checklist anterior: [[Ecommerce - Auditoria Communitas Fase 1 - Reuniao 14-10]].

## Comparação observada

| Aspecto | Produção | Staging | Leitura |
|---|---|---|---|
| Home desktop | Cabeçalho ~221 px; hero promocional igual | Cabeçalho ~144 px; hero igual | Ganho de espaço (~77 px) sem reinvenção visual. |
| Home mobile 390 px | Espaço do topo até banner maior | Busca/banner aparecem antes; header mais compacto | Melhor primeira dobra, mas CMP cobre grande parte do banner nos dois ambientes. |
| Home H1 | `Enxoval profissional para hotéis e pousadas`, posição ~685 px | mesmo H1, posição ~1778 px | Regressão potencial: mensagem B2B principal empurrada para depois de promoções e destaques. |
| Categoria lençóis | Primeira imagem de produto ~1305 px no documento | ~394 px | Grande ganho de acesso ao catálogo. H1 `Lençóis` preservado; ambos mostraram 210 produtos. |
| Texto editorial categoria | Texto extenso original presente no DOM | Apenas trecho de 218 caracteres terminando em `alta…` no `<p class=category__hero--description>`; texto integral não localizado no restante do DOM visível | **Bloqueio SEO/clareza:** não foi apenas movido para baixo, foi truncado/substituído na amostra. Repor o conteúdo integral em bloco de leitura após grade (ou antes, desde que não atrapalhe catálogo) e testar indexação após publicação. |
| Home e categoria SEO | Home H1 e categoria title/description existentes, robots `index,follow` | H1/title/description preservados, robots `noindex,nofollow` | `noindex` correto em staging; na promoção à produção não pode herdar `noindex`. Canonical e JSON-LD não encontrados nessas páginas pelo DOM consultado em ambos, não é regressão exclusiva. |
| PDP SKU 19356 | Preço R$ 65,90 e tier R$ 57,50 a partir de 10; title e conteúdo extensos | Mesmos preço, tier, H1, descrição e title | Nenhuma mudança editorial de PDP observada; melhorias de catálogo não corrigem títulos/meta longos pré-existentes. |
| Carrinho staging | Não testado funcionalmente nesta comparação | `Comprar` abriu carrinho; 1 un. R$ 65,90, 10 un. R$ 57,50 cada e total R$ 575,00; limiar de frete B2B R$ 1.500 mostrado | Fluxo parcial funcional. Não testados CEP, checkout, pagamento e evento recebido nas plataformas. |
| Banners e produtos | Hero `White November` e card Argila com URL terminada em `azul-1` | Mesmos conteúdos; banners do staging apontam para `www.conamore.com.br` | Erro de slug é **herdado**, não regressão nova. Links absolutos impedem QA end-to-end em staging e merecem revisão na migração. |
| Scripts | GTM `GTM-MMGX8ZL`, GA4 `G-CDCKFVTR5M`/`G-V0KMM7L6M6`, menção RD e CMP visíveis | Mesmos IDs/menção e CMP visíveis | Presença não comprova consentimento correto nem entrega de `view_item`, `add_to_cart`, RD, compra ERP. |

**Outros pontos herdados:** meta description da categoria promete pagamento até 5x, enquanto barra do site informa até 4x; inconsistente em ambos. Staging ainda apresenta H1 home distante do topo. No banner de consentimento, tanto staging quanto produção encobrem visualmente o hero móvel até escolha do visitante.

## Próximas validações antes de produzir

1. **Increazy/João:** restaurar o texto completo da categoria em HTML indexável, mantendo a grade perto do topo. Conferir outras categorias afetadas; validar versão mobile.
2. **SEO técnico:** revisar title/metas incoerentes, canonical, JSON-LD, URLs e redirecionamentos; garantir `index,follow` somente em produção e `noindex` no lab. Não alterar URLs publicadas sem plano 301 e Search Console.
3. **Jornada:** comparar catálogo/cores/imagens por SKU, carregar mais, filtros, carrinho vazio, quantidade, CEP, frete B2B, checkout e formas de pagamento sem fechar pedido real.
4. **Mensuração:** validar Consent Mode rejeitar/aceitar, GTM/GA4/RD eventos `view_item`, `add_to_cart`, `begin_checkout` e `compra_erp` no destino; script presente não basta. Revisar links absolutos que escapam do staging.
5. **Aceite:** revisão João + validação visual/funcional + aprovação Conamore antes da publicação; smoke test e monitoramento pós-produção.

**Veredito:** melhoria relevante de UX na descoberta da grade, porém **não aprovar a produção ainda** por regressão do texto editorial na categoria e QA comercial/SEO/tracking incompleto. Não foi comprovado impacto em conversão, ranking ou velocidade.

**Executado | Evidência | Status:** comparação direta de 2 ambientes, 3 tipos de página e teste de carrinho no lab | DOM, metadados, screenshots desktop/mobile e valores de 1/10 unidades observados | Análise preliminar concluída; produção pendente.
