# Cruzamento pagamentos liberados ML × pedidos DEBX — 23/11/2026

**Data:** 23/11/2026 BRT
**Conta ML:** CONAMORE_HOTELARIA (user_id 3742322571)
**Fonte Oracle:** TEST_PED (sessão validada — `SELECT USER FROM DUAL`), somente leitura.

## Fonte e método

- **ML/Mercado Pago:** API — `GET /orders/search?order.status=paid` (75 pedidos pagos), pagamentos via `GET /v1/payments/{id}`. 50 pagamentos com `money_release_status=released` (liberados) e 25 pendentes. Agrupado por `pack_id` (pedido avulso usa o próprio `id`).
- **DEBX (Oracle):** `TEST_PED.F_PEDVENDA` (PDV_PEDREP, PDV_FRMPAG, PDV_VALTOT, PDV_CODREP, PDV_STATUS, PDV_OBSERV), `F_REPRES` (02000 = MERCADO LIVRE) e `TEST_MATRIZ.F_CDEMP` (CPF/CNPJ e identidade).
- **Chave prioritária:** `F_PEDVENDA.PDV_PEDREP` = Nº da venda/agrupador ML. Confirmada em registros reais — 29 dos 31 agrupadores liberados têm PED com PDV_PEDREP igual ao pack (o par Maria José usa os IDs em `PDV_OBSERV`).
- **Critérios:** chave externa exata → chave + valor → CPF/CNPJ + valor → CPF/CNPJ + cliente + data + valor. CPF/CNPJ do ML via `GET /orders/billing-info/MLB/{id}` comparado com `F_CDEMP.EMP_NUMCGC`.
- PED tratado como pedido do ERP, não automaticamente como venda física.

## Resultado

- **31 vendas ML liberadas** (50 sub-pedidos) no período de liberação 28/10 a 22/11/2026.
- **Bruto ML liberado:** R$ 11.413,60 · **Líquido liberado:** R$ 8.464,34.
- **23 CONCILIADO** (R$ 9.290,20): chave externa PDV_PEDREP + forma MP + valor + identidade fiscal todos conferem.
- **6 DIVERGÊNCIA** (R$ 1.915,00): chave externa e valor batem, mas o PED foi digitado com forma de pagamento errada (02 boleto / 03 PIX) em vez de MP. PEDs: 0125323, 0125324, 0125739, 0125744, 0126594 e 0125325.
- **2 CONCILIADO COM RESSALVA** (R$ 208,40, Maria José): packs 2000015659275625 (R$151,60) + 2000015659241785 (R$56,80) → PED 0126830 (R$208,40), IDs em `PDV_OBSERV`. PED de correção 0126879 (R$56,80) mantido como excedente — não tratado como duplicidade.
- **20 PEDs MP sem liberação correspondente** (19 PED EXCEDENTE + 1 REVISAR):
  - 11 PEDs de vendas ML pagas com **liberação ainda pendente** (esperado);
  - 5 PEDs de **teste** (TESTE/TESTE2/TESTEML/20000000000);
  - 2 PEDs de **vendas ML canceladas** (0131258, 0127953);
  - 1 PED de **correção Maria José** (0126879);
  - 1 **REVISAR**: PED 0127320 (R$143,20, CAMILA LADEIRA) sem PDV_PEDREP e sem venda ML liberada correspondente.

## Achados sensíveis

- **Digitação da forma de pagamento (outubro):** 6 PEDs antigos com chave externa e valor corretos, porém forma 02/03 em vez de MP. Recomenda-se corrigir para MP (ou explicar o tratamento contábil).
- **Maria José:** PED 0126830 reúne os dois packs; o PED 0126879 (R$56,80) é correção operacional. Confirmar com faturamento qual entrada gera NF, baixa e expedição.
- **PED 0127320** (CAMILA LADEIRA, R$143,20, forma MP, sem chave externa) merece revisão — não há venda ML liberada correspondente no período.

## Arquivo

`/home/sergio-ladeira/workspace/meli-integration/data/Cruzamento_Pagamentos_Liberados_ML_x_TEST_PED.xlsx`

Abas: **Detalhado** (51 linhas: 31 vendas ML + 20 PEDs excedentes), **Resumo** e **Metodologia**. IDs preservados como texto.
