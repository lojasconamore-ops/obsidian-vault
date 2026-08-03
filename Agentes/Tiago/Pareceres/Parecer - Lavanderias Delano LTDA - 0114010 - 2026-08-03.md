# Parecer de Crédito — Lavanderias Delano LTDA — Pedido 0114010

**Data/Hora:** 2026-08-03 12:13 BRT  
**Cliente:** Lavanderias Delano LTDA  
**Nome fantasia:** Delano Lavanderia  
**CNPJ:** 19.661.494/0001-83  
**ID_DEBX:** 05814 / ID_DEBX2 105814  
**Pedido/orçamento:** 0114010  
**Vendedora:** Isabela Cristina Guerra Toffano  
**Fonte comercial:** PDF `114010 - Lavanderias Delano LTDA.pdf`  
**Fonte bureau:** PDF `ANÁLISE LAVANDERIAS DELANO.pdf` — Equifax / Boa Vista, 03/08/2026 09:34 BRT

---

## Etapa 0 — Lista Negra Conamore

**Resultado:** ✅ Cliente **não consta** na Lista Negra Conamore.

- CNPJ 19.661.494/0001-83: não encontrado
- Razão social Lavanderias Delano LTDA: não encontrada
- Nome fantasia Delano Lavanderia: não encontrado

---

## Parecer

**Parecer:** 🟡 **Aprovar com restrição / entrada mínima**  
**Nível de risco:** **Moderado controlado**

A venda é aceitável, mas o faturamento não deve sair em boleto puro nem com condição “A DEFINIR”. Recomendação: aprovar somente com entrada mínima antes do faturamento e prazo curto no saldo.

---

## 1. Dados do orçamento

**PDF comercial:**

| Campo | Informação |
|---|---:|
| Produtos | Toalhas banho/rosto/piso, lençol queen, fronhas |
| Total produtos | R$ 15.118,00 |
| Frete | R$ 50,00 |
| **Total pedido com frete** | **R$ 15.168,00** |
| Forma de pagamento no PDF | **A DEFINIR** |
| Observação | Oferta especial 7% de desconto para pagamento à vista, válida até 31/07 |
| Validade do orçamento | 05/08/2026 |

**Divergência interna:** Hotel Finder/PDV retornou o mesmo pedido 0114010 como orçamento, mas com `Valor_Total` R$ 14.110,40 + frete R$ 50,00, divergindo do PDF em R$ 1.057,60. Pela regra de precedência, o **PDF é a fonte comercial autoritativa** para valor e exposição. Antes de faturar, corrigir/confirmar o valor no DEBX/PDV.

---

## 2. Histórico interno Conamore — Hotel Finder / DEBX

**Consulta feita no SQL Server `hotel-finder`:**

### Cadastro
- Cliente encontrado em `conamore.Customers`.
- Razão social: Lavanderias Delano LTDA.
- CNPJ: 19.661.494/0001-83.
- Cidade/UF: Marechal Deodoro/AL.
- Endereço: Loteamento Novo Marechal, nº 0, Quadra 20 Lote 45, Centro, CEP 57160-000.
- Customer since: 27/07/2026.

### Pedidos / histórico
- Em `debx.PDV_Detalhes`, há **1 registro para Lavanderias Delano LTDA**, o próprio orçamento 0114010.
- Status: **Orçamento**.
- Condição: **A DEFINIR**.
- Não há linhas faturadas/expedidas para Lavanderias Delano em `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`.

**Classificação do histórico interno:** **sem histórico de pagamento testado / primeira compra efetiva.**

### Observação importante sobre ID_DEBX
A busca ampla por `ID_DEBX` retornou registros antigos de **P. Serviços Administrativos LTDA / Ponto do Câmbio** vinculados ao código `A5814/05814`, com vendas por cartão. Esses registros **não foram considerados como histórico da Lavanderias Delano**, pois a razão social, CNPJ e endereço são diferentes. Não há evidência de grupo econômico pelo mesmo endereço.

### Grupo econômico / mesmo endereço
Consulta de mesmo endereço retornou apenas a própria Lavanderias Delano LTDA. **Não foram encontrados relacionados internos no mesmo endereço.**

---

## 3. Score / Bureau — Equifax Boa Vista

**Relatório:** Equifax / Boa Vista, 03/08/2026 09:34 BRT.

| Indicador | Resultado | Leitura |
|---|---:|---|
| Score Aprovação PJ | **649** | Cautela / médio-baixo, limite superior da faixa 600–649 |
| Probabilidade de inadimplência | **8,0%** | Administrável, no limite da faixa aceitável |
| Cadastro Positivo | Participante com informação | Positivo |
| Pagamento pontual | 100 em todos os meses de ago/2025 a jul/2026 | Muito positivo |
| Pagamento atrasado | Sem registros | Positivo |
| Pendências/restrições | Nada consta | Positivo |
| Cheques sem fundos/sustados/devolvidos | Nada consta | Positivo |
| Protestos | Nada consta | Sem veto |
| Consultas | 1 consulta nos últimos 12 meses | Baixo volume |
| Data de fundação | 05/02/2014 | Empresa com ~12 anos |
| Situação CNPJ | Ativo | Regular |
| CNAE | Lavanderias — 9601-7/01 | Coerente com operação |

**Leitura técnica:** bureau limpo, sem protestos e sem restrições. O score 649 pede cautela, mas não há trava. Como não existe histórico interno de pagamento testado para este CNPJ, o risco deve ser controlado por entrada e prazo.

---

## 4. Coerência do pedido

**Coerência:** ✅ **Boa.**

O mix de produtos é coerente com lavanderia que atende enxoval/hotelaria:
- toalhas de banho, rosto e piso;
- lençóis queen;
- fronhas.

O pedido de R$ 15.168,00 não é pequeno, mas é compatível com reposição/abastecimento de lavanderia comercial. Não há personalização/bordado/silk no PDF, reduzindo risco operacional de produção especial.

---

## 5. Exposição real da Conamore

Base: total do PDF com frete = **R$ 15.168,00**.

| Condição | Entrada | Exposição líquida |
|---|---:|---:|
| Sem entrada / boleto puro | R$ 0,00 | **R$ 15.168,00** |
| 25% entrada | R$ 3.792,00 | **R$ 11.376,00** |
| 50% entrada | R$ 7.584,00 | **R$ 7.584,00** |
| À vista | R$ 15.168,00 | R$ 0,00 |

**Risco de exposição:** médio se 25% de entrada; confortável se 50% de entrada; inadequado se boleto puro/sem entrada.

---

## 6. Validação operacional online

### Evidências encontradas
- Receita WS / dados públicos: CNPJ ativo, fundado em 05/02/2014, CNAE lavanderias, endereço e telefone compatíveis com o PDF/bureau.
- Lavanderia.net.br: página pública de **Delano Lavanderia em Marechal Deodoro/AL**, com descrição de serviço de lavanderia.
- DuckDuckGo Lite: resultados para Solutudo, Lavanderia.net.br, CNPJá, Quero Brasil, Monitor CNPJ, DunsGuide e Instagram `@delanolavanderia_`.
- Google Maps: perfil “Delano Lavanderia” encontrado com **4,2 estrelas**, telefone +55 82 99942-9375, porém aparece como **“Permanently closed”** em endereço antigo/alternativo na Praia do Francês.

### Leitura
**Validação operacional:** 🟡 **Operação parcial / com ponto de atenção.**

A existência da empresa é consistente e o CNPJ está ativo, mas o Google Maps indica um perfil marcado como fechado, possivelmente de endereço antigo. Como o PDF, Receita e bureau indicam endereço no Loteamento Novo Marechal, recomenda-se confirmação comercial simples antes de liberar prazo: telefone/WhatsApp ativo, endereço de entrega e operação atual.

---

## 7. Condição recomendada

### Recomendação principal
✅ **Aprovar com 25% de entrada mínima + saldo em 30/60 dias**, desde que:
1. entrada de **R$ 3.792,00** esteja compensada antes do faturamento;
2. o pedido seja corrigido no DEBX/PDV para retirar “A DEFINIR” e refletir a condição aprovada;
3. seja confirmada a divergência de valor entre PDF e Hotel Finder;
4. comercial confirme que a operação atual está ativa no endereço/telefone informado.

### Condição mais segura, preferível se houver resistência operacional/online
✅ **50% de entrada + saldo 30/60 dias**.

### O que não aprovar
❌ **Não aprovar boleto puro / sem entrada** para este caso, salvo autorização explícita do Sérgio, pois é primeira compra efetiva e a condição está “A DEFINIR”.

---

## 8. Justificativa técnica objetiva

A Lavanderias Delano tem CNPJ ativo desde 2014, bureau limpo, Cadastro Positivo com informação, pagamento pontual 100/100 e ausência total de protestos, cheques e pendências. O pedido é coerente com a atividade de lavanderia. Porém, não há histórico interno de faturamento/pagamento testado na Conamore para este CNPJ: o único registro é o próprio orçamento 0114010, ainda em status de orçamento e com condição “A DEFINIR”. Além disso, a validação online é parcial porque o Google Maps encontrou perfil marcado como fechado, apesar de outros dados públicos indicarem operação ativa.

**Conclusão:** vender é razoável; financiar integralmente não. Aprovar com entrada mínima de 25% e prazo curto controla a exposição em R$ 11.376,00. Para maior segurança, 50% de entrada reduz a exposição para R$ 7.584,00.
