# Integração Pagar.me ↔ Site ↔ DEBX

## Objetivo
Centralizar os pagamentos da Conamore no Pagar.me e sincronizar o resultado em dois pontos:
1. o site / checkout
2. o ERP DEBX

A integração precisa cobrir:
- pagamento aprovado
- pagamento pendente
- pagamento recusado
- cancelamento / estorno
- chargeback
- conciliação para auditoria

## Fluxo proposto

### 1) Site gera o pedido
- pedido criado no site
- pedido recebe um identificador único
- o checkout envia a cobrança para o Pagar.me

### 2) Pagar.me confirma o pagamento
- eventos chegam via webhook
- o sistema registra o status do pagamento
- o pedido é atualizado no site
- o DEBX recebe a confirmação financeira / operacional

### 3) ERP DEBX recebe a baixa ou pendência
- se aprovado: baixa / marcação de pago
- se recusado: mantém pendente ou cancela conforme regra
- se estornado: reverte o lançamento
- se chargeback: marca ocorrência financeira para análise

## O que precisa para implementar de verdade

### A) Do lado do Pagar.me
- chave de API da conta
- segredo do webhook
- lista de eventos que a operação quer tratar
- ambiente de teste e produção
- regras de split, antifraude e parcelamento, se houver

### B) Do lado do site
- stack do checkout atual
- onde o pedido é criado
- como o site guarda o order_id
- endpoint para receber webhook ou serviço intermediário
- regra para reconciliação de pedidos com pagamentos

### C) Do lado do DEBX
- qual a interface disponível para escrita
  - API
  - procedure
  - integração via fila
  - gravação direta em tabela
- tabela / documento de mapeamento de pedido e pagamento
- campos obrigatórios para baixa financeira
- regra para estorno / cancelamento

### D) Campos que precisam ser mapeados
- order_id do site
- id do pagamento no Pagar.me
- status do pagamento
- valor bruto
- valor líquido
- taxa
- parcelas
- CPF / CNPJ do cliente
- email / telefone
- data da confirmação
- forma de pagamento

## Regras de negócio que precisam ser confirmadas
- o que fazer quando o pagamento ficar pendente
- quando marcar o pedido como pago
- se pedido cancelado no site deve cancelar no Pagar.me ou só no DEBX
- se o estorno no Pagar.me deve abrir ocorrência no financeiro
- como tratar pagamento parcial
- como tratar boleto vencido
- como tratar Pix expirado

## O que eu preciso de você para fechar a implementação
1. confirmar onde o checkout do site roda hoje
2. confirmar como o DEBX aceita atualização financeira
3. informar se já existe webhook do Pagar.me ativo
4. informar quais eventos do Pagar.me vocês querem usar primeiro
5. informar se a prioridade é:
   - só notificar o time
   - atualizar pedido no site
   - dar baixa no DEBX
   - fazer tudo em cadeia

## Sugestão de primeira entrega
Se quiser começar rápido, eu faria em 3 etapas:
1. webhook do Pagar.me recebendo eventos de pagamento
2. atualização do status do pedido no site
3. espelhamento do status no DEBX

## Observação
Sem a definição da interface do DEBX e dos eventos exatos do Pagar.me, eu consigo deixar a arquitetura pronta, mas não consigo fechar a integração completa com segurança.
