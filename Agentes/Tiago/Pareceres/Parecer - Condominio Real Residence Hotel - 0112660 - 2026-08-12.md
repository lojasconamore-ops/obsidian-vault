# Parecer de Crédito — CONDOMÍNIO REAL RESIDENCE HOTEL — Pedido 0112660

**Data da análise:** 12/08/2026 — BRT  
**Analista:** Tiago — Gerente Financeiro  
**Documentos analisados:** proposta comercial `112660 - Proposta Comercial Codominio Residencial Hotel.pdf` e relatório Equifax/Boa Vista `ANÁLISE CONDOMINIO REAL RESIDENCE.pdf`.

## Identificação

| Campo | Resultado |
|---|---|
| Razão social | CONDOMINIO REAL RESIDENCE HOTEL |
| Nome fantasia | HOTEL RESIDENCIA |
| CNPJ | 31.510.472/0001-18 |
| ID DEBX | A3633 |
| Endereço cadastrado | Avenida Princesa Isabel, 500, Copacabana, Rio de Janeiro-RJ, CEP 22011-010 |
| E-mail | secretaria@realresidencehotel.com.br |
| Contato informado | Alexandre — (21) 98711-4285 |
| Atividade no bureau | Condomínios prediais — CNAE 81.12-5/00 |
| Natureza jurídica | Condomínio edilício |
| Situação cadastral | Ativa |
| Data de fundação | 10/07/1983 |
| Data da situação cadastral | 19/03/2005 |
| Porte | Demais |
| Empregados no bureau | Faixa de 20 a 99 |

**Observação cadastral:** a proposta traz o endereço de entrega correto, na Avenida Princesa Isabel, 500, Copacabana. O campo de endereço no cabeçalho aparece com texto adicional de localidade (“VALINHOS - SP - 13278078”), mas o CNPJ, o endereço de entrega e o bureau convergem para Rio de Janeiro-RJ. Corrigir/remover esse texto estranho antes do faturamento para evitar erro fiscal/logístico.

## Dados comerciais do pedido

- **Pedido/orçamento:** 0112660.
- **Emissão:** 17/07/2026.
- **Validade:** 14/08/2026.
- **Vendedor:** Carlos Manoel da Silva.
- **Mix:** enxoval hoteleiro — fronhas, lençóis solteiro/casal/king, cobertores, toalhas de banho/rosto/piso e travesseiros rolinho.
- **Frete:** R$ 50,00.
- **Desconto informado:** R$ 4.723,29.
- **Total sem desconto:** R$ 37.790,30.
- **Total com desconto:** R$ 33.067,01.
- **Total do pedido, incluindo frete:** R$ 33.117,01.
- **Pagamento impresso:** entrada de 30% + saldo em boletos de 30/60/90/120/150/180 dias.
- **Prazo de entrega:** até 7 dias úteis; itens informados como pronta entrega.

## Reconciliação comercial e exposição

A proposta apresenta uma divergência matemática de **R$ 0,01** entre o total do pedido e a soma da programação impressa:

- Entrada impressa: **R$ 9.935,10**.
- 6 boletos de R$ 3.863,65: **R$ 23.181,90**.
- Soma da programação: **R$ 33.117,00**.
- Total do pedido informado: **R$ 33.117,01**.

A divergência é apenas de arredondamento, mas deve ser corrigida no PDF/ERP antes da emissão fiscal e dos boletos.

**Exposição líquida solicitada:**

- Total do pedido: **R$ 33.117,01**.
- Entrada de 30%: **R$ 9.935,10**.
- **Saldo financiado: R$ 23.181,91**.
- Percentual de entrada efetivo: aproximadamente **30%**.

A exposição é relevante para uma primeira compra identificada no Hotel Finder; não deve ser liberada como boleto puro.

## Etapa 0 — Lista Negra Conamore

✅ **Cliente não localizado na Lista Negra Conamore**, por CNPJ, razão social ou nome fantasia, na lista consultada, atualizada em 29/06/2026.

Prossegue-se com a análise.

## Etapa 1 — Histórico interno Conamore

### Hotel Finder / SQL Server

O cadastro foi localizado no Hotel Finder:

- **Razão social:** CONDOMINIO REAL RESIDENCE HOTEL.
- **CNPJ:** 31510472000118.
- **ID DEBX:** A3633.
- **Status:** 0 — ativo.
- **Endereço:** Avenida Princesa Isabel, 500, Rio de Janeiro-RJ.

Foi localizado o orçamento **0112660**, de 17/07/2026, no valor de R$ 33.117,01, com a mesma condição de pagamento da proposta. O registro está classificado como **“Orçamento”**, sem data de venda/aprovação; portanto, **não é compra faturada nem histórico de pagamento**.

Não foram localizados pedidos expedidos/faturados anteriores do CNPJ no Hotel Finder. O orçamento atual deve ser tratado como **primeira compra efetiva / histórico interno insuficiente**.

### Oracle DEBX

A sessão Oracle foi validada com sucesso no serviço `conamore`, usuário `TEST_PED`, em leitura. Foram validados os schemas operacionais; para este CNPJ/ID não foram localizados pedidos correspondentes nas tabelas PED consultadas. Também não foram encontrados títulos parcelados associados ao cliente. Foi localizado apenas um título isolado de R$ 84,97, emitido em 10/04/2026, vencido em 11/05/2026 e pago em 12/05/2026, sem pedido correspondente identificado na consulta por código; ele é insuficiente para caracterizar histórico recorrente.

**Classificação interna:** primeira compra / **sem histórico de crédito Conamore suficiente**.

### Partes relacionadas

A busca por endereço, número e cidade não identificou outro cliente Conamore no mesmo endereço. Não foi confirmada relação econômica com outro CNPJ do cadastro interno.

## Etapa 2 — Score / Bureau Equifax | Boa Vista

**Relatório emitido em:** 12/08/2026 às 11:44:08 — BRT.

| Indicador | Resultado | Leitura |
|---|---:|---|
| Score Aprovação PJ | **746** | Forte, próximo da faixa muito forte |
| Probabilidade de inadimplência | **4,0%** | Excelente/administrável |
| Cadastro Positivo | Participante com informação | Positivo |
| Pagamento pontual | Sem série pontuada | Não há histórico suficiente para medir comportamento |
| Pagamento atrasado | Sem registros | Não há atraso reportado |
| Compromissos | R$ 0,00 | Positivo |
| Pendências/restrições financeiras | Nada consta | Positivo |
| Protestos | Nada consta | Positivo |
| Cheques sem fundos/devolvidos | Nada consta | Positivo |
| CNPJ | Ativo | Positivo |
| Consultas no período | 3 | Baixa movimentação consultiva |
| Última compra/maior fatura/maior crédito no bureau | Outubro/2023 | Histórico comercial externo antigo e limitado |

O bureau é **forte e limpo**, mas há uma limitação importante: não há série de pagamentos pontuais, atrasos ou crédito obtido para validar capacidade de pagamento atual. O score não deve, isoladamente, autorizar exposição de R$ 23,2 mil em seis boletos.

## Etapa 3 — Coerência operacional do pedido

✅ **Coerente, com ressalva de segmento.** Embora o CNPJ esteja enquadrado como condomínio edilício, o nome fantasia é Hotel Residencia e o pedido é composto integralmente por itens de enxoval: lençóis, fronhas, cobertores, toalhas e travesseiros. O mix é compatível com operação hoteleira/residencial e a quantidade é plausível para reposição ou equipagem.

Não há personalização, bordado ou produção especial informada. Os itens estão indicados como pronta entrega, o que reduz o risco operacional. Recomenda-se, entretanto, confirmar com o comercial se a compra será para as unidades/áreas hoteleiras do condomínio e validar o responsável financeiro pelo pagamento.

## Etapa 4 — Exposição real da Conamore

- **Exposição bruta do pedido:** R$ 33.117,01.
- **Entrada mínima recomendada para primeira compra:** 50% = aproximadamente R$ 16.558,51.
- **Saldo com 50% de entrada:** aproximadamente R$ 16.558,50.
- **Exposição solicitada com 30% de entrada:** R$ 23.181,91.

A condição solicitada deixa a Conamore financiando cerca de 70% do pedido por até 180 dias, sem histórico interno suficiente. Esse é o principal fator de risco da operação.

## Etapa 5 — Validação operacional online

🟡 **Operação parcial.**

- O CNPJ, razão social, nome fantasia e endereço estão confirmados no relatório Equifax/Boa Vista e na Receita WS.
- A Receita WS retornou CNPJ **ATIVO**, fundação em 1983, porte “Demais”, natureza de condomínio edilício e endereço coincidente.
- Busca pública encontrou referência ao **Hotel Residencia — Copacabana** associada ao endereço, em página de condomínio/imóvel do Viva Real.
- A página pública encontrada foi protegida por Cloudflare quando acessada diretamente; portanto, não foram confirmadas avaliações, ocupação, telefone atual ou canais de reserva.
- Não foi encontrada, nesta validação, uma presença online robusta e diretamente atribuível ao CNPJ, como site próprio, ficha individual confirmada no Google Maps ou perfil de reservas com avaliações verificáveis.

A operação aparenta existir e possui longa antiguidade cadastral, mas a evidência online é insuficiente para classificar como operação forte.

## Parecer final

### 🟡 APROVAR COM RESTRIÇÃO — NÃO aprovar a condição original de 30% + 180 dias

**Nível de risco:** **moderado**, com risco concentrado na ausência de histórico interno e na exposição longa solicitada, apesar do bureau forte e limpo.

### Condição recomendada

Recomendo aprovar a venda somente com uma das seguintes estruturas:

**Opção preferencial — 50% de entrada + saldo curto:**
- Entrada: **R$ 16.558,51** aproximadamente, compensada antes da separação/expedição.
- Saldo aproximado: **R$ 16.558,50** em boleto para **30/60 dias**, preferencialmente dividido em duas parcelas.
- **Sem parcela em 90/120/150/180 dias** na primeira compra.

**Opção alternativa — manter 30% de entrada somente com fracionamento:**
- Entrada de aproximadamente R$ 9.935,10 compensada antes da expedição.
- Liberar primeiro lote limitado, mantendo exposição máxima inicial de **R$ 10 mil a R$ 12 mil**.
- Liberar os lotes seguintes após pagamento/compensação dos títulos anteriores.
- Reavaliar prazo e limite após o primeiro ciclo pago.

Não recomendo faturar a proposta inteira em 30% de entrada com seis boletos até 180 dias.

### Condições obrigatórias antes do faturamento

1. Corrigir no pedido/ERP a divergência de R$ 0,01 entre total e parcelas.
2. Corrigir o campo de endereço com referência a Valinhos-SP; manter Rio de Janeiro-RJ, CEP 22011-010, como endereço fiscal/entrega confirmado.
3. Confirmar a identidade e a alçada do responsável financeiro do condomínio.
4. Validar documentalmente que a compra se destina à operação Hotel Residencia/condomínio no endereço informado.
5. Compensar a entrada antes da separação e expedição.
6. Não liberar prazo superior a 60 dias na primeira operação sem autorização expressa do Sérgio.
7. Reconsultar restrições e situação cadastral se o faturamento ocorrer após a validade da proposta.

## Justificativa técnica objetiva

O cliente não está na Lista Negra, tem CNPJ ativo desde 1983, bureau forte — score 746, probabilidade de inadimplência de 4% e nenhuma restrição, protesto ou cheque — e apresentou pedido operacionalmente coerente com o nome fantasia hoteleiro. Porém, o pedido de R$ 33.117,01 é tratado como primeira compra, sem histórico interno relevante e sem série de pagamentos pontuais no bureau. A condição original financia R$ 23.181,91 por até 180 dias, exposição incompatível com a evidência efetivamente testada. A aprovação é comercialmente viável, mas deve ser condicionada a entrada maior, prazo curto ou fracionamento por lotes.

**Decisão:** aprovar a venda com restrição financeira; **não aprovar o faturamento na condição original** sem ajuste de entrada, prazo ou fracionamento.

**Fontes técnicas:** proposta comercial; relatório Equifax/Boa Vista; Lista Negra Conamore; Hotel Finder SQL Server (`conamore.Customers`, `debx.PDV_Detalhes`); Oracle DEBX (`TEST_MATRIZ`, somente leitura); Receita WS; busca pública online.
