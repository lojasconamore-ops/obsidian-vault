---
tipo: parecer-credito
cliente: ENSEADA HOTEIS E TURISMO LTDA
cnpj: 75.088.237/0001-75
pedido: "0124008"
data: 2026-10-07
parecer: aprovar-com-restricao
risco: baixo-moderado
---

# Parecer de Crédito — Enseada Hotéis e Turismo LTDA

**Data de corte:** 07/10/2026, BRT  
**Pedido/proposta:** 0124008  
**CNPJ:** 75.088.237/0001-75  
**ID DEBX:** 07232  
**Nome operacional:** Condomínio Village Pontal do Sul  
**Alias administrativo no DEBX/proposta:** JCR Administração e Participações LTDA.  
**Representante:** Monica Cristina da Silva Cagliari

## Resumo executivo

**Parecer: 🟡 APROVAR COM RESTRIÇÃO**  
**Nível de risco: baixo a moderado**

Os dois documentos pertencem ao mesmo CNPJ. O cliente está em primeira compra efetiva com a Conamore: o único registro interno é o orçamento atual, ainda não faturado. O bureau é positivo, com score 705, probabilidade de inadimplência de 6%, Cadastro Positivo com informação e ausência completa de pendências, protestos e cheques negativos. A empresa está ativa desde 1972 e opera publicamente o Condomínio Village Pontal do Sul, com 25 chalés.

A condição solicitada é boleto integral em 15 dias, sem entrada. Pela política de alçada da Conamore, liberar mediante:

- **entrada compensada de 25%: R$ 415,70**;
- **saldo em boleto para 15 dias: R$ 1.247,10**;
- exposição líquida máxima: **R$ 1.247,10**.

Boleto integral sem entrada somente mediante autorização expressa do Sérgio.

## Etapa 0 — Lista Negra

✅ Não consta na Lista Negra da Conamore por CNPJ, razão social, nome operacional ou alias administrativo pesquisado.

## Etapa 1 — Identidade e documentos

### Conciliação dos dois PDFs

- Proposta: Enseada Hotéis e Turismo LTDA, CNPJ 75.088.237/0001-75.
- Bureau: Enseada Hotéis e Turismo LTDA, mesmo CNPJ.
- Endereço nos dois documentos: Av. Deputado Aníbal Khury, 17879, Jardim Marines, Pontal do Paraná/PR, CEP 83255-000.
- Os arquivos foram consolidados como um único caso.

### Cadastro interno

- SQL Server: ID 07232, CNPJ correto, status ativo, cadastro criado em 05/10/2026.
- Oracle `TEST_MATRIZ.F_CDEMP`: código 07232, razão social e CNPJ confirmados, status ativo (`0`).
- O código `A7232` pertence a outro cliente — 51.983.271 Adriano Sergio Rodrigues, CNPJ 51.983.271/0001-45, Ouro Preto/MG — e foi excluído integralmente da análise.
- A identificação foi validada por CNPJ + razão social + endereço + código Oracle, não apenas pela semelhança numérica do ID.

### Alias JCR

No cadastro interno, `JCR Administração e Participações LTDA.` aparece como nome/alias, enquanto a razão social legal confirmada é `Enseada Hotéis e Turismo LTDA`. O CNPJ da proposta, bureau, Receita e operação pública é 75.088.237/0001-75. O alias não foi tratado como segundo CNPJ e nenhum histórico de outra empresa foi transferido.

## Etapa 2 — Histórico Conamore

### SQL Server / Hotel Finder

Foi localizado apenas:

- Pedido 0124008
- Data do orçamento: 05/10/2026
- Status: **Orçamento**
- Valor: R$ 1.662,80
- Condição: boleto 15 dias
- Data de venda: inexistente
- Data de aprovação: inexistente

Não há pedido anterior expedido, faturado ou aprovado para este CNPJ.

### Oracle

Consulta realizada em 07/10/2026 às 09:20 BRT nos schemas:

- TEST_MATRIZ
- TEST_ACL
- TEST_CHC
- TEST_GCL
- TEST_BRG

Resultado:

- empresa ativa localizada em TEST_MATRIZ;
- nenhum pedido anterior em `F_PEDVENDA`;
- nenhum título pago, aberto ou vencido em `F_TITULOS`;
- nenhum registro nos demais schemas.

**Classificação:** primeira compra efetiva / histórico interno ainda não testado.

## Etapa 3 — Partes relacionadas

- A busca pelo endereço e número exatos localizou apenas o próprio CNPJ.
- Outros clientes do mesmo CEP possuem endereços, nomes e CNPJs diferentes e foram mantidos separados.
- Foi encontrado `JCR Comércio de Brinquedos LTDA`, CNPJ 21.396.671/0001-93, em Curitiba/PR; não houve confirmação de QSA, endereço ou operação comum, portanto nenhum histórico ou limite foi transferido.
- O QSA atual da Enseada inclui FR4 Imóveis e Participações Societárias LTDA, João Carlos Ribeiro, João Guilherme Reichmann Ribeiro, Maria Celina Canto Alvares Correa e Bruno Ribeiro Evangelista de Macedo. Não foi localizada outra empresa Conamore com vínculo atual suficientemente comprovado.

## Etapa 4 — Score / Bureau

Relatório **Equifax | Boa Vista — Define Risco Positivo**, emitido em **07/10/2026 às 09:02:14**:

- Número de resposta: **040769036-3**
- Score Aprovação PJ: **705**
- Probabilidade de inadimplência: **6%**
- Cadastro Positivo: participante com informação
- Pendências e restrições financeiras: **nada consta**
- Cheques sem fundos: **nada consta**
- Cheques sustados motivo 21: **nada consta**
- Cheques devolvidos informados pelo usuário: **nada consta**
- Protestos: **nada consta**
- Consultas: 2, ambas pela Frigelar em 04/09/2026
- Compromissos: índice zero em todos os meses apresentados
- Comprometimento futuro: índices baixos e concentrados até 60 dias; os campos são pontuações do modelo, não valores monetários

### Cadastro Positivo

O relatório mostra pontuação máxima de pagamento pontual em outubro, dezembro e janeiro, além de setembro de 2026. Todas as faixas de atraso — 6 a 15, 16 a 30, 31 a 60 e acima de 60 dias — aparecem sem ocorrência. Não há atraso médio informado.

### Situação cadastral

- Situação: ativa
- Fundação: 08/06/1972
- Atividade: hotéis — CNAE 5510-8/01
- Faixa de funcionários: 1 a 19
- Endereço coerente com a proposta

A consulta da Receita embutida no bureau tem corte de 10/04/2023 e está desatualizada. Consulta pública atualizada em 07/10/2026 confirmou:

- CNPJ ativo;
- capital social de R$ 524.456,00;
- microempresa;
- operação no Lucro Real nos anos públicos de 2019 a 2024;
- endereço cadastral idêntico;
- quadro societário atual informado acima.

**Interpretação:** bureau forte e limpo. O risco residual decorre da ausência de histórico direto com a Conamore, não de restrição externa.

## Etapa 5 — Coerência do pedido

### Produtos

- 24 protetores de colchão impermeáveis, casal 140×190×30 cm.

A operação pública possui 25 chalés, e o pedido contém 24 protetores. A quantidade é especialmente coerente com reposição/padronização de enxoval do empreendimento.

### Reconciliação financeira

- 24 × R$ 67,20 = R$ 1.612,80
- Total sem desconto: R$ 1.612,80
- Desconto: R$ 0,00
- Total com desconto: R$ 1.612,80
- Frete: R$ 50,00
- **Total do pedido: R$ 1.662,80**

Os valores fecham sem divergência.

### Condição impressa

- Forma de pagamento: boleto 15 dias
- Entrada: inexistente
- Exposição impressa: **R$ 1.662,80**

A proposta não contempla a entrada mínima de 25% definida pela alçada financeira.

### Validade

- Emissão: 05/10/2026
- Validade: 09/10/2026
- Na data da análise, 07/10/2026, a proposta está válida.
- Se o faturamento ocorrer após 09/10/2026, exigir revalidação/reemissão.

## Etapa 6 — Exposição real e condição recomendada

### Condição solicitada

- Total financiado: R$ 1.662,80
- Entrada: R$ 0,00
- Exposição: R$ 1.662,80

### Condição aprovada

- Entrada de 25%: **R$ 415,70**
- Saldo financiado: **R$ 1.247,10**
- Vencimento do saldo: boleto em 15 dias
- Exposição líquida: **R$ 1.247,10**

Trata-se de prazo curto, valor reduzido e exposição compatível com o bureau. A entrada funciona como validação de alçada e capacidade de pagamento na primeira compra.

## Etapa 7 — Validação operacional online

🟢 **Operação forte**

A empresa opera publicamente como **Condomínio Village Pontal do Sul**:

- site de reservas ativo;
- CNPJ 75.088.237/0001-75 declarado no próprio site;
- endereço exato da proposta e do cadastro público;
- 25 chalés para locação temporária;
- unidades de 30 m² a 50 m², para até seis hóspedes;
- estrutura com estacionamento, Wi-Fi, acomodações mobiliadas, cozinha, TV e parte das unidades com ar-condicionado;
- reservas e preços disponíveis online;
- Google Maps: avaliação 4,7;
- telefone e e-mail de reservas publicados.

A operação pública confirma capacidade física e coerência do pedido. A diferença entre o telefone comercial da proposta e o telefone público de reservas é compatível com departamentos distintos e não gerou divergência de identidade, pois CNPJ, razão social, endereço e site coincidem.

## Decisão final

**🟡 APROVAR COM RESTRIÇÃO — risco baixo a moderado.**

Autorizar após:

1. corrigir a condição para **25% de entrada + saldo em boleto para 15 dias**;
2. compensar a entrada de R$ 415,70 antes do faturamento;
3. limitar a exposição a R$ 1.247,10;
4. reemitir a proposta se o faturamento ocorrer após 09/10/2026.

**Alternativa sem entrada:** boleto integral em 15 dias somente com autorização expressa do Sérgio.

**Justificativa técnica objetiva:** empresa ativa desde 1972, bureau limpo com score 705 e PD de 6%, operação pública robusta com 25 chalés, pedido pequeno e perfeitamente coerente com a estrutura. A restrição decorre exclusivamente de ser a primeira compra efetiva e da proposta solicitar boleto sem entrada, não de qualquer ocorrência negativa.
