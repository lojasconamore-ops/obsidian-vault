# Parecer Consolidado — Quinta da Baroneza e Luiz Lemes

**Data:** 07/08/2026 (BRT)  
**Arquivos analisados:**
1. Orçamento de venda nº 0115599 — Clube Hípico Quinta da Baroneza;
2. Relatório Equifax | Boa Vista — Luiz Lemes Martins Ltda. / Hotel Casa Blanca II.

## Alerta de identificação

Os documentos apresentam **CNPJs diferentes** e não podem ser consolidados como um único cliente:

- **Caso A:** Clube Hípico Quinta da Baroneza — CNPJ 03.885.501/0001-90 — DEBX A0831 — Bragança Paulista/SP;
- **Caso B:** Luiz Lemes Martins Ltda. / Hotel Casa Blanca II — CNPJ 17.910.016/0001-34 — DEBX A0030 — Frutal/MG.

As consultas realizadas não identificaram sócio comum, endereço comum ou relação econômica comprovada entre as empresas. Portanto, **score, protestos, histórico, limite e recomendação não são transferidos de um CNPJ para o outro**.

---

# CASO A — Clube Hípico Quinta da Baroneza

## Etapa 0 — Lista Negra

**✅ Não localizado na Lista Negra Conamore.**

## Parecer

# ❌ Reprovar faturamento a prazo neste momento

**Risco para crédito faturado: alto.** Venda antecipada permanece possível.

## Dados comerciais

- **Pedido:** 0115599
- **Emissão:** 06/08/2026
- **CNPJ:** 03.885.501/0001-90
- **ID DEBX:** A0831
- **Valor dos itens:** R$ 17.953,20
- **Frete:** R$ 50,00
- **Total com frete:** R$ 18.003,20
- **Forma de pagamento:** A DEFINIR
- **Mix:** saia para cama box, protetores, travesseiros, fronhas e edredons.

### Divergência comercial

O orçamento exibe R$ 17.953,20 como total sem/com desconto, embora o frete de R$ 50,00 indique total de R$ 18.003,20 e o desconto seja zero. O Hotel Finder/PDV retornou R$ 16.032,30, também com condição `A DEFINIR`. Corrigir orçamento e ERP antes do faturamento.

## Histórico Conamore

Consulta feita no SQL Server `hotel-finder` por CNPJ, razão social e ID DEBX:

- 2 pedidos expedidos;
- histórico expedido: **R$ 8.401,20**;
- ticket médio expedido: **R$ 4.200,60**;
- maior pedido expedido: **R$ 5.475,60**;
- condições já utilizadas: PIX à vista e boleto 30 dias;
- um orçamento cancelado de R$ 6.232,10.

O pedido atual é aproximadamente **4,29 vezes o ticket médio** e **3,29 vezes o maior pedido expedido**.

Foi localizado o CNPJ distinto Sociedade Residencial Quinta da Baroneza, no mesmo complexo/endereço, com histórico próprio. Esse dado é apenas contexto operacional e não permite transferência automática de crédito.

## Score / Bureau

Relatório Equifax | Boa Vista do mesmo CNPJ:

- Score: **917/1.000**;
- Probabilidade de inadimplência: **1,0%**;
- Cadastro Positivo com informação;
- Pagamento pontual: 100% no período apresentado;
- Sem pendências, cheques ou atrasos relevantes;
- **1 protesto ativo de R$ 1.533,28**, datado de 14/07/2026, no 1º Cartório de Bragança Paulista/SP.

O protesto ativo supera os indicadores positivos, conforme a Política de Crédito Conamore.

## Coerência operacional e presença online

**Coerência: adequada.** O cliente é clube recreativo/esportivo e o mix de enxoval é compatível com a operação.

**Validação online: operação parcial/real.** Foram confirmados CNPJ ativo, site institucional da Quinta da Baroneza, resultados no Google Maps e listagem pública do Clube Hípico. Não foram confirmados sinais suficientes para classificar como operação online forte.

## Condição recomendada

- Não faturar a prazo enquanto houver protesto ativo;
- aceitar PIX/TED antecipado ou cartão;
- exigir baixa do protesto e nova consulta de bureau;
- corrigir a divergência do orçamento/PDV;
- em eventual exceção formal da diretoria: mínimo de 50% de entrada, saldo máximo em 30 dias.

Com 50% de entrada sobre R$ 18.003,20:

- entrada: **R$ 9.001,60**;
- exposição: **R$ 9.001,60**.

---

# CASO B — Luiz Lemes Martins Ltda. / Hotel Casa Blanca II

## Etapa 0 — Lista Negra

**✅ Não localizado na Lista Negra Conamore** por CNPJ, razão social ou nome fantasia nas notas consultadas.

## Parecer

# 🟡 Aprovar com restrição — condicionado à apresentação do pedido comercial

Não há orçamento deste CNPJ entre os dois arquivos recebidos. Portanto, não é possível aprovar um valor específico ou calcular a exposição de uma venda determinada. O parecer abaixo é uma avaliação de limite/condição para eventual pedido futuro.

**Nível de risco:** moderado para cliente recorrente; alto segundo o bureau isoladamente.

## Identificação e operação

- **Razão social:** LUIZ LEMES MARTINS LTDA
- **Nome fantasia:** HOTEL CASA BLANCA II
- **CNPJ:** 17.910.016/0001-34
- **ID DEBX:** A0030
- **Situação cadastral:** ATIVA
- **Abertura:** 10/04/2013
- **Natureza:** Sociedade Empresária Limitada
- **CNAE:** Hotéis — 55.10-8/01
- **Porte:** Empresa de Pequeno Porte
- **Capital social informado:** R$ 103.900,00
- **Endereço público:** Avenida Goiás, 1542, Estudantil, Frutal/MG, CEP 38200-000
- **Sócio-administrador informado:** Luiz Lemes Martins

O cadastro interno usa Avenida Goiás, 1520, CEP 38206-052. A diferença de número/CEP deve ser confirmada comercialmente antes de faturar, embora telefone e operação apontem para o mesmo hotel.

## Histórico Conamore

Consulta realizada no Hotel Finder por CNPJ, razão social e nome fantasia. Foram identificados **15 pedidos expedidos**, totalizando **R$ 99.931,90**, com ticket médio de **R$ 6.662,13** e maior pedido de **R$ 14.709,20**.

O histórico mostra recorrência consistente entre 2024 e 2026, com diversas operações em boleto:

- boleto 30/60 dias;
- boleto 30/60/90 dias;
- boleto 30/60/90/120 dias;
- em pedidos anteriores, entrada de 20%, 25% ou 50% em algumas operações;
- também houve operações em cartão.

Foi identificado um orçamento interno recente de R$ 6.180,00 mais frete de R$ 50,00, ainda sem aprovação, com condição `A DEFINIR`. Esse orçamento interno não foi tratado como arquivo comercial enviado pelo usuário e não deve ser faturado sem definição formal da condição.

**Classificação interna indicativa:** Classe B — cliente recorrente com histórico relevante e condições a prazo já testadas. A classificação deve ser revisada se houver títulos vencidos, renegociação ou atraso atual não refletido na consulta.

## Títulos pagos e em aberto — Oracle DEBX

Consulta complementar em 08/08/2026 (BRT): 2 títulos do CNPJ A0831 na `TEST_MATRIZ.F_TITULOS`, ambos pagos, totalizando R$ 8.401,20. Um foi pago no vencimento e outro com 1 dia de diferença. Não há títulos em aberto ou vencidos. Os schemas `TEST_ACL`, `TEST_CHC`, `TEST_GCL` e `TEST_BRG` não apresentaram títulos correspondentes.

Esse resultado melhora a avaliação do relacionamento interno, mas não altera o veto de faturamento a prazo: o protesto externo ativo de R$ 1.533,28 permanece superior aos sinais positivos, conforme a Política de Crédito.

## Score / Bureau

Relatório Equifax | Boa Vista emitido em 07/08/2026:

- Score: **644/1.000** — faixa de cautela;
- Probabilidade de inadimplência: **13,0%** — elevada;
- Cadastro Positivo com informação;
- Pagamento pontual nos últimos 12 meses variando de 97% a 100%, com vários meses em 99%;
- Foram registrados atrasos de 6–15 dias e ocorrências na faixa de 31–60 dias;
- Sem pendências financeiras;
- Sem cheques devolvidos ou sustados;
- Sem protestos;
- Maior crédito informado: R$ 41 mil; maior fatura informada: R$ 28 mil;
- Última compra no bureau: junho/2026.

### Interpretação

O bureau isoladamente recomenda cautela por score 644 e PD 13%, mas não apresenta restrição ativa, protesto ou cheque. Como há histórico Conamore robusto e recorrente, o histórico interno pesa mais que o score isolado. O risco, contudo, não é baixo: os atrasos reportados e a PD elevada justificam manter entrada e limitar prazo.

## Coerência operacional e validação online

**Coerência: forte.** O CNAE é hotelaria e o cliente possui histórico recorrente de compras de enxoval/hotelaria na Conamore.

**Operação online: forte.** O Google Maps identificou o **Casablanca Palace Hotel**, com nota 4,1, endereço Av. Goiás, 1520, Frutal/MG, telefone (34) 3423-6188, website `casablancapalacehotel.com` e presença em Booking.com e Tripadvisor.com. A busca pública também encontrou referências ao Hotel Casa Blanca II no mesmo endereço/telefone.

## Condição recomendada para próximo pedido

Sem um orçamento formal, não aprovar valor específico. Para um pedido dentro do padrão histórico:

- preferencialmente **25% de entrada + saldo em 30/60/90 dias**;
- evitar ampliar para boleto 120 dias sem verificar títulos atuais e pontualidade recente;
- para pedido até aproximadamente o ticket médio histórico, exposição após 25% de entrada deve ser monitorada;
- para pedido acima de R$ 14.709,20, tratar como nova decisão de limite;
- confirmar endereço, condição de pagamento, títulos em aberto e ausência de renegociação antes da aprovação.

Se o pedido interno de R$ 6.230,00 com frete for o pedido efetivo, 25% de entrada representaria:

- entrada: **R$ 1.557,50**;
- exposição: **R$ 4.672,50**.

Esse cálculo é apenas indicativo, pois o orçamento correspondente não foi apresentado nos arquivos recebidos.

## Justificativa técnica objetiva

O CNPJ de Luiz Lemes é independente do CNPJ da Quinta da Baroneza e não pode receber o protesto ou o score do outro cliente. Para Luiz Lemes, o risco é administrável porque há 15 pedidos expedidos, quase R$ 100 mil de histórico Conamore, operação hoteleira confirmada e nenhum protesto ou restrição ativa. Em contrapartida, o score 644, PD 13% e registros de atraso impedem aprovação de prazo aberto ou aumento automático de limite.

**Conclusão do Caso B:** aprovar apenas com restrição, entrada mínima de 25%, prazo controlado e sem aprovação definitiva até receber o orçamento/valor exato.

---

## Conclusão consolidada

| Caso | CNPJ | Parecer | Motivo principal |
|---|---|---|---|
| Clube Hípico Quinta da Baroneza | 03.885.501/0001-90 | ❌ Reprovar faturamento a prazo | Protesto ativo de R$ 1.533,28 + divergência comercial |
| Luiz Lemes / Hotel Casa Blanca II | 17.910.016/0001-34 | 🟡 Aprovar com restrição | Histórico interno forte, mas score 644 e PD 13%; sem orçamento específico |

**Regra final:** não utilizar o relatório de Luiz Lemes para aprovar o pedido da Quinta da Baroneza, nem utilizar o protesto/score da Quinta da Baroneza para reprovar Luiz Lemes. São CNPJs independentes.
