# 📊 Relatório Diário — Tobias (Logística)
**Data:** 04/06/2026 | **Período analisado:** Últimos 60 dias (05/04 a 04/06/2026)

## Resumo executivo
- **Pedidos:** 1.159
- **Receita:** R$ 3.817.142,95
- **Frete total:** R$ 50.328,11
- **Frete médio:** R$ 43,42
- **Ticket médio:** R$ 3.293,48
- **Clientes:** 946
- **Frete sobre receita:** **1,32%**

## Leitura operacional
- O volume está **concentrado em Expedição**: 995 pedidos, R$ 3,11MM, ou **81,5% da receita do período**.
- Os status **D + G** somam **44 pedidos** e **R$ 366.824,09** — isso precisa de validação com TI/ERP porque o significado operacional ainda não está fechado.
- Existem **8 pedidos com mais de 60 dias parados**, totalizando **R$ 12.428,81** em aberto.

## Distribuição por status
- **Expedição:** 995 pedidos | R$ 3.110.725,94 | frete R$ 42.412,50
- **D:** 12 pedidos | R$ 250.563,05 | frete R$ 850,00
- **Aprovado:** 73 pedidos | R$ 222.798,57 | frete R$ 3.389,99
- **G:** 32 pedidos | R$ 116.261,04 | frete R$ 1.450,00
- **Financeiro:** 26 pedidos | R$ 65.828,60 | frete R$ 1.325,60
- **Orçamento:** 16 pedidos | R$ 37.637,15 | frete R$ 750,00
- **Pendente:** 5 pedidos | R$ 13.328,60 | frete R$ 150,02

## Pedidos não concluídos / backlog antigo
### Pedidos com mais de 60 dias parados
- **0082982** — 148 dias — R$ 251,40 — frete R$ 50,00
- **0086636** — 126 dias — R$ 167,90 — frete R$ 0,00
- **0090819** — 101 dias — R$ 212,00 — frete R$ 0,00
- **0091187** — 99 dias — R$ 4.630,00 — frete R$ 0,00
- **0093473** — 85 dias — R$ 149,80 — frete R$ 0,00
- **0087307** — 84 dias — R$ 2.777,32 — frete R$ 0,00
- **0094138** — 80 dias — R$ 1.506,64 — frete R$ 50,00
- **0094329** — 66 dias — R$ 2.733,75 — frete R$ 50,00

## Frete — pontos de atenção
### Top 5 maiores fretes
- **0103881** — frete R$ 500,00 | total R$ 58.895,50
- **0103412** — frete R$ 390,20 | total R$ 4.245,67
- **0098417** — frete R$ 350,00 | total R$ 3.467,00
- **0103930** — frete R$ 300,00 | total R$ 34.603,60
- **0097488** — frete R$ 270,00 | total R$ 2.608,80

### Leitura de frete
- O custo médio está **saudável** no consolidado (1,32% da receita).
- O risco está na **cauda longa**: alguns pedidos têm frete alto sobre ticket baixo, o que pede auditoria por CEP/região/transportadora.

## Intelipost / transportadoras
### Transportadoras ativas na API
- Correios Sedex
- Frota Interna / Frete Valor Fixo
- Via Pajucara
- Jamef
- Rodonaves
- Pacífico
- Rápido Figueiredo
- Favorita Transportes

### Pedido crítico monitorado na Intelipost
- **Pedido Intelipost:** `100-0011640-2`
- **Transportadora:** Via Pajucara — Via Pajucara Standard
- **Volumes:** 8
- **Peso total:** 53 kg
- **Frete:** R$ 408,94
- **Status atual:** Em trânsito / saiu para entrega
- **Previsão:** 04/06/2026
- **Destino:** Campos do Jordão-SP
- **Leitura:** risco operacional **médio**, porque a previsão é para hoje e o último trecho já saiu para entrega.

## O que importa para gestão hoje
1. **Validar o significado de D e G com TI/ERP.**
   - São R$ 366,8 mil sem leitura operacional fechada.
2. **Destravar os 8 pedidos antigos.**
   - R$ 12,4 mil parados há mais de 60 dias.
3. **Monitorar o pedido 100-0011640-2.**
   - Via Pajucara, 8 volumes, previsão hoje.
4. **Auditar os maiores fretes.**
   - Principalmente pedidos com frete alto e ticket menor.
5. **Fechar a segregação por transportadora com fonte de verdade.**
   - O banco atual não traz o vínculo `Numero_Pedido → Cód. Ped. Intelipost`.
   - Para ranking completo por transportadora, preciso da visão ERP/NF com o código Intelipost por pedido.

## Base usada
- **Fonte principal:** `debx.PDV_Detalhes` no SQL Server Hotel Finder
- **Tracking:** Intelipost API (`/shipment_order/{order_number}`)
- **Transportadoras:** `delivery_method` da Intelipost

## Conclusão
A operação está **saudável no consolidado de frete**, mas com dois gargalos claros:
- backlog antigo ainda travado;
- classificação operacional D/G sem definição fechada.

Se quiser, eu monto na sequência uma **versão executiva de 1 página** só com os pontos críticos e recomendações.
