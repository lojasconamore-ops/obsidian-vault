# Relatório Financeiro Diário — 2026-08-13

**Ao DigitalCEO**  
**Base BRT:** 13/08/2026, 08:00  
**Vendas:** 12/08/2026  
**Janela de vencimentos:** 13/08 a 20/08/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas:** **48 pedidos | R$ 45.982,51 | ticket médio R$ 957,97**.
- **Variação diária:** **−R$ 17.194,14 | −27,22%** contra 11/08 (**R$ 63.176,65**).
- **Pagamento/SQL:** Increazy crédito **R$ 13.833,10**; PIX **R$ 11.792,69**; cartões **R$ 12.744,64**; Increazy PIX **R$ 4.883,14**; boletos **R$ 2.728,94**.
- **Origem/SQL:** MAG **34 pedidos | R$ 24.476,11**; sem origem **10 | R$ 18.716,24**; GER **4 | R$ 2.790,16**.
- **Oracle/DEBX — PED:** status A **24 pedidos | R$ 11.250,54**; status X **0**. **Venda física (`MOV_NATIND=100`): 0 movimentos**. Bases separadas; não somadas ao SQL.
- **Pagar.me:** consolidado disponível até aprovações de **11/08**; sem recorte atual de 12/08, portanto não usado no total do dia.

## Alertas de vencimentos

- **Contas a pagar em 13–20/08:** base oficial atual **não localizada** nos arquivos locais/Vault. **Não significa saldo zero.**
- **Recebíveis por proxy de condições de pagamento:** **0 parcelas | R$ 0,00**. O proxy não contém títulos/baixas e não comprova ausência de recebíveis.
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. **Exposição histórica: R$ 109.222,37** — não classificada como vencimento atual.
- **Risco Pagar.me anterior (07/08):** duplicidade potencial **R$ 4.035,90**; outras cobranças para revisão **R$ 8.863,85**. **Risco total sinalizado: R$ 12.899,75**, sem evidência atual de resolução.

## Inadimplência

- **Índice confirmado:** indisponível.
- **Proxy estimado vencido em 30 dias:** **0 parcelas | R$ 0,00**; não equivale a inadimplência, pois a fonte não registra títulos abertos nem baixas.

## Recomendações

1. **Obter hoje a posição oficial de contas a pagar 13–20/08**, com vencimento, valor e baixa.
2. **Confirmar a baixa da exposição histórica de R$ 109.222,37.**
3. **Encerrar a revisão Pagar.me de R$ 12.899,75** e atualizar a base com as aprovações de 12/08.
4. **Implantar aging diário:** vencido, 1–7, 8–30 e >30 dias, baixas e recuperação.

## Fontes validadas

- SQL Server `hotel-finder`: sessão, schema e colunas validados; dados atualizados até 12/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; somente leitura; PED e venda física separados.
- Pagar.me: arquivo consolidado de 12/08 contém aprovações somente até 11/08.
- Arquivos locais/Vault: nenhuma base oficial atual de contas a pagar localizada.
- Gmail/e-mail não utilizado por restrição do perfil.
