# ShinePhone / Growatt — acesso e identificadores

## Resumo

A integração da casa usa a nuvem da **Growatt/ShinePhone**. A leitura confirmada na conversa foi feita pela API pública `growatt_public_api.GrowattApi` com o host `https://openapi.growatt.com`.

## Identificadores estáveis já vistos

- **Plant ID:** `1350678`
- **Planta:** `Sergio Silva Ladeira`
- **Dispositivo:** `XZJ3BMA0K1`
- **Datalogger:** `ZOD5BM7104`

## O que a API mostrou na última leitura confirmada

- Status do dispositivo: **offline**
- Geração de hoje: **0,0 kWh**
- Geração mensal: **764,5 kWh**
- Geração total: **68.683,4 kWh**
- Última atualização vista na conversa: **2026-07-24 17:14:16**

## Padrão de acesso

1. Autenticar no portal Growatt/ShinePhone.
2. Ler o overview da planta primeiro.
3. Conferir a lista de dispositivos.
4. Se o dispositivo estiver offline, tratar a geração em tempo real como indisponível.

## Observações

- A API responde por planta mesmo quando o dispositivo está offline.
- Não persistir token, senha ou credencial em nota, memória ou skill.
- Se precisar de leitura futura, o token deve ser obtido na sessão/portal no momento do uso.
