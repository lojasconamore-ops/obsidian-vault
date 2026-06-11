# 📊 Relatório Diário — Tobias (Logística)
**Data:** 05/06/2026 | **Período analisado:** Últimos 60 dias (06/04 a 05/06/2026)

## Status Intelipost
- **API:** ✅ Online
- **Chave API:** ✅ Configurada
- **Transportadoras ativas:** 8/15
- **Tempo de resposta no health check:** 3,1 ms

### Transportadoras ativas
- Pacifico Standard — Pacífico
- Via Pajucara Standard — Via Pajucara
- Rapido Figueiredo — Rapido Figueiredo
- Frete Valor Fixo — Frota Interna
- Jamef — Jamef
- Rodonaves — Rodonaves
- Favorita Transportes — Favorita Transportes
- Correios Sedex — Correios

## Alertas logísticos do dia
### 1) Pedido crítico em atraso
- **Intelipost:** `100-0011640-2`
- **Transportadora:** Via Pajucara Standard
- **Destino:** Campos do Jordão-SP
- **Volumes:** 8
- **Entregues:** 0/8
- **Previsão:** 02/06/2026 23:59
- **Status atual:** Em trânsito / saiu para entrega
- **Leitura:** pedido **atrasado** e precisa acompanhamento imediato

### 2) Backlog antigo
- **8 pedidos** com mais de 60 dias parados
- **Valor em aberto:** R$ 12.428,81
- Pontos críticos: 0091187, 0087307 e 0094329 concentram maior valor no atraso

### 3) Gap de rastreio ERP ↔ Intelipost
- Os pedidos do ERP (`debx.PDV_Detalhes`) **não batem** com o número de shipment da Intelipost
- Resultado prático: o tracking automático dos top pedidos do PDV retorna **“sem dados Intelipost”**
- Sem tabela de correlação NF ↔ Intelipost, a leitura de criticidade fica parcial

## Resumo executivo
### Indicadores do período
- **Pedidos:** 1.159
- **Receita:** R$ 3.817.142,95
- **Frete total:** R$ 50.328,11
- **Frete médio:** R$ 43,42
- **Ticket médio:** R$ 3.293,48
- **Clientes:** 946

### Leitura operacional
- Operação forte em **Expedição**: 995 pedidos / R$ 3,11MM
- **D + G** seguem como fila relevante e precisam definição operacional fechada com TI/ERP
- Frete consolidado segue **saudável**: 1,32% da receita

## Recomendações operacionais
1. **Prioridade máxima:** tratar o pedido `100-0011640-2` com a Via Pajucara hoje.
2. **Destravar os 8 pedidos com +60 dias** — atacar primeiro os de maior valor.
3. **Fechar o gap ERP ↔ Intelipost** — sem isso o monitoramento crítico fica cego.
4. **Validar o significado dos status D e G** com TI/ERP — há R$ 366,8 mil nessa zona cinzenta.
5. **Manter o health check diário da API** — integração estável, sem incidente sistêmico.

## Base consultada
- `python3 /home/sergio-ladeira/.hermes/profiles/tobias/scripts/intelipost-track.py status`
- `python3 /home/sergio-ladeira/.hermes/profiles/tobias/scripts/intelipost-track.py delivery-methods`
- `python3 /home/sergio-ladeira/.hermes/profiles/tobias/scripts/intelipost-track.py tracking 100-0011640-2`
- `python3 /home/sergio-ladeira/.hermes/profiles/tobias/scripts/daily-order-check.py --summary --track-critical --top 20`
