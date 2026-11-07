# Ajuste de estoques ML — 07/11/2026 19h48 BRT

Sérgio solicitou elevar **todos os estoques anunciados para 10 kits**. Antes de alterar, validada sessão Oracle `TEST_PED` (`SELECT USER FROM DUAL`), schema/colunas da view `TEST_PED.V_ESTOQ` e saldo disponível `VES_SALDO` para **19 SKUs base**. Cada SKU tinha uma linha `VES_LOCAL=CD`, `VES_STATUS=AT`, `VES_UNIMED=UN`; o saldo disponível foi comparado com **10 × peças por kit** (20 peças nos kits de 2; 40 nos kits de 4). Fonte do saldo: leitura efetiva do Oracle às ~19h47 BRT, não confirmação verbal. O valor `VES_PRAT` não foi usado como disponibilidade; `VES_SALDO` é a referência operacional para venda conforme treinamento.

**Atualizados pela API e reconsultados com 10 kits por SKU:** `1140083-2` (2→10), `16411-2` (9→10 em duas ofertas vinculadas), `16438-2` (0→10, anúncio voltou a ativo), `16446-4` (8→10), `17689-2` (9→10 em duas ofertas vinculadas), `18082-4` (8→10 em duas ofertas vinculadas), `18090-4` (7→10), `19339-2` (0→10, anúncio voltou a ativo), `19348-2` (6→10), `19364-2` (9→10), `20140001-4` (9→10). Feito um PUT por `user_product_id`, não um por oferta comum e catálogo.

**Já estavam com 10 e foram mantidos:** `1080001-2`, `1080002-2`, `1080003-2` (duas ofertas compartilhadas), `1080004-2`, `15709-4`, `19356-2`, `21929-4`.

**Exceção crítica — NÃO alterado:** `16429-2` (kit 2 lençóis Queen sem elástico) apresentava `VES_SALDO=-14` peças disponíveis no DEBX, insuficiente para 10 kits (=20 peças), apesar de `VES_PRAT=43`. As duas ofertas vinculadas permanecem pausadas por `out_of_stock` com 0 kit. Confirmar reservas/lançamentos com responsável/Matias; não usar `VES_PRAT` como saldo livre nem elevar no ML sem confirmação de pelo menos 20 peças efetivamente livres após reservas e outros canais.

**Verificação final pela API:** 19 SKUs em 24 ofertas, 18 SKUs com 10 kits, um com zero; **22 anúncios ativos e 2 pausados**, ambos do Queen `16429-2`. Não houve mudança de preço, fotos ou descrição. Log privado: `~/.hermes/profiles/melia/cache/scratch/ml_restock_20261107_result.json`.
