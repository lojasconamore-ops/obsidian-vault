# Parecer de Crédito — Motel Guarapuava

- **Data do parecer:** 20/08/2026 (BRT)
- **Pedido:** 0116372
- **Razão social:** F. C. PACHECO - MOTEL LTDA
- **Nome fantasia:** Motel Guarapuava
- **CNPJ:** 35.170.449/0001-82
- **ID DEBX:** A2044
- **Arquivos analisados:** orçamento 0116372 e relatório Equifax | Boa Vista emitido em 20/08/2026 às 10:58:40

## Etapa 0 — Lista Negra

**Cliente não localizado na Lista Negra Conamore** por CNPJ, razão social ou nome fantasia. Prosseguir com a análise.

## Parecer

**🟡 Aprovar com restrição / aprovação condicionada à correção cadastral e definição formal da condição de pagamento.**

**Nível de risco:** moderado, controlável.

Não liberar faturamento com a condição atual `A DEFINIR`, nem emitir com o endereço impresso sem confirmação. Após os ajustes abaixo, recomendo faturamento com **50% de entrada compensada e saldo em 30/60 dias**, condição já praticada com o cliente. Exposição financeira estimada: **R$ 1.149,00**.

## 1. Documento comercial e exposição

O orçamento foi emitido em 12/08/2026, com validade também até 12/08/2026. Na data do parecer (20/08/2026), está **vencido**: exigir reemissão ou revalidação comercial.

Itens:

- 20 toalhas de banho Smart: R$ 634,00
- 20 lençóis casal: R$ 1.158,00
- 40 fronhas avulsas: R$ 456,00
- **Subtotal dos produtos / Total c/ desconto:** R$ 2.248,00
- **Frete:** R$ 50,00
- **Total do pedido com frete:** R$ 2.298,00
- **Desconto:** R$ 0,00
- **Forma de pagamento impressa:** `A DEFINIR`

A soma dos produtos é R$ 2.248,00; o valor financeiro total com frete é R$ 2.298,00. A condição de pagamento não está definida no documento.

Exposição conforme condição recomendada:

- Total financiável após entrada de 50%: **R$ 1.149,00**
- Parcelas indicativas: **2 x R$ 574,50 em 30/60 dias**, sujeitas ao recálculo/critério comercial final
- Sem entrada, a exposição seria R$ 2.298,00 — não recomendado e incompatível com a política interna

## 2. Histórico Conamore — Hotel Finder / DEBX

Cadastro confirmado por CNPJ, razão social e endereço-base no Hotel Finder:

- **ID atual:** A2044
- **Status:** 0 (ativo)
- **Histórico expedido identificado:** 7 pedidos, todos da mesma razão social e ID A2044/legado 02044
- **Período:** 09/10/2024 a 12/05/2026
- **Total expedido:** R$ 12.358,72
- **Ticket médio:** R$ 1.765,53
- **Maior pedido anterior:** R$ 3.731,00
- **Pedido atual com frete:** R$ 2.298,00 — 61,6% do maior pedido anterior e 1,30x o ticket médio

Pedidos expedidos considerados:

| Pedido | Data da venda | Valor | Condição |
|---|---:|---:|---|
| 0012553 | 09/10/2024 | R$ 1.030,32 | À vista |
| 0012568 | 09/10/2024 | R$ 1.782,20 | Cartão 2x |
| 0029918 | 15/04/2025 | R$ 1.987,60 | Entrada 50% + 30/60 |
| 0043997 | 18/06/2025 | R$ 1.211,60 | Entrada 50% + 30 |
| 0044384 | 20/06/2025 | R$ 198,00 | Cartão 1x |
| 0086051 | 23/01/2026 | R$ 3.731,00 | Entrada 50% + 30/60 |
| 0102751 | 12/05/2026 | R$ 2.418,00 | Entrada 50% + 30/60 |

O pedido 0116372 permanece como **orçamento** e não foi contado como compra expedida. Não foram incorporados registros de outras razões sociais apenas por conterem “Pacheco” no nome; a identidade foi validada por CNPJ/razão social/ID.

### Títulos no Oracle DEBX

Consulta somente leitura realizada em 20/08/2026, com sessão validada no serviço `conamore`, cadeia CNPJ → `TEST_MATRIZ.F_CDEMP` → `TEST_MATRIZ.F_PEDVENDA` → `F_TITULOS`.

- Empresa localizada no Oracle como **A2044**, status ativo
- 7 pedidos expedidos localizados na `TEST_MATRIZ.F_PEDVENDA`
- `TEST_MATRIZ.F_TITULOS`: **15 parcelas individuais**, total original R$ 12.358,72
- **15 pagas; R$ 12.358,72 pagos; 0 em aberto; 0 vencidos** na data de corte
- Schemas sem correspondência para esses pedidos: `TEST_ACL`, `TEST_CHC`, `TEST_GCL` e `TEST_BRG`
- Atrasos identificados: 6 parcelas, com atraso máximo de 8 dias e média de 3 dias entre as parcelas atrasadas
- Leitura de comportamento: paga, mas com atrasos recorrentes e algum desgaste de cobrança. Classificação interna recomendada: **Classe C — bom, mas desgastante**

O histórico é positivo quanto à quitação e suficiente para não tratar o cliente como primeira compra, mas não sustenta ampliação de prazo ou faturamento sem entrada.

## 3. Score / Bureau

Relatório Equifax | Boa Vista para o mesmo CNPJ e razão social:

- **Score:** 667 — faixa média/aceitável
- **Probabilidade de inadimplência:** 8,0% — administrável, no limite superior da faixa
- **Cadastro Positivo:** consumidor não participante; score menos confiável
- **Pendências/restrições financeiras:** nada consta
- **Protestos:** nada consta
- **Cheques sem fundos/sustados/devolvidos:** nada consta
- **CNPJ:** ativo
- **Fundação:** 14/10/2019
- **Situação ativa desde:** 17/03/2021
- **Atividade:** Motéis (CNAE 55.10-8/03)
- **Porte:** Microempresa
- **Capital social informado:** R$ 100.000,00
- **Consultas no período de 01/08/2025 a 01/08/2026:** 3

Não há restrição ativa que bloqueie o crédito. O bureau confirma risco administrável, mas não substitui o histórico interno.

## 4. Coerência operacional

O mix é coerente com um motel: toalhas, lençóis e fronhas para reposição de enxoval. O pedido atual é compatível com o porte histórico de compras e não representa salto agressivo de ticket. Não há personalização ou produção especial indicada.

## 5. Validação operacional online

**Classificação: 🟢 Operação forte.**

Validações realizadas:

- ReceitaWS: CNPJ ativo, atividade principal de motéis, email e telefone compatíveis
- Google Maps: **Motel Gpuava**, nota **4,9/5 com 179 avaliações**, categoria love hotel
- Google Maps exibe site próprio `motelgpuava.com`
- Site próprio acessível, com acomodações, tarifário, contatos, redes sociais, horários e endereço operacional

Endereço encontrado na ReceitaWS, Google Maps e site próprio: **Av. Dep. César Silvestre, 5229, Morro Alto, Guarapuava-PR, CEP 85065-694**.

## 6. Divergência cadastral obrigatória

O orçamento e o cadastro Hotel Finder imprimem **Rua Quinze de Novembro, 5257**. O relatório bureau usa **Rua Quinze de Novembro, 5229**. ReceitaWS, Google Maps e site próprio usam **Av. Deputado César Silvestre, 5229** — mesmo CEP, porém com divergência de logradouro e número.

A divergência pode decorrer de alteração de denominação da via e erro de número no orçamento, mas deve ser confirmada comercialmente antes do faturamento. Corrigir endereço de cobrança/entrega no pedido e garantir que NF, cadastro e entrega apontem para o endereço atualmente utilizado.

## Condição recomendada

1. Reemitir ou revalidar o orçamento vencido.
2. Confirmar e corrigir o endereço para o endereço operacional atual, se validado pelo cliente.
3. Definir no pedido a condição: **50% de entrada compensada + saldo em 30/60 dias**.
4. Liberar faturamento somente após a compensação da entrada.
5. Não aprovar boleto puro, condição `A DEFINIR` ou pedido sem entrada sem autorização explícita da diretoria.
6. Manter o limite de exposição desta operação em aproximadamente **R$ 1.149,00**.

## Conclusão técnica

O cliente tem operação real e forte presença online, CNPJ ativo, bureau sem restrições e histórico Conamore recorrente, quitado e de ticket compatível. O ponto de cautela é o padrão de atrasos recorrentes nas parcelas, o Cadastro Positivo ausente, a condição ainda indefinida e a divergência do endereço no orçamento. Portanto, a recomendação é **aprovar com restrição**, preservando a condição já testada de 50% de entrada e 30/60 dias, após revalidação do documento e saneamento cadastral.

**Fontes:** orçamento PDF 0116372; Equifax | Boa Vista; Lista Negra Conamore; Hotel Finder SQL Server (`conamore.Customers`, `debx.PDV_Detalhes`); Oracle DEBX (`TEST_MATRIZ`); ReceitaWS; Google Maps; site motelgpuava.com.
