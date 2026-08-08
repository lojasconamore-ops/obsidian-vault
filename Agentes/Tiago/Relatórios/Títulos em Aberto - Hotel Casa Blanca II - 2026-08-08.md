# Títulos em Aberto — Hotel Casa Blanca II

**Cliente:** LUIZ LEMES MARTINS EIRELI HOTEL CASA BLANCA II  
**Nome fantasia:** HOTEL CASA BLANCA II  
**CNPJ:** 17.910.016/0001-34  
**Código DEBX:** A0030  
**Data da consulta:** 08/08/2026 (BRT)

## Resumo executivo

- **Schema com registros:** `TEST_MATRIZ`
- **Schemas verificados sem títulos do cliente:** `TEST_ACL`, `TEST_CHC`, `TEST_GCL` e `TEST_BRG`
- **Tabela de títulos:** `TEST_MATRIZ.F_TITULOS`
- **Critério de título parcelado:** `TIT_NUMPED`, `TIT_NUMPAR`, `TIT_DATVEN`, `TIT_DATPGT`, `TIT_VALORI` e `TIT_VALPAG`
- **Pedidos expedidos identificados no cadastro:** 15
- **Parcelas já pagas:** 44 títulos, total original de R$ 81.568,36
- **Títulos em aberto:** 7 parcelas
- **Saldo em aberto:** **R$ 18.363,54**
- **Vencidos em 08/08/2026:** nenhum
- **A vencer em 08/08/2026:** 7 parcelas, R$ 18.363,54

## Títulos em aberto

| Pedido | Parcela | Emissão | Vencimento | Valor em aberto | Situação |
|---|---:|---:|---:|---:|---|
| 0103309 | 3 | 19/05/2026 | 17/08/2026 | R$ 560,00 | A vencer |
| 0105155 | 3 | 01/06/2026 | 31/08/2026 | R$ 3.429,00 | A vencer |
| 0109411 | 2 | 01/07/2026 | 31/08/2026 | R$ 3.461,86 | A vencer |
| 0103309 | 4 | 19/05/2026 | 16/09/2026 | R$ 560,00 | A vencer |
| 0105155 | 4 | 01/06/2026 | 29/09/2026 | R$ 3.429,00 | A vencer |
| 0109411 | 3 | 01/07/2026 | 29/09/2026 | R$ 3.461,82 | A vencer |
| 0109411 | 4 | 01/07/2026 | 29/10/2026 | R$ 3.461,86 | A vencer |
| **Total** | **7** |  |  | **R$ 18.363,54** |  |

## Distribuição por pedido

- **Pedido 0103309:** 2 parcelas abertas — R$ 1.120,00
- **Pedido 0105155:** 2 parcelas abertas — R$ 6.858,00
- **Pedido 0109411:** 3 parcelas abertas — R$ 10.385,54

## Observações de controle

- Os registros de parcelas pagas apresentam `TIT_DATPGT` preenchido e `TIT_VALPAG` igual ao valor original.
- Os títulos em aberto apresentam `TIT_DATPGT` e `TIT_VALPAG` nulos; o saldo foi considerado igual a `TIT_VALORI`.
- Foram excluídos da contagem os registros-resumo sem `TIT_NUMPAR`, pois não são parcelas individuais de contas a receber.
- A consulta foi somente de leitura, sem alteração de dados.
- O saldo aberto é o saldo encontrado no Oracle na data/hora da consulta e deve ser atualizado antes de uma decisão de faturamento, pois pagamentos posteriores podem alterar a posição.

## Atualização para análise de crédito

- O cliente possui histórico recorrente e não apresenta parcela vencida na posição de 08/08/2026.
- Das 44 parcelas pagas, 22 foram pagas até o vencimento e 22 foram compensadas entre 1 e 3 dias após o vencimento.
- O atraso máximo observado foi de 3 dias e a média dos pagamentos com atraso foi de 1,68 dia.
- Interpretação: comportamento **bom e controlado, com pequena fricção de cobrança**, compatível com Classe B; não há evidência de inadimplência estrutural.
- A informação melhora o parecer, mas não elimina a exigência de entrada mínima de 25% nem substitui bureau e validação operacional online.
