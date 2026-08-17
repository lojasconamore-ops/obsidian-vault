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

## Fase 2 — homologação

Iniciada em 2026-08-15.

Implementado:

- Ambiente Python isolado com `lxml`, `requests` e `cryptography`;
- Validação contra os XSD oficiais da versão 2.15;
- Cliente SOAP 1.2 restrito ao ambiente de homologação;
- Header `gnreCabecMsg/versaoDados` e body `gnreDadosMsg`;
- Parser de recibo de 10/14 dígitos;
- Parser dos status 400–404 e situação individual 0–4;
- Solicitação e decodificação do PDF Base64;
- Suporte para extração segura de certificado A1 PKCS#12;
- WSDLs reais de recepção e consulta recuperados por mTLS;
- Namespace e SOAPAction validados contra o contrato publicado;
- Banco de idempotência de transmissão e arquivo seguro de request/response;
- 26 testes automatizados aprovados.

Descobertas:

- `www.testegnre.pe.gov.br` apresenta certificado TLS incompatível com o hostname;
- `testegnre.sefaz.pe.gov.br` resolve para o mesmo servidor e é compatível com o certificado `*.sefaz.pe.gov.br`;
- Sem certificado cliente, o servidor responde HTTP 403;
- 11 XMLs históricos falham no XSD oficial: espaços finais em razão social, razão social acima de 60 caracteres ou IE não numérica.

Bloqueio atual:

- Nenhum bloqueio técnico na homologação;
- Certificado A1 validado até 2027-05-12;
- Handshake mTLS aprovado em TLS 1.2;
- CNPJ transmissor habilitado no Portal GNRE;
- Recepção código `100`, recibo `26000000026482`;
- Processamento código `402`, guia código `0`;
- PDF Base64 recuperado, decodificado e validado como PDF 1.4 de uma página;
- XML original do DEBX não foi alterado: o teste bem-sucedido usou fixture local com datas de 2026-08-16;
- Request, response, resultado e PDF arquivados com permissões restritas;
- Produção automática permanece desabilitada; somente produção assistida com aprovação por hash está autorizada.

## Produção assistida

Autorizada pelo Sergio em 2026-08-16 e implementada sem envio automático.

Controles:

- Inbox, banco e arquivo separados em `runtime/production/`;
- Sincronização considera somente `GNRE*.xml` na raiz de `DIFAL`, ignorando `antigos/`;
- Revisão apresenta SHA-256, quantidade de guias, total, UFs, datas e erros;
- Envio exige aprovação pelo SHA-256 exato do conteúdo;
- Reserva idempotente é persistida antes da chamada externa;
- Consulta de processamento e PDF ficam arquivados e registrados;
- PDFs concluídos são publicados automaticamente e de forma atômica em `\\172.169.0.3\dados\DEBX XML\DIFAL`;
- O nome remoto inclui NF e recibo (`GUIA GNRE NF <número> - RECIBO <recibo>.pdf`), evitando ambiguidade;
- Arquivos remotos existentes com tamanho diferente nunca são sobrescritos;
- Endpoint de produção e WSDL confirmados via mTLS;
- Nenhum timer ou envio automático instalado.

Primeira execução assistida em produção em 2026-08-17: recibo `26000405370641`, lote `402`, guia `0`; PDF validado e publicado como `GUIA GNRE NF 12764 - RECIBO 26000405370641.pdf`.

Estado inicial: raiz remota sem XMLs; somente `antigos/` e o diretório do manual. Dry-run de produção retornou zero arquivos.

## Relações

- [[Banco de Dados e Oracle]]
- [[Integrações, Automação e Monitoramento]]
