# Integração Pagar.me ↔ Site ↔ DEBX

## Objetivo
Nesta primeira etapa, a integração será somente de leitura no Pagar.me.

O foco é:
1. buscar as confirmações de pagamento de um período determinado
2. identificar possíveis pagamentos duplicados do mesmo link
3. gerar uma base de análise para conciliação

Nesta fase não vamos:
- alterar pedidos no site
- dar baixa no DEBX
- cancelar cobranças
- emitir estorno
- disparar automações operacionais

A integração de leitura precisa cobrir:
- pagamento aprovado
- pagamento pendente
- pagamento recusado
- cancelamento / estorno
- chargeback
- conciliação para auditoria
- detecção de duplicidade por link, pedido, cliente e valor

## Fluxo proposto

### 1) Coleta somente leitura
- buscar no Pagar.me os pagamentos de um período definido
- consolidar por link, pedido, cliente, valor e data/hora
- salvar a saída em formato de relatório para análise manual

### 2) Identificação de duplicidade
- marcar como possível duplicidade quando houver mais de um pagamento pago com a mesma chave de referência
- comparar pelo menos:
  - link de pagamento
  - order_id
  - cliente
  - valor
  - intervalo de tempo entre confirmações

### 3) Resultado da análise
- listar os casos suspeitos
- separar os que são duplicidade real dos que são pagamentos diferentes com mesmo valor
- deixar pronto para auditoria financeira

## Critérios iniciais de duplicidade

Um caso deve entrar na revisão manual quando houver:
- mesmo link de pagamento
- status pago em mais de uma transação
- mesmo valor bruto
- mesma referência de pedido ou cliente
- confirmações muito próximas no tempo

Critérios de falsos positivos que precisam ser excluídos:
- pedidos diferentes com mesmo valor
- compras recorrentes legítimas
- reprocessamentos de webhook sem novo pagamento
- cobranças com tentativa falha seguida de nova aprovação

## Próximo passo técnico

Montar um coletor somente leitura com saída em formato de planilha na tela, contendo:
- período consultado
- id da transação no Pagar.me
- número do pedido
- referência do pagamento
- valor
- status
- data de confirmação / aprovação
- cliente
- indicação de possível duplicidade

### Regra do período
A consulta deve sempre usar a data de aprovação do pagamento como filtro principal.

- De terça a sexta: consultar os pagamentos aprovados no dia anterior.
- Na segunda-feira: consultar os pagamentos aprovados na sexta-feira, sábado e domingo imediatamente anteriores.
- Sempre considerar apenas pagamentos aprovados dentro do período definido.

### Chave principal de referência
A primeira chave para agrupar e comparar duplicidade será o cliente.

Depois disso, o processo de validação passa a ser:
1. consultar o período correto pela data de aprovação
2. exportar os pagamentos aprovados
3. agrupar primeiro por cliente
4. revisar os grupos com mais de uma confirmação
5. classificar o caso como duplicidade real ou não

### Saída inicial na tela
A primeira entrega pode aparecer como uma tabela na tela, com colunas como:
- cliente
- data da aprovação
- valor
- referência / link
- quantidade de aprovações no período
- flag de possível duplicidade

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
