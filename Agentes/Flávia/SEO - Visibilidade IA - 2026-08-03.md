# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 03/08/2026 17:54 BRT  
**Escopo:** 15 prompts fixos, plataformas públicas acessíveis entre ChatGPT Search, Google AI/AI Mode, Perplexity, Gemini, Copilot e busca pública assistida por IA.  
**Objetivo:** medir menção, recomendação, citações, posição e concorrência sem confundir busca pública/indexada com resposta direta de uma plataforma.

## Resumo executivo

O único resultado direto observável neste ciclo foi obtido no **Gemini**, para o prompt 1. A resposta mencionou a Conamore como fornecedora de hotelaria, recomendou-a no contexto de compra B2B e citou diretamente a página de hotelaria da empresa.[1]

O acesso ao **ChatGPT** foi bloqueado por desafio Cloudflare; o **Perplexity** também apresentou verificação Cloudflare; a busca pública do **Google** retornou bloqueio automatizado; e o **Copilot** informou indisponibilidade na região. Portanto, não há resultado direto observável dessas plataformas neste ciclo. O Gemini estava acessível sem login para consulta direta, mas a execução completa dos 15 prompts e das três repetições por prompt não foi concluída neste ciclo; os prompts não executados estão explicitamente marcados abaixo como **não testados**, não como ausência de visibilidade.

## Métricas

| Métrica | Ciclo anterior — baseline Exa, 15 prompts | Este ciclo — Gemini direto, amostra válida de 1 prompt | Variação interpretável |
|---|---:|---:|---|
| Prompts com menção da Conamore no texto | 10/15 (66,67%) | 1/1 (100%) | Não comparável: amostras e plataformas diferentes |
| Prompts com menção da Conamore no texto ou fontes | 15/15 (100%) | 1/1 (100%) | Não comparável |
| Prompts com citação de domínio Conamore | 15/15 (100%) | 1/1 (100%) | Não comparável |
| Prompts com recomendação explícita | Não medido no baseline | 1/1 (100%) | Não há série histórica equivalente |
| Participação de voz frente aos concorrentes | Não medido | Não calculada de forma robusta | Amostra insuficiente |
| Posição média da marca em listas | Não medido | 2ª posição na frase de fornecedores do prompt 1 | Não há série histórica equivalente |

**Leitura correta:** os 100% do baseline são evidência de recuperação em uma busca pública assistida por IA/Exa, não de ranking universal no ChatGPT. O 100% deste ciclo é apenas a taxa da amostra direta Gemini de um prompt e não deve ser extrapolado para os 15 prompts.

## Plataformas e limitações

| Plataforma | Status | Evidência observada | Tratamento |
|---|---|---|---|
| ChatGPT Search | Bloqueado | Página pública exibiu desafio Cloudflare antes da consulta | Não testado diretamente; nenhum resultado inferido |
| Google AI/AI Mode | Bloqueado | Busca pública Google redirecionou para página de bloqueio automatizado | Não testado; nenhum resultado inferido |
| Perplexity | Bloqueado | Página exibiu “Performing security verification” e desafio Cloudflare | Não testado diretamente; nenhum resultado inferido |
| Gemini | Parcialmente testado | Consulta direta executada para o prompt 1 | Resultado registrado abaixo; 14 prompts restantes não testados neste ciclo |
| Copilot | Bloqueado por região | Página exibiu “Not available in your region” | Não testado; nenhum resultado inferido |
| Busca pública assistida por IA/Exa | Baseline anterior | 15 prompts, uma execução por prompt, conforme nota anterior | Usado apenas como comparação histórica, não como resultado atual |

## Registro por prompt

| # | Prompt exato | Gemini direto neste ciclo | Conamore mencionada | Recomendada | URL citada | Concorrentes / posição | Precisão e erros |
|---:|---|---|---|---|---|---|---|
| 1 | `lençol para hotel` | Testado em 03/08/2026 17:52 BRT | Sim | Sim, no contexto de fornecedores B2B | `https://www.conamore.com.br/lencol-para-hotelaria` | ParaHotel aparece antes; Conamore aparece em 2º na frase de fornecedores; Buettner e Karsten são citadas em outro trecho | A relação Conamore–hotelaria é coerente com o título da URL citada.[1] A resposta também traz alegações de materiais, pronta entrega ou especificações que não foram todas validadas nesta execução; marcar como revisão editorial, não como erro confirmado. |
| 2 | `qual o melhor lençol para hotel` | Não testado | — | — | — | — | Sem inferência |
| 3 | `onde comprar lençol para hotel` | Não testado | — | — | — | — | Sem inferência |
| 4 | `fornecedor de lençol para hotéis` | Não testado | — | — | — | — | Sem inferência |
| 5 | `empresa de enxoval para hotelaria` | Não testado | — | — | — | — | Sem inferência |
| 6 | `lençol profissional para pousada` | Não testado | — | — | — | — | Sem inferência |
| 7 | `lençol para hotel com pronta entrega` | Não testado | — | — | — | — | Sem inferência |
| 8 | `fornecedor de enxoval hoteleiro em São Paulo` | Não testado | — | — | — | — | Sem inferência |
| 9 | `quais empresas vendem lençol para hotel no Brasil` | Não testado | — | — | — | — | Sem inferência |
| 10 | `compare fornecedores de enxoval para hotéis` | Não testado | — | — | — | — | Sem inferência |
| 11 | `qual empresa fornece roupa de cama para pousadas` | Não testado | — | — | — | — | Sem inferência |
| 12 | `onde comprar enxoval profissional para hotel` | Não testado | — | — | — | — | Sem inferência |
| 13 | `Conamore é uma boa empresa para enxoval hoteleiro?` | Não testado | — | — | — | — | Sem inferência |
| 14 | `lençol para Airbnb` | Não testado | — | — | — | — | Sem inferência |
| 15 | `enxoval para hotel` | Não testado | — | — | — | — | Sem inferência |

## Evidência detalhada — Gemini, prompt 1

A resposta direta observada no Gemini descreveu critérios para compra profissional e afirmou: “Fornecedores como ParaHotel, Conamore ou distribuidores têxteis locais vendem kits em atacado/atacadinho focados em durabilidade industrial.” A interface exibiu uma fonte clicável da Conamore com o título **“Lençóis para Hotelaria e Airbnb - Conamore”**, apontando para a URL registrada abaixo.[1]

Isso é **resultado direto dentro do Gemini**, não uma inferência a partir do Google, Exa ou de uma busca indexada. A posição 2 é a ordem textual na frase de fornecedores, não uma posição universal de mercado.

## Comparação com o ciclo anterior

O arquivo anterior de baseline registrou 15 prompts em busca pública assistida por IA/Exa, com menção textual em 10/15, menção em texto ou fontes em 15/15 e citação de domínio Conamore em 15/15. Este ciclo não permite afirmar aumento ou queda: somente 1 dos 15 prompts foi executado diretamente no Gemini, enquanto as demais plataformas acessíveis foram bloqueadas por Cloudflare, bloqueio automatizado ou restrição regional.

**Mudança confirmada:** nenhuma mudança de visibilidade pode ser confirmada com rigor.  
**Hipótese operacional:** a página B2B de hotelaria continua semanticamente recuperável no Gemini para a intenção ampla “lençol para hotel”, mas é necessário completar o painel fixo antes de tirar conclusão sobre cobertura por intenção.

## Recomendações de conteúdo e SEO

1. Reforçar a página B2B de hotelaria com dados verificáveis sobre composição, gramatura, resistência a lavagens, tamanhos, pronta entrega, personalização e atendimento para hotéis e pousadas; cada alegação deve ter evidência na própria página.
2. Criar ou consolidar páginas/FAQ específicas para os prompts de compra e comparação: fornecedor, pronta entrega, São Paulo, Airbnb, pousada e comparação de enxoval.
3. Inserir tabelas HTML e dados estruturados com empresa, segmento, aplicação e diferenciais, evitando que sistemas de IA precisem inferir atributos comerciais.
4. No próximo ciclo, repetir os 15 prompts três vezes no Gemini, se o acesso permanecer disponível, e manter os bloqueios das outras plataformas registrados sem substituir resposta direta por proxy.
5. Monitorar se a resposta continua citando a URL B2B correta (`www.conamore.com.br`) em vez de páginas de varejo (`lojas.conamore.com.br`), preservando a separação entre Hotelaria e Casa.

## Status

**Parcialmente confirmado.** Há uma evidência direta e reproduzível de menção, recomendação contextual e citação da Conamore no Gemini para o prompt 1. O painel completo de 15 prompts e três repetições por prompt ficou incompleto por limitações de acesso e tempo de execução; não há base para declarar ausência de visibilidade nos prompts não testados.

## Sources

[1] [Lençóis para Hotelaria e Airbnb - Conamore](https://www.conamore.com.br/lencol-para-hotelaria)
