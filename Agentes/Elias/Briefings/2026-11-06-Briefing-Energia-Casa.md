# Energia da casa — 2026-11-06

- **Fonte:** API pública Growatt (`https://openapi.growatt.com`), planta `1350678` (`Sergio Silva Ladeira`), consulta em 06/11/2026 às 13:31:59 BRT.
- **Dispositivo `XZJ3BMA0K1`:** online (`status: 1`, `lost: false`), última atualização em 06/11/2026 às 13:26:59 BRT. Datalogger `ZOD5BM7104`.
- **Geração de ontem (05/11):** 21,4 kWh (histórico diário retornado pela API).
- **Geração de hoje (06/11):** 41,3 kWh (overview).
- **Mês:** 266,3 kWh; **ano:** 12.810,0 kWh; **total:** 72.847,5 kWh (overview).
- **Potência atual da planta:** 0,0 no overview (unidade não especificada); última atualização do overview em 06/11/2026 às 13:30:43 BRT (`GMT-3`).
- `device.power()` retornou 100, mas esse endpoint pode representar o percentual de potência ativa configurada, não a potência instantânea; não foi usado como geração em tempo real.
- **Atenção:** potência atual zero no overview apesar de o dispositivo aparecer online e ter gerado energia hoje; monitorar se persistir.

Credencial lida de variável de ambiente somente durante a consulta; não armazenada nesta nota.
