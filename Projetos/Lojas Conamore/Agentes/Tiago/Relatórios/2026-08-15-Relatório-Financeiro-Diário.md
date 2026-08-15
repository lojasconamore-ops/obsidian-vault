# Relatório Financeiro Diário — 2026-08-15

**Ao DigitalCEO**  
**Base BRT:** 15/08/2026, 08:00  
**Vendas:** 14/08/2026  
**Janela de vencimentos:** 15/08 a 22/08/2026

## Resumo financeiro

- **Vendas aprovadas/SQL:** **43 pedidos | R$ 58.164,42 | ticket médio R$ 1.352,66**.
- **Variação diária:** **+R$ 7.313,87 | +14,38%** contra 13/08 (**R$ 50.850,55**).
- **Pagamento/SQL:** Increazy **R$ 23.216,98**; cartões **R$ 17.966,82**; boletos **R$ 14.834,19**; PIX direto **R$ 2.146,43**.
- **Origem/SQL:** sem origem **14 pedidos | R$ 34.619,68**; MAG **27 | R$ 21.175,74**; GER **2 | R$ 2.369,00**.
- **Pagar.me:** **34 aprovações | R$ 41.304,83 | ticket R$ 1.214,85**. Diferença para SQL: **R$ 16.859,59 | 28,99%**, por escopo/fonte.
- **Pagar.me por loja:** GCL **R$ 18.365,74**; ACL **R$ 11.565,65**; SSL **R$ 11.373,44**; BRG **R$ 0,00**.
- **Pagar.me por meio:** PIX **R$ 22.772,46**; cartão **R$ 18.532,37**.
- **Pagar.me — qualidade:** **34 OK | 0 suspeitas | 0 revisar**.
- **Oracle/DEBX, sem somar ao SQL:** PED status **X/expedido: 128 | R$ 18.781,31**; status **A: 19 | R$ 10.329,87**. Venda física (`MOV_NATIND=100`): **252 movimentos | R$ 16.696,66**.

## Alertas de vencimentos

- **Contas a pagar em 15–22/08:** base oficial atual **não localizada** no Vault nem no Google Drive. **Não significa saldo zero.**
- **Recebíveis estimados por condição de pagamento:** **0 parcelas | R$ 0,00**. Proxy sem títulos/baixas; não comprova ausência de recebíveis.
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. **Exposição histórica: R$ 109.222,37** — não classificada como vencimento atual.
- **Revisão Pagar.me anterior sem resolução localizada:** **2 cobranças | R$ 1.004,96**. A execução atual está limpa.

## Inadimplência

- **Índice confirmado:** indisponível.
- **Proxy estimado vencido em 30 dias:** **0 parcelas | R$ 0,00**; não equivale a inadimplência, pois não há base de títulos abertos e baixas.

## Recomendações

1. **Obter hoje a posição oficial de contas a pagar de 15–22/08**, com vencimento, valor e baixa.
2. **Conciliar a diferença SQL × Pagar.me de R$ 16.859,59**, separando boleto, canais fora do gateway e divergências de período.
3. **Confirmar a baixa da exposição histórica de R$ 109.222,37** e encerrar a revisão anterior de **R$ 1.004,96**.
4. **Implantar aging diário:** vencido, 1–7, 8–30 e >30 dias, com saldo aberto, baixas e recuperação.

## Fontes validadas

- SQL Server `hotel-finder`: sessão, schema e colunas validados; atualizado até 14/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; leitura; PED e venda física separados.
- Pagar.me v5: consolidado gerado nesta execução, janela de aprovação 14/08/2026.
- Google Drive e Vault: nenhuma base oficial atual de contas a pagar localizada por metadados.
- Gmail/e-mail não utilizado por restrição do perfil.
