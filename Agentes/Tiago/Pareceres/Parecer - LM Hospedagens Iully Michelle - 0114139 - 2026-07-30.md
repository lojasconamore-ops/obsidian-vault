# Parecer de Crédito — LM Hospedagens / Iully Michelle — Pedido 0114139

**Data:** 30/07/2026  
**Cliente:** LM Hospedagens  
**Razão/CNPJ:** 51.991.041 IULLY MICHELLE DA CUNHA RABELLO — 51.991.041/0001-28  
**ID_DEBX:** A6876 / ID_DEBX2 6876  
**Vendedor:** Carlos Manoel da Silva  
**Documentos analisados:** Proposta Comercial 0114139 + Relatório Equifax/Boa Vista de 29/07/2026

## Etapa 0 — Lista Negra

✅ **Não localizada na Lista Negra Conamore** por CNPJ, razão social ou nome fantasia.

## Parecer

🟡 **Aprovar com restrição / ajuste de condição**

**Nível de risco:** moderado-alto controlável

## Dados do pedido

- **Pedido / orçamento:** 0114139
- **Emissão:** 28/07/2026
- **Validade:** 30/07/2026
- **Total sem desconto:** R$ 107.960,00
- **Desconto:** R$ 12.708,00
- **Total com desconto / pedido:** R$ 95.302,00, incluindo frete de R$ 50,00
- **Condição impressa no PDF:** entrada R$ 31.767,33 + boleto 30 dias R$ 31.767,33 + boleto 60 dias R$ 31.767,33
- **Exposição pela condição impressa:** R$ 63.534,67, equivalente a 66,67% do pedido
- **Observação importante:** o PDF também traz texto padrão citando “50% à vista e 50% para 30/60 dias”, mas a grade de parcelas impressa está em 1/3 de entrada + 30/60. Antes do faturamento, corrigir a proposta/condição para eliminar divergência.

## Mix e coerência operacional

Pedido composto por enxoval e personalização:

- 1.400 fronhas
- 100 lençóis casal
- 500 lençóis queen
- 100 lençóis king
- 400 toalhas de banho
- 200 toalhas de rosto
- 200 toalhas de piso
- 2.900 personalizações bordado/silk — R$ 23.200,00

**Coerência:** o mix é compatível com operação de hospedagem / administração de flats, principalmente pela composição de lençóis, fronhas e toalhas.  
**Atenção:** há volume alto e personalização relevante, aumentando risco operacional se houver inadimplência ou cancelamento após produção.

## Histórico Conamore

Consulta ao Hotel Finder / SQL Server:

- Cadastro encontrado em `conamore.Customers`:
  - ID_DEBX A6876
  - Nome: LM HOSPEDAGENS
  - CNPJ: 51.991.041/0001-28
  - Status: ativo
  - Endereço cadastral interno: Avenida Sapé, 737, Manaíra, João Pessoa/PB
- `debx.PDV_Detalhes`: apenas o orçamento 0114139, status **Orçamento**, valor R$ 95.302,00.
- `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`: sem histórico faturado encontrado.
- Consulta por mesmo endereço do CNPJ-alvo: não revelou outro cliente relacionado no mesmo endereço interno.

**Classificação interna:** sem histórico de compras faturadas — tratar como **primeira compra / crédito não testado**.

## Score / Bureau

Relatório Equifax / Boa Vista de 29/07/2026:

- **Score PJ:** 650
- **Probabilidade de inadimplência:** 8,0%
- **Status do consumidor:** consumidor sem histórico de crédito
- **CNPJ:** ativo
- **Data de fundação:** 29/08/2023
- **Ramo:** Outros alojamentos não especificados — CNAE 5590-6/99
- **Natureza:** Empresário individual
- **Pendências/restrições financeiras:** nada consta
- **Cheques sem fundos/devolvidos/sustados:** nada consta
- **Protestos:** nada consta
- **Cadastro positivo:** sem histórico efetivo no relatório

**Interpretação:** bureau limpo e aceitável, porém com histórico externo raso. O score 650 / PD 8% é administrável, mas não compensa sozinho o fato de ser primeira compra de R$ 95 mil com personalização.

## Receita / dados públicos

Consulta Receita WS:

- Situação: ATIVA
- Abertura: 29/08/2023
- Porte: Micro Empresa
- Capital social: R$ 0,00
- Atividade principal: outros alojamentos não especificados anteriormente
- Atividade secundária: pensões / alojamento
- Endereço Receita: Rua Padre Meira, 35, Sala 1102, Centro, João Pessoa/PB
- E-mail: lmhospedagens@gmail.com
- Telefone: (83) 9115-5959

## Validação operacional online

Evidências encontradas:

- Site próprio: `lmhospedagensjp.com.br`, com motor de reserva, múltiplos flats/unidades anunciados, preços por diária e detalhes de hospedagem.
- Site alternativo: `lmhospedagens.com`, com indicação de flats de luxo em João Pessoa, Cabo Branco, Manaíra e Tambaú.
- Google Maps: resultado para “LM Serviços & Hospedagem”, 5,0 estrelas, escritório em Manaíra/João Pessoa e telefone local.
- Resultados em plataformas de reserva: Traveloka, Hotels.com/Hoteis.com, Only-Apartments e outros resultados para “LM HOSPEDAGENS - GET ONE”.

**Classificação:** 🟢 operação forte. A operação parece real e coerente com o pedido.

## Condição recomendada

**Não recomendo faturar na condição impressa de 1/3 entrada + 30/60** para primeira compra desse tamanho.

Condição recomendada:

1. **Entrada mínima de 50% antes de iniciar produção/personalização:** R$ 47.651,00
2. **Saldo em 30/60 dias:** 2 boletos de R$ 23.825,50
3. **Sem ampliação para 90 dias neste primeiro pedido.**
4. **Produção personalizada liberada somente após compensação da entrada.**
5. Se houver resistência à entrada de 50%, alternativa conservadora: fracionar o pedido em lotes, liberando novo lote após pagamento/compensação do lote anterior.

## Justificativa técnica objetiva

A operação é real, o CNPJ está ativo, o bureau está limpo e o pedido é coerente com hospedagem. Porém, a Conamore ainda não tem histórico faturado com esse CNPJ, o ticket é alto para primeira compra e há R$ 23.200,00 em personalização, que aumenta risco operacional. A aprovação é possível, mas a exposição precisa ser reduzida.

**Conclusão:** 🟡 aprovar com restrição, condicionando faturamento a **50% de entrada comprovada + saldo 30/60**, com correção da proposta antes de faturar.
