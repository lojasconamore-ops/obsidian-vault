---
tipo: parecer-credito
cliente: POUSADA SANTA ANA LTDA
cnpj: 37.699.350/0001-06
pedido: "0121532"
data: 2026-09-18
parecer: aprovar-com-restricao
risco: moderado
---

# Parecer de Crédito — Pousada Santa Ana LTDA

**Data de corte:** 18/09/2026, BRT  
**Pedido/proposta:** 0121532  
**CNPJ:** 37.699.350/0001-06  
**ID DEBX atual:** A7033  
**Representante:** Carlos Manoel da Silva

## Resumo executivo

**Parecer: 🟡 APROVAR COM RESTRIÇÃO**  
**Nível de risco: moderado**

A empresa tem operação real e consolidada, CNPJ ativo desde 13/07/2020, bureau forte e limpo, Cadastro Positivo com informação e um pedido anterior integralmente quitado. A restrição decorre do comportamento interno desse pedido anterior: a entrada de R$ 5.000,00 foi registrada 195 dias após o vencimento; as outras quatro parcelas foram pagas com atrasos curtos de 1 a 3 dias. Não há saldo em aberto hoje.

**Condição recomendada:**
- **40% de entrada compensada antes do faturamento:** R$ 4.534,00;
- **saldo de R$ 6.801,00 em 30/60/90 dias:** 3 parcelas de R$ 2.267,00;
- não liberar mercadoria apenas com promessa/agendamento da entrada;
- reemitir/corrigir a proposta antes do faturamento, pois o texto-padrão das observações menciona 50% à vista + 30/60, enquanto cabeçalho e cronograma mostram 25% + 30/60/90.

## Etapa 0 — Lista Negra Conamore

✅ **Não consta** na Lista Negra por CNPJ, razão social ou nome fantasia.

## Etapa 1 — Histórico interno Conamore

### Identidade e migração de chave

- Cadastro SQL Server: `A7033`, Pousada Santa Ana, CNPJ 37.699.350/0001-06, endereço Av. Antônio Borges dos Santos, 352, Florianópolis/SC.
- Histórico SQL Server: pedido `0004625` sob chave legada `07033` / `ID_DEBX2 107033`.
- Oracle `TEST_MATRIZ.F_CDEMP`: confirmou o CNPJ sob `EMP_CODEMP = A7033`, razão Pousada Santa Ana LTDA e status ativo (`0`).
- Oracle `TEST_ACL.F_PEDVENDA`: confirmou que o pedido `0004625` pertence a `A7033`. Assim, o histórico legado foi validado por CNPJ/razão e não apenas por semelhança de ID.

### Pedido anterior

- **Pedido:** 0004625
- **Data:** 31/07/2024
- **Status:** Expedição / aprovado
- **Valor:** R$ 12.805,00
- **Condição:** entrada de 40% + saldo 30/60/90/120 dias
- **Forma:** boleto a prazo
- **Quantidade de pedidos faturados encontrada:** 1
- **Ticket histórico médio e máximo:** R$ 12.805,00

O pedido atual de R$ 11.335,00 equivale a **88,52%** do pedido anterior, isto é, **11,48% menor**. Não há salto de ticket.

### Títulos Oracle — comportamento de pagamento

Fonte: `TEST_ACL.F_TITULOS`, cadeia validada `CNPJ → A7033 → pedido 0004625 → títulos`, somente parcelas individuais (`TIT_NUMPAR IS NOT NULL`).

| Componente | Vencimento | Pagamento | Valor original | Atraso |
|---|---:|---:|---:|---:|
| Entrada | 01/08/2024 | 12/02/2025 | R$ 5.000,00 | 195 dias |
| Parcela 1 | 05/09/2024 | 06/09/2024 | R$ 1.951,26 | 1 dia |
| Parcela 2 | 05/10/2024 | 08/10/2024 | R$ 1.951,26 | 3 dias |
| Parcela 3 | 04/11/2024 | 05/11/2024 | R$ 1.951,22 | 1 dia |
| Parcela 4 | 04/12/2024 | 06/12/2024 | R$ 1.951,26 | 2 dias |

- **Valor original total:** R$ 12.805,00
- **Valor pago registrado:** R$ 12.844,68
- **Saldo aberto:** R$ 0,00
- **Títulos vencidos em aberto:** nenhum
- **Atraso máximo:** 195 dias
- O pagamento R$ 39,68 acima do valor original está registrado na última parcela; a causa não foi inferida sem campo explicativo.

**Classificação interna: Classe C — paga, mas exige cautela.** Há quitação integral e ausência de exposição atual, porém a demora relevante na entrada impede classificação A/B. Os demais atrasos foram curtos.

Não foram encontrados pedidos/títulos correspondentes nos schemas `TEST_MATRIZ`, `TEST_CHC`, `TEST_GCL` e `TEST_BRG`; o histórico financeiro está em `TEST_ACL`.

### Pedido atual nos sistemas

O pedido 0121532 ainda não foi localizado em `debx.PDV_Detalhes` nem em `F_PEDVENDA` dos cinco schemas Oracle consultados. Neste corte, o PDF é uma proposta/orçamento ainda não aprovado/integrado; não deve ser tratado como venda faturada.

## Etapa 2 — Score / Bureau

Relatório Equifax | Boa Vista emitido em **18/09/2026 às 10:47:10**, resposta **040758251-1**, visualmente conferido nas três páginas.

- **Score Aprovação PJ:** 732 — forte
- **Probabilidade de inadimplência:** 6,0% — administrável
- **Cadastro Positivo:** participante com informação
- **Pagamento pontual:** pontuação geral 93; série mensal de set/2025 a ago/2026 = 100, 95, 94, 77, 100, 100, 100, 76, 75, 96, 100, 100
- Há sinais modelados nas faixas de atraso de 6–15 e 16–30 dias; não há sinal em 31–60 ou acima de 60 dias
- **Pendências e restrições financeiras:** nada consta
- **Cheques sem fundos/sustados/devolvidos:** nada consta
- **Protestos:** nada consta
- **Consultas:** 1 no período informado
- **Faixa de funcionários:** 1 a 19

O bureau é positivo e coerente com a quitação dos títulos, mas não elimina a ressalva do atraso interno de 195 dias.

A consulta da Receita embutida no bureau tinha corte antigo (22/08/2024). A situação foi atualizada por ReceitaWS/BrasilAPI em 18/09/2026, com dados atualizados em 15/09/2026:
- situação **ATIVA**;
- abertura em 13/07/2020;
- CNAE principal: pensões/alojamento;
- microempresa, optante do Simples;
- capital social: R$ 50.000,00;
- sócia-administradora: Jaqueline Bobsin de Azevedo.

## Etapa 3 — Coerência operacional do pedido

O mix é coerente com uma pousada: fronhas, lençóis solteiro/casal e toalhas de banho/rosto. A operação pública informa aproximadamente 26 quartos, tornando o volume compatível com reposição/renovação de enxoval.

### Reconciliação da proposta

- Soma das linhas de produtos: **R$ 11.285,00**
- Total sem desconto: **R$ 11.285,00**
- Desconto: **R$ 0,00**
- Total com desconto: **R$ 11.285,00**
- Frete: **R$ 50,00**
- Total do pedido: **R$ 11.335,00**
- Cronograma impresso: entrada + 3 boletos de **R$ 2.833,75** cada
- Soma do cronograma: **R$ 11.335,00**

Os valores fecham matematicamente. Existe, porém, **divergência textual**:
- cabeçalho e cronograma: 25% de entrada + 30/60/90;
- texto-padrão das observações: 50% à vista + 50% em 30/60.

O cronograma é a melhor evidência da exposição atual, mas o documento deve ser corrigido porque a recomendação final é 40% + 30/60/90.

### Validade

- Emissão: 18/09/2026
- Validade: 22/09/2026
- Situação no corte: **válida**, mas deve ser reemitida/corrigida com a condição aprovada antes do faturamento.

## Etapa 4 — Exposição real

### Condição impressa no PDF

- Total: R$ 11.335,00
- Entrada de 25%: R$ 2.833,75
- **Exposição líquida:** R$ 8.501,25

Essa exposição é R$ 818,25 maior que os 60% financiados no pedido anterior (R$ 7.683,00), apesar do ticket atual ser menor.

### Condição recomendada

- Entrada de 40%: R$ 4.534,00
- Saldo financiado: R$ 6.801,00
- 3 parcelas: R$ 2.267,00 em 30/60/90
- **Exposição líquida recomendada:** R$ 6.801,00

A entrada compensada antes da liberação elimina a repetição do risco ocorrido na entrada anterior e mantém a exposição abaixo do nível histórico financiado.

## Etapa 5 — Validação operacional online

🟢 **Operação forte**

- Google Maps: Pousada Santa Ana, avaliação 4,6, endereço exato, telefone, site oficial e disponibilidade/preços ativos.
- Site oficial indicado no Maps: `pousadasantaana.com.br`.
- Sembo: 8,6/10 em 61 avaliações; descrição de 26 quartos e endereço exato.
- Momondo: 8,2/10 em 125 avaliações verificadas; endereço exato.
- Instagram: resultados públicos da própria Pousada Santa Ana na Armação do Pântano do Sul.
- Endereço, telefone, atividade e identidade são consistentes entre proposta, bureau, Receita, mapas e plataformas.

Fontes online consultadas:
- https://www.google.com/maps/search/Pousada+Santa+Ana,+Avenida+Antonio+Borges+dos+Santos+352,+Florianopolis,+SC
- https://sembo.nz/places/armacao-brazil/hotels/535689/pousada-santa-ana
- https://momondo.com/hotels/florianopolis/Pousada-Santa-Ana.mhd387959.ksp
- https://brasilapi.com.br/api/cnpj/v1/37699350000106
- https://receitaws.com.br/v1/cnpj/37699350000106

## Partes relacionadas / grupo econômico

A busca por endereço exato no Hotel Finder não encontrou outro CNPJ no número 352. A sócia Jaqueline Bobsin de Azevedo também controla a empresa ativa **Jaqueline Bobsin de Azevedo LTDA / Mercado Manezinho**, CNPJ 65.863.576/0001-28, aberta em 23/03/2026 no número 372 da mesma avenida e mesmo CEP. O vínculo societário e a proximidade física caracterizam parte relacionada, porém:

- a empresa é recente;
- não há cadastro/histórico dela no Hotel Finder;
- sua atividade é varejo alimentar, não hospedagem;
- nenhum histórico ou limite foi transferido entre os CNPJs.

## Decisão final

**🟡 APROVAR COM RESTRIÇÃO — risco moderado.**

Liberar somente após:
1. reemissão/correção da proposta com **40% de entrada + 30/60/90**;
2. compensação efetiva da entrada de **R$ 4.534,00**;
3. confirmação de que não surgiu novo título/restrição até a data do faturamento;
4. manutenção do total em R$ 11.335,00 e da exposição máxima em R$ 6.801,00.

**Justificativa técnica objetiva:** operação real e forte, CNPJ ativo, bureau limpo e score 732, pedido atual menor que o histórico e ausência de saldo aberto sustentam a venda. O atraso de 195 dias na entrada anterior impede liberar a condição de 25% sem mitigação. A entrada de 40% compensada reduz a exposição para abaixo do patamar histórico e permite vender com risco controlado.
