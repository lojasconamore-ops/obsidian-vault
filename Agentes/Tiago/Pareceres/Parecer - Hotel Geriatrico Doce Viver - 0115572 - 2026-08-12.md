# Parecer de Crédito — HOTEL GERIATRICO DOCE VIVER LTDA — Pedido 0115572

**Data da análise:** 12/08/2026 — BRT  
**Analista:** Tiago — Gerente Financeiro  
**Documentos analisados:** proposta comercial `0115572 Hotel Geriatrico.pdf` e relatório Equifax/Boa Vista `ANÁLISE HOTEL GERIATRICO.pdf`.

## Identificação

| Campo | Resultado |
|---|---|
| Razão social | HOTEL GERIATRICO DOCE VIVER LTDA |
| Nome fantasia | RESIDENCIAL GERIATRICO DOCE VIVER |
| CNPJ | 35.009.565/0001-14 |
| ID DEBX | A5610 |
| Endereço no bureau/Receita | Avenida Martim Afonso, 69, Parque Taquaral, Campinas-SP, CEP 13087-250 |
| Endereço na proposta/entrega | Avenida Martim Afonso, 71, Parque Taquaral, Campinas-SP, CEP 13087-250 |
| E-mail da proposta | doceviver1@gmail.com |
| Contato informado | Marcelio — (31) 9270-1990 |
| Atividade | Instituições de longa permanência para idosos — CNAE 87.11-5/02 |
| Natureza jurídica | Sociedade empresária limitada |
| Situação cadastral | Ativa |
| Data de abertura | 27/09/2019 |
| Porte | Microempresa |
| Capital social informado | R$ 120.000,00 |
| Regime informado pela Receita WS | Simples Nacional |
| Sócios-administradores na Receita WS | Erica Werneque Ribas e Elaine Cristina Werneque Miranda |

**Alerta cadastral:** a proposta indica o número 71, enquanto bureau e Receita indicam o número 69. O CEP, logradouro, bairro, cidade e CNPJ coincidem. Pode ser numeração de acesso/unidade, mas deve ser confirmado com o cliente e corrigido no cadastro/entrega antes do faturamento.

## Dados comerciais do pedido

- **Pedido/orçamento:** 0115572.
- **Emissão:** 12/08/2026.
- **Validade:** 12/08/2026.
- **Vendedor:** Maria Fabiana Barreto Paez.
- **Classe comercial:** Clínica.
- **Mix:** 30 lençóis para maca com elástico, 30 fronhas e 30 toalhas de banho.
- **Frete:** R$ 50,00.
- **Desconto:** R$ 0,00.
- **Total dos produtos:** R$ 2.319,00.
- **Total do pedido com frete:** R$ 2.369,00.
- **Pagamento impresso:** entrada de 50% + saldo em boleto de 30 dias.
- **Entrada:** R$ 1.184,50.
- **Saldo financiado:** R$ 1.184,50 em 30 dias.

### Reconciliação comercial

A proposta é consistente: R$ 2.319,00 em produtos + R$ 50,00 de frete = R$ 2.369,00. A entrada de R$ 1.184,50 e o boleto de R$ 1.184,50 totalizam corretamente o pedido.

O Hotel Finder/Oracle registra o orçamento 0115572 no valor de R$ 2.369,00, mas com condição interna `A DEFINIR`/código de pagamento diferente do PDF. O PDF é a fonte comercial do pedido; corrigir a condição no ERP antes do faturamento.

## Etapa 0 — Lista Negra Conamore

✅ **Cliente não localizado na Lista Negra Conamore** por CNPJ, razão social ou nome fantasia.

Prossegue-se com a análise.

## Etapa 1 — Histórico interno Conamore

O cliente foi localizado no Hotel Finder pelo CNPJ 35.009.565/0001-14 e ID DEBX A5610. O pedido atual é recorrente no sentido comercial: foram identificados **17 pedidos expedidos anteriores**, sem contar os orçamentos atuais 0115571 e 0115572.

| Indicador | Resultado |
|---|---:|
| Pedidos expedidos anteriores | 17 |
| Período | 07/08/2024 a 22/05/2026 |
| Total histórico expedido | R$ 38.089,90 |
| Ticket médio | R$ 2.240,58 |
| Maior pedido | R$ 4.406,00 |
| Pedido atual com frete | R$ 2.369,00 |
| Pedido atual / ticket médio | 1,06x |
| Pedido atual / maior pedido | 0,54x |

O pedido atual está perfeitamente alinhado ao padrão histórico de compras, abaixo do maior pedido e praticamente igual ao ticket médio. O cliente já operou várias vezes em condições semelhantes:

- entrada de 50% + boleto de 30 dias;
- cartão parcelado;
- pagamento à vista por PIX/boleta.

### Títulos e comportamento de pagamento — Oracle DEBX

A sessão Oracle foi validada com sucesso no serviço `conamore`, usuário `TEST_PED`, em leitura. Foram consultados os títulos individuais relacionados aos pedidos históricos nos schemas aplicáveis.

- Não foi identificado saldo vencido aberto associado aos pedidos históricos.
- Os títulos localizados foram pagos.
- Houve atrasos pontuais em parte do histórico, principalmente:
  - pedido 0065022: parcela com vencimento em 20/11/2025 paga em 24/11/2025, aproximadamente 4 dias após o vencimento;
  - pedido 0103885: parcela com vencimento em 21/06/2026 paga em 23/07/2026, aproximadamente 32 dias após o vencimento.
- A maior parte dos demais títulos foi paga no vencimento ou com poucos dias de diferença; também houve pagamentos antecipados.

**Classificação interna:** **Classe B/C — cliente recorrente e pagador, com histórico positivo, mas com episódios pontuais de atraso que exigem monitoramento.** Não há evidência de inadimplência estrutural ou dívida aberta na Conamore.

### Partes relacionadas e endereço

A busca por endereço identificou dois CPFs cadastrados no Hotel Finder no mesmo endereço informado na proposta, Avenida Martim Afonso, 71, Campinas-SP:

- Marcelio Miranda — CPF cadastrado no Hotel Finder;
- Matheus Palombino — CPF cadastrado no Hotel Finder.

A Receita WS informa Erica Werneque Ribas e Elaine Cristina Werneque Miranda como sócias-administradoras do CNPJ analisado. Não foi confirmada, apenas com esses dados, a relação societária entre os CPFs do cadastro e a empresa. O achado deve ser tratado como ponto de conferência cadastral, não como transferência automática de histórico ou limite.

## Etapa 2 — Score / Bureau Equifax | Boa Vista

Relatório emitido em **12/08/2026 às 13:58:14 — BRT**.

| Indicador | Resultado | Leitura |
|---|---:|---|
| Score Aprovação PJ | **736** | Forte |
| Probabilidade de inadimplência | **4,0%** | Excelente/administrável |
| Cadastro Positivo | Participante com informação | Positivo |
| Pagamento pontual | **100% em todos os meses da série** | Muito positivo |
| Pagamento atrasado | Sem ocorrências registradas | Positivo |
| Atraso médio | Sem registros | Positivo |
| Compromissos | Sem valor informado | Sem pressão identificada no painel |
| Crédito obtido | Série de baixo valor, aproximadamente 0,2 | Histórico externo limitado |
| Pendências financeiras | Nada consta | Positivo |
| Protestos | Nada consta | Positivo |
| Cheques sem fundos/devolvidos | Nada consta | Positivo |
| Situação do CNPJ | Ativo | Positivo |
| Consultas nos últimos 12 meses | 8 | Baixa/moderada |
| Faixa de funcionários | 1 a 19 | Compatível com microempresa |
| Última compra no bureau | Setembro/2024 | Histórico externo antigo e limitado |

O bureau é forte e limpo. A única limitação é que o histórico externo de crédito é pequeno e antigo; por isso, o histórico efetivamente pago na Conamore tem peso relevante.

## Etapa 3 — Coerência operacional do pedido

✅ **Coerente.** O cliente opera uma instituição de longa permanência para idosos. Lençóis para maca, fronhas e toalhas são itens compatíveis com a rotina assistencial e de hospedagem/cuidados.

O volume é pequeno e coerente com o histórico do cliente. Não há personalização, bordado ou produção especial. O risco operacional do pedido é baixo.

## Etapa 4 — Exposição real da Conamore

- **Total do pedido:** R$ 2.369,00.
- **Entrada de 50%:** R$ 1.184,50.
- **Exposição líquida:** R$ 1.184,50 em 30 dias.
- **Exposição relativa ao ticket médio:** aproximadamente 52,9% do ticket médio histórico.
- **Exposição relativa ao maior pedido:** aproximadamente 26,9% do maior pedido histórico.

A exposição é baixa, está protegida por 50% de entrada e encontra-se abaixo das condições e valores já testados para o cliente.

## Etapa 5 — Validação operacional online

🟢 **Operação forte/parcialmente corroborada.**

- Receita WS confirma CNPJ ativo, fundado em 2019, atividade de instituição de longa permanência para idosos, endereço em Campinas, sócios-administradores e capital social.
- Bureau confirma a mesma razão social, CNPJ, endereço-base, atividade e operação ativa.
- A busca pública encontrou múltiplos diretórios empresariais e referências ao Hotel/Residencial Geriátrico Doce Viver em Campinas.
- O histórico interno mostra 17 pedidos expedidos ao longo de aproximadamente dois anos, confirmando operação recorrente com a Conamore.
- A validação online não localizou, nesta sessão, site próprio robusto ou perfil de avaliações verificável; por isso, a classificação é forte pela convergência cadastral e histórico interno, não por avaliações públicas.

## Parecer final

### ✅ APROVAR

**Nível de risco:** baixo.

### Condição recomendada

Manter a condição da proposta:

- **50% de entrada: R$ 1.184,50**, compensada antes da expedição;
- **50% em boleto de 30 dias: R$ 1.184,50**.

A condição é coerente com o histórico do cliente, que já operou em entrada de 50% + 30 dias, e mantém a exposição líquida baixa.

### Condições de controle

1. Confirmar se o endereço correto de entrega é número 69 ou 71; alinhar proposta, cadastro e documento fiscal.
2. Corrigir no ERP a condição `A DEFINIR`, que diverge da condição impressa no PDF.
3. Compensar a entrada de R$ 1.184,50 antes da separação e expedição.
4. Monitorar o boleto de 30 dias, pois o histórico interno é positivo, mas contém episódios pontuais de atraso.
5. Não ampliar prazo ou limite automaticamente; reavaliar eventual aumento com base nos próximos pagamentos.
6. Manter o CNPJ analisado como referência principal; não transferir automaticamente histórico dos CPFs ou de outras pessoas cadastradas no mesmo endereço.

## Justificativa técnica objetiva

O cliente está fora da Lista Negra, possui CNPJ ativo desde 2019, bureau forte e limpo — score 736, probabilidade de inadimplência de 4%, 100% de pagamentos pontuais e nenhum protesto ou pendência —, além de histórico interno consistente: 17 pedidos expedidos, R$ 38.089,90 em compras e pagamentos localizados sem saldo vencido aberto. O pedido atual de R$ 2.369,00 é coerente com a operação geriátrica, próximo ao ticket médio e protegido por 50% de entrada. A aprovação é recomendada, com controle de compensação da entrada, correção do endereço e ajuste da condição no ERP.

**Decisão:** ✅ **aprovar o faturamento**, condicionado à compensação da entrada e à correção das divergências cadastral e de condição de pagamento.

**Fontes técnicas:** proposta comercial; relatório Equifax/Boa Vista; Lista Negra Conamore; Hotel Finder SQL Server (`conamore.Customers`, `debx.PDV_Detalhes`); Oracle DEBX (`TEST_MATRIZ`, `TEST_GCL`, somente leitura); Receita WS; busca pública online.
