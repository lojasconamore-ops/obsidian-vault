# 🚨 Problema Crítico: Consent Mode Bloqueando GA4

**Data:** 03/08/2026  
**Status:** Crítico — Impactando métricas de engajamento  
**Prioridade:** Alta  
**Responsável:** Increazy (plataforma do site)

---

## 📋 Resumo Executivo

O **Consent Mode** do site Conamore está configurado para bloquear **todos** os cookies de analytics por padrão. Isso impede que o GA4 registre eventos de engajamento (scroll, click, time on page), resultando em:

- **Bounce rate de 98-100%** em todas as origens de tráfego
- **Engajamento de 1,9%** (vs média histórica de 56-61%)
- **Tempo médio inflado** (11m vs média de 3-5m)
- **Dados de conversão comprometidos**

---

## 🔍 Diagnóstico Técnico

### 1. Evidência no dataLayer

Ao carregar a homepage (https://www.conamore.com.br), o **primeiro comando** do dataLayer é:

```javascript
{
  "0": "consent",
  "1": "default",
  "2": {
    "ad_storage": "denied",
    "ad_user_data": "denied",
    "ad_personalization": "denied",
    "analytics_storage": "denied",        ← BLOQUEADO
    "personalization_storage": "denied",
    "functionality_storage": "granted",
    "security_storage": "granted",
    "wait_for_update": 500
  }
}
```

**Problema:** `analytics_storage: "denied"` impede o GA4 de registrar eventos de engajamento.

### 2. Evidência no GA4

#### Dados de 01/08/2026 (pico da anomalia):

| Origem (Source) | Sessões | Engajadas | Bounce | Tempo Médio |
|:---|:---:|:---:|:---:|:---:|
| **(not set)** | 830 | **0** | **100%** | 9m 39s |
| google | 501 | 12 | 97,6% | 6m 25s |
| (data not available) | 360 | 3 | 99,2% | 4m 27s |
| (direct) | 241 | 8 | 96,7% | 5m 18s |
| instagram | 58 | 1 | 98,3% | 1m 07s |
| **Total** | **1.334** | **25** | **98,1%** | **11m 25s** |

#### Dados de 02/08/2026 (persistência):

| Origem (Source) | Sessões | Engajadas | Bounce | Tempo Médio |
|:---|:---:|:---:|:---:|:---:|
| **(not set)** | 520 | **0** | **100%** | 6m 37s |
| google | 274 | 3 | 98,9% | 7m 18s |
| (data not available) | 205 | 1 | 99,5% | 4m 31s |
| (direct) | 114 | 1 | 99,1% | 1m 56s |
| **Total** | **~1.200** | **~6** | **~99%** | **~7m** |

#### Comparação com período saudável (31/07/2026):

| Métrica | 31/07 (normal) | 01/08 (anômalo) | Variação |
|---------|:---:|:---:|:---:|
| Engajamento | 60,9% | **1,9%** | **-97%** |
| Bounce | 39,1% | **98,1%** | **+151%** |
| Tempo médio | 3m 31s | **11m 25s** | **+244%** |

### 3. Análise Hora a Hora (01/08/2026)

Origem `(not set)` — **ZERO engajamento em TODAS as 24 horas**:

| Hora | Sessões | Engajadas |
|:---:|:---:|:---:|
| 00h | 25 | 0 |
| 01h | 12 | 0 |
| 02h | 11 | 0 |
| ... | ... | 0 |
| 10h | 70 | 0 |
| 11h | 63 | 0 |
| ... | ... | 0 |
| 23h | 29 | 0 |
| **Total** | **830** | **0** |

**Conclusão:** Não é bot traffic pontual. É problema estrutural do Consent Mode.

---

## 🎯 Causa Raiz

O **banner de cookies da Increazy** está configurado para:

1. **Default-negar** todos os cookies de analytics
2. **Não disparar** `gtag('consent', 'update', { analytics_storage: 'granted' })` quando o usuário aceita
3. **Não ter** opção clara de "Aceitar todos" ou o botão não dispara o consent update

### Impacto técnico:

- O script do GA4 carrega (`G-V0KMM7L6M6` está ativo no GTM)
- O `config` é disparado (pageview inicial funciona)
- Mas **eventos de engajamento são bloqueados** (scroll, click, time on page)
- Sessões ficam abertas mas sem eventos → GA4 classifica como bounce
- Tempo médio infla (sessão não fecha → conta até timeout de 30min)

---

## 🔧 Solução Recomendada

### Para a Increazy:

**Ajustar o banner de cookies para:**

1. **Disparar consent update quando o usuário aceitar:**
```javascript
// Quando usuário clicar em "Aceitar cookies"
gtag('consent', 'update', {
  ad_storage: 'granted',
  analytics_storage: 'granted',
  ad_user_data: 'granted',
  ad_personalization: 'granted'
});
```

2. **Ter botão claro de "Aceitar todos"** que dispara o update acima

3. **Opcionalmente:** Implementar consent granular (usuário escolhe quais cookies aceita)

### Teste de validação:

Após a correção, verificar no console do browser:

```javascript
// Verificar se consent foi atualizado
window.dataLayer.push({
  'event': 'consent_update',
  'consent_status': 'granted'
});

// Verificar se eventos de engajamento voltaram a disparar
// (scroll, click, time on page devem aparecer no GA4 DebugView)
```

---

## 📊 Impacto Comercial

### Dados comprometidos:

- **Taxa de engajamento:** Subestimada em ~95%
- **Taxa de conversão:** Não é possível calcular corretamente
- **Tempo médio de sessão:** Superestimado (não reflete realidade)
- **Origem do tráfego:** Distorcida (muito `(not set)`)
- **ROI de campanhas:** Impossível calcular com precisão

### Período afetado:

- **Início:** Entre 31/07 e 01/08/2026
- **Status:** Persistente em 02/08/2026
- **Impacto:** Todos os dados de engajamento desde 01/08 são inválidos

### Ações necessárias:

1. **Corrigir Consent Mode** (Increazy)
2. **Validar correção** no GA4 DebugView
3. **Monitorar por 7 dias** para confirmar normalização
4. **Considerar reprocessamento** dos dados de 01/08 em diante (se possível via GA4)
5. **Comunicar time comercial** sobre limitação dos dados recentes

---

## 📎 Evidências Técnicas Anexadas

### 1. DataLayer completo (homepage):

```javascript
window.dataLayer = [
  {"0": "set", "1": "developer_id.dY2E1Nz", "2": true},
  {"event": "gtm.js", "gtm.start": 1785738672855},
  {"0": "consent", "1": "default", "2": {
    "ad_storage": "denied",
    "ad_user_data": "denied",
    "ad_personalization": "denied",
    "analytics_storage": "denied",
    "personalization_storage": "denied",
    "functionality_storage": "granted",
    "security_storage": "granted",
    "wait_for_update": 500
  }},
  {"event": "another_page", "ecommerce": {}},
  {"event": "gtm.dom"},
  {"event": "gtm.load"},
  {"0": "js", "1": "2026-08-03T06:31:17.140Z"},
  {"0": "config", "1": "G-V0KMM7L6M6", "2": {}},
  {"0": "event", "1": "RD Popup e WhatsApp", "2": {
    "rd_asset_id": 1582501,
    "rd_filter": "",
    "rd_action": "viewed"
  }}
];
```

### 2. Scripts GA4/GTM ativos:

- **GA4:** `https://www.googletagmanager.com/gtag/js?id=G-V0KMM7L6M6`
- **GTM:** `https://www.googletagmanager.com/gtm.js?id=GTM-MMGX8ZL`
- **LinkedIn Insight:** `https://snap.licdn.com/li.lms-analytics/insight.min.js`

### 3. Cookies presentes (mesmo com consent denied):

```
_gcl_au, _ga, _ga_V0KMM7L6M6, _ga_CDCKFVTR5M, _uetsid, _uetvid,
veels_uid, FPLC, _fbp, __trf.src, _clck, _clsk, rdtrk, conversion_id, cart_id
```

---

## 📞 Contato e Próximos Passos

**Responsável pela correção:** Increazy (suporte técnico da plataforma)  
**Prazo sugerido:** 24-48h (problema crítico)  
**Validação:** Flávia (Marketing) após correção

### Checklist de resolução:

- [ ] Increazy ajusta banner de cookies
- [ ] Consent update dispara corretamente
- [ ] GA4 DebugView mostra eventos de engajamento
- [ ] Monitoramento por 7 dias confirma normalização
- [ ] Relatório de impacto comercial finalizado
- [ ] Time comercial comunicado sobre limitação dos dados

---

**Documento criado por:** Flávia (Marketing)  
**Data:** 03/08/2026  
**Versão:** 1.0
