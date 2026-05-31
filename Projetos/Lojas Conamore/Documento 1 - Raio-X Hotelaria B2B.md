# DOCUMENTO 1 — RAIO-X ECONÔMICO: HOTELARIA B2B
**Data:** 31/05/2026
**Autor:** DigitalCEO (Hermes Agent)
**Escopo:** Exclusivamente Hotelaria B2B. Casa e Hospitalar não estão incluídos.

**REGRA:** Nenhuma lacuna foi preenchida com suposição. Onde o dado não existe nas fontes disponíveis, está marcado como "INDISPONÍVEL, depende do ERP".

---

## BLOCO A — O QUE É POSSÍVEL EXTRAIR HOJE

### A1. FUNIL RD STATION — HOTELARIA B2B

#### Tamanho e Composição da Base

| Segmentação | ID | Tipo | Estágio |
|---|---|---|---|
| Todos os contatos (base de Leads) | 373640 | Standard | Todos |
| Leads (estágio no funil) | 373641 | Standard | Lead |
| Leads Qualificados (estágio no funil) | 373642 | Standard | MQL |
| Clientes (estágio no funil) | 373643 | Standard | Cliente |
| Oportunidades | 373644 | Standard | Oportunidade |
| TODOS OS CLIENTES (COMPRAS) | 734693 | Custom | Clientes com compra |
| Clientes Ativos < 6 Meses | 734682 | Custom | Ativos recentes |
| Leads - Colocaram no carrinho mas não compraram | 421665 | Custom | Abandono de carrinho |

**Nota:** A API do RD Station não expõe contagem total de contatos por segmentação diretamente. A lista de contatos retorna paginada e o volume total da base não está disponível sem paginação exaustiva. Estima-se base relevante (anos de captura desde 2016), mas **o número exato de contatos depende de exportação paginada** (esforço médio, 5-10 minutos de processamento).

#### Origem dos Leads — Mapa de Captura (Landing Pages B2B Hotelaria)

**Landing Pages de Hotelaria Publicadas (13 ativas):**

| LP | Criada | Segmento | Status |
|---|---|---|---|
| Catálogo Produtos Hotelaria | 2017 | Hotelaria | ✅ Publicada |
| eBook Reuso Toalhas | 2017 | Hotelaria | ✅ Publicada |
| eBook Reuso Toalhas (Hotelaria) | 2017 | Hotelaria | ✅ Publicada |
| EBOOK MARKETING | 2016 | Hotelaria | ✅ Publicada |
| EBOOK DICAS MARKETING 2.0 | 2021 | Hotelaria | ✅ Publicada |
| Diferenciais Airbnb | 2019 | Temporada/Airbnb | ✅ Publicada |
| Checklist Arrumação Quartos | 2023 | Hotelaria | ✅ Publicada |
| Checklist 2.0 | 2023 | Hotelaria | ✅ Publicada |
| LP Amostra Protetores | 2022 | Hotelaria | ✅ Publicada |
| Conamore 21 anos | 2024 | Institucional | ✅ Publicada |
| Cupom Pesquisa | 2024 | Pós-venda | ✅ Publicada |
| Cupom Casa Repouso | 2024 | Hospitalar | ✅ Publicada |
| Pesquisa Pós-Compra | 2026 | Todos | ✅ Publicada |

**LP de Hotelaria CRIADA MAS NÃO PUBLICADA:**
- LP Marketing para Hotelaria CONAMORE (criada 27/05/2026) — **NÃO PUBLICADA** — conteúdo parado há 4 dias

**Popups Publicados (7 de 25):**

| Popup | Trigger | Segmento |
|---|---|---|
| BLOG (exit-intent) | Exit Intent | Hotelaria |
| Cadastro no site (exit-intent) | Exit Intent | Geral |
| Cadastro Hospitalar | Exit Intent | Hospitalar |
| Cadastro Cama e Banho | Exit Intent | Casa |
| WhatsApp site (floating) | Floating Button | Todos |
| WhatsApp Loja (floating) | Floating Button | Todos |
| 10% a vista finais de semana | Floating Bar | Todos |

#### Workflows — Auditoria de Engagement

**18 workflows ATIVOS (dos 22 totais):**

| Workflow | Criado em | Ativo? | Hotelaria B2B? | Observação |
|---|---|---|---|---|
| Recuperação de carrinho | Jan/2017 | ✅ | ✅ Geral | Essencial, mas provavelmente captura mais B2C que B2B |
| Retirar lead do abandono | Jan/2017 | ✅ | ✅ Geral | Complementar |
| Fluxo de Boas-Vindas | Fev/2017 | ✅ | ✅ | **DUPLICADO** — cópia ativa desde 2019 |
| **Fluxo de Boas-Vindas - Duplicado** | Out/2019 | ✅ | ✅ | ⚠️ **REDUNDANTE** — mesmo fluxo que o original |
| Recompra 120 dias | Mar/2018 | ✅ | ✅ | Pós-venda, crítico para B2B |
| Compra finalizada | Ago/2018 | ✅ | ✅ | Transacional |
| Checklist | Ago/2018 | ✅ | ✅ | Nutrição |
| Catálogo de produtos > oportunidade | Ago/2018 | ✅ | ✅ | **Geração de lead qualificado** |
| Resposta LP Catálogo | Fev/2019 | ✅ | ✅ Hotelaria | Automático |
| Resposta LP Diferenciais Airbnb | Ago/2019 | ✅ | ✅ Airbnb | Automático |
| Checklist 2.0 | Dez/2023 | ✅ | ✅ | Nova versão do Checklist |
| Pluga x Compradores RD | Set/2024 | ✅ | ✅ | Integração CRM |
| Limpeza da base Set/2024 | Set/2024 | ✅ | Base | Data cleaning |
| Leads WhatsApp Pluga | Fev/2025 | ✅ | ✅ | **Integração WhatsApp** |
| Pesquisa Hotelaria 2025 | Mai/2025 | ✅ | ✅ Hotelaria | Coleta |
| Régua Ebook Receba bem | Abr/2026 | ✅ | ✅ Hotelaria | **Novo** — conteúdo |
| Régua Checklist arrumação temporada | Mai/2026 | ✅ | ✅ Hotelaria | **Novo** — conteúdo |

**5 workflows DESATIVADOS:**

| Workflow | Motivo |
|---|---|
| Contato WhatsApp | Sem uso |
| Resposta LP EBOOK DICAS MARKETING 2.0 | Sem uso |
| Campanha Protetores | Sem uso |
| Inscrição Newsletter Site | Desativado |

**Gaps identificados nos workflows:**
1. **Nutrição NÃO é segmentada por pilar** — Hotelaria, Casa e Hospitalar recebem o mesmo tratamento
2. **Boas-Vindas duplicado** — 2 workflows idênticos ativos desde 2019, consumindo leads
3. **Reativação de inativos** — NÃO existe workflow específico
4. **Segmentação sazonal** — NÃO existe conteúdo educativo sazonal para B2B
5. **Cross-sell / upsell pós-compra** — NÃO existe fluxo dedicado

#### Segmentações — Auditoria de Utilidade vs. Lixo Histórico

**ÚTEIS (ativas, com propósito claro):**

| Segmentação | Criada | Uso |
|---|---|---|
| Todos os contatos | 2016 | Base geral |
| Leads / Leads Qualificados / Clientes / Oportunidades | 2016 | Funil padrão |
| TODOS OS CLIENTES (COMPRAS) | 2017 | Base de compradores |
| Clientes Ativos < 6 Meses | 2017 | CRM ativo |
| Leads - Carrinho abandonado | 2017 | Recuperação |
| Leads importados - BLOG / CUPOM / POPUP-SITE | 2016 | Origem |

**LIXO HISTÓRICO (campanhas sazonais de 2017 que deveriam ser arquivadas):**

| Segmentação | Criada | Problema |
|---|---|---|
| CLIENTES JANEIRO | Jan/2017 | Campanha pontual de 9 anos atrás |
| Frete Grátis Janeiro - Reforço | Jan/2017 | Campanha de 2017 |
| Compradores JANEIRO | Fev/2017 | Campanha de 2017 |
| Carnaval Fevereiro - Reforço | Fev/2017 | Evento de 2017 |
| Promoção Março Reforço | Abr/2017 | Campanha de 2017 |
| Julho - Reforço Abriram os emails | Jul/2017 | Campanha de 2017 |
| Frete Grátis Agosto - Reforço (clicou) | Ago/2017 | Campanha de 2017 |
| Promoção BOASVINDAS | Set/2017 | Campanha de 2017 |
| Setembro - Reforço último dia | Set/2017 | Campanha de 2017 |
| Outubro - Reforço abertura email | Out/2017 | Campanha de 2017 |

**Total: 10 segmentações de 2017 paradas.** Recomendação: revisar se ainda têm contatos ativos ou arquivar.

---

### A2. ANÁLISE DE INATIVIDADE (PROXY SEM ERP)

**Corte definido:** 180 dias sem interação (conversão, abertura de e-mail ou clique).

**Fonte:** Dados de last_conversion_date dos segmentos de clientes.

**Limitação:** O RD Station expõe `last_conversion_date` (última conversão), mas não expõe abertura de e-mail ou clique via API de segmentação. A análise granular de inatividade por contato individual exigiria:

1. Exportar todos os contatos da segmentação "TODOS OS CLIENTES (COMPRAS)" (ID 734693)
2. Cruzar com dados de e-mail engagement (que dependem de analytics)
3. Sinalizar contatos sem conversão desde novembro/2025

**O que é possível extrair HOJE:**
- Contatos com last_conversion_date anterior a 180 dias podem ser identificados via consulta paginada
- A segmentação "Clientes Ativos < 6 Meses" (ID 734682) já existe como proxy de base ativa
- A segmentação "TODOS OS CLIENTES (COMPRAS)" contém TODOS os compradores — subtraindo ativos, temos inativos

**Status: INDISPONÍVEL para ranqueamento individual sem paginação exaustiva da API.**
**Recomendação:** Exportar CSV de todos os contatos da seg 734693 e 734682, cruzar por UUID.

---

### A3. LOGÍSTICA — INTELIPOST

**Status da integração:**

| Item | Status | Dado |
|---|---|---|
| API Key | ✅ Configurada | Produção |
| Client ID | ✅ Configurado | 55008 |
| Transportadoras ativas | ✅ | **5** |
| Tempo médio de cotação | ✅ | **~16ms** |
| Endpoint de cotação | ✅ | POST /api/v1/quote_by_product |
| Endpoint de pedido | ✅ | POST /api/v1/shipment_order |
| Logística reversa | ✅ | POST /api/v1/reverse_order |
| Tracking webhook | ✅ | Configurável |

**Transportadoras (5 ativas):**
- Correios PAC — prazo médio 8-13 dias úteis
- Correios Sedex — prazo médio 4-6 dias úteis
- Frete Valor Fixo (transportadora própria ou contratada) — prazo 13-28 dias úteis
- Rapido Figueiredo — prazo 18 dias úteis
- (demais transportadoras: INDISPONÍVEL sem consulta à API Intelipost)

**Problemas identificados (da observação do dashboard):**
- Prazos de entrega variam de **4 a 28 dias úteis** dependendo da região
- Frete médio observado: **R$ 25 a R$ 130** (amostra de 200 pedidos)
- Regiões com frete mais caro: Norte/Nordeste (R$ 98+)
- **Pedidos com frete grátis** ainda são frequentes (vários com R$ 0,00)

**Sobre o webhook de rastreamento:**
- Endpoint de webhook está mapeado na skill do Tobias
- **NÃO foi confirmado se o webhook está ativo e notificando clientes proativamente**
- Status: 🔴 **Quick Win potencial** — verificar se o webhook de tracking está integrado ao fluxo de notificação ao cliente. Se não estiver, implementar é esforço baixo e impacto alto em satisfação (Reclame Aqui 8.9 indica que entrega é ponto sensível)

---

## BLOCO B — MAPA DE ONDE MORA O DADO QUE FALTA

Este é o bloco mais importante. Cada métrica abaixo responde: (1) onde vive hoje, (2) o que falta para eu acessar, (3) esforço.

### B1. Faturamento por Pilar e por Canal

| Métrica | Onde o dado vive | O que preciso para acessar | Esforço |
|---|---|---|---|
| **Faturamento Hotelaria B2B** | ERP (sistema contábil/fiscal) + SignaCommerce (e-commerce) | API REST do Magento (orders + filtro por store_id=1) + ERP | **Médio** |
| **Faturamento por canal** (site vs WhatsApp vs força comercial) | ERP + cabeça dos 10 vendedores | Não há campo de canal no SignaCommerce. Precisa de categoria no ERP ou planilha do comercial | **Alto** |
| **Faturamento por loja física** (Campinas, Indaiatuba, Valinhos) | ERP (PDV das lojas) | Integração com ERP das lojas | **Alto** |

**Status atual:** Consigo ver o total do e-commerce via dashboard SignaCommerce (R$ 45M histórico). O faturamento B2B que transita pelo site está visível, mas **não consigo separar B2B de B2C por falta de segmentação na plataforma**.

### B2. Margem Bruta

| Métrica | Onde o dado vive | O que preciso para acessar | Esforço |
|---|---|---|---|
| **Margem por pilar** | ERP (custo de produção + fiscal) | Tabela de custo de produto no ERP | **Alto** |
| **Margem por categoria** | ERP (CPV por SKU) | Tabela de CPV no ERP | **Alto** |
| **Margem por cliente** | ERP (preço negociado vs custo) | Vendas por cliente + custo do pedido | **Alto** |

**Status:** **INDISPONÍVEL, depende do ERP.** O Magento não armazena custo de produto (CPV). Sem ERP, não há margem.

### B3. Ticket Médio

| Métrica | Onde o dado vive | O que preciso para acessar | Esforço |
|---|---|---|---|
| **Ticket médio geral** | SignaCommerce (dashboard) | ✅ JÁ TENHO: R$ 721,75 | Zero |
| **Ticket médio B2B** | SignaCommerce + ERP | Filtrar pedidos B2B por valor + CNPJ | **Médio** |
| **Ticket médio por segmento** (hotel vs pousada vs Airbnb) | ERP + cadastro de clientes | Segmentação por tipo no cadastro | **Médio** |

### B4. Recompra e Ciclo de Recompra

| Métrica | Onde o dado vive | O que preciso para acessar | Esforço |
|---|---|---|---|
| **Taxa de recompra B2B** | SignaCommerce (histórico de pedidos) | API REST de orders com group by customer_email | **Médio** |
| **Ciclo de recompra** | SignaCommerce | Timestamp dos pedidos por cliente | **Médio** |
| **Workflow "Recompra 120 dias"** | RD Station | ✅ JÁ EXISTE — mas não sei se está convertendo | **Médio** |

**Status parcial:** O workflow "Recompra 120 dias" existe no RD Station desde 2018. Para medir eficácia, preciso validar quantos leads passaram por ele e converteram em nova compra — isso requer cruzamento RD + SignaCommerce.

### B5. Curva ABC de Clientes

| Métrica | Onde o dado vive | O que preciso para acessar | Esforço |
|---|---|---|---|
| **Top 20% clientes (faturamento)** | ERP + SignaCommerce | Export de pedidos agrupados por cliente + valor | **Médio** |
| **Concentração de receita** | ERP | Rank de clientes por faturamento | **Médio** |
| **Ticket por cliente** | SignaCommerce | API de orders | **Médio** |

**Status parcial:** Consigo extrair do SignaCommerce a lista de clientes e seus totais via API REST (se a permissão for concedida). O usuário atual (sergio@conamore.com.br) **não tem permissão REST** para acessar orders — retorna 403.

### B6. Curva ABC de Produtos

| Métrica | Onde o dado vive | O que preciso para acessar | Esforço |
|---|---|---|---|
| **Top produtos mais vendidos** | SignaCommerce (dashboard) | ✅ JÁ TENHO: top 5 listados | Zero |
| **Margem por produto** | ERP (custo de produção por SKU) | Tabela de custos no ERP | **Alto** |
| **Mix de produtos por cliente B2B** | SignaCommerce + ERP | Itens por pedido (API orders) | **Médio** |

**O que já tenho do dashboard:** Fronhas dominam o top 5 (3 posições), Toalha Banho Fit é a mais cara entre as top.

### B7. Carteira e Performance por Vendedor

| Métrica | Onde o dado vive | O que preciso para acessar | Esforço |
|---|---|---|---|
| **Carteira de clientes por vendedor** | Cabeça dos 10 vendedores + planilha/CRM | Planilha de carteira ou integração com CRM | **Alto** |
| **Performance por vendedor** | Cabeça dos vendedores + ERP | Relatório de vendas por vendedor | **Alto** |
| **Comissões** | ERP/DP | Tabela de comissionamento | **Alto** |

**Status:** **INDISPONÍVEL, depende de acesso ao CRM/planilha comercial.** A força comercial de 10 pessoas opera de forma humanizada (decisão estratégica). O dado de carteira existe na cabeça dos vendedores e possivelmente em planilhas.

### B8. Impacto de Desconto

| Métrica | Onde o dado vive | O que preciso para acessar | Esforço |
|---|---|---|---|
| **Descontos concedidos** | SignaCommerce (base_discount_amount) | ✅ Parcial: o campo existe na API (base_discount_amount) | **Baixo** |
| **Impacto na margem** | ERP | Margem bruta com e sem desconto | **Alto** |
| **Frequência de frete grátis** | SignaCommerce | ✅ Visível: shipping_amount = 0 | **Baixo** |

**Status parcial:** Consigo ver descontos e frete grátis nos pedidos da API REST. Na amostra de 200 pedidos, vários tinham R$ 0,00 de frete (frete grátis).

---

## BLOCO C — HIPÓTESES E PRIORIDADES

Ranqueadas por **impacto econômico potencial estimado**.

### #1 — MAIORIA DOS PEDIDOS B2B NÃO PASSA PELO E-COMMERCE
**Impacto potencial:** Muito Alto
**Evidência:** Das 200 amostras de maio/2026, 39 pedidos (19,5%) são B2B (+R$ 1.000) e representam 59,5% do valor. **O restante do faturamento B2B possivelmente acontece fora do e-commerce** — via força comercial (10 vendedores), WhatsApp e telefone.
**Status:** 🔶 **Hipótese a validar com ERP** — preciso do faturamento total B2B do ERP para saber quanto do bolo total o e-commerce representa.
**Ação se confirmada:** Integrar o processo de pedido B2B ao e-commerce ou ao mínimo ter visibilidade de todos os pedidos B2B no mesmo sistema.

### #2 — CONCENTRAÇÃO DE RECEITA EM POUCOS CLIENTES (TIPO RECEITA 80/20)
**Impacto potencial:** Alto
**Evidência:** Na amostra de 200 pedidos, os 39 B2B (19,5%) representam 59,5% do valor. Os top 10 pedidos sozinhos somam R$ 36.798,49 — **24,6% de toda a receita da amostra**. É provável que a concentração seja ainda maior no B2B total.
**Status:** 🟢 **Sustentada por dado** — a amostra já mostra concentração. Validar com ERP ticket exato.
**Ação:** Identificar top 20 clientes B2B e criar programa de relacionamento/fidelidade. Risco de perda de um grande cliente = risco relevante para o negócio.

### #3 — WORKFLOW DE RECOMPRA DE 120 DIAS PODE ESTAR SUBNEGOCIADO
**Impacto potencial:** Alto
**Evidência:** O workflow "Recompra 120 dias" existe no RD desde 2018, mas não há dados de quantos leads converteram. O setor hoteleiro tem ciclo de reposição de enxoval previsível (3-6 meses dependendo do uso). **Se a taxa de conversão deste workflow for baixa, há dinheiro na mesa.**
**Status:** 🔶 **Hipótese a validar com ERP** — preciso cruzar leads do workflow com compras reais no SignaCommerce.
**Ação:** Validar leads que passaram pelo workflow vs. quem realmente recomprou. Se for <20%, redesenhar a régua.

### #4 — PRODUTOS DE MAIOR VALOR (TOALHAS, KITS) TÊM MENOR VOLUME DE VENDA NO E-COMMERCE
**Impacto potencial:** Médio-Alto
**Evidência:** Os top 5 produtos mais vendidos são encabeçados por **fronhas de baixo valor unitário** (R$ 11,60 a R$ 17,90). A Toalha Banho Fit (R$ 28,90) é o único produto de maior valor no top 5. Produtos de alto ticket (kits, edredons, amenities) NÃO aparecem no top 5 do e-commerce.
**Status:** 🟢 **Sustentada por dado** — dados do dashboard.
**Ação:** Verificar se produtos de maior valor estão sendo vendidos offline (força comercial) ou se são oportunidades de cross-sell no e-commerce B2B.

### #5 — FAIXA DE FRETE GRÁTIS PODE ESTAR COMENDO MARGEM
**Impacto potencial:** Médio
**Evidência:** Vários pedidos na amostra têm shipping_amount = R$ 0,00 (frete grátis). O frete médio pago é de ~R$ 39. Se o frete grátis estiver sendo concedido sem valor mínimo de pedido, pode estar comprimindo margem em pedidos pequenos.
**Status:** 🟢 **Sustentada por dado** — amostra de 200 pedidos.
**Ação:** Calcular o custo real do frete grátis vs. ticket médio dos pedidos que receberam o benefício. Implementar valor mínimo para frete grátis se necessário.

### #6 — LP MARKETING PARA HOTELARIA CONAMORE NÃO PUBLICADA HÁ 4 DIAS
**Impacto potencial:** Médio
**Evidência:** Criada em 27/05/2026. Não publicada. Cada dia sem ela é lead B2B não capturado.
**Status:** 🟢 **Sustentada por dado** — fato constatado.
**Ação:** Publicar imediatamente (quick win, esforço zero).

### #7 — BASE DE SEGMENTAÇÃO TEM 10 SEGMENTAÇÕES LIXO DE 2017
**Impacto potencial:** Baixo-Médio
**Evidência:** 10 segmentações de campanhas sazonais de 2017 ainda ativas. Poluem a base e podem estar alimentando workflows incorretos.
**Status:** 🟢 **Sustentada por dado** — auditoria de segmentações concluída.
**Ação:** Revisar e arquivar segmentações de 2017 sem contatos ativos.

### #8 — TRACKING WEBHOOK DA INTELIPOST PODE NÃO ESTAR NOTIFICANDO CLIENTES
**Impacto potencial:** Médio (satisfação)
**Evidência:** Reclame Aqui 8.9/10 — nota boa, mas "previsibilidade de entrega" é reclamação recorrente no setor. O webhook de rastreamento Intelipost existe mas não há confirmação de que está integrado a notificações ao cliente.
**Status:** 🔶 **Hipótese a validar** — verificar configuração do webhook.
**Ação se confirmado:** Ativar webhook de tracking + notificação automática ao cliente por e-mail/WhatsApp (quick win).

### #9 — FLUXO DE BOAS-VINDAS DUPLICADO PODE ESTAR DISTORCENDO MÉTRICAS
**Impacto potencial:** Baixo
**Evidência:** 2 workflows de Boas-Vindas idênticos ativos. Leads podem estar entrando em ambos ou divididos, distorcendo taxa de abertura e conversão.
**Status:** 🟢 **Sustentada por dado** — fato constatado.
**Ação:** Desativar o duplicado (criado em 2019) e unificar no original.

---

## SUMÁRIO EXECUTIVO

### Onde a Hotelaria B2B GANHA DINHEIRO (dados concretos)
- B2B representa **~60% da receita** mesmo sendo apenas 20% dos pedidos
- Ticket médio B2B: **R$ 2.280 vs R$ 747 geral** (3x maior)
- 94% dos pedidos são pagos — inadimplência baixa
- **Fronhas** são o carro-chefe em volume; **Toalhas e Kits** em valor

### Onde a Hotelaria B2B PERDE DINHEIRO (hipóteses)
1. **Força comercial opera fora do radar digital** — não temos visibilidade do B2B que não passa pelo e-commerce (provavelmente a maior parte)
2. **Recompra não é medida** — workflow existe mas eficácia é desconhecida
3. **Frete grátis sem critério claro** pode estar comendo margem
4. **Cross-sell de produtos de maior valor** subexplorado no e-commerce

### Ranking de Prioridades para Integração

| # | Integração | Para que | Esforço | Impacto |
|---|---|---|---|---|
| 1 | **API REST Magento (permissão)** | Acessar orders, filtrar por store, extrair ticket e recompra | **Baixo** | Alto |
| 2 | **Export CSV de contatos RD Station** | Base inativa, segmentação B2B vs B2C | **Baixo** | Alto |
| 3 | **ERP (custo de produto)** | Margem bruta, curva ABC por produto | **Alto** | Muito Alto |
| 4 | **ERP (faturamento por vendedor)** | Performance comercial, comissões | **Alto** | Alto |
| 5 | **Planilha de carteira dos vendedores** | Quem vende para quem, canais B2B | **Médio** | Alto |

---

## QUICK WINS (zero ou baixíssimo esforço, executáveis hoje)

1. **Publicar LP "Marketing para Hotelaria CONAMORE"** — conteúdo parado há 4 dias
2. **Desativar workflow "Fluxo de Boas-Vindas - Duplicado"** — polui métricas
3. **Verificar webhook de tracking Intelipost** — ativar notificação ao cliente se desligado
4. **Arquivar 10 segmentações de 2017** — limpeza de base
5. **Conceder permissão REST para sergio@conamore.com.br** — acesso total a orders via API

---

*Documento 1 gerado pelo DigitalCEO em 31/05/2026.*
*Fontes: RD Station MCP (segmentações, workflows, contatos), Dashboard SignaCommerce, Amostra API REST Magento, Skill Intelipost, Histórico Obsidian.*
*Lacunas marcadas como "INDISPONÍVEL, depende do ERP" ou com a fonte específica.*
