# 🗄️ RD Station — Guia Completo de Operação

Manual de operação do RD Station da Conamore.

---

## 🔌 Conexão MCP (27 ferramentas)

A Flávia tem acesso direto ao RD Station via Hermes MCP. 27 tools operacionais.

**Comandos úteis:**
- Ver segmentações: `mcp_rdstation_segmentation_list`
- Buscar workflows: `mcp_rdstation_workflows_search`
- Ver detalhes de workflow: `mcp_rdstation_workflow_get_details`
- Listar LPs: `mcp_rdstation_landing_pages_search`
- Listar popups: `mcp_rdstation_popups_search`
- Listar formulários: `mcp_rdstation_forms_search`
- Ver contato: `mcp_rdstation_get_contact_by_id_email`
- Ver funil do contato: `mcp_rdstation_contact_funnel_stage_get`

> ⚠️ Analytics do funil retorna 401 — provável limitação de plano.

---

## 📄 Landing Pages (21 no total)

### Publicadas (12)
| LP | ID | Conversão | Criada |
|---|---|---|---|
| Catálogo Produtos Hotelaria | 414935 | catalogo-produtos-enxoval-para-hotelaria | 2017 |
| eBook Reuso Toalhas | 399512 | ebook-programa-de-reuso-de-toalhas | 2017 |
| eBook Reuso Toalhas (Hotelaria) | 399514 | ebook-programa-de-reuso-de-toalhas-hotelaria | 2017 |
| EBOOK MARKETING | 213492 | ebook-marketing-hotelaria | 2016 |
| EBOOK DICAS MARKETING 2.0 | 2429462 | ebook-dicas-marketing-2 | 2021 |
| Diferenciais Airbnb | 1074879 | ebook-diferenciais-para-anfitrioes-airbnb | 2019 |
| Checklist Arrumação Quartos | 5326293 | arrume-os-quartos-de-acordo-com-a-estacao | 2023 |
| Checklist 2.0 | 5332160 | checklist-2-0-para-arrumar-os-quartos | 2023 |
| LP Amostra Protetores | 3051145 | lp-envio-de-amostra-protetores | 2022 |
| Conamore 21 anos | 6373338 | conamore-21-anos | 2024 |
| Cupom Pesquisa | 6100462 | cupomairbnb | 2024 |
| Cupom Casa Repouso | 6488293 | cupom-casa-repouso | 2024 |
| Pesquisa Pós-Compra | 9178829 | pesquisa | 2026 |

### Não Publicadas / Rascunho (9)
| LP | Conversão | Observação |
|---|---|---|
| LP Marketing para Hotelaria CONAMORE | lp-marketing-para-hotelaria-conamore | 🔴 Criada 27/05, NÃO PUBLICADA |
| pesquisa-casa | pesquisa-casa | Rascunho |
| pesquisa-negocios | pesquisa-negocios | Rascunho |
| teste | teste-e4c57dfe1a882ef52f25 | Teste |
| Checklist Arrumação | checklist-arrumacao | Duplicada? |
| pesquisa-negocios Duplicado | pesquisa-negocios-duplicado | Duplicada |
| Pesquisa AIRBNB | pesquisa-airbnb | Rascunho |
| LP Pesquisa Pós Compra teste | lp-pesquisa-pos-compra-conamore-hotelaria-teste | Teste |
| eBook Diferenciais Airbnb | diferenciais | Rascunho 2026 |

---

## 🪟 Popups (25 cadastrados, 7 publicados)

### Publicados
| Popup | Trigger | Descrição |
|---|---|---|
| BLOG (exit-intent) | Exit Intent | Captura de leads saindo do blog |
| Cadastro no site (exit-intent) | Exit Intent | Cadastro geral |
| Cadastro Hospitalar (exit-intent) | Exit Intent | Segmento hospitalar |
| Cadastro Cama e Banho (exit-intent) | Exit Intent | Segmento casa |
| WhatsApp site (floating button) | Floating Button | Botão flutuante WhatsApp |
| WhatsApp site Loja (floating button) | Floating Button | Botão WhatsApp loja |
| 10% a vista finais de semana | Floating Bar | Promoção recorrente |

**Observação:** Muitos popups promocionais "10% à vista" estão **não publicados** — provavelmente campanhas pontuais que expiraram.

---

## 📋 Formulários (14)

| Formulário | Conversão | Publicado? |
|---|---|---|
| Checklist: dicas para arrumação | checklist-1 | ✅ |
| Checklist Rede Sociais | checklist-rede-sociais | ✅ |
| Ficha Nacional de Registro de Hóspede | ficha-nacional-de-registro-de-hospede | ✅ |
| Checklist arrumação | checklist-arrumacao | ✅ |
| Land Page RMC | landing-page-rmc | ✅ |
| Formulário RMC | formulario-rmc | ✅ |
| Formulário eBook escolha enxoval | formulario-ebook-escolha-do-enxoval | ✅ |
| Popup Institucional | popup-institucional | ✅ |
| Fale Conosco Site | formulario-fale-conosco-site | ✅ |
| LP Pesquisa Casa | lp-pesquisa-casa | ✅ |
| LP Pesquisa Negócios | lp-pesquisa-negocios | ✅ |
| LP Checklist Imóvel Temporada | lp-checklist-imovel-para-temporada | ✅ |
| LP Pesquisa Pós Compra | lp-checklist-imovel-para-temporada-duplicado | ✅ |
| eBook Diferenciais Airbnb (novo) | ebook-diferenciais-para-anfitrioes-airbnb-formulario | ❌ Rascunho |

---

## 🔄 Workflows (22 total, 17 ativos)

### Resumo dos Ativos
1. **Recuperação de carrinho** — Lead que abandonou
2. **Retirar lead do abandono** — Complemento
3. **Fluxo de Boas-Vindas** — Onboarding (TEM CÓPIA ATIVA)
4. **Recompra 120 dias** — Pós-venda
5. **Compra finalizada** — Transacional
6. **Checklist** — Nutrição conteúdo
7. **Catálogo de produtos > oportunidade** — Geração lead qualificado
8. **Resposta LP Catálogo** — Automático
9. **Resposta LP Diferenciais Airbnb** — Automático
10. **Fluxo de Boas-Vindas Duplicado** — ⚠️ Igual ao #3, revisar
11. **Checklist 2.0** — Nova versão
12. **Pluga x Compradores RD** — Integração CRM
13. **Limpeza da base Set/2024** — Data cleaning
14. **Leads WhatsApp Pluga** — Integração CRM
15. **Pesquisa Hotelaria 2025** — Coleta dados
16. **Pesquisa Casa e Banho 2025** — Coleta dados
17. **Régua Ebook Receba bem** — Conteúdo (novo)
18. **Régua Checklist arrumação temporada** — Conteúdo (novo)

### Desativados (5)
| Nome | Motivo |
|---|---|
| Contato WhatsApp | Sem uso |
| Resposta LP EBOOK DICAS MARKETING 2.0 | Sem uso |
| Campanha Protetores | Sem uso |
| Inscrição Newsletter Site | Desativado |
| (N/A) | — |

---

## 🧹 Limpeza e Organização

### O que revisar
1. **Segmentações sazonais antigas** (2017) — CLIENTES JANEIRO, Carnaval, Promoção Março, Julho-Agosto-Setembro-Outubro — muitas de campanhas específicas, verificar se ainda têm contatos ativos ou se podem ser arquivadas
2. **Fluxo de Boas-Vindas Duplicado** — por que duas cópias ativas?
3. **LPs não publicadas** — decidir se publica, completa ou arquiva
4. **Popups "10% a vista"** — várias versões não publicadas, limpar

---

## 🛡️ Regras de Operação

- **SEMPRE** verifique antes de excluir segmentações ou desativar workflows
- **TESTE** LPs e popups antes de publicar
- **DOCUMENTE** mudanças aqui no Obsidian
- **CONFIRME** com DigitalCEO antes de ações destrutivas
- **MONITORE** resultados 7 dias após mudanças significativas

---

*Documento de treinamento da Flávia. Dados atualizados em 30/05/2026.*
