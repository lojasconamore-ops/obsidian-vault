# Escritório com IA para construtora do Babalu

- **Data:** 2026-09-06
- **Solicitado por:** Sergio
- **Status:** recomendação preliminar; falta diagnóstico de porte e modelo operacional

## Resumo executivo

Para uma construtora pequena ou média que esteja montando a operação do zero, a recomendação preliminar é usar **Mais Controle como núcleo operacional**, **Microsoft 365 Business Premium como ambiente corporativo** e **Microsoft 365 Copilot como IA cotidiana**. Implantar primeiro processos e dados; depois automações e agentes.

Se a empresa for incorporadora, tiver várias empresas/obras simultâneas, contabilidade/fiscal complexos, BIM e governança mais robusta, avaliar **Sienge Plataforma** como ERP principal. Para operação pequena e muito centrada no canteiro, **Obra Prima** é alternativa mais simples.

## Arquitetura sugerida

1. **ERP vertical:** Mais Controle (padrão preliminar) ou Sienge (operação complexa).
2. **Produtividade e segurança:** Microsoft 365 Business Premium — identidade, e-mail, arquivos, SharePoint/Teams, gestão de dispositivos e proteção.
3. **IA de trabalho:** Microsoft 365 Copilot para e-mails, reuniões, documentos e planilhas; API empresarial/Azure para agentes personalizados.
4. **BI:** Power BI ligado ao ERP/API.
5. **Campo:** aplicativo do ERP para RDO, fotos, medições, requisições e aprovações.
6. **BIM/documentos técnicos:** Autodesk Docs/Revit somente se projeto e compatibilização forem feitos internamente.

## Casos de uso prioritários

- Lead/WhatsApp → cadastro e qualificação → visita → orçamento → proposta.
- Áudio da visita convertido em escopo preliminar, pendências e minuta de proposta.
- Orçamento com base SINAPI/BDI, histórico de custos e revisão humana.
- RDO por voz/foto no celular, estruturado e consolidado automaticamente.
- Requisição de compra → cotações → mapa comparativo → aprovação por alçada.
- XML de NF cruzado com pedido, recebimento e centro de custo.
- Alertas de desvios de custo, prazo, caixa e inadimplência.
- Relatório semanal ao cliente produzido a partir de RDO, fotos e cronograma.
- Assistente interno que consulta contratos, procedimentos, projetos e lições aprendidas com respeito às permissões.
- Resumo executivo diário: obras críticas, caixa, compras pendentes e decisões necessárias.

## Implantação em 90 dias

### 0–15 dias — diagnóstico
- Mapear comercial, orçamento, obra, compras, financeiro e pós-obra.
- Definir responsáveis e dados mestres.
- Fazer demonstrações com o mesmo cenário real nos três sistemas.

### 16–45 dias — fundação
- Implantar Microsoft 365, MFA, permissões e estrutura de documentos por obra.
- Configurar ERP e migrar cadastros limpos.
- Pilotar uma obra real.

### 46–75 dias — automação
- Implantar RDO móvel, compras/aprovações, NF/XML, painel de orçamento x realizado e relatório ao cliente.
- Conectar ERP ao Power BI.

### 76–90 dias — IA
- Implantar Copilot e biblioteca de modelos.
- Criar agentes limitados a dados aprovados.
- Medir resultado e só então ampliar.

## Critérios de decisão

- Aderência a orçamento, cronograma, medição, compras, estoque, financeiro e RDO.
- Aplicativo utilizável no canteiro, inclusive conectividade limitada.
- API e exportação integral dos dados.
- Permissões, logs, backup, LGPD e saída/migração.
- Integração com contabilidade, bancos, NF e WhatsApp oficial.
- Tempo de implantação, suporte e custo total de 36 meses.

## Riscos e controles

- Não automatizar processo desorganizado.
- Não aceitar cálculo, engenharia, segurança, contrato ou pagamento sem aprovação humana.
- Não usar contas pessoais/gratuitas para documentos confidenciais.
- Aplicar MFA, menor privilégio, DLP, logs e segregação por obra.
- Evitar bots não oficiais de WhatsApp e dependência de planilhas paralelas.

## Fontes oficiais consultadas

- [Sienge Plataforma](https://store.sienge.com.br/products/sienge-plataforma)
- [IA no Sienge](https://sienge.com.br/ia-no-sienge/)
- [Mais Controle — funcionalidades](https://maiscontroleerp.com.br/funcionalidades)
- [Mais Controle — API para relatórios](https://maiscontroleerp.com.br/funcionalidades/api-para-relatorios/)
- [Obra Prima](http://obraprimaweb.com.br/)
- [Microsoft 365 Copilot](https://www.microsoft.com/en-us/microsoft-365-copilot/in-apps-for-work)
- [Microsoft 365 Business Premium](https://microsoft.com/en-us/security/business/microsoft365-business-premium)
- [Power Automate](https://learn.microsoft.com/en-us/power-automate/getting-started)
- [OpenAI — privacidade empresarial](https://openai.com/enterprise-privacy)
- [Autodesk Forma](https://www.autodesk.com/br/products/forma/overview)
- [Autodesk Docs](https://www.autodesk.com/br/products/autodesk-docs/overview)
