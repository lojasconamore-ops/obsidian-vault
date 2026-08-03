# Reteste GA4 — evolução da anomalia de tráfego

**Data do reteste:** 03/08/2026 08:56 BRT  
**Propriedade:** `properties/379729087`  
**Fuso do relatório:** `America/Sao_Paulo`  
**Dimensões:** date + sessionSource  
**Métricas:** sessions, engagedSessions, bounceRate, averageSessionDuration

## Resultado por dia

| Data | Sessões | Engajadas | Bounce | Tempo médio |
|---|---:|---:|---:|---:|
| 01/08/26 | 1.345 | 798 | 40,67% | agregado por origem |
| 02/08/26 | 2.040 | 9 | 99,56% | agregado por origem |
| 03/08/26* | 317 | 1 | 99,68% | agregado por origem |

\* 03/08 é parcial.

## 01/08/26 — estado atual por origem

- google: 886 sessões, 550 engajadas, bounce 37,92%
- (direct): 200 sessões, 100 engajadas, bounce 50,00%
- instagram: 70 sessões, 49 engajadas, bounce 30,00%
- linkedin: 40 sessões, 4 engajadas, bounce 90,00%
- (not set): 25 sessões, 13 engajadas, bounce 48,00%
- (data not available): 12 sessões, 10 engajadas, bounce 16,67%

## 02/08/26 — anomalia persistente

- (not set): 834 sessões, 0 engajadas, bounce 100%
- google: 480 sessões, 5 engajadas, bounce 98,96%
- (data not available): 346 sessões, 1 engajada, bounce 99,71%
- (direct): 205 sessões, 3 engajadas, bounce 98,54%

## 03/08/26 — anomalia ainda presente, dado parcial

- (not set): 142 sessões, 0 engajadas, bounce 100%
- google: 65 sessões, 1 engajada, bounce 98,46%
- (data not available): 56 sessões, 0 engajadas, bounce 100%
- (direct): 30 sessões, 0 engajadas, bounce 100%

## Conclusão

O quadro mudou: 01/08/26 deixou de apresentar o tráfego fantasma/generalizado reportado anteriormente e agora aparece com engajamento normalizado. A anomalia foi deslocada ou corrigida para esse dia no relatório atual.

O problema permanece claramente em 02/08/26 e continua em 03/08/26 (parcial), afetando simultaneamente google, direct, (not set) e (data not available). Isso continua sendo um sinal de falha de medição/qualidade de sessão, não de uma única origem.

O teste técnico feito no site em 03/08/26 confirmou que, após “Aceitar Tudo”, o Consent Mode atualiza analytics_storage para granted e o GA4 envia PageView. Isso comprova o caminho pós-consentimento, mas não explica sozinho o quadro de 02–03/08; ainda é necessário separar usuários que consentiram, usuários que não consentiram e eventual mudança de processamento/atribuição no GA4.
