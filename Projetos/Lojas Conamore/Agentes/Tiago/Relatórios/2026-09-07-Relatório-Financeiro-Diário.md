# Relatório Financeiro Diário — 2026-09-07

**Ao DigitalCEO**  
**Base BRT:** 07/09/2026, 08:00  
**Vendas do dia anterior:** 06/09/2026  
**Janela financeira:** 07/09–14/09/2026

## Resumo financeiro

- **Pagar.me — 06/09:** **18 cobranças | R$ 11.223,42 | ticket médio R$ 623,52**.
- **Qualidade em 06/09:** **18 OK | 0 suspeitas | 0 revisar**.
- **Por loja:** ACL **18 | R$ 11.223,42**; SSL/GCL/BRG **0 | R$ 0,00**.
- **Por meio:** cartão **10 | R$ 8.149,49**; PIX **8 | R$ 3.073,93**.
- **SQL Server — vendas confirmadas em 06/09:** **17 pedidos | R$ 9.545,74 | ticket médio R$ 561,51**; origem MAG. Fonte principal atualizada até 06/09.
- **Diferença de escopo Pagar.me x SQL:** **R$ 1.677,68** a mais no Pagar.me. **Não somar as fontes.**
- **Oracle/DEBX — PED, separado:** status A **16 pedidos | R$ 9.448,44**; X/expedido **0**; venda física `MOV_NATIND=100` **0 movimentos** em 06/09.
- **Consolidado Pagar.me do fim de semana, 04–06/09:** **76 cobranças | R$ 96.419,31**; **72 OK | R$ 90.611,85**; **4 sinalizadas | R$ 5.807,46 — 6,02%**.

## Alertas de vencimentos

- **Contas a pagar 07/09–14/09:** base oficial atual **não localizada** no Google Drive após **6 buscas** nem no Vault. **Não significa saldo zero.**
- **Contas a receber ACL:** **977 títulos | R$ 126.959,29**.
- **Vencendo hoje, 07/09:** **290 títulos | R$ 37.387,40 — 29,45%** da janela.
- **Demais vencimentos:** 08/09 **99 | R$ 14.607,25**; 09/09 **86 | R$ 8.721,87**; 10/09 **103 | R$ 15.501,93**; 11/09 **91 | R$ 15.654,30**; 12/09 **3 | R$ 291,67**; 13/09 **0 | R$ 0,00**; 14/09 **305 | R$ 34.794,87**.

## Inadimplência

- **Títulos vencidos sem baixa:** **3.975 | R$ 324.355,08**.
- **Índice bruto:** **24,69%** do saldo aberto ACL de **R$ 1.313.914,17**.
- **1–30 dias:** **268 | R$ 37.390,64**.
- **31–60 dias:** **7 | R$ 697,74**.
- **61–90 dias:** **18 | R$ 22.604,37**.
- **Acima de 90 dias:** **3.682 | R$ 263.662,33 — 81,29%** do vencido.
- Indicador operacional sujeito a baixas ainda não processadas; não tratar como inadimplência contábil definitiva sem validação.

## Recomendações

1. **Cobrança:** priorizar **R$ 37.390,64** vencidos há até 30 dias e os **R$ 37.387,40** com vencimento hoje.
2. **Programação:** preparar acompanhamento de **R$ 34.794,87** para 14/09.
3. **Revisão Pagar.me:** validar as **4 cobranças sinalizadas de 04/09 | R$ 5.807,46**: duplicidade provável de **2 × R$ 1.296,10** e 2 PIX do mesmo cliente por **R$ 2.940,36 + R$ 274,90**. **Não estornar sem confirmar pedidos.**
4. **Aging:** revisar o bloco acima de 90 dias, **R$ 263.662,33**, separando atraso real, baixa pendente e legado.
5. **Caixa:** obter a posição oficial de contas a pagar antes de autorizar desembolsos dos próximos 7 dias.

## Fontes validadas

- Pagar.me v5: consolidado gerado nesta execução; janela 04–06/09 e recorte de 06/09.
- SQL Server `hotel-finder`: sessão, schema, colunas e data máxima validados; somente leitura.
- Oracle `conamore`, sessão `TEST_ACL`: sessão e colunas validadas; PED, venda física e `F_TITULOS` separados; somente leitura.
- Google Drive: conexão ativa; 6 buscas financeiras recentes, sem arquivo candidato.
- Vault: nenhuma base atual de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
