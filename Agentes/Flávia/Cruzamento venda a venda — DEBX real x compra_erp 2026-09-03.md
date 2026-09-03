---
title: Cruzamento venda a venda — DEBX real x compra_erp (Increazy)
tags: [debx, oracle, compra_erp, increazy, atribuicao, gap]
gerado: 2026-09-03
fonte: "Oracle DEBX 172.169.0.11/conamore (TEST_PED)"
---

# Cruzamento venda a venda — faturamento DEBX × compra_erp

**Objetivo (Sérgio):** cruzar venda a venda o faturamento real do DEBX contra o `compra_erp`, usando **e-mail** como chave, e entregar o gap exato.

## Janela
Últimos 30 dias (PDV_DATPED ≥ sysdate-30; sysdate = 2026-09-03).

## Onde está o e-mail (descoberta estrutural)

| Base | Campo | População |
|---|---|---|
| compra_erp (Increazy) | `I_PEDVENDA_INTERFACE.IPV_E_MAIL` | **100%** (392/392) |
| PED real (header) | `F_PEDVENDA.PDV_EMAILU` | **0%** (vazio em todos os schemas, inclusive histórico: 0/39.020 TEST_PED) |
| Cadastro mestre cliente | `F_ENDERE.END_E_MAIL` (só TEST_MATRIZ) | 99% (64.931/65.586) |
| C_FICCON | `FCO_EMAIL` | 23% (17.955/78.063) — NÃO liga no PED |

**Conclusão:** o e-mail só é capturado no checkout Increazy. No PED real (`PDV_EMAILU`) está sempre vazio; recuperável via cadastro mestre `F_ENDERE` (que só existe na MATRIZ) por `PDV_CODEND = END_CODEND`.

## Chaves de ligação (validadas)
- **`IPV_NUMPED` = `PDV_NUMPED`** → interface Increazy ↔ PED real. Casa **392/392** (100%). É a chave EXATA de venda a venda.
- **`IPV_CODINC` = `IPI_SLUG`** → interface ↔ pagamento Increazy (`I_PEDINCREAZY`). 367/392.

## Números (30d)

### Lado real (DEBX)
- PED (6 schemas): **4.154 pedidos — R$ 2.668.415,74**
  - MATRIZ 364 (1.362.541) · ACL 2.952 (657.212) · BRG 31 (113.182) · CHC 1 (95,80) · GCL 787 (467.595) · FILIAL 19 (67.790)
- Venda física (`F_MOVTO`, MOV_NATIND=100): **R$ 319.477,78** (ACL 257.405 + GCL 62.072)
- **Total real = R$ 2.987.893,52**

### Lado compra_erp (Increazy)
- Links de pagamento (30d): **392 pedidos** (R$ 1.275.973,52 de PED)
- Dentro da janela por data de pedido: **376** (R$ 1.225.118,41); 16 são pedidos um pouco mais antigos
- Pagamento confirmado (`IPI_STATUS='success'`): **336 pedidos — R$ 1.034.176,04** (30 cancelados, 1 waiting)
- E-mails: 392 (100%), **319 únicos**

## Cruzamento

### Por número de pedido (chave exata)
- Capturado pelo compra_erp: **376 pedidos — R$ 1.225.118,41** (~9% dos pedidos, ~46% do valor PED)
- **GAP (não capturado): 3.778 pedidos — R$ 1.443.297,33** + físico R$ 319.477,78

### Por e-mail (chave pedida pelo Sérgio)
- Real com e-mail recuperável: **1.116 pedidos (27%)** — R$ 2.315.487,18
- Sem e-mail (balcão/não cadastrado): **3.038 pedidos (73%)** — R$ 352.928,56
- Casam por e-mail: **395 pedidos — R$ 1.266.520,59** (⚠️ superestima: e-mail casa por CLIENTE, não por pedido — 395 vs 376 exatos)
- Não casam (gap por e-mail): **721 pedidos — R$ 1.048.966,59**

## Achados-chave
1. **E-mail não é a chave ideal venda a venda.** Casa por cliente (um cliente = vários pedidos → supercasa 395 vs 376). A chave exata é o nº do pedido.
2. **73% das vendas PED reais não têm e-mail recuperável** (só ACL/GCL concentram balcão). MATRIZ/BRG/FILIAL têm 100%.
3. **compra_erp cobre só MATRIZ+ACL+BRG+GCL** (nada de CHC/FILIAL, nada de físico).
4. **Discrepância interna no Increazy:** interface tem 392 pedidos / R$ 1,28M, mas só 336 com pagamento `success` (R$ 1,03M). O `compra_erp` medido no Google Ads (R$ ~454k / 126 conv.) fica BEM abaixo dos R$ 1,03M de pagamentos confirmados — há perda também entre Increazy → Ads (subtotal vs total, e/ou janela/status).

## Próximos passos
- [ ] Confirmar com a Increazy por que `PDV_EMAILU` nunca é preenchido e por que CHC/FILIAL não entram.
- [ ] Investigar a perda Increazy → compra_erp no Ads (R$ 1,03M confirmado vs R$ 454k registrado).
- [ ] Definir se o gap a reportar é por valor (46% coberto) ou por nº de pedidos (9% coberto).

## Artefatos
- `compra_erp_venda_a_venda.csv` (392 linhas)
- `real_venda_a_venda.csv` (4.154 linhas)
- Local: `.hermes/profiles/marketing/tmp/`
