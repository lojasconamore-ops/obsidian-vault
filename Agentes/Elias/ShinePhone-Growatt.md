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
- Geração de ontem: **26,0 kWh**
- Geração mensal: **889,9 kWh**
- Geração anual: **8.771,3 kWh**
- Geração total: **68.808,8 kWh**
- Última atualização vista na conversa: **2026-07-28 13:36:13**

## Última consulta executada nesta sessão

- **Planta:** respondeu normalmente no host `https://openapi.growatt.com`
- **Overview da planta:**
  - current power: `0.0`
  - today energy: `0.0`
  - monthly energy: `889.9`
  - yearly energy: `8771.3`
  - total energy: `68808.8`
  - last update time: `2026-07-28 13:36:13`
- **Lista de dispositivos:** 1 dispositivo
  - device SN: `XZJ3BMA0K1`
  - datalogger SN: `ZOD5BM7104`
  - last update time: `2026-07-28 13:36:55`
  - status: **offline** / `DEVICE_OFFLINE`
- **Observação:** a consulta de potência em tempo real falhou com `DEVICE_OFFLINE`; isso confirma que a planta responde, mas o dispositivo não entrega telemetria ao vivo.

## Padrão de acesso

1. Autenticar no portal Growatt/ShinePhone.
2. Ler o overview da planta primeiro.
3. Conferir a lista de dispositivos.
4. Se o dispositivo estiver offline, tratar a geração em tempo real como indisponível.

## Observações

- A API responde por planta mesmo quando o dispositivo está offline.
- Não persistir token, senha ou credencial em nota, memória ou skill.
- Se precisar de leitura futura, o token deve ser obtido na sessão/portal no momento do uso.
