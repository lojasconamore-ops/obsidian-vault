# Incubadora 101 — análise inicial, 27/10/2026

Fontes: apresentação recebida `Incubadora 101.html` (deck interativo, 27 módulos, dados SELLER em branco); selo/imagem enviada com CONAMORE_HOTELARIA e data 27/10/2026; API do vendedor Mercado Livre; ajuda oficial sobre Full e frete. O README referenciado pelo HTML (`../README.md`, K1..K14) e o dashboard HT para registrar ações **não acompanharam o anexo**. O deck é material de ensino, não fonte suficiente para comprovar termos contratuais ou elegibilidade.

## Regras que precisam confirmação escrita do assessor
- Imagem: meta de 50 vendas e até seis meses. Deck: início do relógio na primeira publicação, marco de 50 vendas até dia 90, 20 vendas/mês em três meses consecutivos até dia 180, saída após 30 dias sem vender ou 14 dias sem anúncio ativo e sem venda. Não foi localizada fonte pública oficial do programa específico “Incubadora 101”; confirmar essas regras, eventuais exceções e conceito de venda elegível no painel/termo.
- A primeira publicação atualmente visível na API da conta é `MLB5354263571` em 08/10/2026 às 18:07 BRT; o selo é de 27/10/2026. Se o relógio iniciar na primeira publicação, já se passaram 19 dias no início formal. Dia 90 seria 06/01/2027 e dia 180 06/04/2027, **apenas se a regra do deck for confirmada**.
- `GET /users/3742322571` em 27/10/2026: reputação `5_green`, `seller_reputation.transactions.completed=22`, `canceled=2`, total=24 em período histórico. Não presumir que o programa conte essas 22 transações como vendas elegíveis: 22 IDs de pedido pago anteriores agrupavam 14 packs/vendas; definir granularidade, cancelamentos e período com o assessor.

## Qualidade do material
- Pontos fortes: escopo da assessoria sem prometer operar a conta, reunião inicial de diagnóstico, menu de 27 temas, foco em ação executável, links a ajuda do ML, alertas de estoque/frete/reputação. Adaptação à Conamore exige escolher temas por risco e margem, não seguir genericamente os 27.
- Corrigir generalizações antes de usar como manual operacional: “pode alterar o título quando quiser” não vale a todos os anúncios (catálogo e `family_name` da integração podem bloquear); “A1 obrigatório para vender” é amplo demais (A1 é requisito específico do Full/faturador, conforme modalidade); “descrição máximo cinco linhas” é recomendação editorial, não limite geral; descontos e custos de frete dependem de reputação, preço, peso, modalidade e política atual (não prometer 50% invariável). Fotos/categoria também têm regras por categoria/estado do anúncio.
- O programa Decola é outro mecanismo; a conta já apresenta reputação verde, então não presumir elegibilidade ao Decola ou benefícios de Ads/Full/Clips citados no material sem conferir no painel.
- A apresentação pode gerar selo personalizado localmente no navegador; não é comprovante de adesão ou de compromisso contratual. O HTML sozinho não captura dados, nem registra combinados: estes ficam no dashboard HT não entregue.

## Plano Conamore para a primeira reunião
1. Solicitar confirmação escrita de elegibilidade, marco inicial, contagem de vendas, metas, saídas e cronograma da assessora.
2. Definir linha de base com data BRT: vendas/packs elegíveis, visitas, conversão por período, margem líquida por kit, reputação e cancelamentos.
3. Levar prioridades da auditoria: saldos DEBX dos lençóis com disponibilidade zero no site, duas fichas de protetor (Queen corrigida; Casal pendente), ofertas com mesmo SKU em catálogo/comum, pesos/medidas reais dos kits e margem com frete/comissão. Corrigir antes de ampliar Ads ou promoções.
4. Acordar tarefas curtas, responsável e prazo no dashboard HT; Melia executa a operação ML autorizada, Natália orienta catálogo/vendas, Tobias frete/SLA, Tiago margem/repasses, Bianco saldo e Flávia campanhas. Assessoria da Incubadora ensina/diagnostica, não acessa nem opera nossa conta segundo o próprio deck.

Referências externas conferidas: `https://www.mercadolivre.com.br/ajuda/31201` (Full) e `https://www.mercadolivre.com.br/ajuda/16467` (frete grátis). Nenhuma configuração, anúncio ou campanha foi alterada por esta análise.
