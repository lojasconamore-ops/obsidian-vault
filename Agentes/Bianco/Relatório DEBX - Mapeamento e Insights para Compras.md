# Relatório DEBX — Mapeamento e Insights para Compras

**Data:** 03/06/2026
**Autor:** Bianco — Gerente de Compras
**Fonte:** SQL Server `hotel-finder` (40.125.121.83) — schema `debx` e `conamore`

---

## 1. Estrutura do Banco

### Conexão Atual (SQL Server — Hotel Finder)

| Info | Valor |
|------|-------|
| Servidor | `40.125.121.83` |
| Database | `hotel-finder` |
 | User | `hotelfinder` |
| Driver | pymssql |
| Schema principal | `debx`, `conamore` |

### Schemas encontrados

| Schema | Conteúdo |
|--------|----------|
| **debx** | Tabelas do ERP — pedidos, orçamentos, vendas |
| **conamore** | Tabelas de negócio — clientes, vendas consolidadas, análise por material |
| **octa** | Integração com Octa CRM (chats, conversas, clientes) |
| **whatsapp** | Mensagens WhatsApp Business |
| **Sales.Analysis** | Resultados de análise de vendas |
| **dbo** | Visões consolidadas |
| **bkp** | Backup de tabelas |

### Tabelas do schema `debx`

| Tabela | Tipo | Registros | Observação |
|--------|------|-----------|------------|
| `PDV_Detalhes` | BASE TABLE | **34.960** | ✅ Principal — pedidos com datas, status, cliente, vendedor, valores, frete |
| `open_orders` | BASE TABLE | 10.572 | ⚠️ **DESATUALIZADA** (dados até 05/2025) |
| `PDV_Output` | BASE TABLE | 2.262 | Subconjunto de pedidos com dados de envio |
| `v_pedidos` | VIEW | — | Agregação por dia/vendedor |
| `v_vendas` | VIEW | — | Vendas consolidadas |
| `v_orcamentos` | VIEW | — | Orçamentos |
| `v_numero_pedidos` | VIEW | — | Contagem de pedidos por dia |

### Tabelas do schema `conamore`

| Tabela | Registros | Relevância para Compras |
|--------|-----------|------------------------|
| **`CAIXA_PERIODO_DETALHADO_POR_MATERIAL`** | **132.967** | ⭐ **A mais importante** — dados por item: SKU, descrição, segmento, classe, quantidade, valor, frete, cliente, estado, condição pgto |
| `CAIXA_PERIODO_COM_ORIGEM` | 30.132 | Pedidos com origem (MAG, GER) — boa para análise de canal |
| `Consolidated_Sales` | 32.624 | Vendas consolidadas por cliente/ano |
| `Customers` | 46.642 | Cadastro de clientes com endereço, CNPJ |
| `Contacts` | 46.642 | Contatos com email e telefone |
| `vendedor_mapping` | 21 | Mapeamento vendedor DEBX → Octa |
| `vendedor_meta` | 136 | Metas mensais por vendedor |

---

## 2. Dicionário — Tabela Estrela para Compras

### `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`

```sql
-- 132.967 registros, dados de ~06/2024 até ~06/2026
SELECT
  Numero_Pedido,    -- ID do pedido
  Item_Code,        -- SKU do produto ⬅
  Item_Descricao,   -- Nome do produto
  SEG_DESCRI,       -- Segmento (MATRIZ, CHC, GCL, ACL, BRG)
  CLS_DESCRI,       -- Classe (HOTEL, AIRBNB, VAREJO, POUSADA, etc.)
  Quantidade,       -- Unidades vendidas
  Valor,            -- Valor líquido do item
  Valor_Bruto,      -- Valor bruto
  Valor_Frete,      -- Frete
  Status_Pedido,    -- Expedição, Aprovado, Cancelado...
  PDV_ORIGEM,       -- Canal (MAG, GER)
  Data_Venda,       -- Data da venda
  Razao_Social,     -- Cliente
  Estado,           -- UF do cliente
  Condicao_Pgto     -- Condição de pagamento
FROM conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL;
```

---

## 3. Insights de Negócio para Compras

### 3.1 Volume Geral (aproximado 2 anos)

| Indicador | Valor |
|-----------|-------|
| Período | Jun/2024 — Jun/2026 |
| Itens vendidos | ~1,46 MM unidades |
| Receita total | ~R$ 7,78 MM |
| Clientes ativos | ~18.500 |

### 3.2 Status dos Pedidos

| Status | Itens | % | Observação |
|--------|-------|---|------------|
| **Expedição** | 130.906 | **98,5%** | ✅ Quase tudo é faturado — saudável |
| Aprovado | 1.097 | 0,8% | Aguardando separação |
| Cancelado | 168 | 0,1% | Perda baixa |

### 3.3 Canais de Venda (PDV_ORIGEM)

| Origem | Itens | Receita | Clientes |
|--------|-------|---------|----------|
| **MAG** (Marketplace) | 66.436 | **R$ 4,24 MM** | 13.611 |
| GER (Direto / Site) | 5.105 | R$ 290,7 K | 887 |
| Sem origem (loja física?) | 61.426 | R$ 3,25 MM | 5.748 |

> 🔍 **Nota:** Quase metade dos itens não tem origem preenchida. Vale investigar com o Matias se é loja física ou lacuna de dado.

### 3.4 Segmentos de Produto

| Segmento | Qtd (un) | Receita | SKUs | Ticket Médio |
|----------|----------|---------|------|-------------|
| **MATRIZ** | 918.323 | **R$ 3,15 MM** | 738 | **R$ 320,56** |
| CHC | 157.259 | R$ 1,75 MM | 843 | R$ 218,83 |
| GCL | 167.767 | R$ 1,51 MM | 652 | R$ 223,35 |
| ACL | 176.171 | R$ 1,21 MM | 717 | R$ 239,10 |
| BRG | 44.151 | R$ 143,4 K | 311 | R$ 332,02 |

> ⚡ **Insight:** MATRIZ é o segmento dominante em volume e receita. BRG tem o maior ticket médio (provavelmente kits ou itens de maior valor agregado).

### 3.5 Top 5 Produtos (por receita total)

| SKU | Produto | Segmento | Qtd | Receita |
|-----|---------|----------|-----|---------|
| 2140006 | EDREDOM QUEEN HOTELARIA BRANCO | MATRIZ | 1.750 | R$ 152,8 K |
| 19348 | LENÇOL CASAL C/ ELÁST. 140x190 | MATRIZ | 20.287 | R$ 142,1 K |
| 16429 | LENÇOL QUEEN SEM ELÁST. 250x250 | MATRIZ | 43.144 | R$ 141,8 K |
| 17689 | LENÇOL CASAL SEM ELÁST. 220x250 | MATRIZ | 29.556 | R$ 131,7 K |
| 1080003 | PROTETOR COLCHÃO IMPERMEÁVEL QUEEN | MATRIZ | 6.001 | R$ 130,0 K |

> 🔍 **Nota:** Lençóis e edredons dominam o ranking. Há também kits de sabonetes (SKU 42213003) com R$ 130K — hotelaria compra em volume.

### 3.6 Sazonalidade

| Mês/Ano | Receita | Clientes | Pedidos |
|---------|---------|----------|---------|
| **Jun/2026** (parcial) | R$ 13,8 K | 44 | 44 |
| Mai/2026 | R$ 348,2 K | 1.132 | 1.263 |
| Abr/2026 | R$ 335,4 K | 1.047 | 1.146 |
| Mar/2026 | R$ 335,9 K | 1.162 | 1.280 |
| Fev/2026 | R$ 297,6 K | 957 | 1.045 |
| Jan/2026 | R$ 322,5 K | 1.040 | 1.160 |
| Dez/2025 | R$ 297,8 K | 971 | 1.085 |
| Nov/2025 | R$ 368,4 K | 1.212 | 1.339 |
| Out/2025 | **R$ 389,5 K** | 1.145 | 1.324 |
| Set/2025 | R$ 335,2 K | 1.016 | 1.158 |
| Ago/2025 | R$ 290,1 K | 955 | 1.061 |
| Jul/2025 | R$ 284,2 K | 1.038 | 1.168 |
| Jun/2025 | R$ 297,9 K | 1.037 | 1.136 |
| Mai/2025 | R$ 374,6 K | 1.298 | 1.416 |
| Abr/2025 | **R$ 395,1 K** | 1.354 | 1.493 |
| Mar/2025 | R$ 325,2 K | 1.219 | 1.306 |

> 📈 **Picos sazonais:** Abr-Mai e Out-Nov (pré-Dia das Mães e Black Friday/Natal).
> 📉 **Vales:** Fev (pós-férias) e Jul-Ago (inverno).

### 3.7 Distribuição Geográfica

| Estado | Clientes | Receita | % |
|--------|----------|---------|---|
| SP | 8.216 | **R$ 3,04 MM** | **44,3%** |
| RJ | 2.126 | R$ 883,6 K | 12,9% |
| MG | 1.773 | R$ 689,1 K | 10,1% |
| SC | 998 | R$ 436,4 K | 6,4% |
| PR | 906 | R$ 377,7 K | 5,5% |
| BA | 784 | R$ 348,6 K | 5,1% |
| RS | 797 | R$ 320,1 K | 4,7% |
| Demais | ~3.000 | R$ 780,0 K | 11,0% |

> ✅ SP + RJ + MG concentram **67%** da receita. Logística e fretes precisam refletir isso.

### 3.8 Condições de Pagamento

| Condição | Faturamento | % |
|----------|------------|---|
| **À vista** | **R$ 2,88 MM** | **36%** |
| Cartão 4x | R$ 2,41 MM | 30% |
| Cartão 5x | R$ 1,06 MM | 13% |
| Cartão 3x | R$ 372,8 K | 5% |
| Cartão 1x/2x | R$ 632,3 K | 8% |
| Demais | R$ 652,9 K | 8% |

> 💡 36% à vista é excelente para fluxo de caixa. Cartão parcelado tem custo de taxa — importante considerar na margem.

---

## 4. Oportunidades e Pendências

### ✅ Já disponível (SQL Server)
- Análise de vendas por SKU, segmento, cliente, período
- Acompanhamento de pedidos por status
- Ranking de produtos para priorizar compras
- Sazonalidade para planejar estoque
- Origem dos pedidos (MAG vs GER)
- Performance por vendedor

### ❌ Não disponível (precisa do Oracle DEBX)
- **Estoque atual** (`v_estoq`) — essencial para decidir o que comprar
- **Estoque por almoxarifado** (`ALMOX`)
- **Produtos** (`F_PRODS`) — cadastro completo de materiais
- **Compras / Pedidos de compra** — não identifiquei tabela de PO no SQL Server
- **Preço de custo / margem** — não temos visão de custo dos produtos

### 🔧 Recomendações para explorar
1. **Obter credencial Oracle DEBX** para acesso a `v_estoq` e `F_PRODS`
2. **Criar script de monitoramento de estoque crítico** (itens com baixo giro x alto volume)
3. **Criar relatório semanal de top vendidos vs estoque disponível**
4. **Integrar análise de sazonalidade com programação de compras**

---

## 5. Disclaimer

- ⚠️ Este relatório foi gerado com base no **SQL Server (Hotel Finder)**, que contém dados de pedidos e vendas.
- ⚠️ O **Oracle DEBX** (ERP principal, 172.169.0.11:1521/conamore) não foi acessado por falta de credenciais — ele tem dados de estoque e cadastro de produtos que complementam esta análise.
- ⚠️ A janela operacional do Oracle DEBX é **08:00 às 18:00 (BRT)**; fora disso a conexão pode falhar com `ORA-01033`.
- ⚠️ A tabela `debx.open_orders` está **desatualizada** (último dado 05/2025). Usar `debx.PDV_Detalhes` ou `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL` para dados atuais.

---

> *Relatório documentado no Obsidian para rastreabilidade. Pendente: solicitar acesso Oracle DEBX para Matias.*
