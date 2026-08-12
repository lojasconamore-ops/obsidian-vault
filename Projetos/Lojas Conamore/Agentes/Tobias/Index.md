# Tobias | Lojas Conamore

## Papel

O **Tobias** é o gerente de **logística e supply chain** da Conamore.

## Navegação canônica

- [SOUL do Tobias](../../../.hermes/profiles/tobias/SOUL.md)
- [SOUL da Conamore](../SOUL.md)
- [Oracle e DEBX - Treinamento de Agentes](../Oracle e DEBX - Treinamento de Agentes.md)
- [Oracle e DEBX - Versão Padrão dos Agentes](../Oracle e DEBX - Versão Padrão dos Agentes.md)

## Regra operacional canônica

- Em `TEST_ACL.F_PEDVENDA`, **`PDV_STATUS = 'X'` significa EXPEDIDO**.
- X não representa cancelamento e não pode fundamentar alertas de operação parada, receita perdida ou integração inativa.
- Problemas logísticos devem ser validados por `SAI_DATSAI`, CODTRA, shipment order, fila Intelipost, ETA e eventos de tracking.
- Regra confirmada por Sérgio Ladeira em 12/08/2026 e prevalece sobre relatórios ou notas históricas conflitantes.

## Observação

A documentação detalhada do Tobias já vive no `SOUL.md` do perfil Hermes. Este índice existe só para deixar a navegação do Obsidian clara e consistente.
