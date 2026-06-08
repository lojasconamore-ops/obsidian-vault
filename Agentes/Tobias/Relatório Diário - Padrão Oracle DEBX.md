# Relatório Diário — Padrão Oracle DEBX

**Status:** aprovado como base do relatório diário de logística
**Escopo fixo:** últimos **15 dias**
**Fuso:** `America/Sao_Paulo`

## Base SQL combinada
O relatório diário passa a usar a lógica Oracle DEBX com cruzamento entre:

- `TEST_ACL.F_SAIDAS` → NFs, valor da nota, frete, cliente e transportadora
- `TEST_ACL.F_MOVTO` → cruzamento NF ↔ pedido
- `TEST_ACL.F_PEDVENDA` → frete do pedido e código de transportadora
- `TEST_PED.FI_MAG_PEDIDOS` → nome legível do cliente e dados de envio
- `TEST_PED.SSL_CAIXA_DETALHADO_MATERIAL` → cliente/empresa e contexto operacional
- `TEST_PED.FI_MAG_DEPA_TRANSP` → mapeamento de transportadora / método de envio

## Formato obrigatório de entrega
1. **Versão gerencial**
   - Totais do período
   - NF, faturamento, frete, ticket e concentração
2. **Versão operacional**
   - Série diária
   - Picos e vales
   - Principais responsáveis / transportadoras quando houver cruzamento
3. **Versão consolidada**
   - Top pedidos / NFs / fretes
   - Origem / canal quando disponível
   - Observações de consistência e parciais

## Regras
- Não misturar janelas maiores com a janela padrão.
- Se o cruzamento de NF, pedido, cliente ou transportadora vier parcial, sinalizar isso.
- Não substituir NF/faturamento por agregado de pedido.
- Preferir nomes legíveis em vez de códigos, quando possível.

## Observação operacional
A rotina antiga baseada em `debx.PDV_Detalhes` fica como referência histórica; o padrão diário oficial agora é o SQL Oracle DEBX acima.
