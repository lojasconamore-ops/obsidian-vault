# Revisão de token Telegram — Adrian e thiagoribeiro — 2026-11-06

**Janela:** 2026-11-06, 06:45 BRT. **Escopo:** somente leitura; nenhum token foi exibido ou alterado.

- Os perfis `adrian` e `thiagoribeiro` têm o **mesmo** `TELEGRAM_BOT_TOKEN` no `.env`.
- `getMe` no Bot API identificou o token como pertencente a `@adrian_conamore_bot` (bot ID 8818698418), não um bot de Thiago Ribeiro.
- O gateway Adrian (`hermes-gateway-adrian.service`) está ativo, PID 2491386; seu polling Telegram foi confirmado saudável às 05:10:42 BRT após o update.
- Não há serviço systemd nem processo de gateway para `thiagoribeiro`; não há `state.db` nem jobs cron nesse perfil. Thiago Ribeiro é humano, não um agente da frota.
- Conclusão: **duplicata de credencial em perfil inativo**, sem conflito de polling observado agora. Se o perfil for iniciado, dois consumidores do mesmo bot poderão disputar updates. A cópia também amplia a superfície de acesso ao token.
- Recomendação executada mediante autorização posterior do Sergio: removida somente a atribuição `TELEGRAM_BOT_TOKEN` de `~/.hermes/profiles/thiagoribeiro/.env`, com escrita atômica e preservação do modo `0600`. A leitura de volta confirmou ausência da atribuição no perfil humano e byte a byte inalterado o `.env` do Adrian. O gateway Adrian permaneceu `active/running`, PID 2491386; nenhum gateway foi reiniciado. Sem evidência de vazamento, não há indicação de rotacionar o token do bot Adrian.
