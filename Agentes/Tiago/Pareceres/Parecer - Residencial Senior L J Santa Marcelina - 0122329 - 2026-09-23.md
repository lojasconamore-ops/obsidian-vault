---
tipo: parecer-credito
cliente: RESIDENCIAL SENIOR L J SANTA MARCELINA LTDA
nome_fantasia: TERCA DA SERRA SANTA MARCELINA
cnpj: 32.679.264/0001-00
pedido: "0122329"
data: 2026-09-23
parecer: reprovar-faturado
risco: alto
---

# Parecer de Crédito — Residencial Sênior L J Santa Marcelina LTDA

**Data de corte:** 23/09/2026, BRT  
**Pedido/proposta:** 0122329  
**CNPJ:** 32.679.264/0001-00  
**Cadastro DEBX informado no PDF:** 06998  
**Nome operacional atual:** Terça da Serra Santa Marcelina  
**Representante:** Monica Cristina da Silva Cagliari

## Resumo executivo

**Parecer: ❌ REPROVAR CRÉDITO FATURADO**  
**Nível de risco: alto**

O bureau Equifax/Boa Vista confirma **19 protestos ativos, totalizando R$ 23.768,38**, além de score 569 e probabilidade de inadimplência de 18%. A proposta solicita boleto puro em 30/60/90, sem entrada, deixando exposição integral de R$ 1.270,00. Pelas regras da Política de Crédito Conamore, restrição ativa relevante supera score, valor reduzido do pedido e evidência operacional.

**Condição permitida:** somente PIX/TED antecipado ou cartão de crédito. Qualquer faturamento excepcional depende de autorização expressa do Sérgio/diretoria.

## Etapa 0 — Lista Negra Conamore

✅ O CNPJ, a razão social e os nomes operacionais não constam na Lista Negra interna consultada.

A ausência na lista interna não elimina o veto, pois o bureau mais recente apresenta protestos ativos.

## Etapa 1 — Histórico interno Conamore

Consulta realizada no SQL Server `hotel-finder`, usando CNPJ normalizado, razão social, nome fantasia, endereço e os termos `Quinta da Colina` e `Santa Marcelina`.

- Nenhum cadastro foi localizado em `conamore.Customers` para o CNPJ 32.679.264/0001-00.
- Nenhum pedido faturado/expedido foi localizado em `debx.PDV_Detalhes`.
- O pedido 0122329 não estava integrado no Hotel Finder no corte da consulta.
- O código `06998` informado no PDF não foi usado isoladamente para transferir histórico, pois não houve confirmação por CNPJ no banco.

**Classificação interna:** sem histórico Conamore comprovado / primeira compra efetiva.

### Verificação ampliada realizada em 23/09/2026 às 18:20 BRT

Após questionamento do CEO, a busca foi repetida de forma ampliada por:

- CNPJ normalizado `32679264000100`;
- pedido `0122329`;
- razão atual e anterior;
- nomes `Quinta da Colina`, `Santa Marcelina` e `Residencial Senior L J`;
- endereço Rua Salim Feres, 299;
- códigos `06998`, `A6998`, `6998` e equivalentes numéricos `6998/106998`;
- tabelas `conamore.Customers`, `debx.PDV_Detalhes` e `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`.

**Resultado:** nenhum pedido ou venda foi encontrado para este CNPJ, razão social ou endereço. O código legado `A6998` pertence a **ALIRIO GOMES FONSECA LTDA / Depósito Bonfim**, CNPJ 71.681.571/0001-87, em Taubaté/SP; portanto, é uma colisão de código e foi expressamente excluído do histórico do cliente.

Foram encontrados pedidos de outras unidades da marca Terça da Serra, como Chácara Primavera e Hortolândia, mas são CNPJs distintos e não foram transferidos para Santa Marcelina.

### Limitação Oracle

A consulta ocorreu às 18:11 BRT, fora da janela operacional diária do Oracle DEBX. Conforme treinamento, o Oracle fica indisponível após as 18:00. A análise prosseguiu com o SQL Server e as demais fontes, sem inventar posição de títulos Oracle.

A ausência de Oracle não altera o veto: os 19 protestos ativos no bureau já são suficientes para reprovar faturamento.

## Etapa 2 — Score / Bureau

Relatório Equifax | Boa Vista emitido em **23/09/2026 às 16:33:50**, resposta **040760935-3**, conferido visualmente nas quatro páginas.

- **CNPJ:** 32.679.264/0001-00
- **Razão exibida no bureau:** Quinta da Colina Casa de Repouso Santa Marcelina LTDA
- **Score Aprovação PJ:** 569 — alto risco
- **Probabilidade de inadimplência:** 18,0% — elevada
- **Cadastro Positivo:** participante com informação
- Não há histórico mensal de pagamento pontual exibido
- A faixa `6 a 15 dias` apresenta índice modelado 100; não foi interpretada como valor monetário nem como quantidade de ocorrências
- **Pendências e restrições financeiras:** nada consta na categoria específica
- **Cheques sem fundos, sustados ou devolvidos:** nada consta
- **Protestos:** **19 ocorrências**, total de **R$ 23.768,38**
- Primeiro protesto: 12/06/2023, R$ 1.299,30
- Último protesto: 01/09/2025, R$ 1.733,50

Últimos protestos detalhados no relatório:

| Registro | Vencimento | Cartório | Cidade/UF | Valor |
|---|---|---|---|---:|
| 01/09/2025 | 16/08/2025 | 3º Cartório | Campinas/SP | R$ 1.733,50 |
| 01/08/2025 | 16/07/2025 | 3º Cartório | Campinas/SP | R$ 1.733,50 |
| 04/07/2025 | 16/06/2025 | 1º Cartório | Campinas/SP | R$ 1.733,50 |
| 16/06/2025 | 19/05/2025 | 2º Cartório | Campinas/SP | R$ 1.232,29 |
| 05/06/2025 | 16/05/2025 | 2º Cartório | Campinas/SP | R$ 1.733,50 |

Os protestos são numerosos, materiais e registrados na própria cidade da empresa. Não se trata de apontamento isolado ou de pequeno valor.

### Atualização cadastral pública

A consulta da Receita embutida no bureau tinha corte de 20/03/2024 e razão social antiga. A BrasilAPI foi consultada em 23/09/2026 e confirmou:

- **Razão atual:** Residencial Senior L J Santa Marcelina LTDA
- **Fantasia:** Terça da Serra Santa Marcelina
- **Situação:** ativa
- **Abertura:** 05/02/2019
- **Atividade principal:** instituições de longa permanência para idosos
- **Capital social:** R$ 100.000,00
- **Porte:** microempresa
- **Endereço:** Rua Salim Feres, 299, Jardim Santa Marcelina, Campinas/SP
- **Sócio-administrador atual:** Leandro Delelis da Cruz Junior, com entrada societária em 13/08/2026

O mesmo CNPJ e endereço confirmam que os dois arquivos se referem à mesma pessoa jurídica, apesar da mudança de razão/nome operacional.

## Etapa 3 — Coerência operacional do pedido

O pedido contém 50 toalhas de banho Fit, item compatível com instituição de longa permanência para idosos. O volume e o ticket são operacionalmente plausíveis.

### Reconciliação da proposta

- Produto: 50 toalhas de banho Fit
- Valor unitário: R$ 25,40
- Soma da linha: **R$ 1.270,00**
- Total sem desconto: **R$ 1.270,00**
- Desconto: **R$ 0,00**
- Frete: **R$ 0,00**
- Total do pedido: **R$ 1.270,00**
- Forma: boleto 30/60/90 dias
- Parcelas impressas: 3 × R$ 423,33 = **R$ 1.269,99**
- Divergência de arredondamento: **R$ 0,01**

A proposta precisa ter uma parcela ajustada em R$ 0,01 caso seja convertida para pagamento antecipado/cartão, para fechar exatamente o total do pedido.

### Validade

- Emissão: 23/09/2026
- Validade: 24/09/2026
- Situação em 23/09/2026: válida, porém **não aprovada para faturamento**.

## Etapa 4 — Exposição real

- Total do pedido: R$ 1.270,00
- Entrada: R$ 0,00
- **Exposição líquida solicitada:** R$ 1.270,00

A condição viola a diretriz interna de exigir pelo menos 25% de entrada e, mesmo com entrada, os protestos ativos impedem concessão de crédito faturado.

## Etapa 5 — Validação operacional online

🟢 **Operação real e forte**, mas isso não neutraliza os protestos.

- Google Maps localizou a operação como **Residencial Sênior Terça da Serra — Santa Marcelina**.
- Avaliação exibida: **4,1**.
- Categoria: residência assistida/instituição para idosos.
- Endereço exato: Rua Salim Feres, 299, Campinas/SP.
- Operação indicada como aberta 24 horas.
- Site oficial associado: `tercadaserra.com.br`.
- Telefone público no Maps: (19) 99893-8936.
- O site direto apresentou proteção Cloudflare ao acesso automatizado; a existência do domínio e o vínculo foram confirmados pelo perfil do Maps.

## Partes relacionadas / grupo econômico

O quadro societário atual indica Leandro Delelis da Cruz Junior. Foi localizada publicamente outra empresa ativa sob o mesmo titular, `54.176.497 LEANDRO DELELIS DA CRUZ JUNIOR`, CNPJ 54.176.497/0001-34, também em Campinas, aberta em 21/02/2024.

- Não foi localizado cadastro ou histórico Conamore para essa empresa.
- Não há confirmação de mesma operação/endereço.
- Nenhuma exposição, histórico ou limite foi transferido entre os CNPJs.

Pesquisas baseadas em antigos sócios da empresa foram descartadas, pois a composição societária foi alterada em 13/08/2026.

## Decisão final

**❌ REPROVAR FATURAMENTO EM BOLETO.**

Condições aceitáveis:
1. PIX ou TED com pagamento integral antecipado; ou
2. cartão de crédito, sujeito à aprovação da adquirente; ou
3. excepcionalmente, faturamento somente com autorização expressa do Sérgio/diretoria após apresentação de certidões de cancelamento/baixa dos 19 protestos e nova consulta de bureau.

**Justificativa técnica objetiva:** score 569, probabilidade de inadimplência de 18%, ausência de histórico Conamore, boleto puro sem entrada e 19 protestos ativos de R$ 23.768,38 tornam o risco incompatível com crédito direto, ainda que o pedido seja pequeno e a operação seja real.
