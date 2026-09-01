---
title: Exceções GNRE por UF — Registro de Correções ERP
date: 2026-08-31T09:30:00-03:00
tags:
  - gnre
  - difal
  - debx
  - erp
  - correcao
  - acompanhamento
status: em-acompanhamento
---

# Exceções GNRE por UF — Registro de Correções ERP

## Propósito

Acompanhar, por UF/receita, as divergências entre o que o **DEBX** gera no XML GNRE e o que cada UF exige. A automação roda por um período cobrindo todas as UFs; cada rejeição é investigada, confirmada via `GnreConfigUF` (produção) e registrada aqui. Ao final do período de observação, todas as pendências de origem são consolidadas em **um único pedido** ao fornecedor do ERP.

## Como usar

1. A cada rejeição GNRE (lote `403` com guia rejeitada), investigar causa raiz.
2. Confirmar a regra oficial com `GnreConfigUF` (produção), por UF + receita.
3. Registrar a exceção nas seções "Detalhe" e "Tabela consolidada".
4. Implementar stopgap automático (módulo em `gnre_automation/`) quando viável.
5. Ao fim da observação, fechar a seção "Pedido ao ERP".

## Tabela consolidada

| UF | Receita | Rejeição | Causa raiz (DEBX) | Stopgap | Pendência ERP |
|----|---------|----------|-------------------|---------|---------------|
| AL | 100102 | 217 — Documento de Origem incompatível | emite `documentoOrigem tipo="10"` (nº da nota); UF exige `tipo="22"` (chave NF-e 44 díg.) | `alagoas.py::prepare_documento_origem_guides` (via Oracle `F_SAIDAS`) | emitir `tipo="22"` |
| BA | 100102 | 217 — Documento de Origem não usado pela Receita | emite `documentoOrigem tipo="10"` (nº da nota); UF exige `tipo="22"` (chave NF-e). Chave já vem no `campoExtra 86` | `alagoas.py::prepare_documento_origem_guides` (via `campoExtra 86`) | emitir `tipo="22"` |
| MS | 100102 | 227 — Valor Principal não informado | emite `valor tipo="21"` (total); UF exige `valor tipo="11"` (principal) | `ms.py::prepare_ms_guides` | emitir `tipo="11"` |
| ES | 100102 | 201 — Esta UF não gera GNRE online | gera guia GNRE para ES, mas ES não é habilitada no GNRE online (DIFAL via DUA-e) | — (pendente; guia rejeitada na UF) | não emitir guia ES; rotear para DUA-e |

## Detalhe por exceção

### AL + receita 100102

- **Rejeição:** `217` — "Documento de Origem incompatível", campo `documentoOrigem`.
- **ConfigUF (produção):** `exigeDocumentoOrigem = S`; único tipo aceito `22 — CHAVE DA NFe` (chave de 44 dígitos).
- **O que o DEBX faz:** `documentoOrigem tipo="10"` com apenas o número da nota.
- **Correção esperada no ERP:** gerar `documentoOrigem tipo="22"` com a chave de acesso da NF-e (44 dígitos) para AL/100102.
- **Stopgap:** `gnre_automation/alagoas.py::prepare_alagoas_guides` — resolve a chave via Oracle (`TEST_MATRIZ.F_SAIDAS.SAI_CHANFE`) e converte `10`→`22`; falha fechada se ausente/ambígua; valida modelo 55, DV e CNPJ emitente.
- **Detecção:** 2026-08-26.

### MS + receita 100102

- **Rejeição:** `227` — "Valor Principal nao informado!", campo `valorPrincipal(tipo:11)`.
- **ConfigUF (produção):** `valorExigido = P` (somente Valor Principal); `exigeValorFecp = N`; `exigeCamposAdicionais = S` (campo extra `88` — "Chave de Acesso da NFe ou do CTe/CTE-OS", obrigatório); `exigeDocumentoOrigem = N`; `exigeContribuinteDestinatario = S`; `exigeConvenio = S`.
- **O que o DEBX faz:** `valor tipo="21"` (Valor Total ICMS) sem informar `tipo="11"` (Valor Principal ICMS).
- **Correção esperada no ERP:** gerar `valor tipo="11"` (Valor Principal ICMS) para MS/100102.
- **Stopgap:** `gnre_automation/ms.py::prepare_ms_guides` — converte `tipo="21"` único em `tipo="11"` quando não há `tipo="11"`; falha fechada se `tipo="21"` ≠ `valorGNRE` (possível multa/juros embutidos).
- **Detecção:** 2026-08-31.

### BA + receita 100102

- **Rejeição:** `217` — "O Documento de Origem informado nao e usado pela Receita informada na UF favorecida!", campo `documentoOrigem`.
- **ConfigUF (produção):** `exigeDocumentoOrigem = S`; tipos aceitos `22 — CHAVE DA NFe` e `23 — CHAVE DO CTe/CTe-OS`; `valorExigido = P`; `exigePeriodoReferencia = S`; `exigeCamposAdicionais = N`.
- **O que o DEBX faz:** `documentoOrigem tipo="10"` com apenas o número da nota. A chave completa da NF-e (44 díg.) já vem no `campoExtra 86`.
- **Correção esperada no ERP:** gerar `documentoOrigem tipo="22"` com a chave de acesso da NF-e (44 dígitos) para BA/100102.
- **Stopgap:** `gnre_automation/alagoas.py::prepare_documento_origem_guides` — para BA, extrai a chave do `campoExtra 86` e converte `10`→`22`; valida modelo 55, DV, número da nota e CNPJ emitente; falha fechada se `campoExtra 86` ausente/inválido. **Não usa Oracle** para BA: `F_SAIDAS` não tem a nota no mesmo dia da emissão.
- **Detecção:** 2026-09-01.

### ES + receita 100102

- **Rejeição:** `201` — "Esta UF nao gera GNRE online.", campo `ufFavorecida`.
- **ConfigUF (produção):** `situacaoConsulta = 999` — "UF nao habilitada neste ambiente!".
- **O que o DEBX faz:** gera guia GNRE para ES (DIFAL), mas ES não participa do GNRE online para essa receita — o recolhimento é via **DUA-e** (SEFAZ-ES).
- **Correção esperada no ERP:** não gerar guia GNRE para ES/100102; rotear o DIFAL do ES para o fluxo DUA-e.
- **Stopgap:** pendente — aguardar confirmação do financeiro/fiscal de que ES deve ficar 100% no DUA-e antes de bloquear a transmissão de guias ES.
- **Detecção:** 2026-09-01.

## Semântica do atributo `tipo` do elemento `<valor>` (XSD `dados_gnre_v2.00.xsd`)

- `11` = Valor Principal ICMS · `12` = Valor Principal Fundo de Pobreza (FP)
- `21` = Valor Total ICMS · `22` = Valor Total FP
- `31`/`32` = Multa ICMS/FP · `41`/`42` = Juros ICMS/FP · `51`/`52` = Atualização Monetária ICMS/FP

O portal deriva o Valor Total a partir do Valor Principal. UFs com `valorExigido` incluindo `P` rejeitam lote que informa só o total.

## Template — nova exceção

```markdown
### <UF> + receita <receita>

- **Rejeição:** `<código>` — "<descrição>", campo `<campo>`.
- **ConfigUF (produção):** ...
- **O que o DEBX faz:** ...
- **Correção esperada no ERP:** ...
- **Stopgap:** `gnre_automation/<módulo>.py::<função>` — ...
- **Detecção:** YYYY-MM-DD.
```

## Pedido ao ERP (consolidação)

Quando o período de observação terminar, transformar a coluna "Pendência ERP" em um único pedido. Agrupar por campo de geração do XML (padrão recorrente: o DEBX emite atributo `tipo` incorreto em campos do DIFAL).

- [ ] AL/100102 — emitir `documentoOrigem tipo="22"` (chave NF-e) em vez de `tipo="10"`
- [ ] BA/100102 — emitir `documentoOrigem tipo="22"` (chave NF-e) em vez de `tipo="10"`
- [ ] MS/100102 — emitir `valor tipo="11"` (principal) em vez de `tipo="21"`
- [ ] ES/100102 — não emitir guia GNRE; rotear DIFAL para DUA-e
- [ ] _(novas entradas durante a observação)_

**Registro do pedido:** chamado/fornecedor + data a preencher quando consolidado.

## Relações

- [[Automação GNRE — MVP Dry-Run]]
- [[Integrações, Automação e Monitoramento]]
- [[Banco de Dados e Oracle]]
