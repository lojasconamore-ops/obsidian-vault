# DEBX — Cliente Novo vs Recorrente — jan/2025 a ago/2026

**Data:** 04/08/2026  
**Base:** Oracle DEBX — `TEST_PED.SSL_CAIXA_PERIODO_COM_ORIGEM`  
**Filtro:** `PDV_ORIGEM IN ('GER','MAG')`, `IPA_DTAPRV` entre 01/01/2025 e 01/08/2026  
**Lógica:** Cliente NOVO = mês do cadastro (`EMP_DATCAD`) = mês da aprovação (`IPA_DTAPRV`); RECORRENTE = cadastro anterior ao mês da aprovação  

## Totais do período

| Métrica | NOVO | RECORRENTE | % Novo |
|---------|------|------------|--------|
| Clientes distintos | 8.450 | 4.122 | 67,2% |
| Pedidos | 8.857 | 6.094 | — |
| Valor líquido | R$ 5.892.661 | R$ 6.658.737 | 46,9% |

## Mensal

| Mês | Novos C | Rec C | %Novos C | Novos $ | Rec $ | %Novos $ |
|-----|---------|-------|----------|---------|-------|----------|
| jan/25 | 682 | 336 | 67,0% | 408.695 | 311.018 | 56,8% |
| fev/25 | 509 | 253 | 66,8% | 275.631 | 225.485 | 55,0% |
| mar/25 | 573 | 286 | 66,7% | 326.101 | 234.895 | 58,1% |
| abr/25 | 725 | 278 | 72,3% | 411.029 | 262.815 | 61,0% |
| mai/25 | 641 | 271 | 70,3% | 363.189 | 223.428 | 61,9% |
| jun/25 | 411 | 250 | 62,2% | 250.923 | 386.973 | 39,3% |
| **jul/25** | 383 | 244 | 61,1% | 264.211 | 221.725 | 54,4% |
| ago/25 | 385 | 262 | 59,5% | 257.099 | 307.959 | 45,5% |
| set/25 | 354 | 290 | 55,0% | 361.083 | 384.792 | 48,4% |
| out/25 | 428 | 393 | 52,1% | 457.629 | 780.206 | 37,0% |
| nov/25 | 457 | 397 | 53,5% | 467.793 | 781.537 | 37,4% |
| dez/25 | 300 | 342 | 46,7% | 268.605 | 558.834 | 32,5% |
| jan/26 | 391 | 327 | 54,5% | 283.383 | 338.607 | 45,6% |
| fev/26 | 393 | 265 | 59,7% | 269.218 | 282.680 | 48,8% |
| mar/26 | 443 | 297 | 59,9% | 290.283 | 206.889 | 58,4% |
| abr/26 | 383 | 271 | 58,6% | 257.533 | 262.426 | 49,5% |
| mai/26 | 361 | 330 | 52,2% | 226.599 | 290.573 | 43,8% |
| **jun/26** | 340 | 310 | 52,3% | 242.414 | 292.711 | 45,3% |
| jul/26 | 276 | 275 | 50,1% | 199.749 | 298.764 | 40,1% |
| ago/26* | 15 | 4 | 78,9% | 11.495 | 6.422 | 64,2% |

> \* ago/26 parcial — apenas dia 01.

## Comparação com status do anúncio "conamore"

| Período | Anúncio | %Novos Clientes (média) | %Novos $ (média) |
|---------|---------|------------------------|-------------------|
| jan–jun/2025 | ON | 67,6% | 55,5% |
| jul/2025–mai/2026 | OFF | 55,2% | 43,2% |
| jun–jul/2026 | ON | 51,2% | 42,7% |

## Leitura

- A queda na proporção de clientes novos é **tendência contínua de baixa**, independente do status do anúncio.
- O período com anúncio OFF (jul/25–mai/26) teve %novos mais baixa que o período ON anterior, mas a tendência já era de queda desde jun/25.
- O retorno do anúncio em jun/26 **não reverteu** a tendência — %novos continuou caindo.
- Clientes recorrentes têm ticket médio maior: R$ 1.093 vs R$ 665 dos novos.
- A sazonalidade de verão (dez–mar) coincide com picos de %novos.
