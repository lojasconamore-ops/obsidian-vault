# Relatório Diário de Marketing — 02/06/2026

**Gerente:** Flávia
**Período analisado:** 26/05/2026 a 01/06/2026 (7 dias completos)
**Fonte principal:** Google Analytics 4 (RD Station MCP offline)

---

## ⚠️ ALERTA — RD Station MCP Indisponível

O servidor MCP do RD Station retornou **401 Unauthorized** — o token OAuth vinculado à chave `019e7a56-18ee-7dd3-a0e5-9c330ecced2b` expirou. As chamadas de API para funil, campanhas e ativos não estão funcionando.

**Ação necessária:** Reautenticar em https://mcp.rdstationmentor.com/marketing → clicar "Conectar neste servidor" → completar fluxo OAuth → atualizar config.yaml → `/reload-mcp`.

Alternativa: usei Google Analytics 4 via Composio (conexão ativa).

---

## CONAMORE Hotelaria OFICIAL — Visão Geral (GA4)

### Tráfego Diário

| Data | Usuários | Sessões | Pageviews | Taxa Engajamento | Taxa Rejeição |
|------|----------|---------|-----------|-----------------|--------------|
| 26/05 (Ter) | 1.300 | 1.686 | 6.958 | 51,3% | 48,7% |
| 27/05 (Qua) | 1.286 | 1.673 | 6.522 | 53,2% | 46,8% |
| 28/05 (Qui) | **1.508** | **1.939** | **7.084** | **54,2%** | 45,8% |
| 29/05 (Sex) | 1.246 | 1.608 | 5.769 | 53,9% | 46,1% |
| 30/05 (Sáb) | 1.217 | 1.500 | 4.800 | 50,0% | 50,0% |
| 31/05 (Dom) | 1.255 | 1.557 | 6.838 | 51,6% | 48,4% |
| 01/06 (Seg) | 1.412 | 1.831 | 6.109 | **1,97%⚠️** | 98,0%⚠️ |

**Totais 7 dias:** 9.224 usuários | 11.794 sessões | 44.080 pageviews
**Média diária:** 1.318 usuários/dia | 1.685 sessões/dia

> 🔴 **Anomalia em 01/06:** Taxa de engajamento caiu para 1,97% contra ~52% dos outros dias. Pode ser problema de rastreamento/fuso, não necessariamente tráfego real. Recomendo verificar implementação do GA4.

---

### Performance por Canal (Hotelaria)

| Canal | Usuários | Sessões | Pageviews | % do Tráfego |
|-------|----------|---------|-----------|-------------|
| **Cross-network** | 2.166 | 2.631 | 9.274 | 22,3% |
| **Direct** | 1.580 | 2.084 | 5.660 | 17,7% |
| **Organic Search** | 1.268 | 1.766 | 7.265 | 15,0% |
| **Paid Search** | 1.209 | 1.826 | 9.750 | 15,5% |
| **Unassigned** ⚠️ | 1.062 | 1.331 | 3.286 | 11,3% |
| **Display** | 902 | 956 | 1.356 | 8,1% |
| **Paid Social** | 690 | 971 | 2.269 | 8,2% |
| **Email (RD Station)** | 327 | 438 | 1.712 | 3,7% |
| **Organic Social** | 219 | 250 | 1.161 | 2,1% |
| **Paid Shopping** | 192 | 210 | 717 | 1,8% |
| **Demais** | 171 | 328 | 2.003 | 2,5% |

---

### Top Campanhas Pagas

| Campanha | Usuários | Sessões | Novos |
|----------|----------|---------|-------|
| 🥇 pmax_hotelaria_geral | 981 | 1.265 | 761 |
| 🥈 pmax_hotelaria_aquisicao | 579 | 697 | 484 |
| 🥉 display_communitas_google_hotelaria_cpc | 447 | 459 | 450 |
| search_communitas_google_institucional_hotelaria_cpa_ampla | 353 | 411 | 273 |
| search_communitas_google_geral_cpa_hotelaria | 346 | 402 | 313 |
| dgen_hotelaria_airbnb | 256 | 287 | 252 |
| dgen_communitas_google_hotelaria_purchase | 215 | 231 | 188 |
| Meta \| Vendas \| Lojas Conamore | 174 | 239 | 114 |
| shopping_hotelaria | 140 | 145 | 129 |

**Email Marketing:**
- Boletim Maio (2805_-_boletim_maio): 268 usuários | 341 sessões
- RD Station / email: 249 usuários (fonte) | 301 sessões

---

### LPS | Conamore Hotelaria (Landing Pages)

| Data | Usuários | Sessões | Pageviews | Engajamento |
|------|----------|---------|-----------|-------------|
| 26/05 | 74 | 90 | 110 | 42,2% |
| 27/05 | 89 | 99 | 117 | 30,3% |
| 28/05 | **152** | **168** | **214** | **46,4%** |
| 29/05 | 84 | 94 | 116 | 40,4% |
| 30/05 | 107 | 117 | 126 | 17,9% |
| 31/05 | 94 | 96 | 102 | 35,4% |
| 01/06 | 110 | 120 | 136 | 36,7% |

**Total LPS:** 618 usuários | 784 sessões | 921 pageviews
**Média:** 88 usuários/dia

---

## Alertas e Oportunidades

### 🔴 Crítico
1. **RD Station MCP offline** — sem acesso a dados de funil, conversões de leads, workflows e campanhas nativas. Impede reporte completo.
2. **Anomalia 01/06** — engajamento em 1,97% no Hotelaria. Verificar se é latência de dados ou tracking quebrado.

### 🟡 Atenção
3. **11,3% do tráfego "Unassigned"** — 1.062 usuários sem canal identificado. Revisar UTMs em tráfego de redes sociais e links compartilhados.
4. **`{campaignname}` sem resolução** — 216 usuários entrando com o placeholder literal. Campaign Manager/UTM template precisa de ajuste.
5. **Taxa de rejeição ~48%** consistente — esperada para tráfego pago, mas vale revisar qualidade das páginas de destino.

### 🟢 Oportunidades
6. **Paid Social crescendo** — 690 usuários. Campanhas Meta com 174 usuários. Vale escalar se CAC estiver saudável.
7. **Peak day na quinta-feira (28/05)** — maior volume da semana. Bom dia para disparos de email e campanhas.
8. **E-mail marketing sólido** — boletim de maio gerou 268 usuários com boa entrega. Próximo boletim deve manter.
9. **LPS com pico de 152 usuários** — landing pages funcionam bem em dias de campanha ativa.

---

## Recomendações para Hoje (02/06)

1. **[Prioridade]** Reautenticar RD Station MCP — seguir o passo a passo da skill rd-station-integration para renovar o token OAuth no rdstationmentor.com
2. **Investigar anomalia** de 01/06 — verificar se foi latência de dados ou problema real de tracking
3. **Ajustar UTMs** do tráfego "Unassigned" — cruzar com fontes de tráfego não identificadas
4. **Preparar próximo e-mail** — manter frequência de boletins que mostraram bom engajamento
5. **Monitorar kickoff de campanhas** — quinta-feira (28/05) foi o melhor dia, alinhar próximos disparos para quinta

---

*Relatório gerado por Flávia — Gerente de Marketing | Lojas Conamore*
*Dados: Google Analytics 4 (Composio) → CONAMORE Hotelaria OFICIAL (G-V0KMM7L6M6)*
