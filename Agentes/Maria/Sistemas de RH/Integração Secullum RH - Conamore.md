# Integração Secullum RH — Conamore

## Situação

- **Sistema:** Secullum RH Ultimate / API histórica Ponto Web — Integração Externa.
- **Conta técnica:** `ti@conamore.com.br`.
- **Usuário no Secullum RH:** TI Hermes, tipo Usuário.
- **Integração externa:** habilitada e usuário autorizado.
- **Ativação da Conta Secullum:** concluída por Sérgio em 15/08/2026, por meio do link recebido por e-mail.
- **Estado atual:** autenticação e autorização da API validadas com sucesso em 15/08/2026 às 06:48 BRT; banco `66279` acessível em modo somente leitura.

## Prova de conexão — 15/08/2026

- Banco autorizado: `66279` — **CONAMORE SSL CAMA MESA E BANHO LTDA**.
- `GET Empresas`: sucesso — 6 registros.
- `GET Departamentos`: sucesso — 15 registros.
- `GET Funcoes`: sucesso — 45 registros.
- Nenhuma operação de escrita ou exclusão foi executada.
- Próxima validação: confrontar essas quantidades e uma amostra cadastral com relatórios/telas oficiais do Secullum antes de automatizar indicadores.

## Segurança e LGPD

- Não registrar senha, token, CPF, PIS ou dados individuais nesta nota.
- Não enviar senha pelo Telegram ou e-mail.
- Credencial local em `~/.hermes/profiles/maria/secrets/secullum.json`, com permissão `600`.
- Scripts em `~/.hermes/profiles/maria/scripts/secullum/`.
- A fase inicial permite apenas consultas de leitura.

## Procedimento de ativação técnica

No terminal do servidor Hermes, executar:

```bash
python3 ~/.hermes/profiles/maria/scripts/secullum/setup_credentials.py
python3 ~/.hermes/profiles/maria/scripts/secullum/client.py list-banks
```

O primeiro comando solicita a senha sem exibi-la. O segundo autentica e lista apenas os bancos Ponto Web autorizados, sem mostrar o token.

Após a prova de conexão:

```bash
python3 ~/.hermes/profiles/maria/scripts/secullum/client.py list-companies
python3 ~/.hermes/profiles/maria/scripts/secullum/client.py list-departments
python3 ~/.hermes/profiles/maria/scripts/secullum/client.py list-functions
```

Se houver mais de um banco autorizado, informar `--bank-id ID`.

## Validação obrigatória antes da automação

1. Confirmar autenticação e banco autorizado.
2. Consultar amostra mínima somente de leitura.
3. Comparar a amostra com relatório oficial emitido pelo Secullum.
4. Confirmar empresas/unidades e regras de competência.
5. Só depois automatizar conferência de ponto e alertas.

## Referências oficiais

- [Exemplo oficial de Integração Externa](https://github.com/Secullum/PontoWebIntegracaoExternaExemplo)
- [Documentação da API](https://pontowebintegracaoexterna.secullum.com.br/docs/index.html)
