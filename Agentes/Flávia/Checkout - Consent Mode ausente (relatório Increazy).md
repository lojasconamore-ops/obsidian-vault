# Relatório Técnico — Consent Mode ausente na página de Checkout (ERP)

**Data:** 28/08/2026
**Responsável:** Flávia (Marketing) — Lojas Conamore
**Destinatário:** Time Increazy / TI (Matias)
**Severidade:** Alta — risco LGPD + anúncios personalizados sem consentimento

---

## 1. Resumo executivo

A página de checkout **`www.conamore.com.br/erp-faturamento?i=<incSlug>`** (wrapper do checkout Increazy) **não dispara o Consent Mode**. Enquanto o restante do site (home e páginas padrão) envia corretamente o estado `denied` antes da escolha do usuário, o checkout roda em modo **implícito** — todas as tags de marketing/análise disparam a plena capacidade, com **anúncios personalizados ativos (`npa=0`)** e cookies de terceiros gravados **antes de qualquer consentimento**.

A causa raiz: o template da página de checkout **não carrega/executa o script do CMP** (banner LGPD) que existe no template padrão do site. O GTM até reconhece o CMP (developer ID `dY2E1Nz`), mas como o comando `consent default` nunca é disparado, o Google assume consentimento implícito.

---

## 2. Evidência — comparação Home vs Checkout

| Parâmetro | Home (correto) | Checkout (quebrado) | O que significa |
|---|---|---|---|
| Evento `consent default` no dataLayer | ✅ presente (`denied`) | ❌ **ausente** | Checkout nunca declara consentimento |
| `gcs` (Google Consent State) | `G100` | ❌ **ausente** | Checkout não informa estado de consentimento ao Google |
| `gcd` (Google Consent Decision) | `13p3p3p3p5l1` (`p`=negado) | `13l3l3l3l1l1` (`l`=indefinido) | Checkout fica em estado "indefinido/limited" |
| `npa` (non-personalized ads) | `1` (anúncios NÃO personalizados) | `0` (**anúncios personalizados ativos**) | Checkout serve ads personalizadas sem consentimento |
| `pscdl` (consent API) | `denied` | `noapi` (**API de consentimento nunca chamada**) | Checkout ignora a camada de consentimento |
| `gdid` (developer ID CMP) | `dY2E1Nz.dNzQzZD` | `dY2E1Nz` (sem sufixo de decisão) | CMP registrado, mas sem decisão de consentimento |
| `usedDefault` (estado GTM) | `true` | `false` | GTM do checkout nunca recebeu consent default |
| Banner LGPD | visível | **ausente** | Checkout não exibe banner |

**Leitura dos dados:** os parâmetros foram extraídos dos beacons reais via `performance.getEntriesByType('resource')`, com `google_tag_data.ics` lido no contexto da página.

---

## 3. Cookies de marketing gravados SEM consentimento (checkout)

| Cookie | Origem | Finalidade |
|---|---|---|
| `_ga`, `_ga_V0KMM7L6M6` | Google Analytics 4 (client) | Análise |
| `_ga_CDCKFVTR5M` | Google Analytics 4 (server-side) | Análise |
| `_gcl_au` | Google Ads | Conversão |
| `_fbp` | Meta (Facebook Pixel) | Publicidade |
| `_clck`, `_clsk` | Microsoft Clarity | Análise de sessão |
| `_uetsid`, `_uetvid` | Microsoft Bing UET | Publicidade |
| `rdtrk` | RD Station | Tracking de lead |
| `veels_uid` | Veels (Increazy) | Identificação |

---

## 4. Tags/vendors disparando sem consentimento

### Google (mais crítico)
| Tag | ID | Eventos observados |
|---|---|---|
| GA4 client-side | `G-V0KMM7L6M6` | `page_view`, `begin_checkout`, `scroll` |
| GA4 server-side | `G-CDCKFVTR5M` | `page_view`, `scroll` |
| GA4 server (gtmserver) | `G-V0KMM7L6M6` | `PageView` + ponte de dados Facebook |
| Google Ads conversion | `AW-1041572367` | `gtag.config`, `page_view`, `begin_checkout` (valor R$ 1.003,04) |
| Google Ads remarketing | `AW-1041572367` | `1p-user-list` + `rmkt/collect` |
| DoubleClick | — | `ad.doubleclick.net/ccm/s/collect` |

### Demais plataformas
| Vendor | ID | Eventos observados |
|---|---|---|
| Meta (Facebook Pixel) | `1586706054993486` | `fbevents.js` + `signals/config` |
| LinkedIn Insight | `pid=3429082` | `attribution_trigger`, `collect` (conversion 13431754) |
| Microsoft Bing UET | `ti=343046885` | `pageLoad`, `begin_checkout` |
| Microsoft Clarity | — | `r.clarity.ms/collect` |
| RD Station | conta `24333` | `pageview-notify`, popups, lead tracking |
| Cloudflare RUM | — | `cdn-cgi/rum` |

---

## 5. Por que isso acontece (causa técnica)

1. O checkout roda num **iframe** `checkout.app.increazy.com/increazy-ux/` embutido no wrapper `erp-faturamento`.
2. O **CMP** (Consent Management Platform / banner LGPD) é carregado pelo template padrão do site, mas **não é carregado no template do checkout**.
3. Sem o CMP, o comando `gtag('consent', 'default', {...denied...})` **nunca é executado**.
4. O GTM sobe em modo **implícito**: `ad_storage`, `analytics_storage`, `ad_user_data` e `ad_personalization` ficam `granted` por padrão.
5. Resultado: todas as tags disparam a plena capacidade, com `npa=0` (anúncios personalizados) e `pscdl=noapi` (sem chamada à API de consentimento).

---

## 6. Impacto

1. **LGPD** — coleta e compartilhamento de dados pessoais (cookies de publicidade/análise) sem consentimento, na página de maior valor comercial (finalização de pedido).
2. **Consent Mode v2 inoperante no funil de conversão** — sem `default denied`, o GA4/Google Ads não conseguem modelar conversões de usuários que recusam consentimento (o mecanismo de "conversion modeling" do Consent Mode v2).
3. **Anúncios personalizados sem base legal** — `npa=0` indica que o Google Ads está servindo anúncios personalizados com dados coletados sem consentimento.
4. **Inconsistência de métricas** — o checkout (etapa mais importante do funil) não respeita o mesmo regime de consentimento do resto do site.

---

## 7. Correção recomendada (time Increazy)

1. **Carregar o CMP no template do checkout** — incluir o script do banner LGPD + disparo de `consent default` na página `erp-faturamento` (e no iframe, se aplicável).
2. Garantir que o `consent default` seja disparado **antes** de `gtag('config')` e antes do carregamento do GTM (posicionar o script do CMP no `<head>`, antes do GTM).
3. Propagação do consentimento ao iframe — se o checkout roda em `checkout.app.increazy.com`, verificar se o consentimento do usuário é herdado do domínio pai (postMessage) ou se o CMP precisa rodar também dentro do iframe.
4. **Teste de aceite** — após correção, validar que ao recusar, o checkout passa a enviar `gcs=G100`, `npa=1`, `pscdl=denied` e `gcd=13p3p3p3p5l1` (mesmos valores da home).

---

## 8. Método de verificação

```javascript
// Na página de checkout, console:
window.dataLayer.filter(d => d[0] === 'consent')           // deve retornar consent default denied
window.google_tag_data.ics.usedDefault                      // deve ser true
window.google_tag_data.ics.entries.analytics_storage.default // deve ser false
```

E nos beacons: presença de `gcs=G100`, `npa=1`, `pscdl=denied`.

---

*Relatório gerado por Flávia (Marketing) com base em captura de rede e dataLayer via navegador automatizado (28/08/2026).*
