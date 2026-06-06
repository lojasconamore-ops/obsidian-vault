# 📊 Relatório Diário — Tobias (Logística)
**Data:** 06/06/2026 | **Período analisado:** Últimos 60 dias (07/04 a 06/06/2026)

## 🔌 Intelipost API
- **Status:** ✅ Online
- **API Key:** ✅ Configurada
- **Transportadoras ativas:** **8/15**
- **Tempo de resposta do health check:** **3,1 ms**

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
- **Cliente:** SCOFANO & SCOFANO TURISMOS LTDA
- **Transportadora:** Via Pajucara Standard
- **Destino:** Campos do Jordão-SP
- **Volumes:** 8
- **Entregues:** 0/8
- **Previsão:** 02/06/2026 23:59
- **Status atual:** In Transit / Saiu para entrega
- **Último evento:** 04/06/2026 06:26
- **Leitura:** **atrasado** (mínimo 2 dias), sem sinal de entrega concluída

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

### 4) Sinalização de extravio/avaria
- **Não houve evidência clara de extravio ou avaria** nos dados consultados hoje
- O risco confirmado é **atraso**

## 📈 Resumo executivo
- **Pedidos (60d):** 1.156
- **Receita:** **R$ 3.815.663,89**
- **Frete total:** **R$ 50.428,28**
- **Frete médio:** **R$ 43,62**
- **Ticket médio:** **R$ 3.300,75**
- **Clientes:** **940**

## 📋 Distribuição por status
- **Expedição:** 996 pedidos | **R$ 3.128.473,45**
- **Aprovado:** 72 pedidos | **R$ 196.076,55**
- **D:** 16 pedidos | **R$ 274.446,36**
- **G:** 35 pedidos | **R$ 127.029,05**
- **Financeiro:** 10 pedidos | **R$ 18.709,82**
- **Orçamento:** 23 pedidos | **R$ 53.044,46**
- **Pendente:** 4 pedidos | **R$ 17.884,20**

## ✅ Recomendações operacionais
1. **Cobrar a Via Pajucara hoje** no pedido `100-0011640-2` até baixa final.
2. **Destravar os 8 pedidos antigos** acima de 60 dias; atacar primeiro os de maior valor.
3. **Fechar o mapeamento ERP ↔ Intelipost** para não operar no escuro.
4. **Validar os status D e G com TI/ERP**; há fila relevante sem classificação clara.
5. **Manter monitoramento diário** da Intelipost; infraestrutura está estável.

## Base consultada
- `python3 /home/sergio-ladeira/.hermes/profiles/tobias/scripts/intelipost-track.py status`
- `python3 /home/sergio-ladeira/.hermes/profiles/tobias/scripts/intelipost-track.py delivery-methods`
- `python3 /home/sergio-ladeira/.hermes/profiles/tobias/scripts/intelipost-track.py tracking "100-0011640-2"`
- `python3 /home/sergio-ladeira/.hermes/profiles/tobias/scripts/daily-order-check.py --track-critical --top 20`
