# Monitoramento — Clone Parasita radiotuzla.com

Propriedade alvo: `sc-domain:conamore.com.br`
Clone: `conamore.com.br.radiotuzla.com` (IP 94.72.141.240)
Descoberto: 17/06/2026 · Disavow + DMCA: 08/08/2026

## Linha do tempo

| Data | DNS | HTTP | Índice (busca) | Status |
|---|---|---|---|---|
| 17/06/2026 | resolve | 200 (servindo) | indexado | 🔴 ATIVO |
| 08/08/2026 | resolve | 200 (servindo) | indexado | 🔴 ATIVO |
| 17/08/2026 | resolve (94.72.141.240) | **503 Internal Server Error** | ainda indexado (Exa 1ª citação) | 🟡 EM PROGRESSO |

## Notas de execução (17/08/2026)

- DNS ainda resolve para 94.72.141.240 (confirmado via 8.8.8.8 e 1.1.1.1 — não é cache local).
- HTTP agora retorna **503 Internal Server Error** (nginx) na home e em paths profundos. O conteúdo do clone NÃO está mais sendo servido — backend/proxy derrubado. Antes servia conteúdo (200).
- Ainda aparece como 1ª citação na busca web (Exa), ou seja, permanece indexado.
- Limitação: a API do Search Console (via Composio) não expõe relatório de "domínios de referência/links" (só na UI do GSC). Semrush/Ahrefs (que têm esse dado) estão sem conexão ativa. Não verificável programaticamente este ciclo.

## Próximo passo

Aguardar o Google re-rastrear o clone (agora 503) e desindexar. Pode levar semanas. Se o 503 persistir, a desindexação é esperada mesmo com o disavow processando em paralelo.
