# Secullum RH — consulta por API da Fabrícia

> **Somente leitura — uso interno e confidencial.**

## Situação

- Acesso autorizado por Sérgio em **08/10/2026**.
- Conta técnica: mesma identidade utilizada pela integração da Maria.
- Banco autorizado: `66279` — CONAMORE SSL CAMA MESA E BANHO LTDA.
- Cliente local: `~/.hermes/profiles/fabricia/scripts/secullum/client.py`.
- Credencial protegida: `~/.hermes/profiles/fabricia/secrets/secullum.json`, permissão `600`.

## Unidades prioritárias

- **BRG:** `CONAMORE BRG CAMA MESA E BANHO LTDA.`
- **Conamore Filial:** `CONAMORE SSL CAMA MESA E BANHO LTDA FILIAL`

## Uso

```bash
python3 ~/.hermes/profiles/fabricia/scripts/secullum/client.py probe
python3 ~/.hermes/profiles/fabricia/scripts/secullum/client.py list-banks
python3 ~/.hermes/profiles/fabricia/scripts/secullum/client.py list-companies --bank-id 66279
```

A Fabrícia pode consultar marcações e produzir conferências das unidades necessárias, sempre com finalidade operacional definida e minimização de dados.

## Regras

- Não exibir ou enviar senha e token.
- Não consultar dados pessoais sem necessidade operacional.
- Não incluir, excluir, ajustar, abonar ou recalcular marcações.
- Linha sem horário não é falta automática.
- Quantidade ímpar de batidas é pendência de conferência, não irregularidade confirmada.
- Ajustes, descontos, advertências e decisões trabalhistas devem ser encaminhados à Maria/RH.
- Como a identidade técnica é compartilhada, o Secullum não diferencia consultas feitas por Maria, Natália ou Fabrícia. Suspeita de exposição exige rotação imediata da senha nos três perfis.
