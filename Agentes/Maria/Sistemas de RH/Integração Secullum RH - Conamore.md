# Integração Secullum RH — Conamore

## Situação

- **Sistema:** Secullum RH Ultimate / API histórica Ponto Web — Integração Externa.
- **Conta técnica:** `ti@conamore.com.br`.
- **Usuário no Secullum RH:** TI Hermes, tipo Usuário.
- **Integração externa:** habilitada e usuário autorizado.
- **Ativação da Conta Secullum:** concluída por Sérgio em 15/08/2026, por meio do link recebido por e-mail.
- **Estado atual:** autenticação e autorização da API validadas com sucesso em 15/08/2026 às 06:48 BRT; banco `66279` acessível em modo somente leitura.

## Prova de conexão — 15/08/2026

- Banco autorizado: `66279` — **CONAMORE SSL CAMA MESA E BANHO LTDA**.
- `GET Empresas`: sucesso — 6 registros.
- `GET Departamentos`: sucesso — 15 registros.
- `GET Funcoes`: sucesso — 45 registros.
- Nenhuma operação de escrita ou exclusão foi executada.
- Próxima validação: confrontar essas quantidades e uma amostra cadastral com relatórios/telas oficiais do Secullum antes de automatizar indicadores.

## Segurança e LGPD

- Não registrar senha, token, CPF, PIS ou dados individuais nesta nota.
- Não enviar senha pelo Telegram ou e-mail.
- Credencial local em `~/.hermes/profiles/maria/secrets/secullum.json`, com permissão `600`.
- Scripts em `~/.hermes/profiles/maria/scripts/secullum/`.
- A fase inicial permite apenas consultas de leitura.

## Procedimento de ativação técnica

No terminal do servidor Hermes, executar:

```bash
python3 ~/.hermes/profiles/maria/scripts/secullum/setup_credentials.py
python3 ~/.hermes/profiles/maria/scripts/secullum/client.py list-banks
```

O primeiro comando solicita a senha sem exibi-la. O segundo autentica e lista apenas os bancos Ponto Web autorizados, sem mostrar o token.

Após a prova de conexão:

```bash
python3 ~/.hermes/profiles/maria/scripts/secullum/client.py list-companies
python3 ~/.hermes/profiles/maria/scripts/secullum/client.py list-departments
python3 ~/.hermes/profiles/maria/scripts/secullum/client.py list-functions
```

Se houver mais de um banco autorizado, informar `--bank-id ID`.

## Fase 2 — amostra operacional agregada

**Janela consultada:** 08/08/2026 a 14/08/2026. Dados individuais não foram registrados nesta nota.

### Cadastro de funcionários

- 226 cadastros retornados pela API.
- 60 ativos estimados, sem data de demissão e visíveis.
- 166 com data de demissão; os mesmos 166 aparecem como invisíveis.
- 56 ativos apresentaram ao menos uma marcação horária no período.

### Ponto e afastamentos

- 570 linhas funcionário/dia retornadas na reconsulta; o endpoint é mutável enquanto o processamento do ponto evolui.
- 56 funcionários distintos com alguma marcação horária.
- 246 linhas com horários: 230 com quantidade par e 16 com quantidade ímpar.
- 41 linhas continham rótulos não horários: 33 `FÉRIAS` e 8 `ATESTAD`; esses rótulos não são batidas.
- As 16 linhas ímpares têm exatamente 3 horários e alcançam 14 funcionários distintos.
- Distribuição das linhas ímpares: 08/08 (1), 11/08 (2), 13/08 (3) e 14/08 (10).
- 283 linhas sem horário ou rótulo: 143 associadas a folga e 140 fora de folga.
- Das 140 fora de folga, 102 pertencem a cadastros demitidos/invisíveis e não devem gerar alerta operacional.
- Restaram 38 linhas de 31 funcionários ativos para conciliação com escala, abono, compensação e relatório oficial — ainda sem classificação como falta.
- 6 registros de afastamento no período.

### Interpretação de RH

Essas ocorrências são **triagem técnica**, não comprovação de falta ou irregularidade. Antes de qualquer contato ou ajuste, cruzar com horários, escalas, folgas, afastamentos, abonos, compensações e relatório oficial do Secullum. A concentração de 10 marcações ímpares em 14/08 merece ser conferida primeiro, inclusive para descartar processamento ainda não concluído ou batidas pendentes de sincronização.

## Teste de comunicação — unidade ACL — 15/08/2026

Teste executado às 09:28 BRT pela API oficial, em modo somente leitura:

- autenticação e banco: OK;
- unidade ACL identificada: OK;
- 14 colaboradores ativos vinculados à ACL;
- consulta de 14/08/2026: 14 linhas retornadas, todas com alguma marcação e nenhuma linha de outra unidade;
- consulta de 15/08/2026: 14 linhas retornadas, com marcações presentes em 2 linhas até o momento do teste;
- fonte de dados bruta: 1 evento da ACL incluído em 15/08/2026 às 08:19:39;
- consulta geral de equipamentos: OK, com 9 equipamentos no banco, mas a rota não informa status de conexão nem vinculação direta do equipamento à unidade.

**Conclusão:** a comunicação ACL → Secullum/API está funcionando. Este teste não comprova, isoladamente, que um REP físico específico esteja online neste exato momento, pois o evento bruto retornado não trouxe `EquipamentoId` e a API de equipamentos não expõe última comunicação.

## Radar Diário do Ponto — implantação

Implantado em 15/08/2026, em modo exclusivamente de leitura.

- **Agendamento:** diariamente às 07:00 BRT.
- **Data analisada:** dia anterior, considerando Brasília.
- **Entrega:** tópico de RH de origem.
- **Job Hermes:** `a396c65961e3` — Radar Diário do Ponto Conamore.
- **Script:** `~/.hermes/profiles/maria/scripts/secullum/daily_radar.py`.
- **Relatório nominal:** XLSX confidencial por unidade em `Sistemas de RH/Relatórios/AAAA-MM/`.
- **Estado agregado protegido:** `~/.hermes/profiles/maria/state/secullum-radar/`, permissão `600`.
- **Unidades:** ACL, BRG, GCL, SSL Matriz e SSL Filial.
- **Indicadores:** ativos, horários completos/incompletos, ausência de linha, ausência de horário, folgas, rótulos como férias/atestado, eventos brutos e última inclusão.
- **Controle:** textos como `FÉRIAS` e `ATESTAD` são classificados como rótulos, nunca como batidas.
- **Salvaguarda:** alertas são triagem; nenhum desconto, advertência, ajuste ou contato automático é realizado.

Teste inicial executado com a referência de 14/08/2026: 60 ativos, 5 unidades, arquivo XLSX com 60 linhas verificado e estado agregado gravado com permissão `600`.

### Lista diária de atrasos superiores a 20 minutos

Implantada em 15/08/2026:

- **Agendamento:** diariamente às 07:10 BRT.
- **Job Hermes:** `7ad383afffc1` — Lista diária de atrasos acima de 20 minutos.
- **Script:** `~/.hermes/profiles/maria/scripts/secullum/daily_delay_list.py`.
- **Data analisada:** dia anterior em Brasília.
- **Critério:** soma, em minutos, de entrada após a base, intervalo de almoço acima da duração prevista e saída antes da base; listar somente quando o total for estritamente superior a 20 minutos.
- **Fonte da jornada:** horários-base diários devolvidos pelo cálculo oficial do Secullum.
- **Exclusão:** colaborador sem nenhuma batida horária no dia não é calculado nem listado.
- **Batida parcial:** somente componentes comprováveis são calculados; ausência de saída ou retorno não é convertida automaticamente em atraso.
- **Entrega:** somente os nomes que ultrapassarem o limite, com unidade e composição do atraso. Se ninguém ultrapassar, informar resultado vazio.
- **Segurança:** leitura apenas; resultados protegidos em `~/.hermes/profiles/maria/state/secullum-atrasos/` com permissão `600`.
- **Confiabilidade:** se algum cálculo oficial falhar, a execução termina com erro em vez de entregar lista parcial como definitiva.

A função de cálculo foi validada com testes de entrada atrasada, almoço excedente, saída antecipada, jornada sem atraso e batida parcial. No ambiente Conamore, a API informou limite de **100 requisições de cálculo por hora por banco**. Os testes repetidos de implantação consumiram temporariamente essa janela; a rotina diária usará uma única execução, estimada em até 60 cálculos, e não concorre com o Radar das 07:00, que não chama a rota de cálculo. A primeira execução agendada ficou para 16/08/2026 às 07:10 BRT, em janela limpa.

## Diagnósticos de infraestrutura

- [[Sistemas de RH/Diagnóstico de Comunicação Secullum e Relógios - 2026-08-15|Diagnóstico de comunicação local — servidor Secullum e relógios — 15/08/2026]]

## Relatórios gerados

- [[Sistemas de RH/Relatórios/2026-08/Index|Relatórios Secullum — agosto de 2026]]
- [[Sistemas de RH/Relatórios/2026-08/Relatório de Entradas e Saídas por Unidade - 2026-08-14.xlsx|Entradas e saídas por unidade — 14/08/2026]]

## Validação obrigatória antes da automação

1. Confirmar autenticação e banco autorizado.
2. Consultar amostra mínima somente de leitura.
3. Comparar a amostra com relatório oficial emitido pelo Secullum.
4. Confirmar empresas/unidades e regras de competência.
5. Só depois automatizar conferência de ponto e alertas.

## Referências oficiais

- [Exemplo oficial de Integração Externa](https://github.com/Secullum/PontoWebIntegracaoExternaExemplo)
- [Documentação da API](https://pontowebintegracaoexterna.secullum.com.br/docs/index.html)
