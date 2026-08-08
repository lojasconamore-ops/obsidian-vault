# Relatório Financeiro Diário — 2026-08-08

**Ao DigitalCEO**  
**Base BRT:** 08/08/2026, 08:00  
**Vendas:** 07/08/2026  
**Janela de vencimentos:** 08/08 a 15/08/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas:** **34 pedidos | R$ 76.611,87 | ticket médio R$ 2.253,29**.
- **Variação diária:** **-R$ 22.784,57 | -22,9%** contra 06/08 (**R$ 99.396,44**).
- **Pedidos em expedição:** **2 | R$ 292,60** — fora do total aprovado.
- **Meios de pagamento:** PIX direto + Increazy PIX **R$ 42.683,63**; Increazy total **R$ 41.383,14**; cartões diretos **R$ 4.182,56**; boletos direto/Increazy **R$ 4.895,90**. Categorias Increazy e meio podem se sobrepor; não somar.
- **Origem:** sem origem **R$ 66.108,24**; MAG **R$ 8.863,63**; GER **R$ 1.640,00**.
- **Pagar.me aprovado:** **38 cobranças | R$ 69.483,00 | ticket médio R$ 1.828,50**.
- **Pagar.me limpo:** **28 | R$ 52.547,35**. **Sinalizado:** **10 | R$ 16.935,65 (24,4%)** — **4 suspeitas/R$ 8.071,80** e **6 para revisão/R$ 8.863,85**.
- **Risco de duplicidade:** **2 pares**, com excesso potencial de **R$ 4.035,90**: Willas Rodrigues **2 × R$ 1.564,90 em 1 segundo**; Marcos Paulo Queiroz **2 × R$ 2.471,00 em 70 segundos**.
- **Por loja/Pagar.me:** BRG **R$ 33.214,96**; SSL **R$ 27.881,12**; ACL **R$ 5.827,60**; GCL **R$ 2.559,32**.
- **Por meio/Pagar.me:** cartão **R$ 35.271,88**; PIX **R$ 33.883,12**; boleto **R$ 328,00**.
- **Oracle/DEBX — PED status X:** **96 pedidos | R$ 9.119,27**. **Venda física:** **189 movimentos | R$ 8.291,37**. Bases separadas e não somadas ao SQL/Pagar.me.

## Alertas de vencimentos

- **Contas a pagar em 08–15/08:** base atual **não localizada** no Drive, vault ou arquivos locais pesquisados. **Não significa saldo zero.**
- **Recebíveis estimados em 08–15/08:** **R$ 0,00 | 0 parcelas** pelo proxy de condições de pagamento. Estimativa sem informação de baixa.
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. **Exposição histórica: R$ 109.222,37** — não classificada como vencimento atual.
- **BLUEHAUS/Pagar.me anterior:** **2 PIX | R$ 5.281,68**, sem registro localizado de resolução.

## Inadimplência

- **Índice confirmado:** indisponível.
- **Proxy de parcelas estimadas vencidas em 30 dias:** **R$ 0,00 | 0 parcelas**. Não equivale a inadimplência por ausência de títulos abertos e baixas.

## Recomendações

1. **Validar imediatamente os 2 pares suspeitos do Pagar.me; exposição duplicada potencial: R$ 4.035,90.**
2. **Revisar as outras 6 cobranças sinalizadas: R$ 8.863,85.**
3. **Obter hoje a posição oficial de contas a pagar 08–15/08**, com vencimento, valor e baixa.
4. **Confirmar resolução dos 2 PIX BLUEHAUS: R$ 5.281,68.**
5. **Confirmar baixa da exposição histórica de R$ 109.222,37** e retirar itens liquidados.
6. **Implantar aging diário de clientes:** saldo vencido, faixas 1–7/8–30/>30 dias e recuperação.

## Fontes validadas

- SQL Server `hotel-finder`: sessão, schema e colunas validados; dados até 07/08/2026.
- Pagar.me v5: consolidado gerado nesta execução; aprovações de 07/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; leitura de 07/08/2026.
- Google Drive: 6 buscas de metadados financeiros recentes, sem resultados.
