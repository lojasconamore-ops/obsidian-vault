# Relatório Financeiro Diário — 2026-09-21

**Ao DigitalCEO**  
**Base BRT:** 21/09/2026, 08:03  
**Vendas do dia anterior:** 20/09/2026  
**Janela de vencimentos:** 21–27/09/2026

## Resumo financeiro

- **SQL Server — vendas confirmadas em 20/09:** **20 pedidos | R$ 9.347,64 | ticket médio R$ 467,38**. Status: **20 aprovados**.
- **Pagar.me — aprovações em 20/09:** **20 cobranças | R$ 9.347,63 | ticket médio R$ 467,38**.
- **Qualidade Pagar.me em 20/09:** **18 OK | R$ 8.264,30**; **0 suspeitas**; **2 revisar | R$ 1.083,33**.
- **Por loja em 20/09:** ACL **20 | R$ 9.347,63**; SSL/GCL/BRG **0**.
- **Por meio em 20/09:** cartão **18 | R$ 9.088,04**; PIX **2 | R$ 259,59**.
- **Conciliação SQL x Pagar.me:** diferença residual de **R$ 0,01**; bases conciliadas.
- **Janela Pagar.me de segunda-feira, 18–20/09:** **85 cobranças | R$ 191.606,83 | ticket médio R$ 2.254,20**. Qualidade: **79 OK | R$ 177.688,26**; **6 revisar | R$ 13.918,57**.
- **Por loja, 18–20/09:** SSL **27 | R$ 139.393,94**; GCL **11 | R$ 26.673,03**; ACL **47 | R$ 25.539,86**; BRG **0**.
- **Por meio, 18–20/09:** cartão **57 | R$ 122.830,35**; PIX **24 | R$ 63.669,25**; boleto **4 | R$ 5.107,23**.
- **Oracle/DEBX — PED em 20/09, separado:** status **A 22 | R$ 10.482,80**. Venda física `MOV_NATIND=100`: **0 movimentos**. PED não representa venda física.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual **não localizada no Vault nem no Google Drive**. **Total confirmado indisponível; não significa saldo zero.**
- **Contas a receber ACL — 21–27/09:** **539 títulos | R$ 60.635,44**.
- **Vencendo hoje, 21/09:** **258 títulos | R$ 25.520,95 — 42,09% da janela semanal**.
- Demais: 22/09 **77 | R$ 8.577,36**; 23/09 **62 | R$ 8.752,28**; 24/09 **67 | R$ 7.164,10**; 25/09 **69 | R$ 9.333,24**; 26/09 **3 | R$ 221,58**; 27/09 **3 | R$ 1.065,93**.
- **Pagar.me/ACL:** 2 aprovações do mesmo cliente em pedidos e valores diferentes, total **R$ 1.083,33**. Classificação: **REVISAR**, sem duplicidade confirmada.
- Dos **R$ 13.918,57** em revisão na janela de fim de semana, **R$ 12.835,24** são o grupo GCL de 18/09 já reportado; **R$ 1.083,33** são ocorrências novas de 20/09.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.935 | R$ 308.903,32**.
- **Índice bruto:** **23,86%** do saldo aberto ACL de **R$ 1.294.874,43**.
- **1–30 dias:** **230 | R$ 23.028,03**.
- **31–60 dias:** **3 | R$ 427,21**.
- **61–90 dias:** **17 | R$ 20.989,97**.
- **Acima de 90 dias:** **3.685 | R$ 264.458,11 — 85,61% do vencido**.
- **Vencidos em 20/09 ainda sem baixa:** **68 títulos | R$ 7.922,58**.
- Indicador operacional sujeito a baixas ainda não processadas; não equivale à inadimplência contábil definitiva.

## Recomendações

1. **Cobrança hoje:** atuar nos **R$ 23.028,03** vencidos até 30 dias, priorizando os **R$ 7.922,58** vencidos em 20/09.
2. **Monitorar vencimentos de hoje:** acompanhar cobrança/baixa dos **R$ 25.520,95**, maior concentração da semana.
3. **Revisar Pagar.me/ACL:** validar as 2 cobranças novas, total **R$ 1.083,33**, antes do fechamento da conciliação.
4. **Cobrar resolução do GCL:** manter pendente a validação dos **R$ 12.835,24** de 18/09 até confirmação operacional.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos; a base atual não foi localizada.
6. **Aging:** separar atraso real, baixa pendente e legado nos **R$ 264.458,11** acima de 90 dias.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; janela de aprovações 18–20/09/2026, com recorte de 20/09.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima 20/09 validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- `F_TITULOS`: recebíveis e aging somente da ACL; não consolida outros schemas.
- Vault e Google Drive: nenhuma base oficial atual de contas a pagar localizada nas buscas financeiras.
- Gmail/e-mail não utilizado por restrição do perfil.
