# 📊 GA4 Diário — Loja Casa | 24/10/2026

**Propriedade:** `394358599` · `G-5709GFVVBK` · lojas.conamore.com.br  
**Dados:** 21/10/2026 (D-3) vs 20/10/2026 (D-4), fuso America/Sao_Paulo (BRT). Extração via GA4 Data API/Composio; sem D-1/D-0.

## Resumo executivo
1. Em 21/10, **134 usuários ativos e 155 sessões**: +61,4% e +80,2% ante 20/10.
2. Engajamento **79,4%**, +4,9 pontos percentuais; rejeição **20,6%**, -4,9 p.p.
3. **2.196 eventos** (+86,9%) e **928 visualizações** (+79,5%).
4. E-commerce registrou **3 transações** (-25,0%) e **R$ 961,04** (+4,0%); não está zerado.
5. Atenção a **5 sessões com landing page `(not set)`** (3,2% das sessões) e 2 sessões `(not set)` em novos/recorrentes; investigar consentimento/atribuição sem atribuir causa definitiva.

## Comparativo geral

| Indicador | 21/10 (D-3) | 20/10 (D-4) | Variação |
|---|---:|---:|---:|
| Usuários ativos | 134 | 83 | +61,4% |
| Sessões | 155 | 86 | +80,2% |
| Usuários novos | 107 | 56 | +91,1% |
| Visualizações de página/tela | 928 | 517 | +79,5% |
| Taxa de engajamento | 79,4% | 74,4% | +4,9 p.p. |
| Taxa de rejeição | 20,6% | 25,6% | -4,9 p.p. |
| Duração média da sessão | 4m 00s | 5m 38s | -29,0% |
| Eventos | 2.196 | 1.175 | +86,9% |
| Transações | 3 | 4 | -25,0% |
| Receita de compras | R$ 961,04 | R$ 923,68 | +4,0% |

*Variações calculadas a partir dos valores brutos da API; taxas arredondadas só na exibição. Receita em BRL conforme metadados da propriedade.*

## Novos vs recorrentes — 21/10

| Classificação GA4 | Usuários ativos | Sessões | Engajamento | Rejeição | Duração média |
|---|---:|---:|---:|---:|---:|
| new | 109 | 109 | 87,2% | 12,8% | 3m 42s |
| returning | 36 | 44 | 63,6% | 36,4% | 4m 57s |
| (not set) | 0 | 2 | 0,0% | 100,0% | 0m 00s |

*Usuários ativos por classificação não são somáveis para obter o total diário: um usuário pode transitar entre categorias. As 2 sessões sem classificação são ruído potencial de mensuração/consent mode, mas a causa não é demonstrada por esta consulta.*

## Canais — origem/mídia, 21/10 (top 15; 14 retornados)

| Origem / mídia | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| google / cpc | 28 | 34 | 64,7% |
| (direct) / (none) | 25 | 27 | 88,9% |
| google / organic | 24 | 25 | 84,0% |
| rd-email / email | 18 | 21 | 90,5% |
| linktr.ee / referral | 16 | 16 | 100,0% |
| RD Station / email | 8 | 8 | 75,0% |
| instagram / paid | 6 | 6 | 50,0% |
| chatgpt.com / ai-assistant | 4 | 4 | 75,0% |
| (not set) | 2 | 3 | 0,0% |
| app.octadesk.com / referral | 2 | 6 | 66,7% |
| IGShopping / Social | 1 | 1 | 100,0% |
| app.rdstation.email / referral | 1 | 2 | 100,0% |
| ig / paid | 1 | 1 | 100,0% |
| ig / social | 1 | 1 | 100,0% |

## Landing pages — 21/10 (top 10 de 49)

| Landing page | Usuários ativos | Sessões | Engajamento |
|---|---:|---:|---:|
| `/` | 61 | 67 | 91,0% |
| `/promocoes-lojas` | 9 | 9 | 77,8% |
| `/lencois` | 7 | 7 | 100,0% |
| `(not set)` | 5 | 5 | 0,0% |
| `/colchas` | 5 | 5 | 100,0% |
| `/toalha-de-rosto-aura-branca-50-80-cm-100-algodao` | 4 | 4 | 50,0% |
| `/hotel-em-casa` | 3 | 3 | 100,0% |
| `/lencois/tamanho.html/jogos-duplos` | 3 | 3 | 100,0% |
| `/edredons-para-casa` | 2 | 3 | 66,7% |
| `/jogo-de-lencol-solteiro-amore-3-pcs-150-fios-100-algod-o-azul-e-miami` | 2 | 2 | 50,0% |

## Dispositivos — 21/10

| Categoria | Usuários ativos | Sessões | Engajamento | Rejeição | Transações |
|---|---:|---:|---:|---:|---:|
| mobile | 91 | 100 | 80,0% | 20,0% | 1 |
| desktop | 41 | 53 | 77,4% | 22,6% | 2 |
| tablet | 2 | 2 | 100,0% | 0,0% | 0 |

## Observações e alertas
- Aumento de volume com melhora na taxa de engajamento, mas duração média caiu de 5m38s para 4m00s; não inferir causalidade só com dois dias.
- Transações caíram de 4 para 3 apesar da receita ligeiramente maior. Amostra pequena; acompanhar tendência antes de concluir mudança de conversão.
- Landing page `(not set)` concentrou 5 sessões sem engajamento (3,2% do dia). Verificar implementação de consentimento, `page_view`/`session_start` e identificação de landing page. As 2 sessões `(not set)` em `newVsReturning` reforçam o alerta de mensuração, sem provar origem comum.
- Origem/mídia tem `rd-email / email` e `RD Station / email`, além de variações de Instagram; padronização UTM pode reduzir fragmentação. Referências de `app.octadesk.com` e `app.rdstation.email` merecem revisão de auto-referência, sem reclassificar dados retroativamente.
- `google / cpc` lidera usuários ativos (28), mas seu engajamento de 64,7% fica abaixo de orgânico (84,0%). Recorte apenas Casa; sem mistura com Hotelaria ou Hospitalar.

**Fonte:** GA4 Data API, `properties/394358599`, consultas `runReport` por `date`, `newVsReturning`, `sessionSourceMedium`, `landingPage` e `deviceCategory`, extraídas em 24/10/2026. Os rankings são limitados ao top solicitado; usuários por dimensão não devem ser somados como usuários únicos do dia.

**Status:** Concluído.
