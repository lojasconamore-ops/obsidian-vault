# 📊 Relatório Diário — Tobias (Logística)
**Data:** 07/06/2026 | **Período analisado:** Últimos 60 dias (08/04 a 07/06/2026)

## 🔌 Intelipost API
- **Status:** ✅ Online
- **API Key:** ✅ Configurada
- **Transportadoras ativas:** **8/15**
- **Tempo de resposta do health check:** **1,0 ms**

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
- **Último evento:** 04/06/2026 06:26
- **Status atual:** In Transit / Saiu para entrega
- **Leitura:** **atraso confirmado** — hoje está **4d 8h** fora da promessa
- **Sinal de extravio/avaria:** não há evidência clara

### 2) Backlog antigo
- **8 pedidos** com mais de 60 dias sem resolução
- **Valor em aberto:** **R$ 12.428,81**
- Maiores valores:
  - **0091187** — R$ 4.630,00
  - **0087307** — R$ 2.777,32
  - **0094329** — R$ 2.733,75

### 3) Leitura operacional
- **Pedidos (60d):** 1.137
- **Receita:** **R$ 3.709.592,67**
- **Frete total:** **R$ 49.572,36**
- **Frete médio:** **R$ 43,60**
- **Ticket médio:** **R$ 3.262,61**
- **Clientes:** **926**
- **Status mais relevantes:** Expedição 977 | D 15 | Aprovado 73 | G 35 | Orçamento 23 | Financeiro 10 | Pendente 4

## ✅ Recomendações operacionais
1. **Cobrar a Via Pajucara hoje** no pedido `100-0011640-2` até baixa final.
2. **Destravar os 8 pedidos antigos**; priorizar `0091187`, `0087307` e `0094329` pelo valor.
3. **Fechar o mapeamento ERP ↔ Intelipost**; sem correlação direta, o monitoramento crítico fica cego.
4. **Validar os status D e G com TI/ERP**; há fila operacional relevante sem leitura fechada.
5. **Manter health check diário**; integração segue estável.

## Base consultada
- `python3 /home/sergio-ladeira/.hermes/scripts/intelipost-track.py status`
- `python3 /home/sergio-ladeira/.hermes/scripts/intelipost-track.py delivery-methods`
- `python3 /home/sergio-ladeira/.hermes/scripts/intelipost-track.py tracking 100-0011640-2`
- `python3 /home/sergio-ladeira/.hermes/scripts/daily-order-check.py --summary --track-critical --top 20`
