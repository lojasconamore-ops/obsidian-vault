# Rotina Operacional — Tobias

**Última atualização:** 31/05/2026
**Baseada em:** Ferramentas disponíveis + indicadores logísticos Conamore

---

## Conexões úteis

- [[Relatório Diário - Template Oracle DEBX]]
- [[Relatório Diário - Padrão Oracle DEBX]]
- [[Análise de Conversas do Octadesk — Treinamento para Logística]]
- [[plano-integracao-intelipost]]

---

## 🗓 Diária (~15 min)

### 1. Tracking de Pedidos Pendentes
Consultar pedidos com status crítico na Intelipost:
- Pedidos em trânsito há mais dias que o prazo estimado
- Pedidos com status `PRE_SHIPMENT_LIST_SUCCEEDED` (pré-lista) que não avançaram

**Ferramenta:** Intelipost API (`python3 scripts/intelipost-track.py tracking <numero>`)

### 2. Verificar Ruptura (Estoque Zero)
Conferir itens críticos (Classe A) que estão com estoque zerado ou abaixo do ponto de ressuprimento.

**Fonte:** ERP (exportação CSV ou consulta direta)

### 3. Health Check da Intelipost
Confirmar que a API está respondendo:
```bash
python3 ~/.hermes/profiles/tobias/scripts/intelipost-track.py status
```

---

## 📆 Semanal (~1h)

### 4. Relatório de Pedidos Antigos
Rodar auditoria de pedidos Intelipost com data de criação > 7 dias sem entrega e sem erro declarado.

**Ferramenta:** `python3 ~/.hermes/profiles/tobias/scripts/old-orders-audit.py`
**Entregar:** Total de pedidos antigos, faturamento em risco, clientes com múltiplos pedidos parados.

### 5. Cross-Reference GA4 + Intelipost
Comparar volume de transações do GA4 Hotelaria com tracking real da Intelipost:
- GA4: `transactions` + `totalRevenue` da propriedade `properties/379729087`
- Intelipost: tracking individual dos pedidos do período
- **Objetivo:** Estimar cobertura da Matriz vs marketplaces, detectar pedidos não criados na Intelipost

### 6. Giro de Estoque (TOP 10)
Identificar itens com giro abaixo de 2 ao ano (estoque parado) e acima de 8 (risco de ruptura).

**KPI:**
| Giro | Ação |
|------|------|
| < 2 | Promoção / liquidação / descarte |
| 2 a 4 | Monitorar, pode precisar de ação |
| 4 a 6 | ✅ Ideal |
| 6 a 8 | Reforçar ressuprimento |
| > 8 | Risco de ruptura — comprar urgente |

### 7. Acuracidade de Estoque
Se houver inventário rotativo na semana, conferir resultado:
- Meta: > 95%
- Se < 90%: investigar causas (erro de picking, extravio, sistema)

### 8. OTIF (On Time In Full)
Coletar dados da semana anterior:
- **OTIF = Pedidos entregues no prazo E completos / Total de pedidos**
- Meta B2B Hotelaria: > 97%
- Meta E-commerce: > 95%
- Abaixo da meta: identificar transportadora ou CD com problema

### 9. Custo Logístico sobre Venda
Calcular indicador semanal:
```
Custo Logístico = (Frete + Armazenagem + Embalagem + Perdas) / Receita Total
```
- Benchmark têxtil: 6% a 10%
- Acima de 10%: investigar frete mais caro, avarias, ineficiência

### 10. Check-in com Transportadoras
Revisar reclamações ou ocorrências da semana com cada transportadora ativa:
- Correios Sedex, Frota Interna, Via Pajucara, Jamef, Rodonaves, Pacífico, Rápido Figueiredo, Favorita Transportes
- Pontos críticos: atraso, avaria, extravio

---

## 📅 Mensal

### 11. Inventário Geral / Rotativo
Conferência física vs lógico do estoque por categoria.

### 12. Avaliação de Fornecedores
Lead time, qualidade, conformidade de entregas.

### 13. Replanejamento Sazonal
Ajustar ponto de ressuprimento e estoque de segurança conforme calendário:
- Jan-Fev: volta às aulas
- Abr-Jun: casamentos/enxovais
- Ago-Out: renovação hotelaria
- Nov-Dez: Black Friday + Natal

---

## ⚡ Gatilhos (fora da rotina)

| Evento | Ação |
|--------|------|
| Transportadora notifica atraso generalizado | Acionar rota alternativa / cotar frete emergencial |
| Greve / greve de caminhoneiros | Acionar plano de contingência — priorizar entregas urgentes |
| Pico inesperado de vendas (GA4 dispara) | Verificar estoque de segurança, acelerar ressuprimento |
| Cliente VIP com pedido parado | Rastrear manualmente e dar satisfação |
| Erro de picking detectado | Acionar WMS/CD, corrigir, registrar causa |

---

> *"Rotina sem métrica é apenas movimento. Tudo que se mede, se gerencia."*
