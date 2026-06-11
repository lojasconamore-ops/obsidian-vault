# 📊 Relatório Diário — Tobias (Logística)
**Data:** 09/06/2026 | **Status da coleta:** Intelipost ok | Oracle DEBX bloqueado (ORA-01033)

## 🔌 Intelipost API
- **Status:** ✅ Online
- **API Key:** ✅ Configurada
- **Transportadoras ativas:** **8/15**
- **Tempo de resposta do health check:** **2,6 ms**

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
- **Leitura:** **atraso confirmado** — hoje está **7 dias** fora da promessa
- **Sinal de extravio/avaria:** não há evidência clara

### 2) Backlog antigo — última leitura operacional disponível
- **8 pedidos** com mais de 60 dias sem resolução
- **Valor em aberto:** **R$ 12.428,81**
- Maiores valores:
  - **0091187** — R$ 4.630,00
  - **0087307** — R$ 2.777,32
  - **0094329** — R$ 2.733,75

### 3) Oracle DEBX indisponível para nova varredura
- **daily-order-check.py** falhou com **ORA-01033**
- Isso impediu atualizar hoje o consolidado de pedidos, frete e backlog via base Oracle

## 📌 Resumo executivo
- **API Intelipost:** online, 8/15 transportadoras ativas.
- **Alerta crítico do dia:** pedido `100-0011640-2` segue atrasado, 0/8 entregues.
- **Backlog antigo:** 8 pedidos travados, R$ 12,4 mil em aberto na última leitura válida.
- **Limitação operacional:** Oracle DEBX caiu em inicialização/encerramento; sem leitura fresca de pedidos hoje.

## ✅ Recomendações operacionais
1. **Cobrar a Via Pajucara hoje** no pedido `100-0011640-2` até baixa final.
2. **Destravar os 8 pedidos antigos**; priorizar os de maior valor.
3. **Restaurar o Oracle DEBX** para liberar a rotina diária de auditoria.
4. **Manter monitoramento diário da Intelipost**; integração segue estável.
