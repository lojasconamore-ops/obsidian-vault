# DUA-e ES — Integração Webservice

## Fonte técnica

- Manual de Integração-Cliente DUA-e, versão 1.01b, agosto de 2023.
- Pacote de schemas `PL_DUAe_v1.01b`.
- Todos os 18 XSDs v1.01 recebidos foram compilados com sucesso em 18/08/2026.
- Versão de leiaute a implementar: `1.01`.

## Endpoints

- Homologação: `https://homologacao.sefaz.es.gov.br/WsDua/DuaService.asmx`
- Produção: `https://app.sefaz.es.gov.br/WsDua/DuaService.asmx`
- WSDL: acrescentar `?wsdl` ao endpoint.

## Transporte e segurança

- SOAP 1.2, Document/Literal, operação síncrona.
- XML UTF-8, namespace `http://www.sefaz.es.gov.br/duae`.
- Certificado ICP-Brasil A1 ou A3, com CNPJ e EKU Client Authentication.
- mTLS obrigatório; não desabilitar validação TLS.
- O certificado pode ser tecnicamente válido e ainda não estar autorizado pela SEFAZ-ES. Códigos relevantes: 205/904 não autorizado; 901 sem certificado; 902 inválido; 903 fora do padrão ICP-Brasil.
- XML de dados limitado a 5 KB.

## Operações necessárias

1. `duaConsultaAreaServico` — obter códigos ativos de área/serviço e receita.
2. `duaConsultaMunicipio` — obter a tabela de códigos de município aceita pelo DUA-e.
3. `duaEmissao` — emitir uma DUA por chamada.
4. `duaConsulta` — consultar a DUA pelo número e CPF/CNPJ do contribuinte.
5. `duaObterPdf` — obter PDF em Base64.
6. `duaPagos` — conciliar pagamentos, se necessário.

## Emissão `duaEmissao`

Campos obrigatórios do leiaute v1.01, na ordem do XSD:

- `tpAmb`: `1` produção ou `2` homologação.
- `cnpjEmi`: CNPJ de quem realiza a emissão; para a automação Conamore, CNPJ da Conamore.
- `cnpjOrg`: CNPJ da SEFAZ-ES, `27080571000130`.
- `cArea`: código de área vigente retornado pelo catálogo.
- `cServ`: código de serviço vigente retornado pelo catálogo.
- `cnpjPes`: CPF/CNPJ do contribuinte responsável pelo DUA; para DIFAL/FCP da operação própria, usar a Conamore, não o destinatário da mercadoria.
- `dRef`: referência `AAAA-MM`.
- `dVen`: vencimento `AAAA-MM-DD`.
- `dPag`: pagamento `AAAA-MM-DD`; não pode ser anterior à data corrente.
- `cMun`: código de município aceito pelo DUA-e, confirmado por `duaConsultaMunicipio`.
- `xInf`: informação complementar, até 256 caracteres; registrar NF-e/chave e natureza do tributo.

Campos opcionais:

- `vMul`, `vJur`, `vAtu`: multa, juros e atualização.
- `vRec`: valor principal; deve ser usado para tributos de valor informado.
- `qtde`: quantidade, quando o serviço exigir.
- `xIde`: identificador do cliente, até 30 caracteres; usar referência determinística da NF/obrigação.
- `fPix`: `true` para solicitar PIX; a emissão pode retornar sem PIX se a integração bancária estiver indisponível.

## Códigos observados no manual

O exemplo oficial do manual mostra:

- Área `1902`: Receita de ICMS.
- Serviço `3867`: ICMS – Diferencial de Alíquota.
- Receita retornada `3867`.

Esses códigos devem ser reconfirmados no catálogo de homologação antes do uso. O manual não documenta o código específico do FCP. Nunca inferir nem reutilizar automaticamente o código GNRE `100102` no DUA-e.

## Retorno da emissão

Sucesso: `cStat=105`.

Persistir:

- `nProt`: protocolo.
- `nDua`: número da DUA.
- `dEmi`: data/hora da emissão.
- `vTot`: total.
- `nBar`: código de barras de 48 dígitos.
- `xPix`: payload PIX, quando retornado.

Depois da emissão, chamar `duaObterPdf` com `nDua` e o mesmo CPF/CNPJ usado como contribuinte. Sucesso do PDF: `cStat=106`; decodificar `xPdf` e validar que começa com `%PDF-`.

## Roteamento da automação Conamore

O XML do DEBX pode conter guias de várias UFs. Processar por guia:

- UF diferente de ES: continuar pelo Portal GNRE nacional.
- UF ES: não transmitir pelo Portal GNRE; converter para DUA-e e emitir individualmente.

Preservar o XML original sem alteração. Criar artefatos derivados e registrar:

- hash do arquivo de origem;
- chave de idempotência por obrigação/guia;
- UF, documento de origem, componente fiscal, valor e data;
- request/response sanitizados;
- protocolo, número DUA, PDF e status de pagamento.

## DIFAL e FCP

- Não misturar DIFAL e FCP em uma única emissão sem confirmação do catálogo da SEFAZ-ES.
- A classificação deve vir do componente fiscal gerado pelo DEBX, não apenas do nome do arquivo.
- O lote real de 18/08/2026 trouxe duas guias ES somente com `valor tipo="21"`. O código DUA-e equivalente desse componente ainda precisa ser confirmado pelo catálogo/SEFAZ-ES.
- O manual comprova o serviço DIFAL `3867`, mas não fornece o serviço FCP.

## Idempotência e falhas

O serviço não documenta chave de idempotência fornecida pelo cliente e a consulta exige `nDua`. Portanto:

- antes do POST, gravar estado `SENDING` e o request;
- em sucesso `105`, persistir imediatamente protocolo e número DUA;
- em timeout ambíguo após envio, não retransmitir automaticamente;
- bloquear para reconciliação manual/suporte, pois um novo POST pode gerar outra DUA;
- rejeições fiscais/regra de negócio não devem ser retentadas sem correção;
- retentar automaticamente apenas falha claramente anterior à transmissão ou indisponibilidade comprovadamente sem aceite.

## Códigos principais

- `101` catálogo área/serviço consultado.
- `103` municípios consultados.
- `104` DUA consultada.
- `105` DUA emitida.
- `106` PDF obtido.
- `201–212` erros genéricos de XML, serviço, ambiente e versão.
- `701–713` rejeições da emissão.
- `801–802` DUA inexistente ou não pertencente ao contribuinte informado.
- `901–904` certificado/autorização.
- `999` erro inesperado.

## Estado da validação em 18/08/2026

- 18/18 XSDs v1.01 compilados com sucesso.
- XML de emissão de homologação validado no `emisDua_v1.01.xsd`.
- Tamanho do XML validado: 471 bytes.
- Cliente de descoberta implementado em `gnre_automation/duae.py`, deliberadamente sem método de emissão nesta fase.
- Consultas de catálogo e municípios cobertas por testes; requests válidos nos XSDs oficiais.
- Suíte completa: 44 testes executados, 44 aprovados.
- Certificado da Conamore válido, com EKU Client Authentication e validade até 12/05/2027.
- DNS dos endpoints resolve, mas TCP/443 expira antes do TLS em homologação, produção e portal `s1-internet`; HTTPS geral da VM funciona normalmente.
- Watchdog silencioso ativo a cada 30 minutos, job `7d6ab9c42c64`; quando o endpoint voltar, consultará somente catálogo e municípios em homologação.
- Nenhuma DUA foi emitida.

## Próximos passos seguros

1. Restaurar/conferir conectividade aos endpoints SEFAZ-ES.
2. Testar handshake mTLS sem POST de negócio.
3. Confirmar autorização do CNPJ da Conamore.
4. Consultar catálogo e localizar os códigos atuais de DIFAL e FCP.
5. Consultar a tabela de municípios.
6. Implementar cliente e parsers com testes determinísticos.
7. Emitir uma DUA controlada em homologação.
8. Validar número, valor, contribuinte, código de barras, PIX e PDF.
9. Somente após aprovação, integrar ao watchdog de produção e excluir ES dos lotes enviados ao Portal GNRE nacional.
