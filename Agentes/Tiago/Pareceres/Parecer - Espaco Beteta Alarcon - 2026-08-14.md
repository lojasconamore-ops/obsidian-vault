# Parecer de Crédito — Espaço Beteta Alarcon / Hotel Pirâmides Jarinu

**Data:** 14/08/2026 (BRT)
**Documento analisado:** relatório Equifax | Boa Vista, consultado em 13/08/2026 às 11:30:41
**CNPJ:** 13.825.407/0001-08
**Razão social:** ESPACO BETETA ALARCON HOTELARIA E EVENTOS LTDA
**Nome fantasia:** HOTEL PIRAMIDES JARINU

## Etapa 0 — Lista Negra

**Resultado:** cliente não localizado na Lista Negra Conamore por CNPJ ou razão social.

## Parecer

**🟡 Aprovar com restrição**

**Nível de risco:** moderado-baixo para o bureau; moderado para a operação Conamore por ausência de histórico faturado identificado.

## Histórico Conamore

Localizado no Hotel Finder com `ID_DEBX A0327`, status ativo. Foi encontrado **1 registro**, o pedido **0116110**, datado de 10/08/2026, ainda classificado como **Orçamento**, no valor de **R$ 15.517,50**, frete de **R$ 50,00**, condição registrada como **boleto 30/60/90 dias**.

Não foi identificado pedido expedido/faturado ou histórico de pagamento compensado nesta consulta. Portanto, o registro não deve ser tratado como comportamento recorrente. O cadastro do Hotel Finder apresenta endereço em São Paulo, enquanto o bureau/Receita informa a operação em Jarinu; exigir confirmação cadastral antes do faturamento.

## Score / Bureau

Relatório Equifax | Boa Vista:

- Score Aprovação PJ: **847/1.000 — muito forte**
- Probabilidade de inadimplência: **2,0%**
- Cadastro Positivo: **participante, com informação**
- Pagamento pontual até 5 dias: **100% em todos os meses exibidos (ago/2025 a jul/2026)**
- Atrasos de 6 a 15, 16 a 30, 31 a 60 e acima de 60 dias: **zero**
- Atraso médio: **0 dia**
- Pendências e restrições financeiras: **nada consta**
- Protestos: **nada consta**
- Cheques sem fundos/devolvidos: **nada consta**
- CNPJ: **ativo**, fundado em 09/06/2011
- CNAE principal: **hotéis**

O bureau é claramente favorável e reduz o risco cadastral, mas não substitui histórico de pagamento na Conamore.

## Coerência operacional

A atividade principal é hotelaria e o nome fantasia corresponde ao Hotel Pirâmides Jarinu. Foram encontradas presença operacional consistente: site próprio (`hotelfazendapiramides.com.br`), listagens em Trip.com, Booking.com e TripAdvisor, além de perfis no Instagram. O TripAdvisor apresenta o hotel com avaliações e classificação entre os hotéis de Jarinu.

**Classificação:** 🟢 Operação forte.

Há, contudo, divergência de endereço: o bureau/Receita aponta Rodovia Edgard Máximo Zambotto, s/n, km 74,5, Jarinu/SP; o cadastro Conamore consultado aponta Avenida Imperatriz Leopoldina, 371, São Paulo/SP. Confirmar endereço, telefone e dados de faturamento com o Comercial antes de emitir NF.

## Exposição real

O orçamento identificado no Hotel Finder é de **R$ 15.517,50**, sem entrada registrada no parcelamento consultado.

- Exposição sem entrada: **R$ 15.517,50**
- Entrada mínima recomendada de 25%: **R$ 3.879,38**
- Exposição após 25% de entrada: **R$ 11.638,13**
- Frete informado separadamente: **R$ 50,00**

## Condição recomendada

Aprovar a venda **somente com 25% de entrada compensada** e saldo em **30/60 dias**, evitando boleto puro em 30/60/90 nesta primeira operação efetiva. Se o Comercial exigir manutenção de 30/60/90, solicitar **50% de entrada** e faturar o saldo somente após conferência cadastral e compensação da entrada.

Não aprovar pedido sem entrada sem autorização explícita do Sérgio.

## Justificativa técnica objetiva

O cliente apresenta bureau excelente, CNPJ ativo há mais de 15 anos, operação hoteleira coerente e presença online forte, sem protestos ou restrições. Porém, a Conamore ainda não possui histórico de pagamento comprovado: o único registro localizado é um orçamento de primeira operação, e há divergência cadastral relevante de endereço entre Hotel Finder e bureau/Receita. A aprovação é comercialmente recomendável, mas com entrada mínima, prazo mais curto e correção/validação cadastral antes do faturamento.

## Fontes e limitações

- PDF Equifax | Boa Vista enviado pelo usuário.
- Lista Negra Conamore, atualizada em 29/06/2026.
- Hotel Finder SQL Server: `conamore.Customers` e `debx.PDV_Detalhes`, consulta de 14/08/2026.
- Receita WS para dados cadastrais públicos, consulta de 14/08/2026.
- Busca pública DuckDuckGo Lite para presença online, consulta de 14/08/2026.
- Não foi consultado Oracle DEBX, pois a validação interna necessária foi obtida no Hotel Finder e não havia solicitação operacional específica de títulos Oracle.
