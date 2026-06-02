# 🧠 Oracle e DEBX — Treinamento de Agentes

Este documento é a referência compartilhada para todos os agentes que precisam consultar o ERP **DEBX** em banco de dados **Oracle**.

## Objetivo

Garantir que todos os agentes consigam fazer consultas operacionais com segurança, clareza e consistência, sem depender de conhecimento improvisado.

## Princípios de uso

- Priorize **consultas de leitura** (`SELECT`).
- Nunca faça alterações de dados sem autorização explícita.
- Valide sempre a pergunta de negócio antes de montar a consulta.
- Quando houver dúvida sobre tabela, coluna, relacionamento ou permissão, acione o **Matias**.
- Prefira consultas objetivas, com filtros e recortes bem definidos.
- Evite consultas pesadas sem necessidade; se a análise puder ser feita com menos linhas, melhor.

## O que cada agente deve saber

- Como identificar a informação certa no ERP antes de consultar.
- Como formular a necessidade em linguagem de negócio.
- Como pedir apoio técnico quando a estrutura do dado não estiver clara.
- Como interpretar o resultado sem assumir conclusões não confirmadas.

## Boas práticas de consulta em Oracle

- Use filtros por data, cliente, pedido, nota, filial ou outra chave de negócio quando possível.
- Inclua limitações de volume quando a pergunta permitir.
- Revise joins e condições para evitar duplicidade ou perda de registros.
- Trate datas e horários com cuidado, principalmente em relatórios operacionais.
- Sempre confirme se o resultado responde à pergunta original.

## Limites e segurança

- Não executar `INSERT`, `UPDATE`, `DELETE`, `MERGE`, `TRUNCATE` ou qualquer alteração em produção sem aprovação.
- Não expor credenciais, tokens ou conexões sensíveis em notas abertas.
- Não inventar nomes de tabelas ou colunas: valide com o Matias ou com documentação interna.

## Quando chamar o Matias

- Dúvida sobre schema, permissão ou estrutura do banco.
- Necessidade de performance, tuning ou análise de plano de execução.
- Problemas de acesso ao Oracle.
- Consultas que possam impactar a operação ou exigir validação técnica.

## Uso no trabalho diário

Sempre que um agente precisar consultar o DEBX:

1. transforme a pergunta de negócio em critérios objetivos;
2. escolha a menor consulta que responda à dúvida;
3. valide o resultado;
4. registre a conclusão de forma clara para a equipe.
