# Parecer de Crédito — Espaço Flor das Águas — Pedido 0114019

**Data da análise:** 28/07/2026 16:49 BRT  
**Analista:** Tiago — Financeiro Conamore  
**Fontes:** Proposta PDF `114019 - Proposta Comercial Espaço Flor das Águas Ltda.pdf`, bureau PDF `ANÁLISE SOFIA HOMES.pdf`, Lista Negra Conamore, Hotel Finder SQL Server, ReceitaWS, DuckDuckGo Lite, Google Maps, website oficial.

---

## 0. Validação dos 2 arquivos recebidos

Os 2 arquivos **não pertencem ao mesmo CNPJ**:

| Arquivo | Cliente | CNPJ |
|---|---|---|
| Proposta comercial 0114019 | Espaço Flor das Águas Ltda | 44.340.810/0001-62 |
| Bureau Equifax/Boa Vista | Sofia Homes Ltda | 18.185.285/0001-48 |

**Conclusão:** o bureau `ANÁLISE SOFIA HOMES.pdf` **não pode ser usado como score/restrição do Espaço Flor das Águas**. Ele foi lido e registrado como arquivo independente, mas a decisão do pedido 0114019 foi feita com base na proposta do Espaço Flor das Águas + histórico interno + ReceitaWS + validação online. Para fechar com bureau pago do Espaço Flor das Águas, é necessário o relatório correto do CNPJ `44.340.810/0001-62`.

---

## 1. Dados da proposta

| Campo | Informação |
|---|---|
| Pedido / orçamento | 0114019 |
| Emissão | 27/07/2026 |
| Validade | 29/07/2026 |
| Cliente | Espaço Flor das Águas Ltda |
| CNPJ | 44.340.810/0001-62 |
| ID_DEBX | A1004 |
| Classe | Hotel |
| Endereço | Rua Caminho do Ouro, 5, Alto do Cruzeiro, Cunha-SP, CEP 12530-000 |
| E-mail | financeiroefda@gmail.com |
| Contato | Narayan |
| Telefone | (12) 99259-9387 / PDF também indica 12 99764-7239 |
| Representante | Carlos Manoel da Silva |
| Valor produtos | R$ 4.096,00 |
| Frete | R$ 50,00 |
| Total do pedido | R$ 4.146,00 |
| Forma de pagamento no cabeçalho | A definir |
| Observação comercial | Faturado mediante análise, com 50% à vista e 50% em 30/60 dias |
| Entrada recomendada | R$ 2.073,00 |
| Exposição líquida | R$ 2.073,00 |
| Parcelas saldo | 2x de R$ 1.036,50 |

## 2. Etapa 0 — Lista Negra Conamore

✅ **Não consta** na Lista Negra Conamore consultada.

Critérios verificados: CNPJ `44.340.810/0001-62`, razão social `ESPAÇO FLOR DAS ÁGUAS LTDA` e similaridade nominal.

## 3. Histórico interno Conamore — Hotel Finder

Cadastro encontrado em `conamore.Customers`:

- **ID_DEBX:** A1004
- **Cliente / razão social:** ESPAÇO FLOR DAS ÁGUAS LTDA
- **CNPJ:** 44.340.810/0001-62
- **Status:** 0
- **Endereço:** Rua Caminho do Ouro, 5, Cunha-SP

Pedidos localizados em `debx.PDV_Detalhes` por ID e por razão social:

| Pedido | Data | Status | Valor | Condição |
|---|---:|---|---:|---|
| 0084446 | 16/01/2026 | Expedição | R$ 4.054,60 | PIX à vista |
| 0022075 | 11/03/2025 | Expedição | R$ 1.412,40 | Cartão 2x |
| 0020546 | 18/02/2025 | Expedição | R$ 12.747,20 | Cartão 6x |
| 0005300 | 14/08/2024 | Expedição | R$ 2.700,10 | Cartão 2x |
| 0005373 | 15/08/2024 | Expedição | R$ 1.763,60 | Cartão 4x |
| 0005182 | 19/11/2024 | Cancelado | R$ 4.814,00 | A definir / cartão corporativo |

**Resumo histórico:**

- **5 pedidos anteriores expedidos/faturados**.
- **Total histórico expedido:** R$ 22.677,90.
- **Ticket médio histórico:** R$ 4.535,58.
- **Pedido atual:** R$ 4.146,00 — equivale a **91,41% do ticket médio histórico**, portanto está coerente com o padrão de compra.
- Maior pedido anterior: R$ 12.747,20; o pedido atual representa apenas **32,52%** do maior pedido histórico.
- Histórico anterior foi principalmente **cartão/PIX**, sem boleto puro relevante localizado. O faturado 50% + 30/60 seria uma condição nova em boleto, porém com exposição baixa.

### Grupo econômico / endereço relacionado

Busca por mesmo endereço em `conamore.Customers` encontrou:

| ID_DEBX | Cliente | CPF/CNPJ | Observação |
|---|---|---|---|
| A1004 | Espaço Flor das Águas Ltda | 44.340.810/0001-62 | Cliente analisado |
| 28311 | Inara Rocha | CPF 350.819.358-67 | Mesmo endereço, sem pedidos em `PDV_Detalhes` |

Não há histórico adicional de compra no relacionado `Inara Rocha`, portanto a decisão fica baseada no histórico próprio do CNPJ A1004.

**Classificação interna:** **Classe B** — recorrente, compra compatível, histórico positivo em valores maiores, mas ainda sem histórico robusto em boleto/faturado.

## 4. Score / Bureau

### Bureau recebido — Sofia Homes Ltda

O arquivo de bureau recebido é de **Sofia Homes Ltda — CNPJ 18.185.285/0001-48**, não do Espaço Flor das Águas.

Dados extraídos do bureau da Sofia Homes:

| Campo | Resultado |
|---|---|
| Score Aprovação PJ | 704 |
| Probabilidade de inadimplência | 6,0% |
| Cadastro Positivo | Participante com informação |
| Pendências e restrições financeiras | Nada consta |
| Cheques sem fundos | Nada consta |
| Cheques sustados motivo 21 | Nada consta |
| Cheques devolvidos informados pelo usuário | Nada consta |
| Protestos | Nada consta |
| Consultas | 6 no período 01/07/2025 a 01/07/2026 |

**Uso na análise:** somente registro de inconsistência documental. **Não utilizado para aprovar o Espaço Flor das Águas.**

### Dados públicos do Espaço Flor das Águas — ReceitaWS

| Campo | Resultado |
|---|---|
| Situação cadastral | ATIVA |
| Abertura | 23/11/2021 |
| Idade aproximada | 4 anos e 8 meses |
| Porte | Empresa de Pequeno Porte |
| Natureza jurídica | Sociedade Empresária Limitada |
| Capital social | R$ 640.000,00 |
| CNAE principal | Hotéis |
| Endereço | Rua Caminho do Ouro, 5, Alto do Cruzeiro, Cunha-SP |
| E-mail | financeiroefda@gmail.com |
| Telefone | (12) 9259-9387 |

**Leitura:** CNPJ ativo, CNAE coerente, porte/capital social compatíveis com operação hoteleira. Falta apenas o bureau pago correto do CNPJ `44.340.810/0001-62`.

## 5. Coerência operacional do pedido

✅ **Pedido coerente** com hotel/pousada:

- 40 fronhas classic.
- 20 lençóis casal sem elástico.
- 30 toalhas de rosto.
- 30 toalhas de banho.

Mix típico de reposição de enxoval de hospedagem. Não há personalização/bordado no pedido, o que reduz risco operacional.

## 6. Exposição real da Conamore

Cálculo para a condição indicada nas observações:

- **Total pedido:** R$ 4.146,00
- **Entrada 50%:** R$ 2.073,00
- **Exposição líquida:** R$ 2.073,00
- **Saldo 30/60:** 2x de R$ 1.036,50

**Classificação da exposição:** baixa.

## 7. Validação operacional online

✅ **Operação forte.** Evidências encontradas:

- **Website oficial:** `flordasaguas.net`, com página de hospedagem ativa.
- Website descreve suítes duplas, suítes triplas/quádruplas, suítes plus, suíte individual, chalés, casa e hospedagens de floresta.
- **Google Maps:** Espaço Flor Das Águas, categoria `Inn`, avaliação 4,7 estrelas, endereço em Rua Caminho do Ouro, Cunha-SP, website e telefone vinculados.
- **Plataformas de hospedagem em resultados públicos:** Booking.com, Hotels.com, Expedia, TripAdvisor, Trip.com, Kayak, Planet of Hotels.

Endereço do Google Maps aparece como número 4 enquanto proposta/Receita/Hotel Finder indicam número 5; é uma divergência pequena de georreferenciamento/localização, não um bloqueio, pois o nome, cidade, logradouro e operação batem.

---

## 8. Parecer final

**Etapa 0 — Lista Negra:** ✅ Cliente não consta.

**Parecer:** 🟡 **Aprovar com restrição operacional/documental controlada**.

**Nível de risco:** **moderado controlado**.

**Histórico Conamore:** cliente recorrente, 5 pedidos expedidos, total histórico R$ 22.677,90, ticket atual coerente e menor que o maior pedido anterior. Histórico positivo, porém majoritariamente PIX/cartão, não boleto recorrente.

**Score / Bureau:** bureau correto do Espaço Flor das Águas **não foi recebido**; o bureau anexado pertence à Sofia Homes e não deve ser usado. ReceitaWS confirma empresa ativa, EPP, capital social de R$ 640 mil, CNAE de hotéis.

**Coerência do pedido:** alta. Mix de enxoval e toalhas é compatível com operação hoteleira.

**Validação operacional online:** operação forte, com site próprio, Google Maps e presença em múltiplas plataformas de hospedagem.

**Condição recomendada:**

✅ Aprovar somente se cumpridos estes pontos:

1. **Corrigir/confirmar a condição no pedido**, porque o cabeçalho mostra `A DEFINIR`; usar no faturamento: **50% entrada + saldo 30/60 dias**.
2. **Entrada de 50% antes da liberação:** R$ 2.073,00.
3. **Saldo em 30/60 dias:** 2x de R$ 1.036,50.
4. **Opcional, para parecer final sem ressalva:** solicitar/usar bureau correto do CNPJ `44.340.810/0001-62`.

**Justificativa técnica objetiva:**

A aprovação com restrição é recomendada porque o cliente tem histórico interno positivo e recorrente, operação real validada e pedido coerente com o ticket histórico. A exposição líquida de R$ 2.073,00 é baixa e controlada pela entrada de 50%. A ressalva é documental: o bureau enviado é de outro CNPJ, e o pedido está com forma de pagamento `A DEFINIR` no cabeçalho. Portanto, liberar apenas com a condição correta registrada e entrada confirmada.
