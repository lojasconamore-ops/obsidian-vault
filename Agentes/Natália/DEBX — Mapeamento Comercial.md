---
title: DEBX — Mapeamento e Insights Comerciais
tags:
  - debx
  - comercial
  - natalia
  - sql-server
---

# DEBX — Mapeamento e Insights Comerciais

**Data do mapeamento:** 03/06/2026
**Autora:** Natália — Gerente Comercial
**Fontes:**
- [[Projetos/Lojas Conamore/Oracle e DEBX - Treinamento de Agentes|Oracle e DEBX — guia operacional]]
- [[Projetos/Lojas Conamore/Oracle e DEBX - Versão Padrão dos Agentes|Oracle e DEBX — versão padrão]]
- [[Agentes/Bianco/Relatório DEBX - Mapeamento e Insights para Compras|Relatório Bianco — Mapeamento para Compras]]
- [[Projetos/Lojas Conamore/Documento 1 - Raio-X Hotelaria B2B|Raio-X Hotelaria B2B (Flávia/DigitalCEO)]]
- SQL Server `hotel-finder` (40.125.121.83)

---

## Infraestrutura do Banco de Dados

### SQL Server (Hotel Finder) — ✅ ACESSÍVEL
- **Servidor:** `40.125.121.83`
- **Database:** `hotel-finder`
- **User:** `hotelfinder`
- **Driver:** pymssql
- **Credenciais:** `Infra/Banco de Dados.md`

### Oracle DEBX (ERP Principal) — ❌ SEM ACESSO (sem credenciais)
- **Servidor:** `172.169.0.11:1521`
- **Service:** `conamore`
- **Schemas:** `TEST_ACL` (PED, F_MOVTO, F_PRODS, v_estoq, ALMOX)
- **Acesso solicitado via Matias**

---

## Schemas do SQL Server

| Schema | Conteúdo | Relevância Comercial |
|--------|----------|---------------------|
| **conamore** | Tabelas de negócio — vendas, clientes, vendedores | ⭐ Principal |
| **debx** | Pedidos do ERP | ⭐ Consulta de pedidos |
| **octa** | Octa CRM — conversas, chats | 🔄 Relacionamento com cliente |
| **whatsapp** | WhatsApp Business | 🔄 Canal de vendas |
| **dbo** | Visões consolidadas | 📊 Relatórios |
| **Sales.Analysis** | Análises de vendas | 📊 Insights |
| **bkp** | Backups | 🗄️ histórico |

---

## Tabela Estrela — `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`

**132.967 registros** | Período: **Jun/2024 a Jun/2026**

### Colunas (21)

| Coluna | Tipo | Uso Comercial |
|--------|------|---------------|
| `Numero_Pedido` | varchar(20) | Identificador do pedido |
| `Item_Code` | varchar(200) | SKU do produto |
| `Item_Descricao` | varchar(max) | Nome do produto |
| `Quantidade` | int | Unidades vendidas |
| `Valor` | decimal | **💰 Valor líquido** |
| `Valor_Bruto` | decimal | Valor bruto |
| `Valor_Frete` | decimal | Custo de frete |
| `Total_Com_Frete` | decimal | Total com frete incluso |
| `Status_Pedido` | varchar(20) | Expedição, Aprovado, Orçamento, Cancelado |
| `PDV_ORIGEM` | varchar(20) | Canal: **MAG** (marketplace) ou **GER** (direto)
| `Data_Venda` | date | Data da venda |
| `Razao_Social` | varchar(200) | **🏢 Nome do cliente** |
| `Estado` | char(2) | UF do cliente |
| `SEG_DESCRI` | varchar(200) | Segmento do produto (MATRIZ, CHC, GCL, ACL, BRG) |
| `CLS_DESCRI` | varchar(200) | **🏷️ Classe de negócio** (HOTEL, POUSADA, AIRBNB, VAREJO, etc.) |
| `Condicao_Pgto` | varchar(100) | **💳 Condição de pagamento** |
| `Vendedor` | varchar(200) | **👤 Vendedor responsável** |
| `Tipo_Pagamento` | varchar(100) | Tipo de pagamento |
| `PDV_DATORC` | varchar(20) | Data do orçamento |

### Valores Distintos Importantes

**Segmentos (SEG_DESCRI):** MATRIZ, CHC, GCL, ACL, BRG

**Classes (CLS_DESCRI) — 21 classes:**
- **Hotelaria:** HOTEL, POUSADA, AIRBNB, GRANDES HOTEIS, ADMINISTRADORES, ALOJAMENTO, MOTEL
- **Saúde:** CLINICA, HOSPITAL, CASA DE REPOUSO
- **Outros B2B:** LAVANDERIA, DISTRIBUIDORES, SALÃO DE BELEZA, ASSOCIAÇÃO, SINDICATO, CLUBE RECREATIVO, FUNDAÇÃO EDUCACIONAL, TIME DE FUTEBOL
- **Varejo:** VAREJO, VAREJO CASA

**Canais (PDV_ORIGEM):** MAG (marketplace/site), GER (geral/direto)

**Status:** Expedição, Aprovado, Cancelado, D, Financeiro, G, Orçamento

---

## Outras Tabelas Relevantes

### `conamore.Customers` (46.642 registros)
Cadastro de clientes com endereço, CNPJ

### `conamore.Contacts` (46.642 registros)
Contatos com email e telefone

### `conamore.vendedor_mapping` (21 registros)
Mapeamento entre código DEBX e Octa

### `conamore.vendedor_meta` (136 registros)
Metas mensais por vendedor

### `debx.PDV_Detalhes` (34.960 registros)
Principal no schema debx — pedidos com datas, status, cliente, vendedor, valores, frete

### `debx.open_orders` (10.572 registros)
⚠️ **DESATUALIZADA** (último dado maio/2025)

---

## Views Importantes

| View | Schema | O que faz |
|------|--------|-----------|
| `V_Orders_Octa_Debx` | conamore | Cruzamento pedidos + Octa |
| `V_Customers_Octa_Debx` | conamore | Cruzamento clientes + Octa |
| `V_Customer_Details` | conamore | Detalhes do cliente |
| `V_Consolidated_Events_Days` | conamore | Eventos consolidados por dia |
| `v_vendas` | debx | Vendas consolidadas |
| `v_pedidos` | debx | Agregação por dia/vendedor |
| `v_orcamentos` | debx | Orçamentos |

---

## Integrações

### Octa CRM (`octa` schema)
- `chats` — **1.229.926 registros** — histórico de conversas
- `customers` — 85.682 registros
- `conversations` — 86.528 registros
- `CarteiraClientes` — 243 registros (carteira de clientes)

### WhatsApp (`whatsapp` schema)
- `Contacts_Octa` — 65.700 registros
- `Messages` — 40 registros
- `BusinessAccounts` — 1 registro

---

## Job Agendado

- **Job:** `Analise-Comercial-DebX-0840`
- **Horário:** Diariamente às **08:40 BRT** (11:40 UTC)
- **Entrega:** Neste chat (Sergio Ladeira)
- **Status:** ⏳ Aguardando primeira execução

---

> *Documentação para consulta rápida da Natália sobre o banco DEBX (SQL Server). O Oracle continua pendente de credenciais.*
