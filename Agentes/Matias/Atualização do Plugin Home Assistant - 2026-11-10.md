# Atualização do plugin Home Assistant — 2026-11-10

- Escopo: perfil Hermes `matias`; executado `hermes plugins update homeassistant` após checagem de atualização.
- Origem anterior: commit `ba30cb0cf86c52bdb5cde98974bc062e97966529`; origem atual: `e7a218f26db88426ab3e7376f0e000b6e356f5e7`.
- O manifesto permanece na versão `2.0.1`; a descrição passou a mencionar `notify.<target>` para a entrega de cron.
- A primeira tentativa não interativa foi recusada pelo gate de consentimento de dependências Python (declaração `tzdata; platform_system == 'Windows'`), sem alterar o plugin. A atualização foi repetida em terminal interativo, com consentimento; terminou com código 0.
- Verificação posterior: `hermes plugins doctor homeassistant` passou (4 tools, 0 hooks); `hermes plugins check-updates --json` retornou `update_available: false` para o plugin.
- O gateway `hermes-gateway-matias.service` permaneceu ativo. Não foi reiniciado; o plugin roda dentro do processo e a nova versão só será carregada após reinício do gateway. A plataforma Home Assistant não está configurada como ativa no perfil Matias.
- Outros perfis e o plugin global não foram alterados por esta atualização.
