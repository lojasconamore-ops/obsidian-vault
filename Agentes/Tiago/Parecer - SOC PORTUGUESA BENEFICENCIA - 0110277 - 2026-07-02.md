# Parecer de Crédito — SOC PORTUGUESA DE BENEFICENCIA DE SANTO ANDRE

**Data:** 02/07/2026
**Orçamento:** 0110277
**Analista:** Tiago (Financeiro)

---

## Dados do Cliente

| Campo | Valor |
|---|---|
| Razão Social | SOC PORTUGUESA DE BENEFICENCIA DE SANTO ANDRE |
| Nome Fantasia | HOSPITAL BENEFICENCIA PORTUGUESA DE SANTO ANDRE |
| CNPJ | 57.507.402/0001-02 |
| ID_DEBX | A7709 |
| Endereço | AVENIDA PORTUGAL, 530 - Centro, Santo André/SP |
| Fundação | 11/08/1966 (60 anos) |
| Natureza Jurídica | Associação Privada |
| Ramo | Atendimento Hospitalar |
| Funcionários | 100 a 499 |
| Site | beneficenciasantoandre.com.br |
| Contato | (11) 2198-5000 / (11) 9642-9000 |
| Email | Secretaria2@beneficenciasantoandre.co |
| Representante | Brenda Kaliane Campos dos Santos |

## Dados do Pedido

| Campo | Valor |
|---|---|
| Item | 200x Toalha de Piso Smart 50x70cm 450g/m² |
| Preço unitário | R$ 14,40 (desc. 10% sobre tabela R$ 16,00) |
| Total Itens | R$ 2.880,00 |
| Frete | R$ 50,00 |
| **Total Pedido** | **R$ 2.930,00** |
| Condição Solicitada | **BOLETO 45 DIAS (ZERO ENTRADA)** |
| Exposição Líquida | **R$ 2.930,00 (100%)** |
| Observação | Todos os itens em estoque. Desconto 10% para pagamento parcelado. |

---

## Análise

### Etapa 0 — Lista Negra
✅ **NÃO CONSTA.** CNPJ, razão social e nome fantasia não encontrados na lista negra Conamore.

### Etapa 1 — Histórico Interno Conamore
⚠️ **PRIMEIRA COMPRA — SEM HISTÓRICO.**
- `conamore.Customers`: cadastro localizado (A7709, Status=0 ativo)
- `debx.PDV_Detalhes`: **0 pedidos** encontrados
- `conamore.CAIXA_PERIODO_DETALHADO_POR_MATERIAL`: **0 registros**
- **Grupo econômico:** Nenhum outro CNPJ no mesmo endereço (AVENIDA PORTUGAL, 530)

### Etapa 2 — Score / Bureau (Equifax | Boa Vista)

**Fonte:** Relatório Equifax | Boa Vista emitido em 02/07/2026.

| Indicador | Valor | Classificação |
|---|---|---|
| Score de Aprovação PJ | **808** | 🟢 Muito forte |
| Probabilidade de Inadimplência | **3,0%** | 🟢 Excelente |
| Cadastro Positivo | Participante com informação | ✅ Positivo |
| Fundação | **11/08/1966** | 60 anos de operação |
| Funcionários | **100 a 499** | Médio-grande porte |

**Pagamentos (12 meses):**

| Mês | Pontual | Atraso 6-15d | Atraso 16-30d | Atraso Médio |
|---|---|---|---|---|
| jul/2025 | 97% | 2% | 1% | 0,4 dias |
| ago/2025 | 93% | — | 6% | 1 dia |
| set–nov/2025 | 100% | — | — | 0 |
| dez/2025 | 76% | 23% | — | 2 dias |
| jan–abr/2026 | 100% | — | — | 0 |
| mai/2026 | 94% | — | 5% | 1 dia |
| jun/2026 | 100% | — | — | 0 |

**Média de atraso: < 2 dias** — atrasos pontuais e curtos, comportamento global muito bom.

| Indicador | Resultado |
|---|---|
| Pendências financeiras | **Nada consta** ✅ |
| Protestos | **Nada consta** ✅ |
| Cheques sem fundos | **Nada consta** ✅ |
| Fornecedores (6-10 anos) | **100%** ✅ |
| Consultas (12 meses) | 76 — entidade ativamente monitorada |

### Etapa 3 — Coerência Operacional
✅ **COERENTE.** Hospital de médio-grande porte comprando 200 toalhas de piso — reposição institucional padrão. Gramatura 450g/m² é adequada para uso hospitalar.

### Etapa 4 — Exposição
- Exposição líquida: **R$ 2.930,00** (100% do pedido — zero entrada)
- ⚠️ **ZERO ENTRADA** — não atende à preferência de mínimo 25% de entrada

### Etapa 5 — Validação Operacional Online
🟢 **OPERAÇÃO FORTE.**

| Fonte | Evidência |
|---|---|
| Google Maps | 4.5★, Hospital e Maternidade, 24h, Av. Portugal 530 |
| Site próprio | beneficenciasantoandre.com.br — ativo |
| Telefone | (11) 2198-5000 |
| Infraestrutura | Acessibilidade ♿, Tomografia Computadorizada |
| Endereço | Consistente entre CNPJ, Google Maps e PDF |

---

## Parecer Final

```
Etapa 0 — Lista Negra: ✅ NÃO CONSTA
Parecer: ✅ APROVAR — mas requer autorização para zero entrada

Nível de risco: BAIXO

Histórico Conamore: Primeira compra — sem histórico
Score / Bureau: Score 808 (🟢 muito forte), PD 3,0% (🟢 excelente), 60 anos de fundação, 100-499 funcionários, ZERO restrições/protestos
Coerência do pedido: Hospital comprando toalhas de piso — coerente
Validação operacional online: Operação forte — hospital 4.5★ no Google Maps, site próprio, 24h, tomografia

Condição recomendada:
⚠️ O cliente solicitou BOLETO 45 DIAS (zero entrada).
   Opção A: APROVAR zero entrada — exposição de apenas R$ 2.930 para instituição de 60 anos com score 808
   Opção B: CONTRAPROPOR 25% entrada (R$ 732,50) + saldo 45 dias — alinhado à política padrão

Justificativa técnica objetiva:
1. Instituição sexagenária (1966), 100-499 funcionários, score 808 — perfil de crédito excepcional
2. ZERO restrições, ZERO protestos, ZERO cheques — ficha completamente limpa
3. 100% dos fornecedores com 6-10 anos de relacionamento — paga seus compromissos
4. Exposição de R$ 2.930 é irrisória para o porte da instituição
5. Hospital verificado no Google Maps (4.5★), site próprio, operação 24h
6. Atrasos eventuais são curtos (média < 2 dias) e não indicam risco sistêmico
```

---

## Cronograma de Recebíveis

### Opção A — Zero Entrada (solicitado)

| Parcela | Valor | Vencimento |
|---|---|---|
| 45 dias | R$ 2.930,00 | ~16/08/2026 |

### Opção B — 25% Entrada (recomendado pela política)

| Parcela | % | Valor | Vencimento |
|---|---|---|---|
| Entrada | 25% | R$ 732,50 | Na emissão |
| 45 dias | 75% | R$ 2.197,50 | ~16/08/2026 |
