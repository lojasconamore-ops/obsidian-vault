# Revisão de token Telegram — Adrian e thiagoribeiro — 2026-11-06

**Janela:** 2026-11-06, 06:45 BRT. **Escopo:** somente leitura; nenhum token foi exibido ou alterado.

- Os perfis `adrian` e `thiagoribeiro` têm o **mesmo** `TELEGRAM_BOT_TOKEN` no `.env`.
- `getMe` no Bot API identificou o token como pertencente a `@adrian_conamore_bot` (bot ID 8818698418), não um bot de Thiago Ribeiro.
- O gateway Adrian (`hermes-gateway-adrian.service`) está ativo, PID 2491386; seu polling Telegram foi confirmado saudável às 05:10:42 BRT após o update.
- Não há serviço systemd nem processo de gateway para `thiagoribeiro`; não há `state.db` nem jobs cron nesse perfil. Thiago Ribeiro é humano, não um agente da frota.
- Conclusão: **duplicata de credencial em perfil inativo**, sem conflito de polling observado agora. Se o perfil for iniciado, dois consumidores do mesmo bot poderão disputar updates. A cópia também amplia a superfície de acesso ao token.
- Recomendação: preservar a credencial do Adrian e, em mudança pontual autorizada, remover o token do perfil humano `thiagoribeiro`; sem evidência de vazamento, não há indicação de rotacionar o token do bot Adrian. Não reiniciar gateways nem alterar tokens durante esta revisão.
