---
tags: [hospitalar, gtm, ga4, google-tag, isolamento, laboratorio]
data: 2026-09-05
status: proposto
---

# Plano de isolamento de destinos — Hospitalar

**Preparado em:** 05/09/2026 06:48 BRT

## Objetivo

Transformar `hospitalar.conamore.com.br` em laboratório controlado de tagueamento sem contaminar GA4, Google Ads, públicos ou Smart Bidding da Hotelaria.

## Estado-alvo inicial

```text
hospitalar.conamore.com.br
  → GTM-WCG6FZW
      → GA4 Hospitalar G-BNBJFTE5VT (único destino de medição)
      → RD Station (manter operação)
      → Cloudflare/Increazy (manter operação)

Temporariamente desligados do laboratório:
  ✕ GA4 Hotelaria G-V0KMM7L6M6
  ✕ GA4 adicional G-4HC4FT0C7X
  ✕ Google Ads AW-1041572367
  ✕ Meta Pixel
  ✕ Bing UET
  ✕ endpoint server-side antigo
```

## Achado que define o procedimento

No container compilado `GTM-WCG6FZW`:

- `G-BNBJFTE5VT` é o GA4 correto do Hospitalar e possui Google tag + eventos próprios.
- `G-4HC4FT0C7X` está explicitamente configurado em uma Google tag e em 13 tags de eventos.
- `G-V0KMM7L6M6` não é referenciado por nenhuma tag ativa do container, embora dispare ao vivo.
- `AW-1041572367` também dispara ao vivo sem existir como tag explícita no container.

Conclusão: `G-V0KMM7L6M6` e `AW-1041572367` são destinos conectados no nível da **Google tag**; não adianta procurar apenas tags GTM com esses IDs.

## Execução segura

### 0. Backup e workspace

1. Exportar a versão publicada de `GTM-WCG6FZW` em JSON.
2. Criar workspace `HOSP-LAB - Isolamento`.
3. Registrar o número da versão atual para rollback.
4. Não alterar `GTM-MMGX8ZL` nem o container server `GTM-N7Z62R96` nesta etapa.

### 1. Desconectar destinos no nível da Google tag

Abrir o GA4 Hospitalar:

`Administrador → Fluxos de dados → Conamore Hospitalar - GA4 → Configurar definições da tag / Google tag → Gerenciar Google tag → Destinos`

Na interface, o nome pode aparecer como **Destinos**, **Gerenciar destinos** ou **Tags de site conectadas**.

Manter:

- `G-BNBJFTE5VT` — Conamore Hospitalar

Desconectar do tag Hospitalar:

- `G-V0KMM7L6M6` — GA4 Hotelaria
- `AW-1041572367` — Google Ads, durante a fase inicial do laboratório

Regras:

- Não excluir a propriedade ou o fluxo `G-V0KMM7L6M6`.
- Não alterar o Google tag da Hotelaria.
- A ação correta é somente retirar esses destinos da associação do Google tag Hospitalar.
- Confirmar na tela que o tag selecionado é o associado ao stream `G-BNBJFTE5VT` antes de salvar.

### 2. Pausar o GA4 adicional G-4HC4FT0C7X no GTM Hospitalar

No workspace do `GTM-WCG6FZW`, pesquisar pelo Measurement ID `G-4HC4FT0C7X` e pausar:

- Google tag base — tag ID compilado `159`.
- `add_payment_info` — `160`.
- `view_search_results` — `167`.
- `purchase` — `172`.
- `add_shipping_info` — `174`.
- `remove_from_cart` — `181`.
- `clique_banner` — `188`.
- `view_item` — `190`.
- `view_cart` — `197`.
- `begin_checkout` — `198`.
- `login` — `206`.
- `view_item_list` — `209`.
- `add_to_cart` — `214`.
- `contato_whatsapp` — `225`.

Primeiro pausar, não excluir. Assim o rollback é imediato.

### 3. Isolar terceiros durante o aprendizado

Pausar temporariamente no GTM Hospitalar:

- Meta Pixel `583931423939058`.
- Bing UET `343046885`.
- Tags LinkedIn de conversão.

RD Station pode permanecer, pois formulários e atendimento são operação do site. Mesmo assim, não usar eventos RD como gatilho de Ads durante o laboratório.

### 4. Não ligar o server-side ainda

O Hospitalar referencia `https://gtm-w9gnwqw-nzbjy.uc.r.appspot.com`, que retorna HTTP 404. Remover esse valor das tags Hospitalar ou deixar as tags pausadas.

Nesta fase, não apontar imediatamente para `gtmserver.conamore.com.br`, porque o container server é compartilhado com a Hotelaria. Primeiro validar todo o client-side somente no GA4 Hospitalar.

Quando o client-side estiver estável, criar no sGTM:

- trigger com `x-ga-measurement_id = G-BNBJFTE5VT`;
- condição adicional de host `hospitalar.conamore.com.br`;
- tags nomeadas com prefixo `[HOSPITALAR]`;
- eventos de teste com sufixo `_test`;
- nenhuma tag Ads primária.

### 5. Teste antes da publicação

No Preview/Tag Assistant, em navegador limpo:

1. Abrir a home sem rolar.
2. Depois rolar e navegar por categoria/produto.
3. Adicionar produto ao carrinho.
4. Iniciar checkout sem concluir compra real.
5. Clicar no WhatsApp.

Critérios de aceite do isolamento:

- Carrega `GTM-WCG6FZW`.
- Beacons GA4 contêm apenas `tid=G-BNBJFTE5VT`.
- Zero requests para `G-V0KMM7L6M6`.
- Zero requests para `G-4HC4FT0C7X`.
- Zero requests para `AW-1041572367` na fase inicial.
- Zero Meta/Bing/LinkedIn se estiverem pausados.
- Eventos aparecem apenas no DebugView da property `372899047`.
- Nenhum evento novo no DebugView da Hotelaria `379729087` com hostname Hospitalar.

### 6. Publicação e monitoramento

Publicar como uma única versão:

`HOSP-LAB 01 — Isolamento de destinos`

Monitorar por 7 dias:

- sessões e eventos no GA4 Hospitalar;
- hostname `hospitalar.conamore.com.br` na property Hotelaria — deve tender a zero após a publicação;
- ausência de tráfego Hospitalar nas propriedades/destinos removidos;
- erros do checkout e formulários.

## Reintrodução controlada

Depois do isolamento confirmado:

1. Consent Mode corrigido pela Increazy.
2. GA4 ecommerce validado.
3. Server-side Hospitalar com filtros próprios.
4. Importar `purchase` Hospitalar no Ads como secundária.
5. Manter 7 dias em observação.
6. Tornar primária apenas com decisão do Sérgio sobre estratégia de campanha.

## Rollback

Se checkout, formulários ou navegação apresentarem erro:

1. republicar imediatamente a versão anterior do `GTM-WCG6FZW`;
2. não reconectar automaticamente o GA4 Hotelaria;
3. corrigir no workspace e repetir Preview antes de nova publicação.
