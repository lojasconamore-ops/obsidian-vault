# Kits de 4 unidades — criados pausados e ativados (24/10/2026)

## Ativação

Após a criação pausada, Sérgio informou diretamente que o DEBX tinha **mais de 40 unidades de cada SKU base** e autorizou a ativação. Oracle continuava inacessível para leitura independente da Melia; não tratar a confirmação verbal como saldo extraído do banco. A API do Mercado Livre foi consultada após cada `PUT status=active` e novamente após intervalo: **os três anúncios estavam `active`, 10 kits por anúncio**, sem alteração de preço. Cada anúncio de 10 kits representa 40 unidades físicas do SKU base. A sincronização contínua de saldo entre DEBX e ML não foi comprovada.

**Pendências operacionais após a ativação:** Tiago deve conferir margem líquida com custo, comissão e frete; validar peso/medidas reais das embalagens contra a ficha atual do ML; melhorar a capa do protetor para identificar a peça e o zíper. Não reajustar preço nem baixar estoque automaticamente sem validação. PED não é venda física.

Decisão de Sérgio: criar os três anúncios com as fotos disponíveis, **10 kits por anúncio**, mantendo-os **pausados** até nova autorização e validações. Criados na conta CONAMORE_HOTELARIA, categoria MLB271349, gold_special, fora do catálogo. Consultas de leitura após a criação confirmaram `status=paused`, `sub_status=paused_by_seller`, 10 kits e descrição explícita com 4 unidades em cada um.

- [MLB7880271166](https://produto.mercadolivre.com.br/MLB-7880271166-kit-4-protetores-travesseiro-repelente-agua-ziper-50x70-branco-_JM) — SKU `15709-4`, 4 protetores de travesseiro com zíper, **repelente à água**, R$ 63,60, 10 kits, 4 fotos oficiais de demonstração do tecido. Fotos não evidenciam claramente zíper/peça completa; melhorar.
- [MLB7880259658](https://produto.mercadolivre.com.br/MLB-7880259658-kit-4-fronhas-confort-180-fios-50x70-sem-abas-branco-_JM) — SKU `16446-4`, 4 fronhas sem abas, R$ 51,60, 10 kits, 3 fotos.
- [MLB7880260044](https://produto.mercadolivre.com.br/MLB-7880260044-kit-4-fronhas-confort-180-fios-50x70-com-abas-branco-_JM) — SKU `21929-4`, 4 fronhas com abas, R$ 75,60, 10 kits, 4 fotos.

**Histórico anterior à ativação:** os três foram criados inicialmente pausados por decisão de Sérgio; o acesso Oracle estava indisponível e o espelho SQL não tinha fonte de estoque identificada. O rascunho original usou pesos de 400 g/800 g (4× o peso unitário do site, sem embalagem externa) e dimensões estimadas. Os atributos de embalagem atuais da API diferem do rascunho; não afirmar que o ML ainda mostra esses pesos. PED não é venda física.

Arquivo de dados: `~/workspace/meli-integration/data/rascunhos_kits_4_travesseiro_fronhas_2026-10-22.json`.
