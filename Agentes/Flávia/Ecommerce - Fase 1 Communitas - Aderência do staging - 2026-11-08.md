# Ecommerce — Fase 1 Communitas: aderência do staging — 08/11/2026

**Fonte dos quinze itens:** [proposta Communitas Fase 1](https://communitascom.github.io/conamore-fase1/). **Ambientes verificados:** [Hotelaria lab](https://www_conamore_com_br.lab.increazy.com/) e [Casa lab](https://lojas_conamore_com_br.lab.increazy.com/). Comparação com produção quando indicada. Leitura por DOM, screenshots e adição de produtos apenas nos carrinhos de staging. Não confundir aparência com aceite comercial, técnico ou de tracking. Relacionado: [[Ecommerce - Comparação staging Hotelaria vs produção - 2026-11-08]].

| # | Proposta Fase 1 | Estado observado | Evidência/limite |
|---:|---|---|---|
| 1 | Reduzir banner e substituir criativo mobile retrato | **Pendente** | Banner Hotelaria desktop no lab ~443 px em viewport 1366; não chegou à meta do mockup (320 px em viewport 1280); Increazy já o listara como pendente. Mobile não revalidado nesta rodada item a item. |
| 2 | Compactar cabeçalho | **Parcial** | Hotelaria e Casa: 144 px e fixed, contra 221 px da produção; não 130 px do mockup e faixa de segmentos ainda visível. |
| 3 | Reposicionar/remover vídeo sobre CTAs (Hotelaria) | **Pendente** | `.veels-popup` continua `position:fixed`, 95×120 px, x10/y443 na home e categoria. Não provei sobreposição em cada botão. |
| 4 | Ordenação e excluir serviços sob consulta | **Parcial** | `Mais relevantes` aparece na categoria de lençóis, mas os dois primeiros cards ainda são RFID e bordado sob consulta; seguem fronhas antes de lençóis. |
| 5 | Mover bloco SEO depois da grade, sem eliminar | **Bloqueado/regressão** | No lab, apenas `<p class=category__hero--description>` de 218 caracteres terminando em `alta…`; texto completo que existe em produção não encontrado no DOM visível após a grade. |
| 6 | Corrigir parcelamento e mostrar nos cards | **Pendente** | Não se encontrou campo de parcelamento nos cards do lab; no carrinho da Casa, após 2 itens, aparecia `Parcele em até 1x`, enquanto barra diz até 4x. |
| 7 | Priorizar 1ª imagem da PDP, sem lazy-load | **Pendente** | Imagens na PDP Hotelaria SKU 19356 e imagens da grade seguem com `loading="lazy"`; não se mediu LCP real. |
| 8 | Escurecer preço e destacar atacado | **Parcial** | Atacado aparece em card, mas botão verde Hotelaria continua `rgb(53,160,107)` e não foi validada cor/contraste de todos os preços; não marcar acessibilidade como aprovada. |
| 9 | Botão de card 44 px e largura total | **Parcial** | Botão Hotelaria mede 44 px de altura, porém ~101–144 px de largura, não largura total; Casa segue com 37 px. |
| 10 | Corrigir carrinho vazio e sobreposição Casa | **Atende visualmente, QA parcial** | Vazio exibe `Carrinho vazio` e CTA; com dois itens, total legível no rodapé, sem colisão óbvia na captura. Remoção, CEP e checkout não testados. |
| 11 | Reduzir box de título da categoria | **Atende visualmente na amostra** | Categoria Lençóis: H1 `Lençóis` ocupa ~35 px e grade começa por volta de y394 em viewport 1366; antes primeira imagem era ~y1305. |
| 12 | Abrir descrição de produto por padrão | **Atende na amostra** | PDP Hotelaria e Casa tinham `active-accordion` e texto de descrição visível, sem clique. |
| 13 | Rever piso do frete grátis Casa | **Pendente crítico** | Carrinho Casa lab com duas peças de R$43,90 total R$87,80 dizia `Faltam apenas R$ 1.412,20` — continua usando piso de R$1.500 do B2B. Não calculado frete por CEP. |
| 14 | Cabeçalho fixo compacto | **Atende estrutura, QA parcial** | `header` CSS `position:fixed`, altura 144 px em ambas as homes; sobreposição em todas as rolagens ainda não foi testada. |
| 15 | Benefícios e captura de e-mail na Casa | **Parcial** | Lab Casa tem barra de benefícios; produção não. Newsletter e vitrine de categorias já aparecem em ambos, de modo que não são novidade atribuível à Fase 1; cadastro/envio não testado. |

**Achados extras:** no PDP Casa de duas variantes Amore aparece a palavra `debug` no texto renderizado. No staging Hotelaria banners da home redirecionam para produção, atrapalhando QA end-to-end. Na home Hotelaria, o H1 B2B foi deslocado para ~1778 px, depois da vitrine. `noindex,nofollow` é adequado para staging, mas não pode ir para produção. GTM/GA4/RD presentes não provam recebimento de eventos. Não foram testados pagamento, checkout, CEP ou compra real.

**Decisão:** avanço visual importante em cabeçalho, primeira dobra da categoria, carrinho vazio e descrição aberta; porém itens 5, 6, 7 e 13 impedem aceite, além da QA incompleta. João/Increazy devem corrigir e revalidar com Conamore antes de produção.
