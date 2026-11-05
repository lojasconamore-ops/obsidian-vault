# Energia da casa — 2026-11-05

- **Fonte:** API pública Growatt (`https://openapi.growatt.com`), planta 1350678 (`Sergio Silva Ladeira`), consulta às 13:31 BRT.
- **Dispositivo XZJ3BMA0K1:** online (`status: 1`, `lost: false`), última atualização 05/11/2026 às 13:31:04 BRT. Datalogger `ZOD5BM7104`.
- **Geração de ontem (04/11):** 61,8 kWh (histórico diário da API).
- **Geração de hoje (05/11):** 12,5 kWh (overview).
- **Mês:** 216,1 kWh; **ano:** 12.759,8 kWh; **total:** 72.797,3 kWh.
- **Potência atual da planta:** 0,0 (overview; unidade não especificada); última atualização da planta 05/11/2026 às 13:28:46 BRT (`GMT-3`).
- `device.power()` retornou 100, mas esse endpoint pode representar percentual de potência ativa configurada, não produção instantânea; não apresentar como geração em tempo real.
- **Atenção:** overview indica potência atual zero apesar de o dispositivo estar online e haver geração acumulada hoje; observar se persistir.

Credencial obtida de variável de ambiente durante a consulta; não armazenada aqui.
