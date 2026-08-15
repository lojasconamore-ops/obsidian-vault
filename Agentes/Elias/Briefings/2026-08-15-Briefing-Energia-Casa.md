# Energia da casa — 2026-08-15

- **Planta:** Sergio Silva Ladeira (`1350678`)
- **Fonte:** API pública Growatt (`growatt_public_api`, `https://openapi.growatt.com`)
- **Consulta:** 15/08/2026 13:31 BRT
- **Status do dispositivo:** offline (`lost=true`, status `-1`)
- **Geração de ontem (14/08/2026):** 0,0 kWh
- **Geração de hoje:** 0,0 kWh
- **Geração mensal:** 0,0 kWh
- **Geração anual:** 8.806,8 kWh
- **Geração total:** 68.844,3 kWh
- **Potência atual informada no overview:** 0,0 kW
- **Atualização da planta:** 29/07/2026 14:16:17 BRT
- **Última atualização do dispositivo:** 29/07/2026 14:05:30 BRT
- **Potência em tempo real do dispositivo:** indisponível; a API retornou `DEVICE_OFFLINE`.
- **Atenção:** o equipamento permanece offline e sem nova telemetria desde 29/07; os 0,0 kWh de ontem e hoje foram confirmados pela API, mas não há leitura em tempo real.

## Nova consulta ao vivo — teste solicitado por Sergio

- **Consulta:** 15/08/2026 14:49 BRT
- **Status confirmado pela telemetria do inversor:** online / normal (`status=1`, sem falha ou alerta)
- **Geração de ontem (14/08/2026):** 37,9 kWh
- **Geração de hoje no overview:** 35,4 kWh
- **Potência atual do inversor:** 5,0842 kW (`pac`), às 14:50:11 BRT
- **Geração mensal:** 566,0 kWh
- **Geração anual:** 9.448,8 kWh
- **Geração total:** 69.486,3 kWh
- **Atualização do overview:** 15/08/2026 14:46:51 BRT
- **Observação técnica:** `plant.list_devices` retornou `status=-1`, mas `lost=false`; a leitura realtime do inversor respondeu em seguida com `status=1`, `Normal`, 5,0842 kW e timestamp atual. Para o status executivo, prevaleceu a telemetria mais recente e específica do dispositivo.
