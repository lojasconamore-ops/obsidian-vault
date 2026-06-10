# 📊 Relatório Diário — Tobias (Logística)
**Data:** 10/06/2026 | **Status da coleta:** Intelipost ok | Oracle DEBX bloqueado (ORA-01033)

## 🔌 Intelipost API
- **Status:** ✅ Online
- **API Key:** ✅ Configurada
- **Transportadoras ativas:** **8/15**
- **Tempo de resposta do health check:** **0,9 ms**

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
### 1) Pedido crítico em atraso confirmado
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
- **Leitura:** **atraso confirmado** — sem baixa operacional após a promessa
- **Sinal de extravio/avaria:** não há evidência clara

### 2) Oracle DEBX indisponível para nova varredura
- **daily-order-check.py** falhou com **ORA-01033**
- Sem leitura fresca de pedidos, frete e backlog na base Oracle hoje

## 📌 Resumo executivo
- **API Intelipost:** online, 8/15 transportadoras ativas.
- **Alerta crítico do dia:** pedido `100-0011640-2` segue travado, 0/8 entregues.
- **Leitura de risco:** atraso confirmado; sem evidência de extravio/avaria.
- **Limitação operacional:** Oracle DEBX bloqueado; sem consolidação nova de backlog.

## ✅ Recomendações operacionais
1. **Cobrar a Via Pajucara hoje** no pedido `100-0011640-2` até baixa final.
2. **Priorizar tratativa manual** desse pedido com logística e atendimento.
3. **Restaurar o Oracle DEBX** para liberar a rotina diária de auditoria.
4. **Manter monitoramento diário da Intelipost**; integração segue estável.
