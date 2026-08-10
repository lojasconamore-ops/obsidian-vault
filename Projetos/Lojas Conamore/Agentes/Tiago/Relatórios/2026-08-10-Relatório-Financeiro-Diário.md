# Relatório Financeiro Diário — 2026-08-10

**Ao DigitalCEO**  
**Base BRT:** 10/08/2026, 08:00  
**Vendas:** 09/08/2026  
**Janela de vencimentos:** 10/08 a 17/08/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas em 09/08:** **36 pedidos | R$ 28.586,33 | ticket médio R$ 794,06**.
- **Variação diária:** **+R$ 25.590,78 | +854,3%** contra 08/08 (**R$ 2.995,55**). Comparação domingo contra sábado; não usar isoladamente como tendência.
- **Pagamento/SQL:** cartões **R$ 23.536,05 (82,3%)**; à vista **R$ 5.050,28 (17,7%)**.
- **Origem/SQL:** MAG **36 pedidos | R$ 28.586,33 (100%)**.
- **Pagar.me em 09/08:** **21 cobranças | R$ 14.079,52 | ticket médio R$ 670,45**; **21 OK, 0 suspeitas, 0 revisar**.
- **Pagar.me por loja em 09/08:** ACL **19 | R$ 9.230,00**; SSL **2 | R$ 4.849,52**.
- **Pagar.me por meio em 09/08:** cartão **16 | R$ 12.751,41 (90,6%)**; PIX **5 | R$ 1.328,11 (9,4%)**.
- **Pagar.me no fim de semana 07–09/08:** **76 cobranças | R$ 99.532,59**; limpas **66 | R$ 82.596,94**; sinalizadas **10 | R$ 16.935,65 (17,0%)** — todas concentradas em 07/08.
- **Oracle/DEBX em 09/08:** PED status A **14 | R$ 6.589,93**. Venda física não interpretada como zero: `F_MOVTO` estava atualizada somente até **08/08**. PED e venda física permanecem separados e não são somados ao SQL/Pagar.me.

## Alertas de vencimentos

- **Contas a pagar em 10–17/08:** base oficial atual **não localizada** em 6 buscas no Google Drive nem nos arquivos locais. **Não significa saldo zero.**
- **Recebíveis estimados em 10–17/08:** **12 parcelas | R$ 27.135,05**, por proxy de condições de pagamento; não contém baixa financeira.
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. **Exposição histórica: R$ 109.222,37** — não classificada como vencimento atual.
- **Risco Pagar.me de 07/08:** 2 pares suspeitos, excesso potencial **R$ 4.035,90**; outras 6 cobranças para revisão **R$ 8.863,85**. O consolidado atual não traz evidência de resolução.
- **BLUEHAUS anterior:** 2 PIX | **R$ 5.281,68**, sem baixa/resolução localizada.

## Inadimplência

- **Índice confirmado:** indisponível.
- O proxy SQL aponta parcelas por prazo contratual, mas não informa títulos abertos nem baixas; portanto, **não é indicador confiável de inadimplência**.

## Recomendações

1. **Obter hoje a posição oficial de contas a pagar 10–17/08**, com vencimento, valor e baixa; risco semanal de caixa segue não mensurável.
2. **Validar os 2 pares suspeitos do Pagar.me:** exposição duplicada potencial **R$ 4.035,90**.
3. **Revisar as outras 6 cobranças sinalizadas:** **R$ 8.863,85**.
4. **Confirmar baixas da exposição histórica de R$ 109.222,37** e do caso BLUEHAUS de **R$ 5.281,68**.
5. **Implantar aging diário de clientes:** saldo vencido, faixas 1–7/8–30/>30 dias e recuperação.

## Fontes validadas

- SQL Server `hotel-finder`: sessão `hotelfinder`, schema e colunas validados; dados até 09/08/2026.
- Pagar.me v5: consolidado gerado nesta execução; janela 07–09/08/2026, com recorte específico de 09/08.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; consultas somente leitura. PED e venda física separados.
- Google Drive: 6 buscas financeiras recentes, completas e sem resultados.
- Arquivos locais/Vault: apenas base de títulos antiga, de 28/06; não usada como posição atual.
- Gmail/e-mail não utilizado por restrição do perfil.
