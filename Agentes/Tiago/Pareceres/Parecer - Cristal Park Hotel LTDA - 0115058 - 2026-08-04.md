# Parecer de Crédito — Cristal Park Hotel LTDA — Pedido 0115058

**Data:** 04/08/2026  
**Responsável:** Tiago — Financeiro  
**Cliente no orçamento:** CRISTAL PARK HOTEL LTDA  
**Nome fantasia:** CRISTAL PARK HOTEL  
**Razão social no bureau:** SILVA COSTA E BORTOLI LTDA  
**CNPJ:** 17.902.306/0001-36  
**ID_DEBX:** A1844  
**Pedido/orçamento:** 0115058  
**Segmento:** Hotel  

## Documentos analisados

1. `115058 - CRISTAL PARK HOTEL LTDA.pdf` — orçamento de venda.
2. `ANÁLISE CRISTAL PARK HOTEL.pdf` — relatório Equifax/Boa Vista.

Os dois documentos referem-se ao mesmo CNPJ. A diferença de razão social é cadastral: o orçamento usa `CRISTAL PARK HOTEL LTDA`, enquanto o bureau identifica a razão social `SILVA COSTA E BORTOLI LTDA` e o nome fantasia `HOTEL CRISTAL PARK`.

## Etapa 0 — Lista Negra Conamore

✅ **Não encontrado na Lista Negra Conamore** por CNPJ, razão social ou nome fantasia.

## Etapa 1 — Histórico interno Conamore

**Fonte consultada:** SQL Server Hotel Finder (`conamore.Customers`, `debx.PDV_Detalhes`, `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`).

Cadastro localizado:

- ID_DEBX: `A1844`
- CNPJ: 17.902.306/0001-36
- Cadastro no Hotel Finder: código de data `0001-01-01` — campo sem data confiável
- Endereço: Rua Otaviano de Paiva, 900, Setor Centro, Cristalina/GO
- Status: ativo

### Compras efetivas identificadas

Foram identificados **4 pedidos expedidos** do próprio cliente, com razão social e CNPJ compatíveis:

| Pedido | Data da venda | Valor total | Condição | Pagamento |
|---|---:|---:|---|---|
| 0055100 | 19/08/2025 | R$ 24.501,23 | Cartão 6x | Increazy Crédito |
| 0055373 | 19/08/2025 | R$ 4.935,49 | Cartão 6x | Increazy Crédito |
| 0055633 | 20/08/2025 | R$ 5.732,20 | Cartão 5x | Increazy Crédito |
| 0064960 | 15/10/2025 | R$ 4.876,16 | Cartão 5x | Increazy Crédito |

**Resumo histórico:**

- Total histórico: **R$ 40.045,08**.
- Ticket médio: **R$ 10.011,27**.
- Maior pedido: **R$ 24.501,23**.
- Última compra: **15/10/2025**.
- Histórico operacional: pedidos com status **Expedição**.
- Condição historicamente testada: **cartão 5x/6x**.
- Não encontrei histórico próprio em boleto a prazo para este CNPJ.

O pedido atual de R$ 2.739,30 representa aproximadamente **27% do ticket médio** e **11% do maior pedido** — redução relevante de ticket, sem salto de exposição.

### Entidades relacionadas

A busca por mesmo endereço retornou somente o próprio Cristal Park Hotel. Foram mantidos separados registros de `CRISTAL IMOVEIS LTDA` e outras empresas com “Cristal” no nome, pois possuem CNPJ/endereço distintos e não houve confirmação de grupo econômico.

**Classificação interna:** cliente recorrente, histórico positivo; classe A/B, condicionado à confirmação de que não houve atrasos ou pendências não refletidos nas tabelas consultadas.

## Etapa 2 — Score / Bureau

**Fonte:** Equifax | Boa Vista — consulta de 04/08/2026 18:02:31.

- Score Aprovação PJ: **826 / 1000** — muito forte.
- Probabilidade de inadimplência: **2,0%** — excelente.
- Cadastro Positivo: participante com informação.
- Pagamento pontual até 5 dias: **100% em todos os meses de ago/2025 a jul/2026**.
- Pagamento atrasado: nenhuma ocorrência nas faixas de 6 a 15, 16 a 30, 31 a 60 ou mais de 60 dias.
- Atraso médio: sem registro.
- Pendências e restrições financeiras: **Nada consta**.
- Cheques sem fundos/sustados/devolvidos: **Nada consta**.
- Protestos: **Nada consta**.
- CNPJ: ativo.
- Fundação: 25/03/2013.
- CNAE principal: hotéis — 55.10-8/01.
- Porte: Empresa de Pequeno Porte.
- Capital social: R$ 40.000,00.

**Leitura:** bureau muito forte, com histórico positivo de pagamento pontual e ausência total de restrições.

## Etapa 3 — Coerência operacional do pedido

Itens do orçamento:

- 10 lençóis king sem elástico.
- 2 colchas piquet king.
- 3 capas para enchimento de edredom king.
- 1 enchimento para edredom king.
- 70 fronhas.

✅ Mix plenamente compatível com reposição de enxoval de hotel. A quantidade de fronhas é coerente com reposição, enquanto os itens king indicam manutenção/renovação de quartos.

## Etapa 4 — Exposição real da Conamore

Pelo PDF:

- Produtos: R$ 2.689,30.
- Frete: R$ 50,00.
- Desconto: R$ 0,00.
- Total com frete: **R$ 2.739,30**.
- Forma de pagamento impressa: **A DEFINIR**.
- Entrada impressa: **não informada**.
- Parcelas impressas: **não informadas**.

Exposição se faturado sem entrada: **R$ 2.739,30**.

Cenários de controle:

- Com 25% de entrada: entrada de R$ 684,82; exposição de R$ 2.054,48.
- Com 50% de entrada: entrada de R$ 1.369,65; exposição de R$ 1.369,65.
- Cartão 5x/6x: condição já praticada para este cliente; confirmar aprovação operacional do cartão.

Como o PDF está com `A DEFINIR`, não há condição efetiva suficiente para liberar faturamento a prazo. Pedidos sem entrada somente podem ser aprovados mediante autorização explícita do Sérgio.

## Etapa 5 — Validação operacional online

Classificação: 🟢 **operação forte**.

Evidências encontradas:

- Google Maps: Hotel Cristal Park, Rua Otaviano de Paiva, 900, Centro, Cristalina/GO, CEP 73850-000.
- Google Maps: classificação aproximada de 4,0 estrelas e identificação como hotel 3 estrelas.
- Google Maps: telefone +55 61 3060-2913, consistente com o cadastro público.
- Google Maps: website apontando para Facebook.
- Google Maps: disponibilidade vinculada a Booking.com e Priceline.
- Busca pública: presença em Booking.com, TripAdvisor, Facebook, Instagram `@cristalpark_hotel` e páginas de reserva.
- Receita WS: CNPJ ativo, aberto em 25/03/2013, CNAE de hotéis, endereço compatível e e-mail `cristalparkhotel@gmail.com`.

A operação é real, ativa e coerente com o cadastro e o orçamento.

## Parecer

✅ **Aprovado com 50% de entrada + saldo em 30/60 dias.**

## Nível de risco

**Baixo.**

## Condição recomendada

Preferência, nesta ordem:

1. **Cartão 5x ou 6x**, repetindo condição já testada no histórico; ou
2. **Mínimo de 25% de entrada + saldo em 30/60 dias**, com entrada compensada antes do faturamento; ou
3. **50% de entrada + saldo em 30/60 dias**, caso a negociação permita maior proteção.

**Não liberar boleto puro/sem entrada enquanto o pedido permanecer como `A DEFINIR`, salvo autorização explícita do Sérgio.**

## Justificativa técnica objetiva

1. Cliente não está na Lista Negra.
2. Há histórico próprio de 4 pedidos expedidos, totalizando R$ 40.045,08.
3. O pedido atual é pequeno frente ao histórico: R$ 2.739,30 contra ticket médio de R$ 10.011,27.
4. Histórico praticado foi cartão 5x/6x, sem boleto a prazo identificado para este CNPJ.
5. Bureau excelente: score 826, PD 2%, 100% de pagamento pontual e zero restrições/protestos.
6. Operação hoteleira confirmada por Google Maps, Booking, TripAdvisor, Facebook, Instagram e Receita WS.
7. O único bloqueio é comercial/operacional: o PDF não define forma de pagamento nem entrada.

**Decisão efetiva:** ✅ Cliente aprovado com **50% de entrada** e saldo em 30/60 dias. A entrada reduz a exposição para R$ 1.369,65.
