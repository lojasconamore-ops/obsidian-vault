# Relatório Financeiro Diário — 2026-09-25

**Ao DigitalCEO**  
**Base BRT:** 25/09/2026, 08:05  
**Vendas analisadas:** 24/09/2026  
**Janela solicitada:** 25/09–01/10/2026

## Resumo financeiro

- **Pagar.me — aprovações em 24/09:** **32 cobranças | R$ 55.707,58 | ticket médio R$ 1.740,86**.
- **Variação diária:** **+R$ 13.918,01 | +33,30%** contra 23/09.
- **Qualidade:** **32 OK | R$ 55.707,58**; **0 suspeitas**; **0 revisar**.
- **Por loja:** SSL **27 | R$ 50.485,51**; GCL **2 | R$ 3.571,19**; ACL **3 | R$ 1.650,88**; BRG **0**.
- **Concentração SSL:** **90,63%** do valor aprovado.
- **Por meio:** PIX **16 | R$ 32.255,63**; cartão **16 | R$ 23.451,95**.
- **SQL Server:** fonte atualizada somente até **22/09/2026**. Vendas de 24/09 indisponíveis por defasagem; não interpretadas como zero.
- **Oracle/DEBX:** indisponível às **08:05 BRT**, com conexão recusada na porta 1521. PED, venda física, recebíveis e aging de 24/09 não puderam ser atualizados.

## Alertas de vencimentos

- **Contas a pagar:** base oficial atual não localizada no Vault; total confirmado indisponível. E-mail não utilizado por restrição do perfil.
- **Contas a receber ACL — posição carregada da validação de 24/09:** para **25–30/09**, **503 títulos | R$ 125.738,82**. O dia **01/10** não foi validado; portanto, este não é o total completo dos próximos 7 dias.
- 25/09: **69 | R$ 9.333,24**.
- 26/09: **3 | R$ 221,58**.
- 27/09: **3 | R$ 1.065,93**.
- 28/09: **271 | R$ 38.733,82**.
- 29/09: **83 | R$ 8.316,15**.
- 30/09: **74 | R$ 68.068,10** — **54,13%** do valor parcial.

## Inadimplência

- **Indicador atual indisponível:** Oracle/DEBX fora do ar nesta execução.
- **Última posição validada em 24/09:** vencidos sem baixa **3.780 títulos | R$ 293.415,80**; saldo aberto ACL **R$ 1.301.294,19**; índice bruto **22,55%**.
- Aging anterior: 1–30 dias **R$ 5.882,37**; 31–60 **R$ 2.085,35**; 61–90 **R$ 2.174,58**; acima de 90 dias **R$ 283.273,50**.
- Valores acima são **carregados**, sujeitos a baixas posteriores; não representam posição contábil atual confirmada.

## Recomendações

1. **Caixa 30/09:** antecipar cobrança dos **R$ 68.068,10**; segunda concentração em 28/09, **R$ 38.733,82**.
2. **Cobrança:** assim que o Oracle retornar, atualizar aging e priorizar títulos de 1–30 dias e vencidos em 24/09.
3. **Conciliação:** fechamento Pagar.me de 24/09 está limpo, sem flags; conferir o crédito líquido e a concentração de **90,63% na SSL**.
4. **Dados:** restabelecer Oracle e atualizar o SQL Server, parado em 22/09, antes de comparar Pagar.me x ERP.
5. **Contas a pagar:** obter posição oficial antes de autorizar desembolsos; nenhuma base corrente foi localizada.

## Fontes

- Pagar.me v5: consolidado gerado nesta execução, janela 24/09/2026.
- SQL Server `hotel-finder`: sessão e colunas validadas; data máxima 22/09/2026; somente leitura.
- Oracle `conamore`: tentativa read-only às 08:05 BRT; conexão recusada.
- Última posição Oracle validada: relatório de 24/09/2026.
