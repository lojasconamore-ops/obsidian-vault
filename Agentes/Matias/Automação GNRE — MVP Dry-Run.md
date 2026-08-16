---
title: Automação GNRE — MVP Dry-Run
date: 2026-08-15T21:08:38-03:00
tags:
  - gnre
  - difal
  - debx
  - automacao
  - ti
status: em-desenvolvimento
---

# Automação GNRE — MVP Dry-Run

## Objetivo

Automatizar futuramente o transporte dos lotes GNRE gerados pelo ERP DEBX e o retorno das guias, preservando inicialmente uma fase segura de leitura e validação sem transmissão.

## Origem

```text
\\172.169.0.3\dados\DEBX XML\DIFAL
```

- Domínio SMB: `con`.
- Credencial operacional armazenada fora do Vault, em arquivo local com modo `600`.
- Arquivos `GNRE*.xml`: lotes para pagamento do DIFAL gerados pelo DEBX.
- Arquivos PDF: exemplos das guias geradas.

## Artefato

```text
/home/sergio-ladeira/.hermes/profiles/matias/projects/gnre-automation
```

Componentes:

- Sincronização SMB incremental e somente download;
- Parser do `TLote_GNRE` versão 2.00;
- Validações locais;
- Controle idempotente SHA-256 em SQLite/WAL;
- CLI dry-run com transmissão permanentemente desabilitada nesta fase;
- Testes automatizados;
- Templates systemd preparados, mas não instalados.

## Baseline inicial

Execução realizada em 2026-08-15:

- 672 arquivos `GNRE*.xml` lidos;
- 663 conteúdos únicos válidos nas regras locais;
- 9 arquivos duplicados por conteúdo (SHA-256);
- 3.046 guias identificadas;
- 26 UFs favorecidas identificadas;
- 0 XML inválido após concluir a sincronização;
- 13 testes automatizados aprovados no Python 3.10.12.

## Segurança

- Nenhum lote foi enviado ao Portal GNRE;
- Nenhum arquivo foi escrito, movido ou excluído no compartilhamento do DEBX;
- CPF, CNPJ e chaves de NF-e não são exibidos no relatório operacional;
- A instalação do timer systemd depende de comunicação/autorização antes de alterar a operação contínua.

## Próximas fases

1. Obter WSDL, XSD e documentação oficial atualizados;
2. Confirmar ambiente de homologação e eventual certificado A1;
3. Implementar cliente SOAP separado do dry-run;
4. Testar envio, recibo, consulta e PDF em homologação;
5. Conciliar XML versus guia;
6. Entrar em produção assistida somente após validação fiscal/financeira.

## Relações

- [[Banco de Dados e Oracle]]
- [[Integrações, Automação e Monitoramento]]
