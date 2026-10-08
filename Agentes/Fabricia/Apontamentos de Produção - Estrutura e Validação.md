# Apontamentos de Produção — Estrutura e Validação

> Documento de referência para preenchimento da planilha de apontamentos a partir dos apontamentos manuais (papel) dos operadores.

## Fonte dos dados

- **Arquivo:** `OUTUBRO.xlsx` (e equivalentes mensais)
- **Local SMB:** `//172.169.0.3/dados/Compras/Fabrica - Projeto 2025/2026/<MES>/`
- **Aba:** `Apontamentos`

## Estrutura da aba "Apontamentos" (colunas A:AC)

| Col | Campo | Tipo | Observação |
|---|---|---|---|
| A | Colaborador | texto | nome do operador |
| B | Operacao | texto | categoria (Corte/Costura/Revisao/Embalagem) |
| C | Disponibilidade Bruta | hora | jornada disponível do dia (só 1ª linha do dia) |
| D | Dia | data | data completa |
| E | Hora inicio | hora | início da operação |
| F | Hora Fim | hora | fim da operação |
| G | Codigo | num/texto | código da operação |
| H | Sigla | texto | sigla da operação |
| I | Operacao (2) | texto | descrição da operação |
| J | Item | texto | código-descrição |
| K | Sigla-operacao | texto | sigla-descrição |
| L | OF | — | ordem de fabricação (muitas vezes vazio) |
| M | Cod Produto | — | código do produto |
| N | Qtd | número | peças produzidas |
| O | Parada Almoco | hora | pausa almoço |
| P | Parada Lanches | hora | pausa lanches |
| Q | Parada Treinam. | hora | pausa treinamento |
| R | Parada (outros) | hora | outras paradas |
| S | Tempo Unitario | texto HH:MM:SS | tempo padrão por peça |
| T | Tempo Produtivo Total | hora | Qtd × Tempo Unitário |
| U | Tempo Realizado | hora | tempo efetivo (início→fim − paradas) |
| V | Dia (num) | número | dia numérico |
| W | Mes | número | mês |
| X | Ano | número | ano |
| Y | % | decimal | eficiência = Produtivo / Realizado |
| Z | observação | texto | obs livre |
| AA | Agrupador Op | texto | agrupamento da operação |
| AB | CONSUMO | decimal | consumo de insumo |
| AC | Producao Metros | decimal | produção em metros |

## Conceitos (IGE)

```
Tempo Produtivo = Qtd × Tempo Unitário
Produtividade   = Tempo Produtivo ÷ Tempo Disponível
Eficiência      = Tempo Produtivo ÷ Tempo Realizado
IGE             = Produtividade × Eficiência
```

- **% > 1** = produziu mais rápido que o padrão.
- **% < 1** = produziu mais devagar que o padrão.

## Checklist de validação (ao digitar apontamento manual)

1. **Colaborador** legível e sem variação de nome (ex.: ANDRE vs ANDRÉ).
2. **Data correta** (Dia, Mes, Ano consistentes entre si).
3. **Horário coerente** — Hora Fim > Hora Inicio; sem sobreposição com a operação anterior do mesmo colaborador.
4. **Paradas descontadas** — almoço/lanche subtraídos do Tempo Realizado.
5. **Qtd × Tempo Unitário ≈ Tempo Produtivo Total** (bater a conta).
6. **Tempo Realizado ≈ (Fim − Início) − paradas** (bater a conta).
7. **Código/Sigla/Operação** existem e batem (validar contra abas `códigos`, `OPERAÇÕES` ou `De para Operacao`).
8. **Qtd suspeita** — valor muito alto/baixo para a operação (provável erro de digitação).
9. **Tempo Unitário** em formato correto (HH:MM:SS), sem "00:02:0" malformado.
10. **Disponibilidade Bruta** preenchida na 1ª linha do dia do colaborador.

## Referências

- [[Index|Índice da Fabricia]]
- [[Gestão de Produção e PCP]]
