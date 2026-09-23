---
tipo: relatorio-historico-comercial
grupo_marca: Terça da Serra
data: 2026-09-23
fonte_principal: SQL Server hotel-finder
---

# Histórico Comercial — Terça da Serra

**Data de corte:** 23/09/2026, 19:16 BRT  
**Objetivo:** levantar vendas e comportamento de pagamento das unidades com cadastro/pedidos sob a marca Terça da Serra, sem transferir automaticamente crédito entre CNPJs.

## Resumo consolidado

- Unidades cadastradas encontradas: 3
- Vendas concluídas/expedidas atribuíveis: 3
- Valor total concluído: **R$ 11.219,10**
- Pedido adicional aprovado, ainda não testado no vencimento: **R$ 2.540,00**
- Total concluído + aprovado: **R$ 13.759,10**
- Pedidos cancelados atribuíveis: 6
- Valor total dos cancelados: **R$ 12.706,40**
- Histórico concluído por forma: cartão de crédito e PIX
- Histórico de boleto direto: apenas um pedido aprovado em 22/09/2026, ainda sem prazo transcorrido suficiente para avaliar pontualidade

## 1. Terça da Serra Hortolândia

- Razão: Terça da Serra Residencial Senior Hortolândia EIRELI
- CNPJ: 32.583.736/0001-26
- ID atual: A3216
- ID legado confirmado por razão: 03216
- Cidade: Hortolândia/SP

### Venda concluída

- Pedido 0114656
- Data da venda: 31/07/2026
- Aprovação: 01/08/2026
- Status: Expedição
- Valor: **R$ 4.654,20**
- Condição: cartão de crédito em 5x
- Canal: Increazy crédito

### Cancelamentos

- Pedido 0021984 — R$ 704,00 — cancelado
- Pedido 0065656 — R$ 8.418,00 — cancelado
- Total cancelado: **R$ 9.122,00**

### Leitura do pagamento

A única venda concluída foi no cartão. Isso comprova compra real e conclusão comercial, mas **não testa boleto direto da Conamore**, pois o risco/parcelamento passou pela adquirente.

## 2. Terça da Serra Chácara Primavera

- Razão: Terça da Serra Residencial Senior — Chácara Primavera LTDA
- CNPJ: 30.071.193/0001-32
- ID atual: A3806
- ID legado confirmado por razão: 03806
- Cidade: Campinas/SP

### Vendas concluídas

1. Pedido 0087405
   - Venda: 09/02/2026
   - Aprovação: 10/02/2026
   - Status: Expedição
   - Valor: **R$ 3.722,00**
   - Condição: cartão de crédito em 3x

2. Pedido 0089964
   - Venda: 10/03/2026
   - Aprovação: 11/03/2026
   - Status: Expedição
   - Valor: **R$ 2.842,90**
   - Condição: PIX à vista

Subtotal concluído: **R$ 6.564,90**

### Pedido aprovado recente

3. Pedido 0121445
   - Data: 22/09/2026
   - Status: Aprovado
   - Valor: **R$ 2.540,00**
   - Condição: boleto 30/60/90 dias
   - Entrada: não identificada na condição

O pedido foi aprovado apenas um dia antes do corte. Portanto, **ainda não existe histórico de vencimento ou pontualidade desse boleto**. Ele representa a primeira exposição direta identificada da Conamore em boleto para uma unidade Terça da Serra.

### Cancelamentos

- Pedido 0018293 — R$ 1.106,60 — cancelado
- Pedido 0032400 — R$ 339,20 — cancelado
- Total cancelado: **R$ 1.445,80**

### Leitura do pagamento

O histórico concluído é positivo no sentido operacional: uma venda por cartão e uma por PIX foram expedidas. Entretanto, cartão/PIX não equivalem a crédito direto testado. O boleto de R$ 2.540,00 ainda está em início de ciclo e não permite concluir se a unidade paga boletos pontualmente.

## 3. Terça da Serra Nova Campinas II

- Cadastro: Terça da Serra Nova Campinas II
- Razão: Residencial Senior Ela Nova Campinas LTDA
- CNPJ: 44.600.315/0001-45
- ID atual: A6194
- ID legado confirmado por razão: 06194
- Cidade: Campinas/SP

### Histórico

- Pedido 0014140 — R$ 987,50 — cancelado
- Pedido 0018292 — R$ 1.151,10 — cancelado
- Total cancelado: **R$ 2.138,60**
- Vendas concluídas encontradas: **nenhuma**

Não existe comportamento de pagamento válido para classificar esta unidade.

## Colisões de ID excluídas

As chaves legadas `03216`, `03806` e `06194` também retornaram registros de pessoas/empresas não relacionadas, como Anna Paula Bassi, Lucia Shichijo e Nádia Cotrim. Esses registros foram excluídos porque razão social e identidade não correspondem às unidades Terça da Serra.

O histórico acima inclui apenas linhas confirmadas pela razão social da unidade, evitando transferência indevida por colisão de ID DEBX.

## Conclusão financeira

### Comportamento comprovado

- **R$ 11.219,10 em vendas concluídas**, distribuídas entre cartão e PIX.
- Nenhuma evidência de inadimplência interna nessas três vendas, porque foram concluídas por meios com liquidação antecipada/adquirente.
- Não há histórico maduro de boleto direto: o único boleto identificado foi aprovado em 22/09/2026 e ainda não chegou ao primeiro vencimento.

### Impacto para Santa Marcelina

O histórico de outras unidades demonstra que a marca já compra da Conamore e possui operação comercial real. Porém:

- são CNPJs juridicamente distintos;
- não há comprovação de mesmo controlador entre todas as unidades;
- vendas anteriores ocorreram principalmente em cartão e PIX;
- o histórico não constitui limite de boleto transferível;
- os 19 protestos do CNPJ Santa Marcelina permanecem veto para faturamento.

Portanto, o histórico da marca **não altera o parecer de reprovação de boleto para o CNPJ 32.679.264/0001-00**. Pode apoiar a venda somente por PIX/TED antecipado ou cartão.

## Limitação da análise de títulos

O Oracle DEBX retornou `ORA-01033` após as 18:00 BRT, conforme a janela conhecida de indisponibilidade. O SQL Server não possui espelho de datas de vencimento/pagamento dos títulos. Assim:

- cartão e PIX foram classificados pelo canal e status de expedição;
- não foi alegada pontualidade de boleto sem dados de `F_TITULOS`;
- o boleto 0121445 foi classificado como exposição recente e ainda não testada.
