# Parecer de Crédito — Luiz Lemes Martins Ltda. / Hotel Casa Blanca II

**Data da análise:** 07/08/2026 (BRT)  
**Pedido:** 0115549  
**CNPJ:** 17.910.016/0001-34  
**ID DEBX:** A0030  
**Arquivos utilizados:**
- Orçamento de venda nº 0115549, emitido em 06/08/2026;
- Relatório Equifax | Boa Vista, emitido em 07/08/2026 às 11:35:18.

Os dois arquivos referem-se ao mesmo CNPJ e foram consolidados nesta análise. O caso não deve ser misturado com o orçamento da Quinta da Baroneza, cujo CNPJ é diferente.

## Etapa 0 — Lista Negra

**Resultado: ✅ Cliente não localizado na Lista Negra Conamore.**

## Parecer

# 🟡 Aprovar com restrição

**Nível de risco:** moderado para a operação recorrente; alto pelo bureau isoladamente.  
**Aprovação condicionada à entrada mínima e à correção da divergência do orçamento.**

## Identificação e situação cadastral

- **Razão social:** LUIZ LEMES MARTINS LTDA
- **Nome fantasia:** HOTEL CASA BLANCA II
- **CNPJ:** 17.910.016/0001-34
- **Natureza jurídica:** Sociedade Empresária Limitada
- **CNAE principal:** Hotéis — 55.10-8/01
- **Situação:** ATIVA
- **Abertura:** 10/04/2013
- **Porte:** Empresa de Pequeno Porte
- **Capital social informado:** R$ 103.900,00
- **Sócio-administrador informado:** Luiz Lemes Martins
- **Endereço do orçamento:** Avenida Goiás, 1520, Bairro Estudantil, Frutal/MG, CEP 38206-052

Receita WS e Hotel Finder confirmam a empresa e a operação hoteleira. A Receita WS apresenta o mesmo endereço-base, com divergência de CEP e número 1542 em relação a algumas bases públicas; o endereço do orçamento deve ser considerado o endereço comercial da venda e confirmado antes da emissão fiscal caso haja divergência no cadastro.

## Etapa 1 — Histórico Conamore / Hotel Finder

Consulta realizada no SQL Server `hotel-finder` por CNPJ, razão social, nome fantasia e ID DEBX.

### Histórico identificado

- **ID DEBX:** A0030
- **Pedidos expedidos identificados:** 17 registros, sendo 15 com data e 2 registros legados sem data preenchida
- **Valor histórico expedido dos 17 registros:** R$ 100.868,12
- **Valor histórico dos 15 registros datados:** R$ 99.931,90
- **Ticket médio dos 15 registros datados:** R$ 6.662,13
- **Maior pedido:** R$ 14.709,20
- **Período dos registros datados:** setembro/2024 a junho/2026; dois registros antigos não possuem data preenchida
- **Status:** recorrência consistente, sem evidência de cancelamento recorrente ou bloqueio no retorno consultado.

Condições já praticadas:

- boleto 30/60 dias;
- boleto 30/60/90 dias;
- boleto 30/60/90/120 dias;
- entrada de 20%, 25% e 50% em pedidos anteriores;
- cartão em algumas operações.

### Comparação com o pedido atual

- **Pedido atual com frete:** R$ 6.180,00
- Aproximadamente **92,8% do ticket médio histórico**;
- Aproximadamente **42,0% do maior pedido expedido**.

O valor do pedido é compatível com o histórico e não representa salto de limite. Esse é o principal fator favorável da decisão.

**Classificação interna indicativa:** Classe B — cliente recorrente, com histórico expressivo e prazo já testado. O bureau, entretanto, recomenda manter controle de entrada e prazo.

### Leitura financeira dos títulos no Oracle DEBX

Consulta complementar realizada em 08/08/2026 (BRT), pela cadeia `CNPJ → EMP_CODEMP A0030 → PDV_NUMPED → TEST_MATRIZ.F_TITULOS`, com conferência nos schemas `TEST_ACL`, `TEST_CHC`, `TEST_GCL` e `TEST_BRG`.

- **44 parcelas pagas**, total original de R$ 81.568,36;
- **22 parcelas pagas até o vencimento**;
- **22 parcelas compensadas de 1 a 3 dias após o vencimento**;
- atraso máximo observado: **3 dias**;
- atraso médio entre as parcelas pagas após o vencimento: **1,68 dia**;
- **7 parcelas em aberto**, todas a vencer;
- saldo em aberto na data de corte: **R$ 18.363,54**;
- não havia título vencido na data da consulta.

A leitura confirma capacidade de pagamento e ausência de inadimplência estrutural, mas também mostra pequena fricção recorrente de cobrança. Portanto, o histórico financeiro interno permanece compatível com **Classe B**, e não com Classe A plena. O saldo a vencer deve ser somado à exposição do próximo pedido.

## Etapa 2 — Score / Bureau

Relatório Equifax | Boa Vista do mesmo CNPJ:

- **Cadastro Positivo:** participante com informação;
- **Score Aprovação PJ:** **644/1.000** — faixa de cautela;
- **Probabilidade de inadimplência:** **13,0%** — elevada;
- **Pagamento pontual:** entre 97% e 100% nos 12 meses apresentados;
- **Atrasos:** registros de 6–15 dias e ocorrências na faixa de 31–60 dias;
- **Pendências financeiras:** nada consta;
- **Cheques sem fundos/devolvidos:** nada consta;
- **Protestos:** nada consta;
- **Consultas:** 11 no período de 01/08/2025 a 01/08/2026;
- **Maior fatura informada:** R$ 28 mil;
- **Maior crédito informado:** R$ 41 mil.

### Interpretação

O score 644 e a PD de 13% não permitem crédito aberto sem mitigação. Por outro lado, não há protestos, restrições ou cheques, e o histórico interno é forte, recorrente e coerente. Para cliente recorrente, o histórico Conamore tem maior peso que o score isolado, mas os atrasos reportados justificam entrada e redução do prazo máximo.

## Etapa 3 — Coerência operacional

**Coerente.** O cliente é hotel, e o mix é compatível com reposição de enxoval:

- 50 toalhas de rosto;
- 50 toalhas de piso;
- 100 fronhas;
- 50 lençóis de casal.

O volume é compatível com o porte e com o histórico de compras do Hotel Casa Blanca II.

## Etapa 4 — Reconciliação comercial e exposição

### Totais do orçamento

- Soma dos itens: **R$ 6.130,00**;
- Frete: **R$ 50,00**;
- Total Pedido indicado: **R$ 6.180,00**;
- Total sem desconto: **R$ 6.130,00**;
- Total com desconto: **R$ 6.130,00**;
- Desconto: **R$ 0,00**;
- Forma de pagamento: **boleto 30/60/90/120**.

### Divergência a corrigir

O orçamento soma R$ 6.130,00 nos campos de total sem/com desconto, mas informa Total Pedido de R$ 6.180,00 devido ao frete de R$ 50,00. O valor de R$ 6.180,00 é a referência comercial correta para exposição total, desde que o frete seja efetivamente cobrado, mas o documento deve ser corrigido para eliminar a inconsistência.

### Exposição recomendada

A política interna e a preferência de alçada exigem entrada mínima de 25% em faturamentos a prazo:

- **Total considerado:** R$ 6.180,00;
- **Entrada de 25%:** R$ 1.545,00;
- **Exposição líquida:** R$ 4.635,00.

A entrada reduz a exposição para valor inferior ao ticket médio histórico e mantém a venda dentro de uma faixa confortável.

## Etapa 5 — Validação operacional online

**Classificação: 🟢 Operação forte.**

Evidências verificadas:

- CNPJ ativo e CNAE de hotelaria;
- Hotel Casa Blanca II / Casablanca Palace Hotel identificado no Google Maps;
- endereço compatível na Avenida Goiás, 1520, Frutal/MG;
- telefone compatível: (34) 3423-6188;
- website próprio: `casablancapalacehotel.com`;
- nota aproximada de 4,1 no Google Maps;
- presença em Booking.com e Tripadvisor.com;
- referências públicas adicionais ao hotel no mesmo endereço e telefone.

## Condição recomendada

### Aprovar somente com

- **25% de entrada: R$ 1.545,00**;
- saldo de **R$ 4.635,00**;
- preferencialmente em **30/60/90 dias**;
- não manter os 120 dias sem nova autorização, pois o bureau apresenta score 644 e PD 13%;
- confirmação de que não há títulos vencidos na data do faturamento; o saldo a vencer identificado na consulta (**R$ 18.363,54**) deve ser somado à exposição total;
- correção do total no orçamento/ERP para refletir adequadamente itens, frete e total final.

O cliente já operou anteriormente em 30/60/90/120 dias, mas a condição recomendada para este pedido é mais conservadora que algumas condições históricas por causa do score e da probabilidade de inadimplência atuais.

## Justificativa técnica objetiva

O cliente é recorrente, tem 17 registros de expedição identificados — 15 datados e 2 legados sem data — e aproximadamente R$ 100,9 mil de histórico Conamore. O pedido atual de R$ 6.180,00 é compatível com o ticket histórico dos pedidos datados, a operação online é forte, o CNPJ está ativo e não há protestos ou restrições no bureau.

A restrição decorre do score 644, da probabilidade de inadimplência de 13% e dos registros de atrasos de até 60 dias. A entrada de 25% reduz a exposição para R$ 4.635,00, abaixo do ticket médio histórico, equilibrando segurança financeira e continuidade comercial.

**Decisão final: 🟡 aprovar com restrição, 25% de entrada, saldo em 30/60/90 dias, sem 120 dias, após correção do orçamento e validação de títulos em aberto.**

## Atualização pós-aprovação — 08/08/2026

Sérgio Ladeira aprovou a operação após a leitura complementar dos títulos do DEBX. A aprovação mantém as condições acima e incorpora o saldo de R$ 18.363,54 a vencer na exposição consolidada do cliente. O padrão observado — parcelas pagas no vencimento ou com compensação de até 3 dias — reforça a continuidade do crédito, mas exige monitoramento e não autoriza classificar o cliente como Classe A plena.

## Fontes e limitações

- Orçamento PDF nº 0115549 — fonte dos itens, valor, frete e condição solicitada;
- Equifax | Boa Vista — relatório de 07/08/2026;
- SQL Server Hotel Finder — cadastro e histórico de pedidos;
- Receita WS — situação cadastral, atividade, porte e QSA;
- Google Maps, website próprio, Booking.com e Tripadvisor — validação operacional;
- Consulta realizada em modo somente leitura; nenhuma alteração foi feita no banco.
