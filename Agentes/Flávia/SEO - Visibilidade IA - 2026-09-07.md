# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 07/09/2026, 09:01–09:04 BRT  
**Escopo planejado:** Gemini direto, 15 prompts fixos × 2 rodadas = 30 submissões  
**Fonte de evidência:** `Direct platform` — tentativa de acesso à interface  
**Status:** **BLOQUEADO OPERACIONALMENTE** — navegador de automação indisponível; 0/30 prompts submetidos.

---

## Resumo executivo

O ciclo não produziu nova medição de visibilidade. Duas tentativas independentes de abrir `https://gemini.google.com/app` falharam antes do carregamento: o endpoint do navegador de automação em `localhost:9222` recusou conexão após 30 segundos. Nenhum prompt foi enviado e nenhuma resposta do Gemini foi observada.

Uma rota alternativa pelo `computer_use` também foi verificada: o host não tem navegador gráfico em execução nem janela disponível. A inspeção do sistema confirmou ainda que não há executável Chrome/Chromium/Firefox disponível, não há `DISPLAY`/`WAYLAND_DISPLAY` e não existe processo ouvindo na porta 9222.

Isso é **indisponibilidade da infraestrutura de navegação**, não resultado negativo da Conamore e não evidência atual de login/bloqueio do Gemini. Nenhuma plataforma proxy foi usada como substituta.

---

## Disponibilidade da plataforma

| Plataforma | Planejado | Testado | Status | Evidência |
|---|---:|---:|---|---|
| Gemini direto | 30 submissões | 0/30 | `not run` — ferramenta indisponível | Duas tentativas; CDP `localhost:9222` recusou conexão |
| ChatGPT | 0 | 0 | não executado | Fora do escopo prioritário; Gemini não chegou a ser executado |
| Perplexity | 0 | 0 | não executado | Fora do escopo prioritário |
| Copilot | 0 | 0 | não executado | Fora do escopo prioritário |

## Métricas do ciclo

| Métrica | Resultado |
|---|---:|
| Submissões válidas | 0/30 |
| Respostas observadas | 0/30 |
| Menções textuais | N/A — sem denominador testado |
| Menção ou fonte | N/A — sem denominador testado |
| Citações diretas de domínio Conamore | N/A — sem denominador testado |
| Recomendações explícitas | N/A — sem denominador testado |
| Concorrentes citados | N/A — nenhuma resposta observada |

---

## Matriz de evidência — prompt × rodada

| Rodada | # | Prompt exato | Status | Menção | URLs/concorrentes |
|---:|---:|---|---|---|---|
| 1 | 1 | `lençol para hotel` | not run | N/A | N/A |
| 1 | 2 | `qual o melhor lençol para hotel` | not run | N/A | N/A |
| 1 | 3 | `lençol profissional para pousada` | not run | N/A | N/A |
| 1 | 4 | `lençol para Airbnb` | not run | N/A | N/A |
| 1 | 5 | `enxoval para hotel` | not run | N/A | N/A |
| 1 | 6 | `onde comprar lençol para hotel` | not run | N/A | N/A |
| 1 | 7 | `fornecedor de lençol para hotéis` | not run | N/A | N/A |
| 1 | 8 | `lençol para hotel com pronta entrega` | not run | N/A | N/A |
| 1 | 9 | `fornecedor de enxoval hoteleiro em São Paulo` | not run | N/A | N/A |
| 1 | 10 | `onde comprar enxoval profissional para hotel` | not run | N/A | N/A |
| 1 | 11 | `quais empresas vendem lençol para hotel no Brasil` | not run | N/A | N/A |
| 1 | 12 | `compare fornecedores de enxoval para hotéis` | not run | N/A | N/A |
| 1 | 13 | `qual empresa fornece roupa de cama para pousadas` | not run | N/A | N/A |
| 1 | 14 | `Conamore é uma boa empresa para enxoval hoteleiro?` | not run | N/A | N/A |
| 1 | 15 | `empresa de enxoval para hotelaria` | not run | N/A | N/A |
| 2 | 1 | `lençol para hotel` | not run | N/A | N/A |
| 2 | 2 | `qual o melhor lençol para hotel` | not run | N/A | N/A |
| 2 | 3 | `lençol profissional para pousada` | not run | N/A | N/A |
| 2 | 4 | `lençol para Airbnb` | not run | N/A | N/A |
| 2 | 5 | `enxoval para hotel` | not run | N/A | N/A |
| 2 | 6 | `onde comprar lençol para hotel` | not run | N/A | N/A |
| 2 | 7 | `fornecedor de lençol para hotéis` | not run | N/A | N/A |
| 2 | 8 | `lençol para hotel com pronta entrega` | not run | N/A | N/A |
| 2 | 9 | `fornecedor de enxoval hoteleiro em São Paulo` | not run | N/A | N/A |
| 2 | 10 | `onde comprar enxoval profissional para hotel` | not run | N/A | N/A |
| 2 | 11 | `quais empresas vendem lençol para hotel no Brasil` | not run | N/A | N/A |
| 2 | 12 | `compare fornecedores de enxoval para hotéis` | not run | N/A | N/A |
| 2 | 13 | `qual empresa fornece roupa de cama para pousadas` | not run | N/A | N/A |
| 2 | 14 | `Conamore é uma boa empresa para enxoval hoteleiro?` | not run | N/A | N/A |
| 2 | 15 | `empresa de enxoval para hotelaria` | not run | N/A | N/A |

**Reconciliação:** esperado 30; submetido 0; respostas/evidências 0; não executado 30.

---

## Comparação com ciclos anteriores

O ciclo atual não é comparável porque não contém respostas válidas. O ciclo imediatamente anterior, em 31/08/2026, também ficou bloqueado pela mesma indisponibilidade do endpoint CDP. O último ciclo direto completo, com o mesmo conjunto de 15 prompts e duas rodadas, foi 08/08/2026.

| Ciclo | Gemini | R1 | R2 | Consolidado | Comparabilidade |
|---|---|---:|---:|---:|---|
| 08/08/2026 | 30/30 testados | 5/15 (33,3%) | 7/15 (46,7%) | média 6/15 (40,0%) | baseline completo |
| 31/08/2026 | 0/30 testados | N/A | N/A | N/A | não comparável |
| 07/09/2026 | 0/30 testados | N/A | N/A | N/A | não comparável |

Não há base para afirmar alta, queda ou estabilidade da visibilidade da Conamore neste ciclo.

---

## Evidência técnica

Tentativa 1 — nova sessão isolada:

```text
browser-harness: fatal: BU_CDP_URL=http://localhost:9222 unreachable after 30s:
<urlopen error [Errno 111] Connection refused>
```

Tentativa 2 — recuperação da aba e nova navegação:

```text
browser-harness: fatal: BU_CDP_URL=http://localhost:9222 unreachable after 30s:
<urlopen error [Errno 111] Connection refused>
```

Verificações alternativas no host:

```text
Chrome/Chromium/Firefox: nenhum executável encontrado
DISPLAY: vazio
WAYLAND_DISPLAY: vazio
Porta TCP 9222: sem processo ouvindo
computer_use: nenhum navegador gráfico ou janela disponível
```

---

## Leitura executiva

- Nenhum sinal novo foi obtido sobre presença, ausência, concorrentes ou citações da Conamore no Gemini.
- A repetição do mesmo bloqueio por dois ciclos consecutivos (31/08 e 07/09) caracteriza problema persistente na infraestrutura do job, não oscilação de visibilidade.
- O histórico válido permanece sendo 08/08/2026: média de 6/15 prompts com menção (40,0%), com forte variância entre rodadas.
- Próxima ação operacional: restaurar um Chrome/Chromium dedicado com CDP na porta 9222 para o profile `marketing`; depois repetir as 30 submissões completas.

---

## Status final

| Executado | Evidência | Status |
|---|---|---|
| Acesso direto ao Gemini | 2 tentativas; CDP recusou conexão | ⚠️ Bloqueado operacionalmente |
| Gemini R1 | 0/15 submissões | ❌ Não executado |
| Gemini R2 | 0/15 submissões | ❌ Não executado |
| Rota alternativa `computer_use` | Sem navegador/janela gráfica no host | ⚠️ Indisponível |
| Relatório Obsidian | `Agentes/Flávia/SEO - Visibilidade IA - 2026-09-07.md` | ✅ Salvo |

**Status analítico:** **BLOQUEADO** — ciclo sem amostra válida; não interpretar 0/30 como ausência da marca.

*Relatório gerado por Flávia (Marketing) em 07/09/2026, 09:04 BRT.*
