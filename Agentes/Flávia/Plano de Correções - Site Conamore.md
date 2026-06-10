# Plano de Correções — Site Conamore

**Data:** 10/06/2026
**Base:** auditoria rápida da home `www.conamore.com.br`

## 1) Prioridade crítica: higiene técnica de URL
- Corrigir o link interno `http://hotelaria.conamore.com.br/` para **HTTPS**.
- Validar se há outros links internos ainda em HTTP.
- Testar retorno final com `curl -I -L`.

**Critério de aceite**
- Nenhum link interno principal deve apontar para HTTP.
- Todos os destinos estratégicos devem responder `200` ou `301` para a URL correta.

## 2) Prioridade alta: SEO on-page da home
- Trocar o title genérico `Inicial | Conamore` por algo mais comercial e pesquisável.
- Manter a proposta de valor B2B já boa no H1.
- Revisar meta description para incluir diferenciais e CTA.

**Sugestão de título**
- `Enxoval para Hotelaria, Casa e Hospitalar | Conamore`

## 3) Prioridade alta: metadados sociais e compartilhamento
- Adicionar:
  - `og:title`
  - `og:description`
  - `og:image`
  - `twitter:card`
- Se possível, incluir URL canônica social e imagem específica da home.

**Critério de aceite**
- Link compartilhado em WhatsApp/redes precisa gerar preview bonito e consistente.

## 4) Prioridade alta: estrutura para SEO rico
- Implementar `JSON-LD` na home.
- Começar com `Organization` e, se fizer sentido, `WebSite`.
- Avaliar `Product`/`BreadcrumbList` nas categorias e produtos.

## 5) Prioridade média: limpeza visual e foco da primeira dobra
- Revisar densidade de elementos na primeira dobra.
- Reduzir competição entre menu, toast/popup, hero e carrosséis.
- Ajustar o timing de qualquer popup/aviso para não brigar com a oferta principal.

**Objetivo**
- A home precisa vender mais rápido e com menos ruído.

## 6) Prioridade média: acessibilidade e qualidade de mídia
- Corrigir imagens sem `alt`.
- Revisar peso das imagens da home.
- Validar lazy loading e tamanhos reais dos assets.

## 7) Prioridade média: performance e peso técnico
- Revisar os **50 scripts** carregados na home.
- Identificar scripts essenciais vs. scripts que podem ser adiados.
- Medir impacto de cada terceiro no tempo de carregamento.

## Ordem recomendada de execução
1. Corrigir HTTP/HTTPS e links internos
2. Ajustar title, meta description e OG tags
3. Inserir JSON-LD
4. Revisar primeira dobra e popups
5. Corrigir alt text e otimizar mídia
6. Reduzir scripts e peso técnico

## Validação final
Após as mudanças, refazer:
- `curl -I -L` na home e nos principais links
- inspeção do HTML para metadata
- teste visual da primeira dobra no navegador
- checagem de preview em WhatsApp/Telegram

## Observação
A base comercial do site está boa. O problema agora não é oferta — é **higiene técnica + clareza de compartilhamento + foco visual**.
