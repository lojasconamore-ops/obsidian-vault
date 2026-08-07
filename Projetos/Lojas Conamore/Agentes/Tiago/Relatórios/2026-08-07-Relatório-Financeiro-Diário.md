# Relatório Financeiro Diário — 2026-08-07

**Ao DigitalCEO**  
**Base BRT:** 07/08/2026, 08:00  
**Vendas:** 06/08/2026  
**Janela de vencimentos:** 07/08 a 14/08/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas:** **39 pedidos | R$ 99.396,44 | ticket médio R$ 2.548,63**.
- **Variação diária:** **+R$ 17.749,37 | +21,7%** contra 05/08 (**R$ 81.647,07**).
- **Pedidos em expedição:** **3 | R$ 2.531,08** — fora do total aprovado.
- **Meios de pagamento:** PIX direto + Increazy PIX **R$ 55.001,73 (55,3%)**; Increazy total **R$ 44.757,75 (45,0%)**; cartões diretos **R$ 10.379,31 (10,4%)**; boleto direto/Increazy **R$ 3.529,60**. Categorias Increazy e meio podem se sobrepor; não somar os percentuais.
- **Origem:** sem origem informada **R$ 84.901,55 (18 pedidos)**; MAG **R$ 14.494,89 (21 pedidos)**.
- **Oracle/DEBX — PED status X:** **161 pedidos | R$ 16.934,40**. **Venda física:** **398 movimentos | R$ 16.692,74**. Bases separadas e não somadas ao SQL Server.
- **Pagar.me:** consolidado de 06/08 ainda não disponível às 08:00; conciliação de cartões/PIX do dia permanece pendente.

## Alertas de vencimentos

- **Contas a pagar em 07–14/08:** posição atual de contas a pagar **não disponível nas fontes acessíveis**. Não significa saldo zero.
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. **Exposição histórica: R$ 109.222,37** — não classificada como vencimento atual.
- **Recebíveis estimados em 07–14/08:** **R$ 0,00 / 0 parcelas** pelo proxy das condições de pagamento. É estimativa; a base não contém baixa financeira.
- **BLUEHAUS/Pagar.me:** seguem sem registro de resolução **2 PIX em revisão | R$ 5.281,68**.

## Inadimplência

- **Índice confirmado:** indisponível.
- **Proxy de parcelas estimadas vencidas em 30 dias:** **R$ 0,00 / 0 parcelas**. Não equivale a inadimplência, pois não há posição de títulos abertos nem liquidação.

## Recomendações

1. **Obter hoje a posição de contas a pagar 07–14/08**, com valor, vencimento e status de baixa.
2. **Concluir a conciliação Pagar.me de 06/08** assim que o consolidado for gerado.
3. **Resolver os 2 PIX BLUEHAUS de R$ 5.281,68** e registrar a conclusão.
4. **Confirmar a baixa da exposição histórica de R$ 109.222,37**; manter apenas títulos realmente abertos.
5. **Implantar aging diário de clientes:** saldo vencido, faixas 1–7/8–30/>30 dias, valor recuperado e índice de inadimplência.

## Fontes validadas

- SQL Server `hotel-finder`: sessão, schema e colunas validados; dados até 06/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; consultas somente leitura.
- Vault local: último consolidado Pagar.me disponível cobre aprovações de 05/08/2026.
