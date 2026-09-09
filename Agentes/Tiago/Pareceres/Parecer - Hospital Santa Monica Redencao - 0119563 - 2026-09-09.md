# Parecer de Crédito — Hospital Santa Mônica / SOMEHR

**Data da análise:** 09/09/2026 (BRT)  
**Pedido/orçamento:** 0119563  
**ID DEBX confirmado:** A4038  
**Razão social:** SOMEHR SOCIEDADE MEDICO HOSPITALAR DE REDENCAO LTDA  
**Nome fantasia:** HOSPITAL SANTA MONICA  
**CNPJ:** 03.350.922/0001-17  
**Endereço:** Rua São Félix do Xingu, 744, Morada da Paz, Redenção/PA, CEP 68550-530  
**Contato:** Leda  
**Representante:** Carmem Lucia de Oliveira

## Etapa 0 — Lista Negra Conamore

✅ **Cliente não consta na Lista Negra Conamore**, após conferência por CNPJ, razão social, nome fantasia e ID DEBX.

## Parecer

🟡 **APROVAR COM RESTRIÇÕES DE CONTROLE DOCUMENTAL E FINANCEIRO**

**Nível de risco:** baixo no crédito; moderado no controle documental até a regularização do pedido no DEBX e a confirmação da posição atual de títulos.

A venda pode ser aprovada na condição comercial impressa, mas **não deve ser faturada com o documento/registro atual**. Antes do faturamento, é obrigatório:

1. reemitir ou revalidar o orçamento, pois a validade impressa expirou em 03/09/2026;
2. corrigir no DEBX o valor, frete e condição de pagamento para coincidir com o PDF;
3. formalizar o cronograma: 50% de entrada e duas parcelas do saldo em 30/60 dias;
4. receber e compensar a entrada de R$ 2.724,00;
5. confirmar ausência de títulos vencidos no Oracle quando o banco retornar à janela operacional.

## Etapa 1 — Histórico interno Conamore

### Identidade e qualidade cadastral

O cadastro correto é **A4038**, vinculado à SOMEHR / Hospital Santa Mônica, CNPJ e endereço coincidentes com o orçamento. O Hotel Finder armazena o CNPJ com 13 dígitos (`3350922000117`), sem o zero inicial; a identidade foi confirmada por CNPJ normalizado, razão social, fantasia, endereço e cidade.

Existe colisão de chave migrada: o código atual `04038` pertence a terceiro. Foram preservados apenas os registros legados em que a própria linha de pedido identifica expressamente a SOMEHR; nenhum histórico de terceiro foi transferido.

### Pedidos anteriores válidos em `debx.PDV_Detalhes`

| Pedido | Venda | Status | Valor | Condição |
|---|---:|---|---:|---|
| 0004411 | 30/07/2024 | Expedição | R$ 599,80 | Boleto 30 dias |
| 0016059 | 05/12/2024 | Expedição | R$ 4.706,80 | 50% entrada + 30/60 dias |
| 0044369 | 20/06/2025 | Expedição | R$ 1.287,77 | À vista / PIX |
| 0045579 | 07/07/2025 | Expedição | R$ 1.498,00 | 50% entrada + 30/60 dias |
| 0054238 | 13/08/2025 | Expedição | R$ 1.627,00 | À vista / PIX |
| 0078982 | 05/02/2026 | Expedição | R$ 1.337,77 | À vista / boleto Increazy |
| 0100991 | 15/05/2026 | Expedição | R$ 3.585,00 | 50% entrada + 30/60 dias |

**Resumo do histórico válido:**
- 7 pedidos anteriores em Expedição;
- período: 30/07/2024 a 15/05/2026;
- volume histórico: **R$ 14.642,14**;
- ticket médio: **R$ 2.091,73**;
- maior pedido: **R$ 4.706,80**;
- pedido 0118495, no valor de R$ 1.803,00, aparece como **Cancelado** e foi excluído do histórico faturado;
- pedido atual 0119563 permanece como **Orçamento**, não como venda;
- o ticket atual de R$ 5.448,00 corresponde a **2,60x o ticket médio** e **1,16x o maior pedido expedido**: há aumento, mas não atinge o gatilho de salto extremo da política (>5x média ou >3x maior pedido);
- a condição solicitada de 50% de entrada + 30/60 dias já foi praticada anteriormente.

**Classificação interna:** **Classe B — bom**, de forma conservadora. Há recorrência e prazo já testado, sem evidência registrada de cobrança problemática. A classificação não foi elevada para A porque a posição detalhada de títulos e pontualidade não pôde ser atualizada no Oracle nesta análise.

### Partes relacionadas / mesmo endereço

Foram encontrados no mesmo endereço físico:

- Centro de Cardiologia Intervencionista do Sul do Pará Ltda, CNPJ 55.152.818/0001-11, ID 89460 — registros próprios, inclusive Expedição de R$ 2.518,50 em 28/03/2025;
- Humana Soluções em Saúde Ltda, CNPJ 52.900.749/0001-99, ID A7672 — Expedição de R$ 6.344,00 em 19/05/2026.

O vínculo societário não foi confirmado. Portanto, por prudência, o histórico e a exposição dessas empresas **não foram agregados** ao limite da SOMEHR. A UF `CE` no cadastro da Humana, apesar do endereço em Redenção/PA, é uma inconsistência cadastral adicional.

## Etapa 2 — Score / Bureau

Foi utilizado o relatório Equifax/Boa Vista do mesmo CNPJ, emitido em **29/08/2026**, já arquivado na análise anterior do cliente:

- **Score Aprovação PJ:** 753 — muito forte;
- **probabilidade de inadimplência:** 4,0% — excelente;
- **Cadastro Positivo:** participante, com informação;
- **pagamento pontual:** indicadores mensais entre 99% e 100%;
- **pendências/restrições financeiras:** nada consta;
- **cheques sem fundos/sustados/devolvidos:** nada consta;
- **protestos:** nada consta;
- **situação cadastral:** ativa;
- **fundação:** 16/08/1999;
- **atividade principal:** atendimento hospitalar, exceto pronto-socorro.

O bureau recente é favorável e não contém sinal de veto. A consulta pública atual da Serasa confirma CNPJ ativo, razão social, endereço, data de abertura e CNAE; a página pública não substitui uma nova consulta paga para restrições.

## Etapa 3 — Coerência operacional do pedido

Itens conferidos visualmente no PDF:

- 5 kits de 250 sabonetes de 15 g: R$ 823,50;
- 5 kits de 250 sachês de shampoo e condicionador de 30 ml: R$ 879,50;
- 50 cobertores microfibra Queen 220 x 240 cm: R$ 2.745,00;
- 50 personalizações bordado/silk: R$ 400,00.

O mix é coerente com uma operação hospitalar: amenities para higiene e cobertores para leitos/uso institucional. A quantidade é plausível para um hospital ativo. A personalização representa R$ 400,00, ou 7,34% do pedido, e aumenta o risco de reaproveitamento; a entrada de 50% mitiga esse risco. A observação do PDF informa “Produtos em estoque”.

## Etapa 4 — Exposição real e conferência comercial

### Totais do PDF, conferidos visualmente

- total sem desconto: R$ 4.848,00;
- desconto: R$ 0,00;
- total com desconto: R$ 4.848,00;
- frete: R$ 600,00;
- **total do pedido: R$ 5.448,00**.

A soma dos itens é R$ 4.848,00 e fecha com o total de mercadorias. Com o frete, o total do pedido fecha em R$ 5.448,00.

### Condição recomendada

Manter a condição impressa: **50% de entrada via PIX + saldo em boleto para 30/60 dias**.

- entrada: **R$ 2.724,00**;
- parcela em 30 dias: **R$ 1.362,00**;
- parcela em 60 dias: **R$ 1.362,00**;
- **exposição líquida financiada: R$ 2.724,00**.

A condição supera a entrada mínima interna de 25%, foi praticada anteriormente e mantém a exposição controlada.

### Divergência PDF × Hotel Finder / DEBX

O registro do pedido 0119563 no Hotel Finder mostra:

- valor total: R$ 5.148,00;
- frete: R$ 300,00;
- condição e tipo de pagamento: `A DEFINIR`.

O PDF mostra R$ 5.448,00, frete de R$ 600,00 e “ENTRADA 50% SALDO 30/60 DIAS”. Há divergência material de **R$ 300,00** no total/frete e ausência da condição formal no DEBX. O PDF é a fonte comercial do parecer, mas o DEBX deve ser corrigido antes da aprovação operacional/faturamento.

**Faturamento sem entrada:** somente mediante autorização expressa do Sérgio.

## Etapa 5 — Validação operacional online

🟢 **Operação forte.**

Evidências atuais e convergentes:

- Serasa pública: CNPJ ativo, fundado em 16/08/1999, CNAE hospitalar e endereço coincidente;
- diretório baseado no CNES: Hospital Santa Mônica, CNES 3185591, hospital geral, Rua São Félix do Xingu, 744, Redenção/PA;
- perfil empresarial com endereço coincidente, operação 24 horas, site, Facebook, Google Maps e Instagram `@hospitalsantamonica_oficial`;
- perfil com avaliação agregada de 4,1/5 e mais de 100 avaliações;
- telefone e endereço públicos coerentes com o cadastro e o orçamento.

A operação pública é consistente com o porte e o pedido.

## Controle Oracle / títulos

A conexão Oracle foi tentada em 09/09/2026 às 18:43 BRT e retornou `ORA-01033`, dentro da janela noturna de indisponibilidade. Portanto, não foi possível atualizar nesta análise os títulos pagos, em aberto, vencidos e futuros. A liberação para faturamento fica condicionada à confirmação de **zero títulos vencidos** assim que o banco estiver disponível.

## Justificativa técnica objetiva

O crédito é favorável porque a SOMEHR é cliente recorrente, possui 7 pedidos anteriores expedidos, já operou com 50% de entrada + 30/60 dias, apresenta bureau recente muito forte (score 753, PD 4%, Cadastro Positivo informado e nenhuma restrição/protesto) e mantém operação hospitalar pública, antiga e coerente. O pedido atual aumentou frente ao histórico, porém permanece apenas 16% acima do maior pedido expedido e tem 50% de entrada, limitando a exposição a R$ 2.724,00.

O impedimento atual é de controle, não de capacidade de crédito: o orçamento está vencido, o DEBX diverge do PDF em R$ 300,00 e registra pagamento `A DEFINIR`, além de a posição atual de títulos não ter sido validada por indisponibilidade do Oracle. Regularizados esses pontos e compensada a entrada, o faturamento pode prosseguir.

## Fontes consultadas

- orçamento Conamore nº 0119563, conferido por extração e imagem;
- Lista Negra Conamore;
- parecer anterior e relatório Equifax/Boa Vista de 29/08/2026 para o mesmo CNPJ;
- Hotel Finder SQL Server: `conamore.Customers` e `debx.PDV_Detalhes`;
- tentativa de consulta Oracle DEBX em 09/09/2026 às 18:43 BRT;
- Serasa Experian pública;
- diretório CNES/Hospitais e Clínicas;
- diretório TodosNegócios, com links para Maps, site e redes sociais.
