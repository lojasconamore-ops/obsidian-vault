# 📊 Relatório Diário — Tobias (Logística)
**Data:** 08/06/2026 | **Período analisado:** Últimos 60 dias (09/04 a 08/06/2026)

## 🔌 Intelipost API
- **Status:** ✅ Online
- **API Key:** ✅ Configurada
- **Transportadoras ativas:** **8/15**
- **Tempo de resposta do health check:** **0,4 ms**

### Transportadoras ativas
- Pacifico Standard — Pacífico
- Via Pajucara Standard — Via Pajucara
- Rapido Figueiredo — Rapido Figueiredo
- Frete Valor Fixo — Frota Interna
- Jamef — Jamef
- Rodonaves — Rodonaves
- Favorita Transportes — Favorita Transportes
- Correios Sedex — Correios

## 🚨 Alertas logísticos do dia
### 1) Pedido em atraso confirmado
- **Intelipost:** `100-0011640-2`
- **Venda/ERP:** `0104766`
- **Cliente:** SCOFANO & SCOFANO TURISMOS LTDA
- **Transportadora:** Via Pajucara Standard
- **Destino:** Campos do Jordão-SP
- **Volumes:** 8
- **Entregues:** 0/8
- **Previsão original:** 02/06/2026 23:59
- **Último evento:** 28/05/2026 05:27
- **Status atual:** In Transit / Em trânsito
- **Leitura:** **atraso confirmado** — hoje está **6 dias** fora da promessa
- **Sinal de extravio/avaria:** não há evidência clara

### 2) Backlog antigo
- **8 pedidos** com mais de 60 dias sem resolução
- **Valor em aberto:** **R$ 12.428,81**
- Maiores valores:
  - **0091187** — R$ 4.630,00
  - **0087307** — R$ 2.777,32
  - **0094329** — R$ 2.733,75

### 3) Gap de rastreio ERP ↔ Intelipost
- Os top pedidos do ERP (`debx.PDV_Detalhes`) continuam sem correlação direta com Intelipost
- O tracking automático dos 20 maiores pedidos retorna **“sem dados Intelipost”**
- Sem a tabela NF ↔ shipment, a análise crítica fica parcial

## 📈 Resumo executivo
- **Pedidos (60d):** 1.111
- **Receita:** **R$ 3.643.521,62**
- **Frete total:** **R$ 48.269,51**
- **Frete médio:** **R$ 43,45**
- **Ticket médio:** **R$ 3.279,50**
- **Clientes:** **907**

## 📋 Distribuição por status
- **Expedição:** 954 pedidos | **R$ 2.967.711,61**
- **D:** 15 pedidos | **R$ 269.251,66**
- **Aprovado:** 73 pedidos | **R$ 196.332,65**
- **G:** 33 pedidos | **R$ 121.110,25**
- **Orçamento:** 22 pedidos | **R$ 52.521,43**
- **Financeiro:** 10 pedidos | **R$ 18.709,82**
- **Pendente:** 4 pedidos | **R$ 17.884,20**

## ✅ Recomendações operacionais
1. **Cobrar a Via Pajucara hoje** no pedido `100-0011640-2` até baixa final.
2. **Destravar os 8 pedidos antigos** acima de 60 dias; atacar primeiro os de maior valor.
3. **Fechar o mapeamento ERP ↔ Intelipost**; sem correlação direta, o monitoramento crítico fica cego.
4. **Validar os status D e G com TI/ERP**; há fila relevante sem classificação clara.
5. **Manter monitoramento diário** da Intelipost; infraestrutura segue estável.

## Base consultada
- `python3 /home/sergio-ladeira/.hermes/scripts/intelipost-track.py status`
- `python3 /home/sergio-ladeira/.hermes/scripts/intelipost-track.py delivery-methods`
- `python3 /home/sergio-ladeira/.hermes/scripts/intelipost-track.py tracking 100-0011640-2`
- `python3 /home/sergio-ladeira/.hermes/scripts/daily-order-check.py --summary --track-critical --top 20`
