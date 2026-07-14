# Parecer de Crédito — Grêmio Sargento Expedicionário Geraldo Santana

**Data da análise:** 15/06/2026
**Analista:** Tiago (Gerente Financeiro)
**Origem:** Orçamento nº 107073 + Relatório Equifax/Boa Vista

---

## Dados do Cliente

| Campo | Valor |
|---|---|
| Razão Social | GREMIO SARGENTO EXPEDICIONARIO GERALDO SANTANA |
| Nome Fantasia | Grêmio Geraldo Santana |
| CNPJ | 92.937.473/0001-38 |
| ID_DEBX | 30920 |
| Endereço | Rua Luiz de Camões, 337 — Santo Antônio, Porto Alegre-RS |
| Contato | Luciano — (51) 9487-1068 — hotel@geraldosantana.com.br |
| Representante | Maria Fabiana Barreto Paez |
| Fundação | 02/10/1969 (57 anos!) |
| CNPJ ativo desde | 04/07/1998 (28 anos) |
| Natureza Jurídica | Associação Privada (3999) |
| Ramo | Clubes sociais, esportivos e similares |
| Funcionários | 20 a 99 |
| Classe Conamore | HOTEL |

---

## Pedido em Análise (Orçamento 107073)

| Item | Qtd | Valor Unit. | Total |
|---|---|---|---|
| Lençol Solteiro Prime c/ Elást. 90×190cm Percal 200 fios 100% algodão | 20 | R$ 69,90 | R$ 1.398,00 |
| Lençol Solteiro Prime s/ Elást. 160×250cm 200 fios 100% algodão | 20 | R$ 73,60 | R$ 1.472,00 |
| Toalha de Banho Frame 80×140cm fio retorcido 450g/m² | 40 | R$ 49,40 | R$ 1.976,00 |
| Edredom Solteiro Hotelaria Branco 1,60×2,50 | 10 | R$ 154,10 | R$ 1.541,00 |
| Edredom Casal Hotelaria Branco 2,20×2,50 | 6 | R$ 202,60 | R$ 1.215,60 |
| Frete | — | — | R$ 50,00 |
| **Total** | **96** | | **R$ 7.652,60** |

| Condição Proposta | Valor |
|---|---|
| Entrada 50% | R$ 3.826,30 |
| Saldo 30 dias | R$ 1.913,15 |
| Saldo 60 dias | R$ 1.913,15 |
| Validade | 15/06/2026 |

---

## Etapa 0 — Lista Negra

✅ **Cliente NÃO pertence à Lista Negra Conamore.**
CNPJ 92.937.473/0001-38 e razão social não constam nos 62 registros bloqueados.

---

## Etapa 1 — Histórico Interno Conamore

**Base:** SQL Server `hotel-finder` — busca por Razao_Social + ID_DEBX2 (método completo)

**Cadastro:** ID_DEBX 30920, desde 25/07/2024 (~23 meses).

### Histórico de Pedidos (3 faturados + 1 orçamento atual)

| # | Pedido | Data | Status | Valor | Condição | Vendedor |
|---|---|---|---|---|---|---|
| 1 | 0004430 | 25/07/2024 | Expedição | R$ 2.013,00 | Entrada 50% + 30/60 dias | Hamilton Polizelli |
| 2 | 0054853 | 15/08/2025 | Expedição | R$ 2.127,70 | À Vista | Maria Fabiana |
| 3 | 0065458 | 16/10/2025 | Expedição | R$ 3.460,90 | À Vista | Maria Fabiana |
| 4 | 0107073 | 10/06/2026 | **Orçamento** | R$ 7.652,60 | Entrada 50% + 30/60 | Maria Fabiana |

### Detalhamento por pedido

**0004430** (07/2024) — Entrada 50% + 30/60 — R$ 2.013,00
- 20 un. Lençol Solteiro c/ Elást. Percal 180 fios
- 20 un. Lençol Casal c/ Elást. Percal 180 fios
- 30 un. Protetor Travesseiro Impermeável
- *Primeira compra: enxoval básico de cama*

**0054853** (08/2025) — À Vista — R$ 2.127,70
- 2 un. Edredom Casal Hotelaria
- 2 un. Cobertor Microfibra Casal
- 6 un. Lençol Casal Classic c/ Elást.
- 6 un. Lençol Casal Classic s/ Elást.
- 6 un. Fronha Avulsa Classic
- 12 un. Toalha de Banho Quality
- 12 un. Toalha de Rosto Quality
- 4 un. Toalha de Piso Fit
- 1 un. Cobertor Flannel Casal
- *Ampliação: mix mais diversificado*

**0065458** (10/2025) — À Vista — R$ 3.460,90
- 12 un. Fronha Avulsa Prime 200 fios
- 6 un. Lençol Casal Prime c/ Elást. 200 fios
- 6 un. Lençol Casal Prime s/ Elást. 200 fios
- 12 un. Toalha de Banho Giant 580g/m²
- 12 un. Toalha de Rosto Giant
- 4 un. Toalha de Piso Fit
- 3 un. Cobertor Flannel Solteiro
- 6 un. Cobertor Flannel Casal
- 3 un. Lençol Solteiro Classic c/ Elást.
- 3 un. Lençol Solteiro Classic s/ Elást.
- *Upgrade: migrando para linha Prime (200 fios), toalhas Giant*

### Resumo

| Indicador | Valor |
|---|---|
| Total histórico faturado | R$ 7.601,60 |
| Pedidos faturados | **3** |
| Ticket médio | R$ 2.533,87 |
| Maior pedido | R$ 3.460,90 |
| Primeira compra | 25/07/2024 (23 meses) |
| Última compra faturada | 16/10/2025 (8 meses) |
| Frequência | ~1 pedido a cada 5 meses |

### Evolução do Ticket

R$ 2.013 → R$ 2.127 → R$ 3.460 → **R$ 7.653** (atual)

📈 **Crescimento com upgrade de qualidade.** O cliente começou com linha básica (Percal 180 fios), passou para Classic (200 fios misto), depois Prime (200 fios 100% algodão) e toalhas Giant. O pedido atual mantém a trajetória de sofisticação: linha Prime + toalhas Frame + edredons. O salto de 2,2× sobre o maior pedido anterior é explicado pela mudança de mix (produtos de maior valor agregado) e pelo intervalo mais longo desde a última compra (8 meses).

### Condições já operadas com sucesso

- ✅ Entrada 50% + 30/60 dias (1ª compra — R$ 2.013)
- ✅ À Vista (2 compras)
- ✅ 3/3 Expedição — zero cancelamentos

### Classificação: **Classe B — Bom**
Cliente regular, 23 meses de relacionamento, 3 pedidos faturados com sucesso. Já operou a condição proposta (entrada + prazo) na primeira compra. Comportamento de pagamento consistente (à vista nas compras seguintes sugere boa saúde financeira). Upgrade gradual de qualidade indica operação saudável e em crescimento.

---

## Etapa 2 — Score / Bureau (Equifax/Boa Vista)

| Indicador | Valor | Classificação |
|---|---|---|
| **Score** | **858** | 🟢 **Muito Forte** (750+) |
| Prob. inadimplência | 2,0% | 🟢 **Excelente** (≤5%) |
| Pagamento pontual (meses c/ dado) | 100% (jun, nov/25, mai/26) | 🟢 Impecável |
| Atraso (qualquer faixa) | **Zero** | 🟢 Perfeito |
| Atraso médio | 0 dias | 🟢 |
| Cadastro Positivo | Participante com informação | 🟢 |
| Pendências/restrições | Nada Consta | 🟢 |
| Protestos | Nada Consta | 🟢 |
| Cheques | Nada Consta | 🟢 |
| Situação CNPJ | Ativo (desde 04/07/1998) | 🟢 **28 anos** |
| Fundação | 02/10/1969 | 🟢 **57 anos** |
| Consultas (12 meses) | 16 | Normal para o porte |
| Última compra (mercado) | mai/2026 | Operação ativa |

**Conclusão Bureau:** 🏆 **Perfil excepcional.** Score 858, apenas 2% de probabilidade de inadimplência, pagamentos 100% pontuais, zero atrasos, zero restrições. Entidade com 57 anos de história e CNPJ ativo há 28 anos. Associação privada consolidada com 20-99 funcionários.

---

## Etapa 3 — Coerência Operacional do Pedido

**Grêmio Geraldo Santana** é um clube/associação em Porto Alegre-RS, classificado como "Event venue" no Google Maps, com hotel/alojamento próprio (email: hotel@geraldosantana.com.br).

- **Segmento:** Clube social/esportivo com hospedagem — classe HOTEL na Conamore
- **Mix:** Lençóis Prime 200 fios 100% algodão + toalhas Frame + edredons — **upgrade de qualidade** consistente com a trajetória do cliente
- **Volume:** 96 peças para entidade com 20-99 funcionários — coerente
- **Progressão:** Básico (07/2024) → Ampliação (08/2025) → Upgrade qualidade (10/2025) → Consolidação Premium (06/2026)
- **Salto de ticket (2,2×):** Justificado por: (a) itens de linha superior (Prime vs Classic, Frame vs Quality), (b) intervalo de 8 meses desde a última compra, (c) edredons (itens de ticket alto)

✅ **Pedido coerente** com a trajetória de upgrade e o porte da entidade.

---

## Etapa 4 — Exposição Real da Conamore

| Componente | Valor |
|---|---|
| Total do pedido | R$ 7.652,60 |
| Entrada (50%) | R$ 3.826,30 |
| **Exposição líquida** | **R$ 3.826,30** |

🟢 **Exposição moderada-baixa** — 50% coberto na entrada. Parcelas de R$ 1.913,15 em 30 e 60 dias, valor administrável para entidade com 57 anos de operação.

---

## Etapa 5 — Validação Operacional Online

| Fonte | Status | Evidência |
|---|---|---|
| Google Maps | ✅ | Grêmio Geraldo Santana — 4.6★ — "Event venue" |
| Site próprio | ✅ | geraldosantana.com.br |
| Telefone | ✅ | (51) 3223-5520 |
| Endereço | ✅ | Rua Luiz de Camões, 337 — coincide com orçamento |
| Acessibilidade | ✅ | Wheelchair accessible |
| Funcionários | ✅ | 20-99 (bureau) |

🟢 **Operação Forte** — entidade consolidada, 4.6★ no Google Maps, website próprio, telefone ativo, endereço consistente.

---

## Parecer Final

```
Etapa 0 — Lista Negra: ✅ NÃO consta
Parecer: ✅ APROVAR

Nível de risco: BAIXO

Histórico Conamore: Cliente desde 07/2024 (23 meses). 3 pedidos faturados (100% Expedição).
  Total histórico R$ 7,6k | Ticket médio R$ 2,5k | Maior pedido R$ 3,5k.
  Já operou Entrada 50% + 30/60 dias com sucesso na 1ª compra.
  Evolução com upgrade de qualidade (Básico → Classic → Prime).
  Classe B — Bom.

Score / Bureau: 🏆 858 (Muito Forte) | Prob. 2,0% | 100% pagamento pontual.
  Zero atrasos, zero restrições, zero protestos. Entidade com 57 anos de história
  e CNPJ ativo há 28 anos. Perfil de bureau EXCEPCIONAL.

Coerência do pedido: Coerente com trajetória de upgrade. Cliente migrando para
  linha Prime/Frame (produtos premium). Salto de 2,2× justificado por mix superior
  e intervalo de 8 meses desde última compra.

Validação operacional online: 🟢 Operação Forte. Grêmio Geraldo Santana no Google
  Maps (4.6★), website geraldosantana.com.br, telefone ativo, endereço confere.

Condição recomendada: MANTER CONDIÇÕES DA PROPOSTA
  • Entrada 50% (R$ 3.826,30)
  • Saldo 30/60 dias (R$ 1.913,15 + R$ 1.913,15)
  • Exposição líquida: R$ 3.826,30

Justificativa técnica objetiva: Cliente com 23 meses de relacionamento, 3 pedidos
  faturados com sucesso e zero cancelamentos. Já operou a mesma condição proposta.
  Bureau excepcional: score 858, 2% de prob. de inadimplência, 57 anos de entidade,
  28 anos de CNPJ ativo. Operação real comprovada (Google 4.6★, site, telefone).
  Salto de ticket de 2,2× é justificado pelo upgrade de qualidade (Prime/Frame).
  Exposição líquida moderada (R$ 3,8k) com 50% de entrada.
```

---

> **Princípio aplicado:** *"Vender com risco inteligente."* — Cliente com histórico consistente de upgrade, bureau impecável e operação real consolidada há 57 anos. Aprovar com a condição proposta é risco controlado.
