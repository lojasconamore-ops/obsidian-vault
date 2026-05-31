# 🔗 Checklist para Increazy — Correção de URLs e Redirecionamentos

**Data:** 30/05/2026
**Solicitante:** Conamore — Marketing Digital (Flávia)
**Prioridade:** Alta

---

## Contexto

O site conamore.com.br (plataforma Increazy) apresenta **21 URLs quebradas** no menu de navegação principal e páginas institucionais. Além disso, há **duplicidade de conteúdo** entre páginas com e sem extensão `.html`, o que prejudica o SEO.

**Impacto estimado:** mais de 20.000 acessos/mês caindo em páginas 404.

---

## 🔴 Solicitação 1 — Corrigir URLs do Menu Principal

Os links da navegação principal do site apontam para URLs que retornam **404**. Precisamos que as URLs dos menus sejam corrigidas para as abaixo:

| Item do Menu | URL Atual (ERRADA) | URL Correta |
|---|---|---|
| Lençóis | `/lencois` | `/lencol-para-hotelaria` |
| Toalhas | `/toalhas` | `/toalhas-para-hoteis-pousadas` |
| Colchas | `/colchas` | `/colchas-e-cobreleitos` |
| Edredons | `/edredons` | `/edredons-para-hotelaria` |
| Protetores | `/protetores` | `/protetores-de-colchao` |
| Cobertores | `/cobertores` | `/cobertor-hotelaria` |
| Amenities | `/amenities` | `/amenities-para-hotelaria` |

---

## 🟡 Solicitação 2 — Redirecionamentos 301 (Adicionar)

Mesmo corrigindo o menu, os URLs antigos podem estar indexados ou salvos em links externos. Pedimos a criação dos seguintes **redirecionamentos permanentes (301)**:

| URL de Origem | Destino |
|---|---|
| `/lencois` | `/lencol-para-hotelaria` |
| `/lencois.html` | `/lencol-para-hotelaria` |
| `/lencol-para-hotelaria.html` | `/lencol-para-hotelaria` |
| `/toalhas` | `/toalhas-para-hoteis-pousadas` |
| `/colchas` | `/colchas-e-cobreleitos` |
| `/edredons` | `/edredons-para-hotelaria` |
| `/protetores` | `/protetores-de-colchao` |
| `/cobertores` | `/cobertor-hotelaria` |
| `/amenities` | `/amenities-para-hotelaria` |
| `/hotelaria` | `/` (página inicial) |
| `/hospitalar` | `/` (página inicial) |
| `/casa` | `/` (página inicial) |
| `/blog` | `https://hotelaria.conamore.com.br/` |
| `/contato` | `/contatos` |
| `/sobre-nos` | `/quem-somos` |
| `/kit-airbnb` | `/enxoval-para-airbnb` |

---

## 🟡 Solicitação 3 — Subcategorias do Menu

Os sub-links do dropdown (Tamanho, Linha de Produto) precisam de correção. Os URLs atuais não funcionam sem `.html`.

| Menu | Sub-item | URL Atual | URL Correta |
|---|---|---|---|
| Lençóis > Linha de Produtos | (link pai) | `/lencol-para-hotelaria/linha-de-produto` | `/lencol-para-hotelaria/linha-de-produto.html` |
| Edredons | (link pai genérico) | `/edredons` | `/edredons-para-hotelaria` |
| Edredons > Tamanho | (link pai) | `/edredons-para-hotelaria/tamanho` | `/edredons-para-hotelaria.html/tamanho` |
| Edredons > Linha de Produto | (link pai) | `/edredons-para-hotelaria/linha-de-produto` | `/edredons-para-hotelaria.html/linha-de-produto` |
| Colchas > Por Tamanho | (link pai) | `/colchas-e-cobreleitos/por-tamanho-colcha` | `/colchas-e-cobreleitos/por-tamanho-colcha.html` |
| Colchas > Linha de Produto | (link pai) | `/colchas-e-cobreleitos/linha-de-produto` | `/colchas-e-cobreleitos/linha-de-produto.html` |

---

## 🟢 Solicitação 4 — Duplicidade de Conteúdo (Canonical)

As seguintes páginas existem em **duas versões** (com e sem `.html`), gerando conteúdo duplicado. É necessário:
- adicionar tag `<link rel="canonical">` apontando para a versão **sem .html**
- configurar redirect 301 da versão com `.html` para a versão sem

| Versão com `.html` | Versão Canônica |
|---|---|
| `/lencol-para-hotelaria.html` | `/lencol-para-hotelaria` |
| `/lencois.html` | `/lencol-para-hotelaria` |

---

## 📋 Instruções para Execução

1. **Corrigir os links no menu de navegação** (Admin Increazy → Configurações do Tema → Menu)
2. **Configurar redirecionamentos 301** (Admin Increazy → Redirecionamentos, ou via Cloudflare)
3. **Ajustar canonical tags** nas páginas com duplicidade
4. **Testar cada URL** após a correção para confirmar que retornam HTTP 200

---

## 📊 Anexo — Evidências

Capturas de tela e logs disponíveis mediante solicitação.

**Tráfego registrado no GA4 para URLs quebradas (últimos 30 dias):**
- `/lencois` — 3.451 page views (caindo em 404)
- `/lencois.html` — 2.141 page views
- `/lencol-para-hotelaria.html` — 8.198 page views (duplicada da versão sem .html)

---

*Documento gerado por Flávia — Marketing Digital Conamore*
