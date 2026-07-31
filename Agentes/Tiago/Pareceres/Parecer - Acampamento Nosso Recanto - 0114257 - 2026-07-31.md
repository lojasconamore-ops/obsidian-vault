# Parecer de Crédito — Acampamento Nosso Recanto — Pedido 0114257

**Data da análise:** 31/07/2026  
**Analista:** Tiago — Financeiro Conamore  
**Cliente:** ACAMPAMENTO NOSSO RECANTO LTDA  
**CNPJ:** 62.438.841/0006-47  
**ID_DEBX:** A3207  
**Pedido/orçamento:** 0114257  
**Representante:** Maria Fabiana Barreto Paez  
**Contato:** Marília — marilia.barbosa@nr.com.br — +55 12 99644-8161  

---

## Etapa 0 — Lista Negra Conamore

✅ **Cliente não localizado na Lista Negra Conamore** por CNPJ, razão social ou nome fantasia.

---

## Parecer

✅ **Aprovar** o faturamento conforme condição do PDF: **50% de entrada + saldo em 30/60 dias**.

**Nível de risco:** baixo a moderado.  
**Condição:** aprovada desde que a entrada esteja paga/compensada antes de produção/faturamento e o cadastro/forma de pagamento no pedido seja corrigido para refletir a condição real do PDF.

---

## Dados da proposta comercial

- **Total dos produtos:** R$ 20.365,32
- **Frete:** R$ 50,00
- **Total do pedido:** R$ 20.415,32
- **Entrada:** R$ 10.207,66
- **Saldo:** R$ 10.207,66 em 2 parcelas:
  - 30 dias: R$ 5.103,83
  - 60 dias: R$ 5.103,83
- **Exposição líquida Conamore:** R$ 10.207,66
- **Entrada percentual:** 50,00%
- **Validade:** 31/07/2026
- **Prazo operacional informado:** fabricação dos lençóis em 20 dias + 13 dias úteis para entrega.

### Mix de itens

Pedido de enxoval têxtil coerente com alojamento/acampamento/resort:
- lençol maca sem elástico 1,20 x 2,20 — 240 un.
- lençol maca com elástico 90 x 190 x 15 — 240 un.
- lençol solteiro sem elástico — 12 un.
- lençol solteiro com elástico — 12 un.
- fronha avulsa 50 x 70 — 252 un.

---

## Histórico interno Conamore / Hotel Finder

Consulta realizada no SQL Server Hotel Finder:

- Cadastro localizado em `conamore.Customers`:
  - ID_DEBX: A3207
  - CNPJ: 62438841000647
  - Status: 0
  - Razão/Nome fantasia no cadastro: Acampamento Nosso Recanto Ltda.
- `debx.PDV_Detalhes` retornou apenas o próprio orçamento **0114257**, status **Orçamento**, valor R$ 20.415,32.
- `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`: sem pedidos faturados/expedidos encontrados para o cliente.
- Consulta por raiz de CNPJ `62438841%`: apenas este cadastro foi localizado.
- Consulta de relacionados por mesmo endereço cadastral: nenhum relacionado relevante além do próprio cliente.

**Classificação interna:** cliente sem histórico faturado testado na Conamore; tratar como primeira compra para fins de comportamento de pagamento interno.

**Observação crítica:** o Hotel Finder mostra o pedido com `Condicao_Pgto = A DEFINIR` e `Tipo_Pagamento = PAGAMENTO INCREAZY PIX`, divergente do PDF. Para crédito, o PDF foi tratado como fonte comercial autoritativa. Recomenda-se corrigir o pedido/cadastro antes do faturamento para constar **50% entrada + saldo 30/60 dias**.

---

## Score / Bureau — Equifax | Boa Vista

Relatório de 31/07/2026 — 11:49:38.

- **Score Aprovação PJ:** 845 / 1000
- **Probabilidade de inadimplência:** 2,0%
- **Cadastro Positivo:** consumidor participante com informação
- **Pagamento pontual:** 100% nos 12 meses apresentados
- **Pagamento atrasado:** sem atrasos registrados nas faixas 6–15, 16–30, 31–60 e +60 dias
- **Pendências e restrições financeiras:** nada consta
- **Cheques sem fundos:** nada consta
- **Cheques sustados / devolvidos:** nada consta
- **Protestos:** nada consta
- **Situação CNPJ:** ativo
- **Fundação:** 12/05/2000
- **Atividade:** outros alojamentos não especificados — CNAE 5590-6/99
- **Faixa de funcionários:** 100 a 499

**Leitura de risco:** bureau forte, limpo e com bom histórico positivo. Não há restrição ativa. Para primeira compra interna, o bureau sustenta aprovação com entrada robusta.

---

## Validação cadastral / Receita WS

Consulta pública Receita WS:

- **Situação:** ATIVA
- **Tipo:** filial
- **Abertura:** 12/05/2000
- **Capital social:** R$ 436.000,00
- **Natureza jurídica:** Sociedade Simples Limitada
- **CNAE principal:** Outros alojamentos não especificados anteriormente
- **CNAE secundário:** Campings
- **Endereço:** Rodovia SP 50, s/n, km 146,5, Retiro, Sapucaí-Mirim/MG, CEP 37690-000

---

## Validação operacional online

🟢 **Operação forte.** Evidências encontradas:

- Site oficial: `nr.com.br`
- O site apresenta a marca NR, produtos/serviços educacionais, férias, formatura, viagens e resorts.
- Página oficial identifica **NR Resort — Sapucaí-Mirim**, com operação compatível com alojamento/acampamento.
- O rodapé do site informa **Acampamento Nosso Recanto Ltda. CNPJ 62.438.841/0001-32** e unidade NR Resort Sapucaí-Mirim com CEP 37690-000 e telefone.
- Busca pública retornou referências a NR, Acampamento Nosso Recanto em Sapucaí-Mirim/MG, Facebook e diretórios cadastrais.

---

## Coerência do pedido

✅ Pedido coerente.

O cliente atua como acampamento/resort/estrutura de hospedagem educacional. O mix de lençóis e fronhas é compatível com reposição/renovação de enxoval para alojamentos. Volume é relevante, mas não incompatível com a faixa operacional indicada pelo bureau (100 a 499 funcionários) e com a operação pública encontrada.

Não há personalização explícita; há fabricação de lençóis, o que recomenda entrada compensada antes da produção.

---

## Exposição e condição recomendada

- **Total financiado pela Conamore:** R$ 10.207,66
- **Entrada:** R$ 10.207,66 — 50%
- **Prazo financiado:** 30/60 dias

**Condição recomendada:**
1. Manter **50% de entrada**.
2. Liberar produção/faturamento somente após compensação da entrada.
3. Financiar saldo em **30/60 dias**.
4. Não aprovar boleto puro/sem entrada neste primeiro histórico interno.
5. Corrigir o pedido no DEBX/Hotel Finder para refletir a condição real antes do faturamento.

---

## Justificativa técnica objetiva

Apesar de não haver histórico faturado testado na Conamore, o conjunto de evidências é favorável: cliente antigo e ativo, bureau forte com score 845 e PD 2,0%, 100% de pontualidade, zero restrições/protestos/cheques, operação pública robusta e pedido coerente com atividade de alojamento/camping. A entrada de 50% reduz a exposição líquida para R$ 10.207,66, valor administrável frente ao porte e sinais externos.

**Parecer final:** ✅ **Aprovar com 50% de entrada + saldo 30/60 dias**, sem flexibilizar para boleto puro nesta primeira compra interna.
