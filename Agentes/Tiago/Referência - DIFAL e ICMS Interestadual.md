# Referência — DIFAL e ICMS Interestadual

**Data:** 22/07/2026
**Autor:** Tiago — Gerente Financeiro
**Fontes:** EC 87/2015, LC 190/2022, Convênio ICMS 236/2021, CF/88 art. 155, ADI 5.464/STF, IN SEFAZ/CE nº 43/2024, RC 32359/2025 (SEFAZ-SP)

> Usar como referência permanente para emissão de NF-e interestadual de enxoval.
> Atualizar se houver mudança na legislação.

---

## 1. Regra geral: o que define tudo

O fator determinante **não é o regime da Conamore**, mas sim:

> **O cliente de destino é contribuinte ou não contribuinte do ICMS?**

| Cliente | IE? | Exemplos |
|---|---|---|
| Contribuinte | Sim | Hotel, pousada, hospital, clínica, empresa |
| Não contribuinte | Não | Pessoa física, associação sem IE, entidade sem inscrição estadual |

---

## 2. Cenário A — Cliente CONTRIBUINTE (uso e consumo)

**Cenário mais comum da Conamore B2B.**

### CFOP

| Origem da mercadoria | CFOP |
|---|---|
| Produção própria (fábrica) | **6.101** |
| Revenda (terceiros) | **6.102** |

> ⚠️ O CFOP de venda é sempre **6.xxx**. O CFOP 2.556/2.557 é usado pelo **comprador** na entrada — a Conamore NUNCA usa CFOP iniciado em 2.

### Preenchimento da NF-e

- **Consumidor final:** sim
- **Indicador de IE do destinatário:** contribuinte
- **Finalidade:** uso e consumo
- **DIFAL:** responsabilidade do **destinatário** (não recolher na NF)

### Observação padrão (todos os estados)

```
Mercadoria destinada a uso e consumo do estabelecimento destinatário.
O recolhimento do diferencial de alíquota do ICMS – DIFAL, quando devido,
é de responsabilidade do destinatário, contribuinte do ICMS, nos termos
do art. 155, § 2º, incisos VII e VIII, "a", da Constituição Federal.
```

### Observação específica para o Ceará (adicional)

```
DIFAL a ser recolhido pelo destinatário nos termos da EC nº 87/2015
c/c Cláusula Décima do Convênio ICMS 93/2015 e IN SEFAZ/CE nº 43/2024.
```

### Regime da Conamore neste cenário

| Regime | Obrigação |
|---|---|
| **SSL (Lucro Real)** | Nenhuma — DIFAL é do cliente |
| **ACL/GCL/BRG (Simples)** | Nenhuma — DIFAL é do cliente |

> ✅ **Não há diferença entre regimes.** Ambos só destacam o ICMS interestadual normal.

---

## 3. Cenário B — Cliente NÃO CONTRIBUINTE + Conamore LUCRO REAL (SSL)

### CFOP

| Origem da mercadoria | CFOP |
|---|---|
| Produção própria (fábrica) | **6.107** |
| Revenda (terceiros) | **6.108** |

### Obrigações da Conamore SSL

- Destacar alíquota interestadual de ICMS
- Calcular e destacar o **DIFAL** na NF-e (grupo ICMSUFDest)
- Recolher o DIFAL ao estado de destino (GNRE ou IE de substituto)
- Preencher campos próprios do DIFAL no XML

### Observação padrão

```
Operação interestadual destinada a consumidor final não contribuinte
do ICMS. DIFAL devido ao Estado de destino, apurado nos termos da
EC nº 87/2015, da LC nº 190/2022 e do Convênio ICMS nº 236/2021.
```

### Se houver GNRE por operação

```
DIFAL recolhido por meio da GNRE nº [número], no valor de R$ [valor].
```

---

## 4. Cenário C — Cliente NÃO CONTRIBUINTE + Conamore SIMPLES (ACL/GCL/BRG)

### CFOP

| Origem da mercadoria | CFOP |
|---|---|
| Produção própria (fábrica) | **6.107** |
| Revenda (terceiros) | **6.108** |

### DIFAL

> 🛡️ **ISENTO.** O Simples Nacional NÃO está obrigado a recolher DIFAL em vendas interestaduais para consumidor final não contribuinte, conforme decisão do STF (ADI 5.464) e entendimento da SEFAZ-SP (RC 32359/2025).

### Preenchimento adicional

- **CSOSN:** 102 (tributação normal pelo Simples, sem ST)

### Observação padrão

```
Operação realizada por empresa optante pelo Simples Nacional.
Não gera direito a crédito fiscal de ICMS. Remetente não sujeito
ao recolhimento do DIFAL destinado a consumidor final não contribuinte,
conforme decisão do STF (ADI 5.464) e entendimento da Secretaria
da Fazenda do Estado de São Paulo.
```

---

## 5. Tabela-resumo

| Situação do cliente | Lucro Real (SSL) | Simples Nacional (ACL/GCL/BRG) |
|---|---|---|
| **Contribuinte** (hotel, hospital) | DIFAL do cliente | DIFAL do cliente |
| **Não contribuinte** (PF, sem IE) | DIFAL da Conamore | **Isento** |
| CFOP produção própria | 6.101 ou 6.107 | 6.101 ou 6.107 |
| CFOP revenda | 6.102 ou 6.108 | 6.102 ou 6.108 |

---

## 6. Alíquotas interestaduais (saindo de SP)

| Destino | Alíquota |
|---|---|
| **Sul e Sudeste** (exceto ES): PR, SC, RS, MG, RJ | **12%** |
| **Norte, Nordeste, Centro-Oeste e ES**: CE, BA, PE, GO, DF, AM, PA, ES... | **7%** |
| Produto importado (Res. 13/2012) | **4%** |

### Exemplo: SP → CE

| | % |
|---|---|
| Interestadual (SP→CE) | **7%** |
| Interna Ceará (modal) | **18%** |
| **DIFAL =** | **11%** |

> ⚠️ Verificar FCP (Fundo de Combate à Pobreza) e adicionais por NCM. O Ceará aplica FCP de 2% para alguns produtos.

---

## 7. Particularidades por estado

### Ceará

- **Norma:** IN SEFAZ/CE nº 43/2024, Norma de Execução nº 04/2024
- **Cálculo:** base dupla (imposto por dentro)
- **Ferramenta:** SEFAZ-CE lançou calculadora de DIFAL em set/2025
- **Códigos de ajuste EFD:** CE000006 (uso/consumo), CE000002 (ativo)
- **Dispensa GIA-ST:** desde 2026 para contribuintes de outras UF com IE substituto

### Demais estados

- A observação do **Cenário A** (contribuinte) é universal — serve para qualquer estado
- Para **não contribuinte**, cada estado tem regras próprias de GNRE, IE substituto e prazos
- Consultar a legislação do estado de destino antes da primeira operação

---

## 8. Recomendações para o ERP

1. **Cadastrar 3 observações-padrão:**
   - `OBS-DIFAL-CONTRIBUINTE` → Cenário A
   - `OBS-DIFAL-NAO-CONTRIBUINTE-LR` → Cenário B
   - `OBS-DIFAL-NAO-CONTRIBUINTE-SN` → Cenário C

2. **Exigir no cadastro do cliente:**
   - Consumidor final? (sim/não)
   - Contribuinte do ICMS? (sim/não)
   - Inscrição Estadual (se contribuinte)

3. **Validar IE antes da emissão:** conferir se a IE está ativa no SINTEGRA ou cadastro da SEFAZ

---

*Documento de referência. Atualizado em 22/07/2026.*
