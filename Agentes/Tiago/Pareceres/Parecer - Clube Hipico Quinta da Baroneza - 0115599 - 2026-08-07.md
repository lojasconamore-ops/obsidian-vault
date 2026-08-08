# Parecer de Crédito — Clube Hípico Quinta da Baroneza

**Data da análise:** 07/08/2026 (BRT)  
**Pedido:** 0115599  
**CNPJ:** 03.885.501/0001-90  
**ID DEBX:** A0831  
**Arquivos utilizados:**
- Orçamento de venda nº 0115599, emitido em 06/08/2026;
- Relatório Equifax | Boa Vista, emitido em 07/08/2026 às 17:58:11.

Os dois arquivos referem-se ao mesmo CNPJ e foram consolidados nesta análise.

## Etapa 0 — Lista Negra

**Resultado: ✅ Cliente não localizado na Lista Negra Conamore.**

A análise prossegue. Esta conclusão não elimina a restrição externa identificada no bureau, tratada na Etapa 2.

## Parecer

# ❌ Reprovar faturamento a prazo neste momento

**Nível de risco para crédito faturado: alto.**  
**Venda à vista / antecipada: admissível, sujeita à conferência comercial e financeira.**  
**Exceção:** somente com autorização explícita da diretoria, documentada.

## Identificação e operação

- **Razão social:** CLUBE HIPICO QUINTA DA BARONEZA
- **Natureza jurídica:** Associação Privada
- **Atividade principal:** Clubes sociais, esportivos e similares — CNAE 93.12-3/00
- **Atividade secundária:** Restaurantes e similares
- **Endereço cadastral:** Rodovia Alkındar Monteiro Junqueira, s/n, Km 33,5, Quinta da Baroneza II, Bragança Paulista/SP, CEP 12918-001
- **Contato no orçamento:** compras@quintadabaroneza.com.br; (11) 2490-2000 no cadastro público
- **Data de abertura:** 23/05/2000 — empresa/associação madura
- **Situação cadastral:** ATIVA
- **Porte:** DEMAIS
- **Capital social informado na Receita WS:** R$ 0,00 — sinal de capacidade financeira limitada como indicador isolado; não é prova de insolvência.

## Histórico Conamore / Hotel Finder

Consulta realizada no SQL Server `hotel-finder`, usando CNPJ, razão social e ID DEBX. O cadastro foi localizado como **A0831**, com status ativo.

### Histórico do cliente-alvo — A0831

| Pedido | Data | Status | Valor | Condição |
|---|---:|---|---:|---|
| 0005707 | 22/08/2024 | Expedição | R$ 5.475,60 | PIX à vista |
| 0066346 | 22/10/2025 | Cancelado | R$ 6.232,10 | Boleto 30 dias |
| 0076448 | 09/12/2025 | Expedição | R$ 2.925,60 | Boleto 30 dias |

- **Pedidos expedidos identificados:** 2
- **Histórico expedido:** R$ 8.401,20
- **Ticket médio expedido:** R$ 4.200,60
- **Maior pedido expedido:** R$ 5.475,60
- **Condição a prazo já praticada:** boleto 30 dias
- **Pedido cancelado:** R$ 6.232,10, também com boleto 30 dias; o motivo financeiro não está disponível no retorno consultado.

Foi localizado também o cadastro **A4580 — Sociedade Residencial Quinta da Baroneza**, no mesmo complexo/endereço, com um pedido expedido de R$ 5.475,60. O compartilhamento do endereço confirma vínculo operacional com o empreendimento, mas **não autoriza transferir automaticamente o histórico ou o crédito entre CNPJs distintos**. O histórico principal deste parecer permanece o do CNPJ 03.885.501/0001-90.

**Classificação interna preliminar:** histórico positivo, porém ainda curto para sustentar o salto de limite solicitado; o cliente já utilizou boleto 30 dias, mas a operação atual é materialmente maior.

### Títulos pagos e em aberto — Oracle DEBX

Consulta complementar realizada em 08/08/2026 (BRT), pela cadeia `CNPJ → EMP_CODEMP A0831 → PDV_NUMPED → TEST_MATRIZ.F_TITULOS`, com conferência nos schemas `TEST_ACL`, `TEST_CHC`, `TEST_GCL` e `TEST_BRG`.

- **2 títulos parcelados identificados**, ambos pagos;
- **R$ 8.401,20** em títulos liquidados;
- 1 título pago no vencimento;
- 1 título compensado 1 dia após o vencimento;
- atraso máximo observado: **1 dia**;
- **nenhum título em aberto**;
- **nenhum título vencido** na data da consulta;
- `TEST_ACL`, `TEST_CHC`, `TEST_GCL` e `TEST_BRG`: sem títulos correspondentes.

Essa leitura reforça que não há dívida em aberto com a Conamore e que o histórico interno de pagamento é controlado. Contudo, são apenas dois títulos e o bureau registra um protesto externo ativo; portanto, o bom comportamento interno não elimina a trava de crédito a prazo.

**Classificação interna revisada:** Classe B — histórico curto, mas positivo e sem saldo vencido; insuficiente para neutralizar protesto externo ativo ou justificar salto automático de limite.

## Etapa 2 — Score / Bureau

Relatório Equifax | Boa Vista para o mesmo CNPJ:

- **Cadastro Positivo:** participante com informação
- **Score Aprovação PJ:** **917/1.000** — muito forte
- **Probabilidade de inadimplência:** **1,0%** — excelente
- **Pagamento pontual:** 100% em todos os meses apresentados, de ago/2025 a jul/2026
- **Atrasos:** nenhum registro nas faixas de 6–15, 16–30, 31–60 ou acima de 60 dias
- **Pendências e restrições financeiras:** nada consta
- **Cheques:** nada consta
- **Consultas:** 41 no período de 01/08/2025 a 01/08/2026
- **Protestos:** **1 protesto ativo, no valor de R$ 1.533,28, datado de 14/07/2026, 1º Cartório de Bragança Paulista/SP**
  - vencimento informado: 04/12/2024

### Interpretação

O score e o comportamento de pagamento são excelentes, mas a Política de Crédito Conamore determina que **restrição ativa relevante supera o score**. Portanto, o protesto ativo impede a aprovação de faturamento a prazo, apesar dos demais indicadores favoráveis.

## Etapa 3 — Coerência operacional

**Coerente.** O cliente é um clube recreativo/esportivo associado ao complexo Quinta da Baroneza, e o mix é composto por itens de enxoval e hotelaria: fronhas, edredons, protetores, travesseiros e saia para cama box.

O volume também é operacionalmente plausível, mas representa aumento relevante frente ao histórico individual:

- Pedido atual com frete: **R$ 18.003,20**
- Aproximadamente **4,29 vezes o ticket médio expedido**
- Aproximadamente **3,29 vezes o maior pedido expedido**

Esse salto exigiria controle de exposição mesmo sem o protesto.

## Etapa 4 — Reconciliação comercial e exposição

O orçamento apresenta divergência de totais que deve ser corrigida antes de qualquer faturamento:

- **Soma dos itens / Total sem desconto:** R$ 17.953,20
- **Frete:** R$ 50,00
- **Total com frete indicado como Total Pedido:** R$ 18.003,20
- **Total c/ desconto:** R$ 17.953,20
- **Desconto:** R$ 0,00
- **Forma de pagamento:** `A DEFINIR`
- **Parcelamento/entrada:** não informado

A soma dos itens mais o frete é R$ 18.003,20. O documento, porém, também exibe R$ 17.953,20 como total com desconto, embora o desconto seja zero. O ERP/PDV retornou igualmente `A DEFINIR` e valor de R$ 16.032,30, divergente do orçamento. O PDF é a fonte comercial principal, mas a inconsistência precisa ser corrigida.

### Exposição líquida indicativa

Como não há entrada nem condição definida, a exposição potencial é o total com frete:

- **Sem entrada:** R$ 18.003,20 de exposição
- **Com 25% de entrada:** entrada de R$ 4.500,80; exposição de R$ 13.502,40
- **Com 50% de entrada:** entrada de R$ 9.001,60; exposição de R$ 9.001,60

Esses cenários são apenas referência de controle e **não autorizam faturamento enquanto houver protesto ativo**.

## Etapa 5 — Validação operacional online

**Classificação: 🟡 Operação parcial, com sinais consistentes de existência real.**

Evidências verificadas:

- Receita WS: CNPJ ativo, atividade e endereço compatíveis;
- Site oficial `nabaroneza.com.br`: página institucional “Quinta da Baroneza | Clubes” acessível;
- Google Maps: resultados para Quinta da Baroneza e Clube Hípico/Restaurante na localidade;
- Busca pública: listagem do Clube Hípico Quinta Baroneza em Bragança Paulista no Yelp.

Não foram confirmadas, nesta consulta, avaliações quantitativas robustas em Google Maps nem presença social oficial inequívoca do CNPJ. A operação é real e coerente, mas a validação online não substitui a regularização do protesto.

## Condição recomendada

### Para liberar o pedido agora

1. **Não faturar a prazo.**
2. Solicitar comprovação de baixa/regularização do protesto de R$ 1.533,28 e nova validação do bureau.
3. Corrigir a divergência entre orçamento, total, frete e PDV/ERP.
4. Até a baixa confirmada: aceitar somente **PIX/TED antecipado ou cartão**, com pagamento integral antes da expedição.
5. Se a diretoria autorizar excepcionalmente a venda a prazo, exigir autorização expressa e, como mitigação mínima, **50% de entrada + saldo máximo em 30 dias**, mantendo a exposição em R$ 9.001,60 antes de qualquer revisão do limite.

### Reanálise com títulos do Oracle — 08/08/2026

A consulta de contas a receber não encontrou títulos vencidos ou em aberto na Conamore. Foram identificados 2 títulos, ambos liquidados: um no vencimento e outro com 1 dia de diferença. Esse resultado reforça a capacidade de pagamento no relacionamento interno, mas não altera a decisão de crédito porque permanece 1 protesto externo ativo de R$ 1.533,28. Pela Política de Crédito, a restrição ativa supera score, pontualidade e ausência de dívida interna.

## Justificativa técnica objetiva

O cliente tem CNPJ ativo desde 2000, operação verificável, score 917, PD 1%, cadastro positivo e 100% de pontualidade no bureau. Também possui dois pedidos expedidos na Conamore, incluindo boleto de 30 dias. Esses fatores são positivos.

Entretanto, há **um protesto ativo recente de R$ 1.533,28**, e a Política de Crédito determina que uma restrição ativa relevante supera score e demais sinais positivos. Além disso, o pedido de R$ 18.003,20 representa salto de 3,29 vezes o maior pedido expedido e o documento/ERP apresenta divergência de total e condição de pagamento.

**Conclusão:** venda pode ser preservada com pagamento antecipado, mas **não há base para aprovar faturamento a prazo sem baixa do protesto, correção documental e nova validação**.

## Fontes e limitações

- Orçamento PDF nº 0115599 — fonte dos itens e termos comerciais;
- Equifax | Boa Vista — relatório de 07/08/2026;
- SQL Server Hotel Finder — cadastro e pedidos internos;
- Oracle DEBX `TEST_MATRIZ.F_TITULOS` — títulos pagos e em aberto, consultado em 08/08/2026;
- Receita WS — situação cadastral e atividade;
- Site oficial, Google Maps e Yelp — validação operacional;
- Oracle DEBX foi consultado em modo somente leitura; nenhuma alteração foi realizada em banco.
