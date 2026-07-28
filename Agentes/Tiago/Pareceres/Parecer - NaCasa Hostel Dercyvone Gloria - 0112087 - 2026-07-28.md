# Parecer de Crédito — NaCasa Hostel / Dercyvone Gloria — Pedido 0112087

**Data da análise:** 28/07/2026 09:07 BRT  
**Analista:** Tiago — Financeiro Conamore  
**Fontes:** Proposta PDF `0112087`, Lista Negra Conamore, Hotel Finder SQL Server, ReceitaWS, website oficial, DuckDuckGo Lite, Google Maps.

---

## 1. Dados da proposta

| Campo | Informação |
|---|---|
| Pedido / orçamento | 0112087 |
| Emissão | 14/07/2026 |
| Validade | 31/07/2026 |
| Cliente / marca | NaCasa Hostel |
| Razão social / CNPJ | 56.344.973 DERCYVONE GLORIA DA SILVA GOES — 56.344.973/0001-00 |
| ID_DEBX | 36335 |
| Classe | Pousada |
| Endereço fiscal/entrega | Rua Rio Madeira, 6, Nossa Senhora das Graças, Manaus-AM, CEP 69053-030 |
| E-mail no PDF | nacasahostel@hotmail.com |
| Representante | Otavio Santos Viotto |
| Valor produtos | R$ 4.929,80 |
| Frete | R$ 300,00 |
| Total do pedido | R$ 5.229,80 |
| Forma de pagamento PDF | Entrada 50% + saldo 30/60/90 dias |
| Entrada indicada | PIX R$ 2.614,90 |
| Exposição líquida | R$ 2.614,90 |
| Parcelas saldo | 3x de aprox. R$ 871,63 / R$ 871,64 |

## 2. Etapa 0 — Lista Negra Conamore

✅ **Não consta** na Lista Negra Conamore consultada em `Agentes/Tiago/Lista Negra.md`.

Critérios verificados: CNPJ `56.344.973/0001-00`, razão social `DERCYVONE GLORIA DA SILVA GOES`, marca `NACASA HOSTEL` e similaridade nominal.

## 3. Histórico interno Conamore — Hotel Finder

Cadastro encontrado em `conamore.Customers`:

- **ID_DEBX:** 36335
- **Cliente:** NACASA HOSTEL
- **Razão social:** 56.344.973 DERCYVONE GLORIA DA SILVA GOES
- **Status:** 0
- **Cadastro desde:** 23/10/2024
- **Endereço:** Rua Rio Madeira, 6, Manaus-AM

Pedidos encontrados em `debx.PDV_Detalhes`:

| Pedido | Data orçamento | Status | Valor | Condição |
|---|---:|---|---:|---|
| 0112087 | 14/07/2026 | Orçamento | R$ 5.229,80 | A definir no PDV; PDF indica 50% + 30/60/90 |
| 0034134 | 30/04/2025 | Expedição | R$ 7.208,30 | Entrada 50% + saldo 30/60 dias |
| 0013474 | 24/10/2024 | Expedição | R$ 4.007,52 | À vista / PIX |
| 0013386 | 23/10/2024 | Expedição | R$ 4.263,60 | Cartão 6x |

**Resumo histórico:**

- **3 pedidos anteriores expedidos/faturados**.
- **Total histórico expedido:** R$ 15.479,42.
- **Ticket médio histórico:** R$ 5.159,81.
- **Pedido atual:** R$ 5.229,80, praticamente igual ao ticket médio histórico (**101,36% do ticket médio**) e menor que o último boleto com entrada (**72,55% do pedido 0034134**).
- Condição a prazo já testada em 2025: **50% de entrada + 30/60 dias**, com valor maior que o atual.
- Não foi localizado outro cliente no mesmo endereço em `conamore.Customers`; sem evidência de grupo econômico relacionado no Hotel Finder.

**Classificação interna:** **Classe B+ / A- operacional** — histórico positivo e recorrente, sem sinal interno de bloqueio ou desgaste na fonte consultada; pagamento a prazo já praticado com entrada de 50%.

## 4. Score / Bureau / Dados cadastrais públicos

**Bureau pago:** não foi anexado relatório Equifax/Serasa/Boa Vista nesta análise. Portanto, não afirmo score nem ausência formal de protestos/restrições de bureau pago.

Fallback ReceitaWS para CNPJ `56.344.973/0001-00`:

| Campo | Resultado |
|---|---|
| Situação cadastral | ATIVA |
| Abertura | 07/08/2024 |
| Idade da empresa | Aproximadamente 1 ano e 11 meses na data da análise |
| Porte | Micro Empresa |
| Natureza jurídica | Empresário Individual |
| Capital social | R$ 5.000,00 |
| CNAE principal | Pensões / alojamento |
| Endereço | Avenida/Rua Rio Madeira, 6, Nossa Senhora das Graças, Manaus-AM |
| Telefone Receita | (92) 9174-8417 |
| E-mail Receita | dercygloria@gmail.com |

**Leitura:** empresa ativa, CNAE coerente com hospedagem, mas CNPJ ainda novo e capital social baixo. Esse ponto pediria cautela em primeira compra; neste caso é mitigado pelo histórico interno Conamore e pela entrada de 50%.

## 5. Coerência operacional do pedido

✅ **Pedido coerente** com hostel/pousada:

- Lençóis casal e solteiro em percal 200 fios.
- Fronhas avulsas.
- Kits de amenities shampoo/condicionador.
- Bordado/silk em fronhas e lençóis.

A personalização aumenta o risco operacional porque a mercadoria perde liquidez para revenda, mas a condição de **50% de entrada** é adequada para cobrir esse risco.

## 6. Exposição real da Conamore

Cálculo:

- **Total pedido:** R$ 5.229,80
- **Entrada:** R$ 2.614,90
- **Exposição líquida:** R$ 2.614,90
- **Saldo:** 30/60/90 dias, aprox. 3x de R$ 871,63/R$ 871,64

**Classificação da exposição:** baixa e controlada.

## 7. Validação operacional online

✅ **Operação forte.** Evidências encontradas:

- **Website oficial:** `nacasahostel.com`, com descrição da operação, 6 quartos, 6 banheiros, localização em Av./Rua Rio Madeira, Casa 6, Quadra 37, Vieiralves / Nossa Senhora das Graças, Manaus-AM.
- **Motor de reservas oficial:** `booking.hqbeds.com.br/nacasa/` vinculado ao site.
- **Google Maps:** ficha `Na Casa Hostel`, categoria Hotel, endereço em Av. Rio Madeira, Casa 6, telefone +55 92 99210-2929, website `nacasahostel.com`, fotos, preço e comparador com Booking.com.
- **Plataformas de hospedagem em resultados públicos:** Booking.com, Hostelworld, Trip.com, Planet of Hotels, Agoda.

Endereço e atividade são coerentes com o CNPJ, PDF e proposta.

---

## Parecer final

**Etapa 0 — Lista Negra:** ✅ Cliente não consta na Lista Negra Conamore.

**Parecer:** ✅ **Aprovar faturamento conforme proposta**.

**Nível de risco:** **baixo a moderado controlado**.

**Histórico Conamore:** cliente recorrente, 3 pedidos anteriores expedidos, total histórico R$ 15.479,42, ticket médio R$ 5.159,81. Pedido atual está dentro do padrão histórico e abaixo do último pedido a prazo com entrada.

**Score / Bureau:** bureau pago não anexado; ReceitaWS confirma CNPJ ativo, CNAE de alojamento e dados coerentes. Empresa nova e ME exigem cautela, mas o histórico interno e a entrada reduzem o risco.

**Coerência do pedido:** alta. Mix de enxoval + amenities + bordado é adequado para hostel/pousada.

**Validação operacional online:** operação forte — site próprio, Google Maps, motor de reserva e presença em plataformas de hospedagem.

**Condição recomendada:**

✅ **Manter exatamente a condição da proposta:**

- **50% de entrada via PIX:** R$ 2.614,90 antes de iniciar/seguir produção personalizada.
- **Saldo 30/60/90 dias:** R$ 2.614,90 em 3 parcelas de aproximadamente R$ 871,63/R$ 871,64.
- Não liberar produção/faturamento sem confirmação da entrada, por haver itens personalizados.

**Justificativa técnica objetiva:**

A aprovação é adequada porque o cliente é recorrente, tem três pedidos anteriores expedidos, já operou condição a prazo com 50% de entrada em pedido maior, o valor atual está alinhado ao ticket histórico e a exposição líquida é baixa. A empresa é operacionalmente validada online e o pedido é coerente com hostel/pousada. O único ponto de cautela é o CNPJ relativamente novo e sem bureau pago anexado; por isso a entrada de 50% deve ser mantida como trava obrigatória.
