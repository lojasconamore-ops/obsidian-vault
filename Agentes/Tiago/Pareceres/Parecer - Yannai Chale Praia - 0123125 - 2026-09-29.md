---
tipo: parecer-credito
cliente: YANNAI CHALE PRAIA LTDA
cnpj: 26.011.689/0001-43
pedido: "0123125"
data: 2026-09-29
parecer: aprovar-com-restricao
risco: baixo-moderado
---

# Parecer de Crédito — Yannai Chalé Praia LTDA

**Data de corte:** 29/09/2026, BRT  
**Pedido/proposta:** 0123125  
**CNPJ:** 26.011.689/0001-43  
**ID DEBX:** A3733  
**Representante:** Marcos Vinicius Ferreira de Alencar

## Resumo executivo

**Parecer: 🟡 APROVAR COM RESTRIÇÃO OPERACIONAL**  
**Nível de risco: baixo a moderado**

O cliente possui quatro pedidos confirmados e expedidos sob o CNPJ/razão atual, totalizando R$ 9.464,60. Todos os 12 títulos desses pedidos estão pagos, sem saldo em aberto ou vencido. Foram observados nove atrasos curtos, entre 1 e 4 dias, com média de 1,78 dia entre os atrasados. O comportamento é compatível com Classe B: bom pagador, com pequena fricção de compensação.

A proposta atual está com forma de pagamento `A DEFINIR` e não contém entrada ou cronograma. A venda pode ser aprovada após correção do documento para:

- **25% de entrada compensada:** R$ 694,60;
- **saldo em 30/60/90:** 3 parcelas de R$ 694,60;
- **exposição líquida:** R$ 2.083,80.

## Etapa 0 — Lista Negra Conamore

✅ Não consta na Lista Negra por CNPJ, razão social, nome fantasia ou alias histórico pesquisado.

## Etapa 1 — Histórico interno Conamore

### Identidade

- Cadastro SQL Server: A3733, Yannai Chalé Praia, CNPJ 26.011.689/0001-43, Av. Pedro Paula/Paulo de Moraes, 549, Ilhabela/SP.
- Oracle `TEST_MATRIZ.F_CDEMP`: confirmou `EMP_CODEMP = A3733`, CNPJ correto e status ativo (`0`).
- A chave numérica `03733` atualmente também aparece vinculada a outra pessoa no SQL Server; os registros dessa pessoa foram excluídos.
- A identidade do cliente foi determinada por CNPJ + razão social + Oracle A3733, e não apenas pelo número normalizado do código.

### Pedidos confirmados sob Yannai Chalé Praia LTDA

1. **0062792** — R$ 3.138,00 — venda em 03/10/2025 — Expedição  
   Condição: entrada de 50% + 30/60 dias.

2. **0082951** — R$ 1.305,00 — venda em 07/01/2026 — Expedição  
   Condição: entrada de 50% + 30/60 dias.

3. **0089616** — R$ 3.395,60 — venda em 18/02/2026 — Expedição  
   Condição: boleto 30/60/90 dias.

4. **0099017** — R$ 1.626,00 — venda em 17/04/2026 — Expedição  
   Condição: boleto 30/60/90 dias.

**Resumo confirmado:**

- Pedidos expedidos: 4
- Total histórico: **R$ 9.464,60**
- Ticket médio: **R$ 2.366,15**
- Maior pedido: **R$ 3.395,60**
- Primeiro pedido confirmado: 03/10/2025
- Último pedido confirmado: 17/04/2026
- Pedido atual versus média: 1,17x
- Pedido atual versus maior pedido: 0,82x

O ticket atual é coerente com o histórico e está abaixo do maior pedido já realizado.

### Títulos pagos — Oracle

Fonte: `TEST_MATRIZ.F_TITULOS`, cadeia `CNPJ → A3733 → pedidos → títulos`, somente parcelas individuais.

- Títulos confirmados dos quatro pedidos: 12
- Títulos pagos: 12
- Títulos em aberto: 0
- Títulos vencidos em aberto: 0
- Pagos no vencimento: 3
- Pagos após o vencimento: 9
- Atraso máximo: 4 dias
- Atraso médio entre os atrasados: 1,78 dia
- Valor original confirmado: R$ 9.464,60
- Valor pago registrado: R$ 9.539,46
- Diferença registrada acima do original: R$ 74,86; não foi inferida a causa sem campo explicativo, embora seja compatível com encargos/compensações.

**Classificação interna:** Classe B — bom, regular e confiável, com pequenos atrasos de compensação.

### Registro legado associado, mantido separado

O Oracle também relaciona ao código A3733 o pedido 0039180, de R$ 3.315,40, sob o nome `Creusa Lima Duarte Chalés`, totalmente pago. O SQL Server o apresenta sob chave legada 03733 e nome diferente. Há sinais de continuidade operacional no mesmo endereço/empreendimento, mas não houve confirmação suficiente de identidade jurídica pelo CNPJ. Por controle, esse pedido não foi incluído nos quatro pedidos e R$ 9.464,60 confirmados do Yannai.

### Pedido atual

O pedido 0123125 não apareceu ainda no SQL Server nem no Oracle no corte da consulta. Portanto, o PDF permanece uma proposta/orçamento, não uma venda faturada.

## Etapa 2 — Score / Bureau

Não foi fornecido relatório pago de bureau Equifax/Serasa para este pedido. A análise externa foi feita pelo cadastro público e pela operação online; não foram inventados score, probabilidade de inadimplência ou consulta de protestos.

Cadastro público atualizado em 29/09/2026:

- Situação cadastral: **ativa**
- Fundação: 23/08/2016
- Idade empresarial: aproximadamente 10 anos
- CNAE principal: hotéis
- Porte: microempresa
- Capital social: R$ 51.000,00
- Optante do Simples Nacional
- Sócia-administradora atual: Cinthia Fabian de Almeida Duarte, desde 08/03/2023
- Endereço e CNPJ coerentes com a proposta e a operação pública

A ausência do bureau é mitigada pelo histórico interno direto de quatro pedidos e 12 títulos quitados, mas justifica não liberar condição `A DEFINIR` ou boleto sem entrada.

## Etapa 3 — Coerência operacional do pedido

O pedido contém:

- 10 lençóis queen com elástico;
- 10 lençóis queen sem elástico;
- 64 fronhas;
- 32 toalhas de piso.

O mix é coerente com reposição de enxoval para pousada/hotel e compatível com a operação do Yannai Chalé Praia.

### Reconciliação da proposta

- Soma das linhas: **R$ 2.728,40**
- Total sem desconto: R$ 2.728,40
- Desconto: R$ 0,00
- Total com desconto: R$ 2.728,40
- Frete: R$ 50,00
- **Total do pedido: R$ 2.778,40**
- Forma impressa: `A DEFINIR`
- Entrada impressa: inexistente
- Cronograma de parcelas: inexistente

Os valores comerciais fecham, mas a condição financeira precisa ser definida e reemitida antes do faturamento.

### Validade

- Emissão: 29/09/2026
- Validade: 29/09/2026
- A proposta é válida apenas no dia da emissão. Se não for faturada em 29/09/2026, deverá ser revalidada/reemitida.

## Etapa 4 — Exposição real

### Documento atual

- Total: R$ 2.778,40
- Entrada definida: R$ 0,00
- **Exposição potencial se faturado como está:** R$ 2.778,40

Não deve ser faturado com `A DEFINIR`.

### Condição recomendada

- Entrada de 25%: **R$ 694,60**
- Saldo financiado: **R$ 2.083,80**
- 30/60/90: **3 parcelas de R$ 694,60**
- Exposição líquida recomendada: **R$ 2.083,80**

Essa condição é mais conservadora que os dois últimos pedidos, que foram concedidos em boleto puro 30/60/90 e foram integralmente pagos.

## Etapa 5 — Validação operacional online

🟢 **Operação forte**

- Google Maps: Yannai Chalé Praia, classificação de hotel 4 estrelas e avaliação 4,5.
- Endereço exato: Av. Pedro de Paula Moraes, 549, Saco da Capela, Ilhabela/SP.
- Telefone público: (12) 98257-0016.
- Site oficial vinculado: `yannaichalepraia.com.br`.
- Perfil ativo com disponibilidade e preços em plataformas de reserva, incluindo Hotels.com.
- Estrutura pública: café da manhã, estacionamento, piscina, ar-condicionado e aceitação de animais.
- Cadastro público, Maps, proposta e histórico interno apresentam identidade operacional coerente.

O acesso automatizado direto ao site oficial sofreu reset de conexão, mas o domínio e sua vinculação foram confirmados pelo Google Maps e pelas plataformas de reserva.

## Partes relacionadas / grupo econômico

- A busca por endereço exato no Hotel Finder encontrou apenas o próprio Yannai no número 549.
- O QSA atual indica Cinthia Fabian de Almeida Duarte.
- Não foi confirmada outra empresa com propriedade atual e operação que permita transferir histórico ou exposição.
- Empresas apenas no mesmo CEP ou na mesma avenida foram mantidas separadas.

## Decisão final

**🟡 APROVAR COM RESTRIÇÃO OPERACIONAL — risco baixo a moderado.**

Liberar após:

1. corrigir a forma de pagamento de `A DEFINIR` para **25% de entrada + 30/60/90**;
2. compensar a entrada de R$ 694,60 antes do faturamento;
3. manter exposição máxima de R$ 2.083,80;
4. reemitir a proposta se o faturamento ocorrer após 29/09/2026.

**Justificativa técnica objetiva:** o Yannai possui histórico direto e positivo, com quatro pedidos expedidos, R$ 9.464,60 em compras e 12 títulos integralmente pagos. Os atrasos foram pequenos, de no máximo quatro dias, e o pedido atual é coerente com o ticket histórico. A restrição decorre apenas da condição `A DEFINIR`, da ausência de entrada no documento e da falta de bureau pago atualizado.
