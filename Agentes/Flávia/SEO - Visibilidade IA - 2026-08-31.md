# SEO — Visibilidade em IA — Conamore

**Data/hora do ciclo:** 31/08/2026, 09:01 BRT  
**Escopo planejado:** Gemini direto, 15 prompts fixos × 2 rodadas = 30 submissões  
**Fonte de evidência:** `Direct platform` (tentativa de acesso à interface)  
**Status:** BLOQUEADO OPERACIONALMENTE — automação do navegador indisponível; 0/30 prompts submetidos.

---

## Resumo executivo

O ciclo não produziu uma nova medição de visibilidade. Duas tentativas de abrir `https://gemini.google.com/app` falharam antes do carregamento porque o navegador de automação não estava disponível no host (`BU_CDP_URL=http://localhost:9222`, conexão recusada). Nenhum prompt foi enviado e nenhuma resposta do Gemini foi observada.

Isso é **indisponibilidade da ferramenta**, não resultado negativo da Conamore e não evidência de bloqueio/login do Gemini. Conforme o escopo deste ciclo, não foi usado Exa, iAsk ou outra plataforma como substituto.

---

## Disponibilidade da plataforma

| Plataforma | Planejado | Testado | Status | Evidência |
|---|---:|---:|---|---|
| Gemini direto | 30 submissões | 0/30 | `not run` — ferramenta indisponível | Duas tentativas; CDP em `localhost:9222` recusou conexão após 30s |
| ChatGPT | 0 | 0 | não executado | Fora do escopo/prioridade |
| Perplexity | 0 | 0 | não executado | Fora do escopo/prioridade |
| Copilot | 0 | 0 | não executado | Fora do escopo/prioridade |

## Métricas do ciclo

| Métrica | Resultado |
|---|---:|
| Submissões válidas | 0/30 |
| Respostas observadas | 0/30 |
| Menções textuais | N/A — sem denominador testado |
| Citações de domínio Conamore | N/A — sem denominador testado |
| Recomendações explícitas | N/A — sem denominador testado |
| Concorrentes citados | N/A — nenhuma resposta observada |

---

## Matriz prompt × rodada

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

## Comparação com ciclo anterior comparável

O ciclo atual não é comparável por não conter respostas válidas. Último ciclo Gemini direto completo com o mesmo desenho de 2 rodadas: **08/08/2026**.

| Ciclo | Gemini | R1 | R2 | Consolidado |
|---|---|---:|---:|---:|
| 08/08/2026 | 30/30 testados | 5/15 (33,3%) | 7/15 (46,7%) | média 6/15 (40,0%) |
| 31/08/2026 | 0/30 testados | N/A | N/A | não comparável |

Não há base para afirmar alta, queda ou estabilidade da visibilidade neste ciclo.

---

## Evidência técnica

Tentativa 1, sessão isolada:

```text
browser-harness: fatal: BU_CDP_URL=http://localhost:9222 unreachable after 30s:
<urlopen error [Errno 111] Connection refused>
```

Tentativa 2, sessão padrão com recuperação de aba:

```text
browser-harness: fatal: BU_CDP_URL=http://localhost:9222 unreachable after 30s:
<urlopen error [Errno 111] Connection refused>
```

Verificação local adicional: nenhum executável `google-chrome`, `chromium` ou `chromium-browser` foi encontrado para iniciar manualmente o endpoint CDP.

---

## Leitura executiva e próxima ação

- Não surgiu novo sinal sobre presença, ausência, concorrentes ou citações da Conamore no Gemini.
- O bloqueio é de infraestrutura do executor; o histórico anterior de login obrigatório do Gemini não foi reconfirmado hoje.
- Próximo teste: restaurar o Chrome de automação/CDP na porta 9222 e repetir integralmente as 30 submissões, sem misturar proxy ou outra plataforma no denominador Gemini.

---

## Status final

| Executado | Evidência | Status |
|---|---|---|
| Acesso direto ao Gemini | 2 tentativas; CDP recusou conexão | ⚠️ Bloqueado operacionalmente |
| Gemini R1 | 0/15 submissões | ❌ Não executado |
| Gemini R2 | 0/15 submissões | ❌ Não executado |
| Relatório Obsidian | `Agentes/Flávia/SEO - Visibilidade IA - 2026-08-31.md` | ✅ Salvo |

*Relatório gerado por Flávia (Marketing) em 31/08/2026, 09:01 BRT.*
