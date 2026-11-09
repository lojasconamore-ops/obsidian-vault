# SEO — Visibilidade em IA — Conamore — 09/11/2026

**Plataforma:** Gemini público, modo Flash-Lite, sem login. **Janela observada:** 09:03–09:14 BRT (horário por submissão nos registros brutos). **Escopo previsto:** 15 prompts fixos × 2 rodadas = 30 respostas independentes. **Status: PARCIAL — 3/30 respostas com conversa independente e evidência confiável.** ChatGPT, Perplexity e Copilot não executados.

## Incidente de qualidade e metodologia

Os prompts 1, 2 e 3 da primeira rodada foram enviados em conversas novas distintas, com URLs de sessão diferentes. Texto da resposta foi isolado do elemento `model-response message-content`; os chips de fonte foram removidos da cópia da prosa para distinguir menção textual de citação. A estabilização do texto foi observada antes da captura. Os metadados `jslog` dos chips exibiram URLs de fonte, mas **a caixa de detalhes das fontes não foi aberta** para confirmação visual do destino final.

Houve outras tentativas de envio (até P15 na rodada 1 e P4 na rodada 2), mas a ação visual de “New chat” não iniciou conversas novas: 17 registros adicionais usaram a mesma URL de conversa, com respostas acumuladas; em ao menos uma captura, a resposta anterior foi associada ao prompt seguinte. **Esses registros são exploratórios, excluídos de todas as métricas**; não equivalem a 17 testes independentes. Uma tentativa posterior de refazer em abas novas foi interrompida por timeouts do daemon do navegador (`Runtime.evaluate`, `Target.createTarget`, `Input.dispatchMouseEvent`). Logo, R1 P4–P15 e toda R2 ficam **não validados / não testados para o protocolo**, e não recebem “não” por ausência de menção. Os registros brutos temporários estão em `/home/sergio-ladeira/.hermes/profiles/marketing/cache/browser-use/workspace/cron_542783c5d7eb_0c5523e64a344e3babb718ea7a485c84/gemini-2026-11-09.jsonl`; a pasta de trabalho do browser não é evidência durável, razão pela qual os trechos e URLs auditáveis abaixo estão neste relatório.

## Matriz de evidências válidas

| Nº | Prompt exato | R1 — texto | R1 — fonte Conamore | R2 | Evidência da resposta |
|---:|---|---|---|---|---|
| 1 | `lençol para hotel` | não | sim, chips Conamore | não validado | “Escolher o lençol ideal para hotel, pousada ou locação por temporada (como Airbnb) exige equilibrar três fatores fundamentais: o conforto percebido pelo hóspede [...] a durabilidade [...] e a praticidade operacional [...]”. URL de sessão: `https://gemini.google.com/app/504d7e85fc427644` |
| 2 | `qual o melhor lençol para hotel` | não | não observada | não validado | “Para escolher o lençol de hotel perfeito [...] o segredo não é apenas olhar a quantidade de fios, mas sim o tipo de material, a trama e a qualidade [...]”. URL de sessão: `https://gemini.google.com/app/510c8890ba37c1b9` |
| 3 | `lençol profissional para pousada` | não | não observada | não validado | “Guia Completo: Escolhendo Lençóis Profissionais para Pousada [...]”. A prosa lista Karsten, Teka e Santista. URL de sessão: `https://gemini.google.com/app/2b8334f5916fc254` |
| 4–15 | demais prompts fixos do ciclo | **não validado** | **não validado** | **não validado** | Contexto acumulado e/ou browser indisponível; nenhum resultado classificável. |

**Métricas válidas da amostra parcial, Gemini somente:** menção na prosa **0/3**; menção ou fonte **1/3**; URL do domínio B2B em metadados de citação **1/3**; recomendação explícita da Conamore na prosa **0/3**. Amostra pequena, concentrada em Produto, **não extrapolável ao painel de 30**. Nenhuma resposta validada para o prompt de marca P14. Precisão factual e posição em lista não mensuradas. Os nomes de concorrentes citados em P3 são observação textual, não share of voice geral.

## URLs identificadas em chip de fonte do P1

- B2B Hotelaria: https://www.conamore.com.br/lencol-para-hotelaria
- Blog Hotelaria: https://hotelaria.conamore.com.br/como-escolher-os-melhores-lencois-para-sua-hospedagem-e-garantir-o-conforto-dos-hospedes/

Essas URLs constam no metadado do botão de fonte com rótulo “Conamore” na resposta direta do Gemini. **Não foram abertas na interface para validar redirecionamentos ou destino final.** A menção ocorre em chips de fonte, não no texto corrido do P1. Não há evidência de clique ou tráfego GA4.

## Comparação com 02/11 e ação

O ciclo [[SEO - Visibilidade IA - 2026-11-02]] concluiu 30/30, com 9/30 menções textuais (5/15 na primeira rodada e 4/15 na segunda). O ciclo atual tem apenas 3/30 respostas independentes válidas, portanto **não é comparável como tendência**. Evidência positiva pontual: a página B2B `/lencol-para-hotelaria` apareceu nos metadados de citação de P1, apesar de nenhuma menção da marca na prosa deste prompt. Reexecutar os 27 pares faltantes em sessões comprovadamente novas, checando uma única pergunta e uma única resposta por sessão antes de somar; abrir os detalhes dos chips de fonte. Não atribuir variação a SEO nem inferir tráfego.

**Executado | Evidência | Status:** Gemini direto 3/30 válidos | três URLs de sessão, trechos e URLs de fonte acima | **PARCIAL: navegador instável e contexto acumulado nas demais tentativas**.
