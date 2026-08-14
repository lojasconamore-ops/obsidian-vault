# Relatório Financeiro Diário — 2026-08-14

**Ao DigitalCEO**  
**Base BRT:** 14/08/2026, 08:00  
**Vendas:** 13/08/2026  
**Janela de vencimentos:** 14/08 a 21/08/2026

## Resumo financeiro

- **Vendas aprovadas/SQL:** **35 pedidos | R$ 50.850,55 | ticket médio R$ 1.452,87**.
- **Variação diária:** **+R$ 4.868,04 | +10,59%** contra 12/08 (**R$ 45.982,51**).
- **Pagamento/SQL:** Increazy crédito **R$ 28.716,90**; boletos **R$ 6.611,80**; PIX **R$ 5.964,23**; cartões **R$ 7.395,39**; Increazy PIX **R$ 2.162,23**.
- **Origem/SQL:** sem origem **17 pedidos | R$ 37.490,93**; MAG **16 | R$ 9.836,22**; GER **2 | R$ 3.523,40**.
- **Pagar.me:** **43 aprovações | R$ 50.582,33 | ticket R$ 1.176,33**. Diferença para SQL: **R$ 268,22 (0,53%)**, por escopo/fonte.
- **Pagar.me por loja:** GCL **R$ 20.653,90**; SSL **R$ 17.995,78**; ACL **R$ 11.932,65**; BRG **R$ 0,00**.
- **Pagar.me por meio:** cartão **R$ 43.446,47**; PIX **R$ 7.081,34**; boleto **R$ 54,52**.
- **Oracle/DEBX, sem somar ao SQL:** PED status **X/expedido: 139 | R$ 14.580,42**; status **A: 16 | R$ 8.099,17**. Venda física (`MOV_NATIND=100`): **271 movimentos | R$ 13.030,57**.

## Alertas de vencimentos

- **Contas a pagar em 14–21/08:** base oficial atual **não localizada** no Vault nem no Google Drive. **Não significa saldo zero.**
- **Recebíveis estimados por condição de pagamento:** **0 parcelas | R$ 0,00**. Proxy sem títulos/baixas; não comprova ausência de recebíveis.
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. **Exposição histórica: R$ 109.222,37** — não classificada como vencimento atual.
- **Pagar.me para revisão:** **2 cobranças | R$ 1.004,96** do mesmo cliente, em pedidos e valores diferentes; **sem duplicidade exata confirmada**.

## Inadimplência

- **Índice confirmado:** indisponível.
- **Proxy estimado vencido em 30 dias:** **0 parcelas | R$ 0,00**; não equivale a inadimplência, pois não há base de títulos abertos e baixas.

## Recomendações

1. **Revisar hoje as 2 cobranças Pagar.me de R$ 1.004,96** e documentar como legítimas ou duplicidade.
2. **Obter a posição oficial de contas a pagar de 14–21/08**, com vencimento, valor e baixa.
3. **Confirmar a baixa da exposição histórica de R$ 109.222,37.**
4. **Implantar aging diário:** vencido, 1–7, 8–30 e >30 dias, com baixas e recuperação.

## Fontes validadas

- SQL Server `hotel-finder`: sessão, schema e colunas validados; atualizado até 13/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; leitura; PED e venda física separados.
- Pagar.me v5: consolidado gerado nesta execução, janela de aprovação 13/08/2026.
- Google Drive e Vault: nenhuma base oficial atual de contas a pagar localizada por metadados.
- Gmail/e-mail não utilizado por restrição do perfil.
