# Manual de Conferência Mensal da Folha — Conamore

**Status:** procedimento oficial de referência para análise mensal pela Maria (RH)  
**Versão do documento-fonte:** 1.0  
**Base metodológica:** folha de maio/2026  
**Recebido e arquivado em:** 04/08/2026  
**Documento original:** [[Manual-Conferencia-Folha-Conamore-v1.0.docx]]

> [!important] Regra central
> Nenhuma divergência deve ser ajustada por suposição. Toda diferença deve ser demonstrada, classificada e encaminhada para validação.

## Objetivo e resultado esperado

Conferir mensalmente folha, encargos e guias das empresas Conamore, com rastreabilidade por empresa, estabelecimento, colaborador, rubrica e componente da guia. A conclusão deve ser uma destas:

- **Sem divergência**
- **Divergência explicada**
- **Divergência pendente de correção**

Os números de maio/2026 são apenas referência de validação do método, nunca valores fixos para competências futuras.

## Documentos necessários por competência

- Resumo geral da folha por empresa e estabelecimento
- Relatório analítico por colaborador, com rubricas, bases e descontos
- Relatório de encargos por empresa
- INSS por trabalhador e lotação tributária
- IRRF da folha
- DCTFWeb e DARF numerado
- Guia e relatório do FGTS Digital
- Pró-labore e contribuintes individuais
- Férias, rescisões, afastamentos e salário-maternidade
- Fechamento e totalizadores do eSocial, quando disponíveis
- Suportes de compensações, créditos e deduções
- Relação mensal de admissões, demissões, alterações salariais, faltas, variáveis e adiantamentos

## Fluxo mensal obrigatório

1. **Identificar a competência:** mês/ano, empresas, estabelecimentos, data de fechamento e versão dos relatórios.
2. **Validar a população:** headcount, admissões, desligamentos, afastamentos, férias, pró-labore e rescisões.
3. **Conferir remunerações:** salários, extras, comissões, prêmios, adicionais, férias, 13º, rescisões e demais verbas.
4. **Conferir descontos:** INSS, IRRF, faltas, atrasos, adiantamentos, benefícios, pensões e outros.
5. **Reconciliar bases:** INSS, FGTS e IRRF contra o analítico.
6. **Calcular encargos teóricos:** separar empregados, pró-labore, matriz, filial e regimes tributários.
7. **Comparar as guias:** DCTFWeb/DARF e FGTS Digital por componente e código.
8. **Investigar diferenças:** rastrear até colaborador, rubrica, estabelecimento, incidência ou compensação.
9. **Emitir relatório:** resumo, divergências, evidências, riscos, impacto e ações.
10. **Arquivar evidências:** planilha de cálculo, relatórios utilizados e parecer final.

## Regras específicas — SSL (Lucro Real)

**Estabelecimentos:** 1144 matriz e 1145 filial.

- Analisar cada estabelecimento separadamente e depois consolidar.
- **CPP empregados:** base previdenciária patronal × 20%.
- **CPP pró-labore/contribuinte individual:** base aplicável × 20%.
- **RAT/GILRAT ajustado:** RAT 3,0% × FAP 0,5000 = **1,5%**, somente sobre empregados.
- **Terceiros/Sistema S:** **5,8%** sobre empregados, conforme enquadramento validado.
- Não aplicar RAT/GILRAT nem Terceiros sobre pró-labore/contribuinte individual.
- **FGTS teórico básico:** base de FGTS × 8%, respeitando alíquotas e eventos diferenciados.
- INSS do empregado deve usar tabela progressiva vigente e considerar teto, múltiplos vínculos, férias, 13º e afastamentos.
- Salário-maternidade pode ser dedução previdenciária quando comprovado.
- Compensações, créditos, retenções e ajustes devem ter suporte documental e nunca servir como “diferença residual”.
- Revalidar FAP anualmente e confirmar enquadramento/percentuais de Terceiros.

### Composição gerencial da DCTFWeb/DARF — SSL

INSS empregados após deduções + INSS contribuinte individual/pró-labore + CPP empregados 20% + CPP contribuinte individual/pró-labore 20% + RAT/GILRAT 1,5% sobre empregados + Terceiros 5,8% sobre empregados + IRRF da folha − compensações/deduções legais.

Códigos de referência do modelo validado, a confirmar em cada competência:

| Código | Componente |
|---:|---|
| 1082 | INSS dos empregados |
| 1099 | Contribuinte individual |
| 1138 | CPP empregados e contribuinte individual |
| 1646 | RAT/GILRAT |
| 1170 | Salário-Educação |
| 1176 | INCRA |
| 1191 | SENAC |
| 1196 | SESC |

### Reconciliação matriz e filial

1. Calcular 1144 matriz separadamente.
2. Calcular 1145 filial separadamente.
3. Conferir bases e encargos por estabelecimento.
4. Somar por componente: empregados, pró-labore, CPP, RAT, Terceiros, IRRF e deduções.
5. Comparar o consolidado com a guia emitida na matriz.
6. Não aprovar apenas porque o total geral coincide; os componentes também devem reconciliar.

## Empresas do Simples Nacional

Para ACL, GCL, BRG e demais empresas do Simples:

- não replicar automaticamente a lógica da SSL;
- não presumir CPP patronal fora do DAS;
- confirmar anexo, atividade, segregação de receitas, folha e eventual Anexo IV;
- registrar o fundamento adotado pelo contador.

## Testes e alertas

- Headcount alterado sem movimentação registrada
- Salário-base diferente sem reajuste documentado
- Variáveis fora do padrão ou sem relatório de origem
- Adiantamentos sem correspondência com pagamentos anteriores
- Faltas/atrasos incompatíveis com o ponto
- Rubrica tributável fora da base do INSS ou indenizatória incluída indevidamente
- Diferença entre bases de FGTS e INSS sem evento justificável
- RAT/Terceiros sobre pró-labore ou percentual incorreto
- Dedução de salário-maternidade sem evento correspondente
- Rescisões incompatíveis com TRCT e encargos
- Guia cujo total coincide, mas componentes divergem
- Aplicação da lógica da SSL às empresas do Simples

## Registro de divergências

Para cada divergência, registrar:

- empresa e estabelecimento;
- competência;
- relatório/guia afetado;
- componente ou código;
- valor esperado, apresentado, diferença absoluta e percentual;
- colaboradores/rubricas envolvidos;
- hipótese da causa e evidência encontrada;
- responsável, prazo e status.

### Classificação

- **A — Erro confirmado:** cálculo, incidência, cadastro ou guia incorreta.
- **B — Diferença explicada:** diferença legítima, comprovada por teto, compensação, afastamento, incidência distinta ou evento específico.
- **C — Pendente de evidência:** documentação insuficiente para concluir.
- **D — Risco relevante:** potencial fiscal, trabalhista ou financeiro; validar imediatamente com contador/consultor e escalar às áreas responsáveis.

## Estrutura do parecer mensal

1. Competência e empresas analisadas
2. Documentos recebidos e ausentes
3. Resumo: headcount, remuneração, bases, descontos e líquido
4. Encargos: INSS, CPP, RAT, Terceiros, IRRF e FGTS
5. SSL: matriz, filial e guia consolidada
6. Empresas do Simples
7. Divergências
8. Explicações e evidências
9. Riscos e impacto financeiro
10. Ações, responsáveis e prazos
11. Conclusão

## Checklist de aprovação

- [ ] Todas as empresas e estabelecimentos incluídos
- [ ] Headcount reconciliado
- [ ] Salários, variáveis, férias e rescisões conferidos
- [ ] Bases de INSS, FGTS e IRRF reconciliadas
- [ ] Pró-labore separado dos empregados
- [ ] CPP conferida
- [ ] RAT 1,5% aplicado apenas sobre empregados da SSL
- [ ] Terceiros 5,8% aplicados apenas sobre empregados da SSL
- [ ] Deduções e compensações comprovadas
- [ ] SSL matriz e filial conferidas separadamente
- [ ] Guia consolidada reconciliada por componente
- [ ] Empresas do Simples analisadas conforme enquadramento
- [ ] Divergências classificadas e quantificadas
- [ ] Parecer e evidências arquivados

## Governança

Atualizar este registro em caso de mudança de regime tributário, CNAE, FAP, lotação tributária, estrutura societária ou sistema de folha/eSocial. Dúvidas jurídicas, fiscais ou previdenciárias devem ser validadas com o contador ou consultor responsável antes de qualquer correção.
