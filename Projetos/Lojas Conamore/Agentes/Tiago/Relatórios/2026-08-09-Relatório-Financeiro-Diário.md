# Relatório Financeiro Diário — 2026-08-09

**Ao DigitalCEO**  
**Base BRT:** 09/08/2026, 08:00  
**Vendas:** 08/08/2026  
**Janela de vencimentos:** 09/08 a 16/08/2026

## Resumo financeiro

- **SQL Server — vendas aprovadas:** **4 pedidos | R$ 2.995,55 | ticket médio R$ 748,89**.
- **Variação diária:** **-R$ 73.616,32 | -96,1%** contra 07/08 (**R$ 76.611,87**). Movimento de sábado; comparar com sábado equivalente antes de concluir tendência.
- **Pagamento:** Mastercard **R$ 1.526,30 (51,0%)**; Increazy crédito **R$ 1.074,90 (35,9%)**; Visa **R$ 394,35 (13,2%)**.
- **Origem:** MAG **3 pedidos | R$ 1.920,65 (64,1%)**; sem origem **1 pedido | R$ 1.074,90 (35,9%)**.
- **Overlay operacional `debx.PDV_Detalhes`:** **1 pedido aprovado | R$ 1.074,90**. Não substitui a fonte confirmada.
- **Pagar.me de 08/08:** consolidado da execução de 09/08 **ainda não disponível às 08:00**; conciliação pendente.
- **Oracle/DEBX — PED status X:** **117 pedidos | R$ 22.324,17**. **Venda física:** **313 movimentos | R$ 19.218,79**. Bases separadas e não somadas ao SQL Server.

## Alertas de vencimentos

- **Contas a pagar em 09–16/08:** base oficial **não localizada** no Google Drive nem nos arquivos locais. **Não significa saldo zero.**
- **Recebíveis estimados em 09–16/08:** **0 parcelas | R$ 0,00**, pelo proxy de condições de pagamento; não contém informação de baixa.
- **Pendências históricas sem baixa confirmada:** Grupo GPS **R$ 73.820,00**; aluguel **R$ 34.000,00**; Jamef **R$ 1.402,37**. **Exposição histórica: R$ 109.222,37** — não classificada como vencimento atual.
- **Riscos Pagar.me anteriores sem resolução localizada:** duplicidade potencial de 07/08 **R$ 4.035,90**; outras cobranças em revisão **R$ 8.863,85**; BLUEHAUS **2 PIX | R$ 5.281,68**.

## Inadimplência

- **Índice confirmado:** indisponível.
- **Proxy de parcelas estimadas vencidas em 30 dias:** **0 parcelas | R$ 0,00**. Não equivale a inadimplência por ausência de títulos abertos e baixas.

## Recomendações

1. **Obter a posição oficial de contas a pagar 09–16/08**, com valor, vencimento e baixa.
2. **Concluir a conciliação Pagar.me de 08/08** quando o consolidado estiver disponível.
3. **Encerrar ou registrar status dos riscos Pagar.me anteriores:** R$ 4.035,90 de possível duplicidade, R$ 8.863,85 em revisão e BLUEHAUS R$ 5.281,68.
4. **Confirmar as baixas da exposição histórica de R$ 109.222,37** e retirar itens liquidados.
5. **Implantar aging diário de clientes:** saldo vencido, faixas 1–7/8–30/>30 dias e recuperação.

## Fontes validadas

- SQL Server `hotel-finder`: sessão `hotelfinder`, schema e colunas validados; dados até 08/08/2026.
- Oracle `conamore`, sessão `TEST_ACL`: sessão, schema e colunas validados; consultas somente leitura. PED e venda física tratados separadamente.
- Google Drive: 6 buscas financeiras recentes, todas completas e sem resultados.
- Arquivos locais/Vault: nenhum relatório oficial atual de contas a pagar localizado; consolidação Pagar.me de 09/08 ausente às 08:00.
- Gmail/e-mail não utilizado por restrição do perfil.
