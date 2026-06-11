# Fluxo tradicional de compras — Conamore

```mermaid
flowchart TD
    A[Identificação da necessidade\n(estoque mínimo, demanda, produção, manutenção)] --> B[Requisição de compra no ERP\nitem, quantidade, centro de custo, prazo, urgência]
    B --> C{Saldo em estoque / cobertura\nresolve a necessidade?}
    C -- Sim --> Z[Fim\nSem compra nova]
    C -- Não --> D[Validação no ERP\ncontrato vigente, fornecedor homologado, orçamento, duplicidade de pedido]
    D --> E{Compra já coberta\nem contrato ou pedido aberto?}
    E -- Sim --> F[Seguir condição vigente\npreço, prazo e frete do acordo]
    E -- Não --> G[Cotação / sourcing\nsolicitar propostas de fornecedores homologados]
    F --> H
    G --> H[Comparação técnica e comercial\npreço, prazo, frete, qualidade, histórico, garantia]
    H --> I[Negociação com fornecedor\nfechar melhor custo total e menor risco]
    I --> J{Valor / categoria exige aprovação?}
    J -- Sim --> K[Fluxo de aprovação no ERP\nCompras + Gestor + Financeiro + Diretoria, conforme alçada]
    J -- Não --> L[Emitir pedido de compra (PO) no ERP]
    K --> L[Emitir pedido de compra (PO) no ERP]
    L --> M[Fornecedor confirma pedido\nquantidade, prazo e condições]
    M --> N{Prazo atende operação\n(lógica de estoque / fábrica / logística)?}
    N -- Não --> O[Replanejar\nnovo fornecedor, expedição parcial ou ajuste de prazo]
    N -- Sim --> P[Agendar recebimento\ncom logística / almoxarifado]
    O --> P
    P --> Q[Recebimento físico\nconferência de quantidade, qualidade e integridade]
    Q --> R{Conforme pedido?}
    R -- Não --> S[Registrar divergência no ERP\nrecusa, devolução, complemento ou abatimento]
    R -- Sim --> T[Recebimento fiscal / entrada\nNFe, impostos e atualização de estoque]
    S --> U{Divergência resolvida?}
    U -- Não --> V[Encerrar tratativa com fornecedor\nreclamação, devolução ou substituição]
    U -- Sim --> T
    T --> W[Conciliação 3 vias\nPO x recebimento x nota fiscal]
    W --> X{Tudo OK para pagamento?}
    X -- Não --> Y[Travar pagamento\nabrir ocorrência para Compras / Fiscal / Financeiro]
    X -- Sim --> AA[Programar pagamento\nconforme vencimento e fluxo de caixa]
    AA --> AB[Encerrar pedido no ERP\nbaixar status e atualizar KPIs]
    AB --> AC[Análise de desempenho\npreço, prazo, OTIF, qualidade, ocorrências]
```

## Observações de governança
- Toda compra relevante deve nascer de uma *requisição formal* no ERP.
- *Sem estoque, contrato ou aprovação, não há pedido.*
- *Preço não fecha sozinho*: prazo, qualidade, imposto, frete e confiabilidade entram na conta.
- O ERP robusto deve suportar:
  - alçada de aprovação por valor e categoria
  - cadastro e homologação de fornecedores
  - controle de orçamento e centro de custo
  - pedido de compra, recebimento e nota fiscal integrados
  - conciliação 3 vias
  - rastreabilidade de exceções e auditoria

## Versão operacional para a Conamore
1. Demanda surge na operação, estoque, fábrica ou manutenção.
2. Compras valida necessidade, cobertura e prioridade.
3. ERP verifica contrato, saldo, orçamento e alçada.
4. Se necessário, roda cotação e negociação.
5. Aprova, emite PO e registra compromisso.
6. Logística/almoxarifado agenda recebimento.
7. Recebe, confere, dá entrada fiscal e concilia.
8. Financeiro paga no vencimento.
9. Compras analisa fornecedor e atualiza histórico.

## Regra prática
- *Urgência não substitui processo*.
- *Exceção existe, mas precisa ficar registrada*.
- *O objetivo é abastecimento com previsibilidade, margem e rastreabilidade.*
