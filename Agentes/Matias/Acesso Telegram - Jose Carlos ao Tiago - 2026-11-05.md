# Acesso Telegram — José Carlos ao Tiago (Financeiro)

**Data:** 2026-11-05, 12:06–12:10 BRT. **Solicitante:** Sergio Ladeira. **Escopo:** permitir ao gerente do Financeiro José Carlos falar com o agente Tiago em mensagem privada no Telegram.

## Identificação e ação
- Nome e usuário informados pelo Sergio: José Carlos Silva, `@Jose_Carlos_Silva4`.
- O bot Tiago recebeu duas mensagens privadas desse ID e as bloqueou inicialmente: ID numérico `5185151933`.
- Conferência independente pelo Telegram Bot API `getChat(5185151933)` com token do próprio Tiago: `username=Jose_Carlos_Silva4`, `first_name=Jose Carlos`, `last_name=Silva`, `type=private`.
- Acrescentado **somente** `5185151933` ao `TELEGRAM_ALLOWED_USERS` do perfil `tiago` em `.env`. Usuários anteriores foram mantidos. Nenhuma credencial foi modificada ou copiada.
- Executado `systemctl reload hermes-gateway-tiago.service` (SIGUSR1 com reinício graceful do gateway Tiago). PID anterior `2372178`; novo PID `2455836`. Serviço `active/running`, polling do Telegram confirmado saudável às 12:09:58 BRT.

## Limites da verificação
- A configuração foi lida de volta e o gateway reconectou; ainda não houve mensagem **nova de José Carlos após o reinício** para comprovar o fluxo fim a fim. Solicitar um teste simples ao usuário se preciso.
- Não alterados outros agentes, lista de grupos, contas ou permissões fora do bot Tiago.
