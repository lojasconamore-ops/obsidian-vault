# Nuvemshop — aplicações e aderência para a Conamore

**Data:** 07/10/2026  
**Status:** avaliação estratégica inicial, sem recomendação de migração aprovada.

## O que é

A Nuvemshop é uma plataforma SaaS de comércio eletrônico. Ela fornece vitrine, checkout, pagamentos, logística, estoque, marketing, atendimento, integrações, ponto de venda e conexão com canais como redes sociais e marketplaces. Não é um marketplace: é a infraestrutura da loja própria e do ecossistema de vendas.

## Recursos relevantes

- Loja responsiva e checkout integrado.
- Nuvem Pago e integrações com outros meios de pagamento.
- Nuvem Envio e integrações logísticas.
- Gestão de catálogo, estoque, pedidos e clientes.
- Conexão com Mercado Livre, Amazon, Shopee, Google Shopping e redes sociais.
- PDV para registrar vendas físicas e compartilhar catálogo/estoque.
- B2B e B2C na mesma loja, com preços por login e pedido mínimo.
- Múltiplos centros de distribuição.
- APIs e webhooks para integração com ERP, estoque, pedidos, clientes, faturamento e cancelamentos.
- Nuvem Marketing, Nuvem Chat e ferramentas de IA.

## Aplicações para a Conamore

### 1. Conamore Casa

É o caso de uso com maior aderência inicial: loja B2C, lojas físicas, catálogo visual, campanhas, retirada local e futura operação no Mercado Livre. A Nuvemshop poderia substituir a camada Magento/PWA e centralizar vitrine, checkout e canais. O Oracle deve permanecer como fonte de verdade para estoque, preços, pedidos, faturamento e fiscal.

Não substituir o PDV/Oracle das lojas físicas sem homologação fiscal e operacional. O PDV Nuvemshop deve ser tratado apenas como hipótese de fase posterior.

### 2. Hotelaria B2B

A plataforma possui tabelas de preço, compra mínima e identificação do cliente atacadista por login. No Next, pode operar múltiplas tabelas, catálogo restrito e condições B2B por CNPJ. Isso poderia permitir autosserviço para hotéis pequenos, pousadas, Airbnb e administradores, mantendo negociações personalizadas e contas estratégicas com o time comercial.

A aderência depende de provar integração com Oracle, condições comerciais, representantes, crédito, frete negociado, impostos e pedidos que continuam no comercial.

### 3. Mercado Livre

A Nuvemshop pode ser usada como hub de catálogo/canais e integrar a loja própria com Mercado Livre, Amazon e Shopee. Para a operação em preparação, poderia reduzir recadastro e sincronizar estoque/pedidos. Ainda assim, o Oracle deve continuar como mestre; evitar criar um segundo estoque independente.

### 4. Pagamento e frete

Nuvem Pago pode melhorar a experiência do checkout D2C, mas deve ser comparado com taxas, aprovação, antecipação, chargeback e conciliação atuais. A plataforma permite outros gateways, porém apenas um fica com checkout transparente por vez.

Nuvem Envio pode ser útil para Casa e pedidos padronizados. A Hotelaria possui pedidos maiores, transportadoras, negociação e particularidades de frete; precisa validar integrações externas e tabelas próprias.

### 5. Marketing e atendimento

Nuvem Marketing e Nuvem Chat sobrepõem parte do RD Station e do Octadesk. Não ativar por padrão. Primeiro definir qual ferramenta será fonte de verdade para consentimento, contatos, automações, WhatsApp, descadastro e atribuição. Duplicar as plataformas tende a fragmentar dados e aumentar custo.

## Plano mais provável

Pela receita e complexidade da Conamore, o plano Next é o candidato mais coerente para uma migração completa. Planos inferiores podem servir para protótipo, mas têm limites de tabelas B2B, CDs, suporte e customização.

## Riscos e gates

1. Integração Oracle/DEBX para SKU, preço, estoque, pedidos, cancelamentos, nota e rastreio.
2. SEO: manter URLs, canônicos, metadados, schema e redirecionamentos 301.
3. Reimplementar GA4, GTM, Consent Mode, sGTM, compra_erp e conversões offline.
4. Validar regras B2B, tabelas, CNPJ, compra mínima, representantes e crédito.
5. Homologar frete de produtos volumosos e pedidos B2B.
6. Evitar conflito com RD Station e Octadesk.
7. Validar marketplace e estoque sem duplicidade.
8. Comparar TCO total: plano, agência, apps, middleware, manutenção, pagamento e logística.

## Recomendação

Não migrar toda a Conamore diretamente. Solicitar demonstração técnica do Nuvemshop Next e executar prova de conceito fechada, sem alterar domínio, com dados reais e integrações simuladas.

Ordem sugerida:

1. Avaliar Conamore Casa como primeira candidata.
2. Provar sincronização Oracle → Nuvemshop e Nuvemshop → Oracle.
3. Testar checkout, frete, GA4/GTM e Mercado Livre.
4. Simular B2B com pelo menos três perfis comerciais reais.
5. Comparar performance, conversão, custo operacional e TCO com a estrutura atual.
6. Só então decidir por migração, coexistência ou descarte.

## Fontes oficiais

1. https://www.nuvemshop.com.br/funcionalidades
2. https://www.nuvemshop.com.br/next
3. https://www.nuvemshop.com.br/solucoes/venda-no-atacado
4. https://dev.nuvemshop.com.br/docs/erp-guide/overview
5. https://www.nuvemshop.com.br/canais/loja-fisica
6. https://atendimento.nuvemshop.com.br/pt_BR/meios-de-pagamento/guia-meios-de-pagamento-disponiveis-na-sua-nuvemshop
7. https://www.nuvemshop.com.br/planos-e-precos
