# Relatório Financeiro Diário — 2026-08-16

**Ao DigitalCEO**  
**Base BRT:** 16/08/2026, 08:00  
**Vendas:** 15/08/2026  
**Janela de vencimentos:** 16/08 a 23/08/2026

## Resumo financeiro

- **Vendas aprovadas/SQL:** **12 pedidos | R$ 6.769,11 | ticket médio R$ 564,09**.
- **Variação diária:** **-R$ 51.395,31 | -88,36%** contra 14/08 (**43 pedidos | R$ 58.164,42**).
- **Pagamento/SQL:** à vista **R$ 4.251,59**; cartão 2x **R$ 1.758,42**; cartão 4x **R$ 759,10**.
- **Origem/SQL:** MAG **12 pedidos | R$ 6.769,11**.
- **Pagar.me:** **12 aprovações | R$ 6.769,22 | ticket R$ 564,10**. Diferença para SQL: **R$ 0,11 | 0,0016%**.
- **Pagar.me por loja:** SSL **R$ 3.577,73**; ACL **R$ 3.191,49**; GCL **R$ 0,00**; BRG **R$ 0,00**.
- **Pagar.me por meio:** PIX **R$ 4.251,70**; cartão **R$ 2.517,52**.
- **Pagar.me — qualidade:** **12 OK | 0 suspeitas | 0 revisar**.
- **Oracle/DEBX, sem somar ao SQL:** PED status **X/expedido: 102 | R$ 13.233,45**; status **A: 11 | R$ 5.751,63**. Venda física (`MOV_NATIND=100`): **247 movimentos | R$ 12.473,46**.

## Alertas de vencimentos

- **Contas a pagar em 16–23/08:** base oficial atual **não localizada no Vault**; Google Drive **não autenticado neste perfil**. **Não significa saldo zero.**
- **Recebíveis estimados por condição de pagamento:** **0 parcelas | R$ 0,00**. Proxy sem títulos/baixas; não comprova ausência de recebíveis.
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. **Exposição histórica: R$ 109.222,37** — não classificada como vencimento atual.
- **Revisão Pagar.me anterior sem resolução localizada:** **2 cobranças | R$ 1.004,96**. A execução de 15/08 está limpa.

## Inadimplência

- **Índice confirmado:** indisponível.
- **Proxy estimado vencido em 30 dias:** **0 parcelas | R$ 0,00**; não equivale a inadimplência, pois não há base de títulos abertos e baixas.

## Recomendações

1. **Obter a posição oficial de contas a pagar de 16–23/08**, com vencimento, valor e baixa; risco semanal de caixa não é mensurável na base atual.
2. **Confirmar a baixa da exposição histórica de R$ 109.222,37** e encerrar a revisão anterior de **R$ 1.004,96**.
3. **Tratar a queda diária de 88,36% como alerta comercial**, validando se decorre do sábado ou de perda real de volume.
4. **Implantar aging diário:** vencido, 1–7, 8–30 e >30 dias, com saldo aberto, baixas e recuperação.

## Fontes validadas

- SQL Server `hotel-finder`: sessão, schema e colunas validados; atualizado até 15/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; leitura; PED e venda física separados.
- Pagar.me v5: consolidado gerado nesta execução, janela de aprovação 15/08/2026.
- Vault: nenhuma base oficial atual de contas a pagar localizada por busca textual.
- Google Drive: consulta indisponível por falta de autenticação neste perfil.
- Gmail/e-mail não utilizado por restrição do perfil.
