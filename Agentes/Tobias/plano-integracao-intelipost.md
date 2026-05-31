# Integração — API Intelipost

**Data:** 31/05/2026
**Autor:** Tobias — Gerente de Logística e Supply Chain
**Status:** ✅ IMPLEMENTADA E OPERACIONAL

---

## 1. Visão Geral

A Intelipost é a plataforma de gestão de fretes (TMS) utilizada pela Lojas Conamore.
Ela fornece uma API RESTful que permite:
- Cotação de frete em tempo real com múltiplas transportadoras
- Criação e gerenciamento de pedidos de entrega
- Logística reversa (trocas e devoluções)
- Rastreamento de entregas (via consulta ou webhook)
- Gestão de transportadoras, depósitos e auditoria de fretes

## 2. Base URL e Autenticação

**Base URL:** `https://api.intelipost.com.br/api/v1/`

**Autenticação:** API Key via Header HTTP

Headers obrigatórios em toda requisição:
| Header | Descrição |
|--------|-----------|
| `api-key` | Chave de autenticação (fornecida pela Intelipost) |
| `platform` | Plataforma de origem |
| `platform-version` | Versão da plataforma |
| `plugin` | Nome do conector |
| `plugin-version` | Versão do conector |
| `Content-Type` | `application/json` |

## 3. Rate Limit

- **Limite:** 100 requisições por minuto
- **Resposta de bloqueio:** HTTP 429 (Too Many Requests)
- **Headers de monitoramento:**
  - `ratelimit-limit` / `ratelimit-remaining` / `ratelimit-reset`
  - `x-ratelimit-limit-minute` / `x-ratelimit-remaining-minute`

## 4. Endpoints Principais

### 4.1 Cotação de Frete
**`POST /api/v1/quote_by_product`**

Cálculo de frete por produto. Recebe CEP de origem/destino, dimensões e peso dos produtos, e retorna opções de frete com prazos e valores.

**Parâmetros principais do request:**
- `origin_zip_code` — CEP do CD (obrigatório)
- `destination_zip_code` — CEP do cliente (obrigatório)
- `quoting_mode` — Modo de cotação (DYNAMIC_BOX_ALL_ITEMS, REGISTERED_BOXES, DYNAMIC_BOX_SINGLE_ITEM, DYNAMIC_BOX_BY_SKU)
- `products[]` — Lista de produtos com: weight, cost_of_goods, width, height, length, quantity, sku_id
- `additional_information` — lead_time_business_days, sales_channel, free_shipping, etc.

**Retorno:** Lista de `delivery_options` com:
- `delivery_estimate_business_days` — Prazo em dias úteis
- `description` — Descrição da forma de envio
- `final_shipping_cost` — Preço final do frete
- `delivery_method_id` — ID do método de envio (usar ao criar pedido)

### 4.2 Criação de Pedido de Entrega
**`POST /api/v1/shipment_order`**

Cria um pedido de envio na Intelipost.

**Parâmetros principais:**
- `order_number` — ID do pedido (obrigatório)
- `delivery_method_id` — Método de entrega escolhido (obrigatório)
- `customer_shipping_costs` — Frete cobrado do cliente (obrigatório)
- `quote_id` — ID da cotação que gerou o pedido
- `provider_shipping_costs` — Custo do frete pago à transportadora
- `end_customer` — Dados do cliente: nome, endereço, CPF/CNPJ, telefone
- `shipment_order_volume_array` — Volumes com dimensões, peso, nota fiscal
- `origin_zip_code` / `origin_warehouse_code` — Identificação do CD de origem
- `estimated_delivery_date` — Data estimada de entrega
- `shipped_date` — Data de despacho

### 4.3 Logística Reversa
**`POST /api/v1/reverse_order`**

Cria pedido de coleta para troca/devolução.

**Particularidades:**
- `shipment_order_type: "RETURN"` — Identifica como reversa
- `parent_shipment_order_number` — Vincula ao pedido original
- Aceita coleta (PICKUP) ou postagem (DROPOFF)

### 4.4 Rastreamento

Duas formas de obter rastreamento:
1. **Webhook (push):** Implementar endpoint HTTP que recebe notificações automáticas de atualização de status
2. **API (pull):** Consultar ativamente o status do pedido via API da Intelipost

### 4.5 Contingência / Fallback

Mecanismo offline para cotação quando a API da Intelipost estiver indisponível.
- Download de tabelas de fallback (ranges de CEP × peso)
- Implementar busca binária no cache local
- SDK PHP disponível em: https://github.com/intelipost/sdk-php

## 5. O Que Podemos Integrar

### Prioridade Alta (MVP)
1. **Cotação de frete no checkout** — Calcular frete em tempo real no site e marketplaces
2. **Criação de pedido de entrega** — Após faturamento, criar automaticamente o pedido na Intelipost
3. **Rastreamento** — Exibir status de entrega para o cliente (via consulta API ou webhook)

### Prioridade Média
4. **Logística reversa** — Gerenciar trocas e devoluções automatizadas
5. **Múltiplos depósitos** — Integrar os 3 CDs (lojas físicas + fábrica em Campinas)
6. **Notificação ao cliente** — WhatsApp/SMS com atualizações de rastreio

### Prioridade Futura
7. **Auditoria de fretes** — Conferência de faturas de transportadora vs. dados reais
8. **Pickup Points** — Retirada em loja
9. **Entrega agendada** — Agendamento de janela de entrega

## 6. Integração com Nosso ERP/WMS

### Fluxo Principal
```
Checkout (site/marketplace)
  → Cotação Intelipost (quote_by_product)
  → Cliente escolhe frete
  → Pedido gerado no ERP
  → Faturamento/no fiscal
  → Criação do pedido de entrega (shipment_order)
  → Despacho na transportadora
  → Rastreamento automático
  → Notificação ao cliente
  → Confirmação de entrega
```

### Sistemas envolvidos
- **ERP** — Origem dos pedidos, controle de estoque, faturamento
- **WMS** — Separação, embalagem, expedição
- **E-commerce** — Checkout, exibição de frete
- **Marketplaces** — Integração via APIs próprias

## 7. Próximos Passos

1. [ ] Solicitar api-key de homologação com a Intelipost (ou verificar se já temos)
2. [ ] Mapear CD/warehouses no sistema da Intelipost (Campinas + lojas)
3. [ ] Implementar endpoint de cotação no checkout
4. [ ] Implementar criação de pedido pós-faturamento
5. [ ] Configurar webhook de rastreamento ou implementar consulta periódica
6. [ ] Homologar fluxo completo com time Intelipost
7. [ ] Implantar fallback (contingência) para indisponibilidade

## 8. Status da Implementação (31/05/2026)

### ✅ Concluído — Operacional

| Item | Status |
|------|--------|
| API Key ativa no ambiente (.env) | ✅ |
| Script CLI de tracking (`intelipost-track.py`) | ✅ |
| Skill Hermes (`intelipost-integracao`) | ✅ |
| Consulta de rastreamento por order_number | ✅ (endpoint `/shipment_order/{id}`) |
| Consulta de dados brutos do pedido | ✅ |
| Cotação de frete (quote) | ✅ |
| Listagem de transportadoras ativas | ✅ |
| Verificação de saúde da API (status) | ✅ |
| Documentação no Obsidian Vault | ✅ |
| Rate limit — 100 req/min | ✅ monitorado |

### ⚠️ Limitações Conhecidas

- **API não tem endpoints de listagem/relatório** — consulta apenas individual por número de pedido
- **Sem dados agregados** — não é possível extrair total de pedidos no mês, % entregue no prazo, volumes por transportadora diretamente da API
- **Para volume/contexto:** cruzar com GA4 Hotelaria (`properties/379729087`) — métrica `transactions` e `totalRevenue`
- **Tracking via `_events` endpoint** usa JWT expirado — não usar
- **Não usar browser tool para rastrear** — site público intelipost.com.br é B2B/marketing, sem tracking público

### 🔧 Como Usar (scripts)

```bash
cd ~/.hermes/profiles/tobias
source .env
python3 scripts/intelipost-track.py tracking "100-XXXXXXXX-X"   # rastrear pedido
python3 scripts/intelipost-track.py quote <cep_origem> <cep_destino>  # cotar frete
python3 scripts/intelipost-track.py delivery-methods  # listar transportadoras
python3 scripts/intelipost-track.py status  # health check da API
```

### 🚧 Pendente (Próximos Passos)

- [ ] Webhook de tracking (push) — precisa de URL pública para receber notificações automáticas
- [ ] Integração com ERP/WMS para criação automática de shipment_order pós-faturamento
- [ ] Logística reversa via API (troca/devolução automatizada)
- [ ] Dashboard consolidado Intelipost + GA4 (volume de pedidos + tracking)
- [ ] Contingência/fallback offline para indisponibilidade da API

## 9. Transportadoras Ativas (Conamore)

- Correios Sedex (EXPRESS)
- Frota Interna / Frete Valor Fixo
- Via Pajucara Standard
- Jamef Standard
- Rodonaves Standard
- Pacífico Standard
- Rápido Figueiredo
- Favorita Transportes

## 10. Contato Intelipost

- **E-mail para integrações:** integracoes@intelipost.com.br
- **SDK PHP:** https://github.com/intelipost/sdk-php
- **Documentação oficial:** https://docs.intelipost.com.br
