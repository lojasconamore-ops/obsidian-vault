# Parecer de Crédito — Hospital Santa Mônica / SOMEHR

**Data da análise:** 29/08/2026 (BRT)  
**Pedido/orçamento:** 0118495  
**ID DEBX confirmado:** A4038  
**Razão social:** SOMEHR SOCIEDADE MEDICO HOSPITALAR DE REDENCAO LTDA  
**Nome fantasia:** HOSPITAL SANTA MONICA  
**CNPJ:** 03.350.922/0001-17  
**Endereço:** Rua São Félix do Xingu, 744, Morada da Paz, Redenção/PA, CEP 68550-530  
**Contato:** Leda  
**Arquivos consolidados:** orçamento de venda + relatório Equifax/Boa Vista, ambos do mesmo CNPJ.

## Etapa 0 — Lista Negra Conamore

✅ **Cliente não consta na Lista Negra Conamore**, após conferência por CNPJ, razão social e nome fantasia.

## Parecer

🟡 **APROVAR COM RESTRIÇÕES DE CONTROLE DOCUMENTAL E CONDIÇÃO DE PAGAMENTO**

**Nível de risco:** baixo no crédito; moderado no controle documental enquanto o orçamento permanecer vencido e com pagamento “A DEFINIR”.

A venda pode ser aprovada, mas **não deve ser faturada com o documento atual**. Antes do faturamento, é obrigatório:

1. reemitir/revalidar o orçamento, pois a validade impressa expirou em 27/08/2026;
2. substituir “A DEFINIR” por uma condição formal;
3. receber e compensar a entrada mínima;
4. confirmar que não há título vencido no DEBX/Oracle quando o banco voltar à janela operacional.

## Etapa 1 — Histórico interno Conamore

### Identidade e qualidade cadastral

O cadastro correto é **A4038**, vinculado a Hospital Santa Mônica / SOMEHR, mesmo CNPJ e endereço do orçamento.

Foi encontrada colisão de chave migrada: o código **04038** aparece atualmente em `conamore.Customers` para **GABRIELLA FABOZZI ECOLAUNDRY**, CNPJ 38.169.233/0001-95. Esse cadastro é de terceiro e **não teve seu histórico transferido** para a SOMEHR. Os registros históricos 04038 abaixo foram mantidos somente porque `PDV_Detalhes` confirma a razão social SOMEHR; os registros atuais do terceiro foram excluídos.

### Pedidos anteriores confirmados em `debx.PDV_Detalhes`

| Pedido | Venda | Status | Valor | Condição |
|---|---:|---|---:|---|
| 0004411 | 30/07/2024 | Expedição | R$ 599,80 | Boleto 30 dias |
| 0016059 | 05/12/2024 | Expedição | R$ 4.706,80 | 50% entrada + 30/60 dias |
| 0044369 | 20/06/2025 | Expedição | R$ 1.287,77 | À vista / PIX |
| 0045579 | 07/07/2025 | Expedição | R$ 1.498,00 | 50% entrada + 30/60 dias |
| 0054238 | 13/08/2025 | Expedição | R$ 1.627,00 | À vista / PIX |
| 0078982 | 05/02/2026 | Expedição | R$ 1.337,77 | À vista / boleto Increazy |
| 0100991 | 15/05/2026 | Expedição | R$ 3.585,00 | 50% entrada + 30/60 dias |

**Resumo do histórico:**
- 7 pedidos anteriores em Expedição;
- período: 30/07/2024 a 15/05/2026;
- volume histórico: **R$ 14.642,14**;
- ticket médio: **R$ 2.091,73**;
- maior pedido: **R$ 4.706,80**;
- pedido atual de R$ 1.803,00 equivale a 86,20% do ticket médio e 38,31% do maior pedido — sem salto de exposição;
- condições já praticadas: à vista, boleto 30 dias e 50% de entrada + 30/60 dias.

**Classificação interna:** **Classe B — bom**, de forma conservadora. Há recorrência e condições a prazo já praticadas, porém a posição detalhada de títulos pagos/em aberto não pôde ser confirmada nesta análise porque o Oracle retornou `ORA-01033` durante a janela de indisponibilidade. Não há evidência disponível de cobrança problemática.

### Partes relacionadas / mesmo endereço

Foram localizados no Hotel Finder, no mesmo endereço físico:

- **Centro de Cardiologia Intervencionista do Sul do Pará Ltda**, CNPJ 55.152.818/0001-11, ID 89460;
- **Humana Soluções em Saúde Ltda**, CNPJ 52.900.749/0001-99, ID A7672.

Essas empresas têm pedidos próprios no sistema, mas **o vínculo societário não foi confirmado**. Por prudência, seus valores e histórico não foram somados ao limite da SOMEHR. Há ainda inconsistência cadastral de UF no registro da Humana, reforçando a necessidade de não consolidar automaticamente.

## Etapa 2 — Score / Bureau

Relatório Equifax/Boa Vista emitido em 29/08/2026 às 12:52:17, para o mesmo CNPJ do orçamento.

- **Score Aprovação PJ:** 753 — muito forte;
- **probabilidade de inadimplência:** 4,0% — excelente;
- **Cadastro Positivo:** participante, com informação;
- **pagamento pontual:** indicadores mensais entre 99% e 100%;
- **pendências/restrições financeiras:** nada consta;
- **cheques sem fundos/sustados/devolvidos:** nada consta;
- **protestos:** nada consta;
- **situação cadastral:** ativa;
- **fundação:** 16/08/1999;
- **atividade:** atendimento hospitalar, exceto pronto-socorro;
- **consultas ao bureau:** 7 no período de 01/08/2025 a 01/08/2026.

O bureau é favorável e não apresenta sinal de veto.

## Etapa 3 — Coerência operacional do pedido

O pedido contém:

- 5 kits de 250 sabonetes de 15 g (Herbal), total R$ 823,50;
- 5 kits de 250 sachês de shampoo e condicionador de 30 ml, total R$ 879,50.

Amenities de higiene são coerentes com a operação de um hospital. O volume e o valor são compatíveis com o histórico da cliente, sem personalização ou produção especial identificada.

## Etapa 4 — Exposição real e conferência comercial

### Totais conferidos visualmente no orçamento

- total sem desconto: R$ 1.703,00;
- desconto: R$ 0,00;
- total com desconto: R$ 1.703,00;
- frete: R$ 100,00;
- **total pedido: R$ 1.803,00**.

Os totais matemáticos estão consistentes. Entretanto:

- forma de pagamento: **A DEFINIR**;
- não há parcela, entrada ou vencimento impressos;
- o orçamento foi emitido e venceu em 27/08/2026;
- no Hotel Finder, o orçamento aparece como `PAGAMENTO INCREAZY PIX`, mas com condição `A DEFINIR`. O PDF permanece a fonte comercial e precisa ser corrigido.

### Condição recomendada

**25% de entrada via PIX + saldo em boleto para 30 dias.**

- entrada: **R$ 450,75**;
- exposição líquida financiada: **R$ 1.352,25**.

Essa condição é mais segura que o boleto puro de 30 dias já praticado e mantém a exposição abaixo do ticket histórico. Como alternativa conservadora já testada, pode-se usar **50% de entrada + saldo em 30/60 dias**, com exposição de R$ 901,50.

**Faturamento sem entrada:** somente mediante autorização expressa do Sérgio.

## Etapa 5 — Validação operacional online

🟢 **Operação forte.**

Foram encontrados sinais consistentes e convergentes:

- registros públicos de empresa ativa e hospital geral no mesmo CNPJ/endereço;
- presença em diretórios de saúde/CNES com endereço e telefone coerentes;
- site institucional associado ao Hospital Santa Mônica de Redenção;
- Instagram e Facebook atribuídos ao hospital;
- indicação de funcionamento 24 horas e serviços hospitalares;
- endereço online coincidente com orçamento, bureau e Hotel Finder.

A empresa apresenta longa existência operacional e presença pública compatível com o pedido.

## Justificativa técnica objetiva

O crédito é favorável porque a SOMEHR é cliente recorrente, possui 7 pedidos anteriores expedidos, ticket atual abaixo da média histórica, bureau muito forte (score 753 e PD 4%), Cadastro Positivo informado, ausência de restrições/protestos e operação hospitalar real e coerente. O risco principal não é de crédito, mas de controle: o orçamento venceu e não define a forma de pagamento. Portanto, a aprovação deve ficar condicionada à reemissão do pedido, entrada compensada e validação de ausência de títulos vencidos assim que o Oracle estiver disponível.

## Fontes consultadas

- Orçamento Conamore nº 0118495;
- relatório Equifax/Boa Vista nº 040747081-9;
- Lista Negra Conamore;
- Hotel Finder SQL Server: `conamore.Customers`, `debx.PDV_Detalhes` e `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`;
- Oracle DEBX: tentativa de consulta somente leitura, indisponível com `ORA-01033` às 13h BRT;
- validação pública: registros empresariais, diretórios de saúde/CNES, site e redes sociais.
