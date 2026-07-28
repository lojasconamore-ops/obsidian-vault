# Roteiro — consulta ShinePhone / Growatt

## Objetivo

Consultar a planta residencial da casa com foco em:
- status do dispositivo
- geração de hoje
- geração de ontem
- última atualização
- ponto de atenção

## Fonte técnica

- Biblioteca: `growatt_public_api.GrowattApi`
- Host: `https://openapi.growatt.com`
- Plant ID: `1350678`
- Planta: `Sergio Silva Ladeira`
- Dispositivo: `XZJ3BMA0K1`
- Datalogger: `ZOD5BM7104`

## Roteiro operacional

1. Carregar o token de acesso da sessão atual, sem persistir em nota.
2. Criar o cliente `GrowattApi` apontando para `https://openapi.growatt.com`.
3. Consultar o overview da planta.
4. Consultar a lista de dispositivos da planta.
5. Consultar o dispositivo principal para verificar se está online ou offline.
6. Registrar somente os dados estáveis e úteis para o briefing diário.

## Critério de leitura

- Se a planta responder e o dispositivo estiver offline, tratar o dado em tempo real como indisponível.
- Se houver leitura normal, reportar:
  - status
  - geração de hoje
  - geração de ontem
  - última atualização
  - observação objetiva

## Observação

Não gravar token, senha ou credencial na nota, memória ou skill.
