# Parecer de Crédito — Clean Studios — Pedido Potencial R$ 100 mil

**Data da análise:** 28/07/2026 19:22 BRT  
**Analista:** Tiago — Financeiro Conamore  
**Fontes:** Bureau Equifax/Boa Vista `ANÁLISE CLEAN STUDIO.pdf`, Lista Negra Conamore, Hotel Finder SQL Server, ReceitaWS, Google Maps e website oficial.

---

## 1. Identificação

| Campo | Informação |
|---|---|
| Razão social | CLEAN STUDIOS SERVICOS DE LIMPEZA LTDA |
| Nome fantasia | Clean Studios |
| CNPJ | 52.167.941/0001-18 |
| ID_DEBX atual | A2502 |
| ID_DEBX histórico em PDV | 02502 / A2502 — atenção à migração de código |
| Sócio-administrador | Guilherme Bausas Fuertes |
| Atividade principal | Limpeza em prédios e domicílios |
| Atividades secundárias | Instalação/manutenção de ar-condicionado, comércio varejista de cama/mesa/banho, lavanderias |
| Pedido pretendido | Aproximadamente R$ 100.000,00 |
| Proposta comercial | Não anexada nesta análise |

---

## 2. Etapa 0 — Lista Negra Conamore

✅ **Não consta** na Lista Negra Conamore consultada.

Critérios considerados: CNPJ `52.167.941/0001-18`, razão social `CLEAN STUDIOS SERVICOS DE LIMPEZA LTDA`, nome fantasia `CLEAN STUDIOS` e similaridade nominal.

---

## 3. Histórico interno Conamore — Hotel Finder

Cliente localizado em `conamore.Customers`:

- **ID_DEBX atual:** A2502
- **CNPJ:** 52.167.941/0001-18
- **Endereço no Hotel Finder/bureau:** Rua Pe. Jerônimo Vernin, 204, São Paulo-SP
- **Status:** 0

Busca por mesmo endereço retornou somente o próprio cliente; sem grupo econômico interno localizado no mesmo endereço.

### Pedidos expedidos/faturados localizados

Foram localizados **21 pedidos expedidos** para Clean Studios, considerando histórico por razão social e migração de ID_DEBX `02502` → `A2502`.

| Indicador | Valor |
|---|---:|
| Pedidos expedidos | 21 |
| Total histórico expedido | R$ 185.405,35 |
| Ticket médio histórico | R$ 8.828,83 |
| Maior pedido histórico | R$ 18.342,00 |
| Condições praticadas | Majoritariamente PIX/à vista e cartão 6x |
| Boleto/faturado relevante | Não localizado como prática recorrente |
| Pedido cancelado relevante | R$ 26.250,00 — 28/04/2026, cancelado, condição à vista |

### Leitura do histórico

O histórico é **forte em recorrência e volume acumulado**, mas o comportamento financeiro testado é essencialmente **à vista/cartão**, não crédito faturado relevante. O pedido pretendido de R$ 100 mil é muito acima do padrão histórico:

- **R$ 100 mil = 11,33x o ticket médio histórico**.
- **R$ 100 mil = 5,45x o maior pedido já expedido**.

**Classificação interna:** Classe B em recorrência/relacionamento, mas **não testado para limite de crédito alto**.

---

## 4. Score / Bureau — Equifax / Boa Vista

Relatório emitido em 28/07/2026 16:50:49.

| Campo | Resultado |
|---|---|
| Score | 628 |
| Probabilidade de inadimplência | 13,0% |
| Status do consumidor | Sem histórico de crédito |
| Cadastro Positivo | Não considerado / sem histórico |
| Pagamento pontual | Sem dados |
| Pagamento atrasado | Sem dados |
| Pendências e restrições financeiras | Nada consta |
| Cheques sem fundos | Nada consta |
| Cheques sustados motivo 21 | Nada consta |
| Cheques devolvidos informados pelo usuário | Nada consta |
| Protestos | Nada consta |
| Consultas | 5 no período 01/07/2025 a 01/07/2026 |
| CNPJ no bureau | Ativo desde 13/09/2023 |
| Faixa de funcionários | Sem informação suficiente |

### Leitura do bureau

O bureau é **limpo**, sem protestos, cheques ou restrições — não há veto externo. Porém, score 628 com PD 13% e consumidor sem histórico de crédito indica **risco elevado por ausência de histórico financeiro formal**.

Esse é um caso de score sem histórico, mas diferente de pedidos pequenos recorrentes: o valor pretendido de R$ 100 mil eleva muito a exposição e impede aprovação liberal.

---

## 5. Dados cadastrais públicos — ReceitaWS

| Campo | Resultado |
|---|---|
| Situação | ATIVA |
| Abertura | 13/09/2023 |
| Idade | Aproximadamente 2 anos e 10 meses |
| Porte | Empresa de Pequeno Porte |
| Capital social | R$ 1.000,00 |
| Natureza jurídica | Sociedade Empresária Limitada |
| Atividade principal | Limpeza em prédios e domicílios |
| Atividades secundárias relevantes | Comércio varejista de artigos de cama, mesa e banho; lavanderias |
| E-mail | guilherme@cleanstudios.com.br |
| Telefone | (11) 9110-9902 |
| Endereço Receita / site / Google | Rua Mairinque, 83, Vila Clementino, São Paulo-SP |

**Observação:** bureau e Hotel Finder indicam endereço antigo/diferente, Rua Pe. Jerônimo Vernin, 204. Receita, website e Google Maps indicam Rua Mairinque, 83. Recomendo atualizar cadastro antes de eventual faturamento.

---

## 6. Coerência operacional do pedido potencial

A Clean Studios atua com limpeza, manutenção, lavanderia e gestão de enxoval para short stay em São Paulo. O website informa:

- Especialização no mercado de short stay em São Paulo.
- Gestão de enxoval.
- Gestão de lavanderia.
- Reposição de amenities.
- Atendimento a múltiplos studios.
- Faixas de operação no formulário: 10–50, 51–150, 151–300 e mais de 500 unidades.

**Leitura:** um pedido de enxoval alto pode fazer sentido se estiver vinculado a expansão relevante ou contrato de grande volume. Porém, sem proposta detalhada de itens, unidade atendida, cronograma e condição, o salto para R$ 100 mil deve ser tratado como **risco de limite**, não como simples recompra.

---

## 7. Exposição real simulada — pedido R$ 100.000,00

| Condição | Entrada | Exposição líquida |
|---|---:|---:|
| Sem entrada | R$ 0,00 | R$ 100.000,00 |
| 25% entrada | R$ 25.000,00 | R$ 75.000,00 |
| 30% entrada | R$ 30.000,00 | R$ 70.000,00 |
| 50% entrada | R$ 50.000,00 | R$ 50.000,00 |
| 70% entrada | R$ 70.000,00 | R$ 30.000,00 |
| 80% entrada | R$ 80.000,00 | R$ 20.000,00 |

Mesmo com 50% de entrada, a exposição de R$ 50 mil ainda seria **2,7x o maior pedido histórico**. Com 25% de entrada, a exposição de R$ 75 mil é alta demais para o histórico e para o bureau.

---

## 8. Validação operacional online

✅ **Operação online forte.** Evidências encontradas:

- Website oficial ativo: `cleanstudios.com.br`.
- Google Maps: Clean Studios Serviços de Limpeza, avaliação 4,6, categoria cleaners, endereço Rua Mairinque, 83, São Paulo-SP, telefone e website.
- Website declara especialização em short stay, limpeza pós-checkout, gestão de lavanderia/enxoval e suporte operacional.
- Website exibe avaliações de clientes e menciona Airbnb/locação por temporada.

**Classificação:** operação forte, com coerência entre atividade e provável compra de enxoval.

---

## 9. Parecer final

**Etapa 0 — Lista Negra:** ✅ Não consta.

**Parecer:** 🟡 **Não aprovar R$ 100 mil faturado nos moldes comuns. Aprovar somente com forte restrição, entrada alta e/ou fracionamento.**

**Nível de risco:** **alto para exposição de R$ 100 mil; moderado se a exposição for limitada a até R$ 20–30 mil.**

**Histórico Conamore:** recorrente e positivo em volume acumulado, com 21 pedidos expedidos e R$ 185,4 mil de histórico. Porém, maior pedido foi R$ 18,3 mil e o cliente não tem histórico relevante de faturamento/boleto alto. O pedido pretendido é 5,45x o maior pedido anterior.

**Score / Bureau:** score 628, PD 13%, sem histórico de crédito, mas limpo: zero protestos, zero cheques, zero restrições. Bureau não reprova por restrição, mas não sustenta limite alto.

**Coerência do pedido:** operacionalmente plausível pelo segmento short stay/limpeza/lavanderia/enxoval, mas precisa de proposta detalhada e justificativa de expansão.

**Validação operacional online:** forte — site, Google Maps e operação coerente.

### Condição recomendada

**Não recomendo aprovar boleto/faturado de R$ 100 mil com 25% de entrada ou sem entrada.**

Condições aceitáveis:

1. **Mais segura — recomendada:** fracionar o pedido em lotes de até **R$ 25–30 mil**, liberando novos lotes somente após pagamento/compensação do lote anterior.
2. **Se for pedido único de R$ 100 mil:** exigir **mínimo 70% a 80% de entrada**:
   - 70% entrada: R$ 70.000,00; exposição R$ 30.000,00.
   - 80% entrada: R$ 80.000,00; exposição R$ 20.000,00.
3. Saldo máximo em **30/60 dias**, sem alongar para 90 dias neste primeiro ticket alto.
4. Se houver personalização/bordado ou produção especial: **80% de entrada** ou pagamento integral antes da produção.
5. Atualizar cadastro/endereço antes de faturar e anexar proposta detalhada com itens, finalidade e cronograma.

### Justificativa técnica objetiva

A Clean Studios é cliente real, recorrente e com histórico acumulado relevante na Conamore, mas o pedido pretendido de R$ 100 mil é muito acima do comportamento histórico e o bureau não dá suporte para limite alto: score 628, PD 13%, sem histórico de crédito e capital social de R$ 1 mil. Como não há restrições/protestos e a operação é forte, não é caso de reprovação comercial total; é caso de **controle de exposição**. A Conamore deve vender, mas não financiar R$ 70–100 mil nesse primeiro salto de ticket.
