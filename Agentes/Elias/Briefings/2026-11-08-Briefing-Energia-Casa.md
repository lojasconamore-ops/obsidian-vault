# Energia da casa — 2026-11-08

- **Fonte:** API pública Growatt (`https://openapi.growatt.com`), planta 1350678 (`Sergio Silva Ladeira`), consulta às 13:32:39 BRT.
- **Dispositivo XZJ3BMA0K1:** online (`status: 1`, `lost: false`), atualização 08/11/2026 às 13:30:52 BRT. Datalogger `ZOD5BM7104`.
- **Geração de ontem (07/11):** 33,4 kWh (histórico diário da API).
- **Geração de hoje (08/11):** 13,3 kWh (overview).
- **Mês:** 330,6 kWh; **ano:** 12.874,3 kWh; **total:** 72.911,8 kWh.
- **Potência atual da planta:** 0,0 (overview; unidade não especificada); atualização do overview 08/11/2026 às 13:31:31 BRT (`GMT-3`).
- `device.power()` retornou `100`, mas o endpoint pode representar percentual de potência ativa configurada, não produção instantânea; não usar como geração em tempo real.
- **Atenção:** potência atual da planta indicada como zero, apesar do dispositivo online e da geração acumulada hoje; acompanhar se persistir.

Credencial utilizada apenas via variável de ambiente; não armazenada nesta nota.
