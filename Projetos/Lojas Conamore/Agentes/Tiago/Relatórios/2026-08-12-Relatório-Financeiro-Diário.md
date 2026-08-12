# Relatório Financeiro Diário — 2026-08-12

**Ao DigitalCEO**  
**Base BRT:** 12/08/2026, 08:01  
**Vendas:** 11/08/2026  
**Janela de vencimentos:** 12/08 a 19/08/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas:** **30 pedidos | R$ 63.176,65 | ticket médio R$ 2.105,89**.
- **Pagamento/SQL:** Increazy crédito **R$ 23.426,90**; boleto a prazo **R$ 20.415,32**; Increazy PIX **R$ 9.939,93**; demais cartões/PIX **R$ 9.394,50**.
- **Origem/SQL:** sem origem informada **16 pedidos | R$ 53.782,15**; MAG **14 pedidos | R$ 9.394,50**.
- **Pagar.me:** **39 cobranças | R$ 48.792,39 | ticket médio R$ 1.251,09**; **39 OK, 0 suspeitas, 0 revisar**.
- **Pagar.me por loja:** SSL **11 | R$ 29.439,25**; GCL **8 | R$ 11.001,35**; ACL **20 | R$ 8.351,79**; BRG **0 | R$ 0,00**.
- **Pagar.me por meio:** cartão **26 | R$ 34.504,92**; PIX **13 | R$ 14.287,47**.
- **Oracle/DEBX — PED status X:** **99 pedidos | R$ 22.492,49**. **Venda física (`MOV_NATIND=100`): 222 movimentos | R$ 14.992,69**. Bases separadas; não somadas ao SQL/Pagar.me.

## Alertas de vencimentos

- **Contas a pagar em 12–19/08:** base oficial atual **não localizada** nos arquivos locais/Vault; consulta ao Drive indisponível neste perfil. **Não significa saldo zero.**
- **Recebíveis por proxy de condições de pagamento:** **0 parcelas | R$ 0,00**. O proxy não contém baixas e não comprova ausência de recebíveis.
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. **Exposição histórica: R$ 109.222,37** — não classificada como vencimento atual.
- **Risco Pagar.me anterior (07/08):** excesso potencial em duplicidades **R$ 4.035,90**; outras cobranças para revisão **R$ 8.863,85**. Sem evidência atual de resolução.

## Inadimplência

- **Índice confirmado:** indisponível.
- **Proxy estimado vencido em 30 dias:** **0 parcelas | R$ 0,00**; não equivale a inadimplência por ausência de títulos abertos e baixas.

## Recomendações

1. **Obter hoje a posição oficial de contas a pagar 12–19/08**, com vencimento, valor e baixa.
2. **Confirmar a baixa da exposição histórica de R$ 109.222,37.**
3. **Encerrar a revisão Pagar.me de 07/08:** risco total sinalizado **R$ 12.899,75**.
4. **Implantar aging diário:** saldo vencido, faixas 1–7/8–30/>30 dias, baixas e recuperação.

## Fontes validadas

- SQL Server `hotel-finder`: sessão, schema e colunas validados; dados atualizados até 11/08/2026.
- Pagar.me v5: consolidado gerado nesta execução para aprovações de 11/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; somente leitura; PED e venda física separados.
- Arquivos locais/Vault: nenhuma base oficial atual de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
