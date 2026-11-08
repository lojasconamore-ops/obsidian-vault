# GA4 + Google Ads — conversões otimizadas e off-line (08/11/2026)

**Consulta read-only às 17h30+ BRT.** Ads `customers/2335779078`; GA4 Hotelaria `properties/379729087`, Casa `394358599`, Hospitalar `372899047`. Janela recente consolidada até 05/11/2026 (sem D-1/D-0). Fonte: Composio Google Ads API GAQL `conversion_action`, `customer`, `segments.month × segments.conversion_action_name`; GA4 Data API `eventName × date/yearMonth/hostName/sessionSourceMedium`. Configuração atual ≠ snapshot de agosto. **Os meses do Ads são meses de atribuição do clique**, não data de implantação/upload.

## Veredito

- **Enhanced conversions:** pré-requisitos habilitados na conta Ads (`accepted_customer_data_terms=true`, `effective_enablement_setting=ON`, self-managed); **envio/match de PII hash e cobertura não comprovados** nesta consulta. Nome de ação `Conv. Otimiz` não prova ECL. API v26 removeu flag antiga, usa enablement_setting. Ver [Google — Manage offline conversions](https://developers.google.com/google-ads/api/docs/conversions/upload-offline).
- **Venda off-line por webhook Increazy (`compra_erp`):** recebe eventos no GA4 e conversões atribuídas no Ads em out/nov; **funciona parcialmente**. Isso é ação `WEBPAGE`, não importação `UPLOAD_CLICKS` de vendas ERP. Última evidência diária GA4 05/11/2026: 42 `compra_erp`; Ads 01–05/11: 17,052466 conversões atribuídas, DDA, não 17 pedidos.
- **Uploads off-line de leads:** há ações `UPLOAD_CLICKS` atribuídas, portanto o diagnóstico antigo de “zero uploads” está desatualizado. `Lead Convertido` em jul–ago/2026, sem registros na janela set–nov; `Lead qualificado (offline) - MyMetric` desde set/2026 e validação desde ago/2026, ambos com registros em nov. São **leads**, não fechamento de pedidos ERP. Seus resultados são secundários (`primary_for_goal=false`).
- **GA4 Hotelaria:** `purchase_erp` é key event (400 out/2026; 75 de 01–05/nov) e primeira evidência de evento em 25/09/2024; `compra_erp` começa em 24/06/2025 (713 out; 91 em 01–05/nov) mas **0 key events**; em out–05/nov todos os 804 `compra_erp` reportaram `hostName=(not set)` e `sessionSourceMedium=(not set)`. Evento recebido não significa atribuição de sessão resolvida. O `purchase` distinto tem 1.105 eventos em out/2026; não somar esses eventos como pedidos únicos.
- **Casa:** GA4 tem `purchase`, não `compra_erp` ou uploads ERP na amostra; Ads ação importada `CONAMORE Casa - GA4 ... purchase` continua secundária, 23 `all_conversions` em out e 3 em nov/01–05. **Hospitalar:** `purchase` no GA4, sem `compra_erp` na amostra. Não misturar segmentos.

## Ads — configuração atual e comparação

| Ação | Tipo | Primária hoje | Out/2026 | 01–05/nov/2026 | Nota |
|---|---|---|---:|---:|---|
| `WEB Conamore Offline ERP (compra_erp)` (`6886109455`) | WEBPAGE | Sim | 98,816644 conversions | 17,052466 conversions | DDA; recebe compra via tag/webhook |
| `[SERVERSIDE] Conv. Otimiz - Purchase` (`6900165034`) | WEBPAGE | **Sim** (mudou desde snapshot 14/08) | 8,043141 conversions / 294,092592 all_conversions | 33,956859 conversions / 43,956859 all_conversions | Verificar troca recente de primária e sobreposição |
| `01092024 Compra Otimizada (Web)` (`6877012980`) | WEBPAGE | **Não** (mudou desde snapshot) | 284,229773 all_conversions | 47,299268 all_conversions | Ainda recebe sinal, possível redundância |
| `SERVER SIDE Compra ERP` (`6902372843`) | WEBPAGE | Não | Sem linha em out/nov | Sem linha | Não presumir que seja a tag em uso |
| `Lead qualificado (offline) - MyMetric` (`7879122924`) | UPLOAD_CLICKS | Não | 7,461016 all_conversions | 27,061329 all_conversions | Lead atribuído, não venda |
| `Lead qualificado (offline) - MyMetric - Validação` (`7889538664`) | UPLOAD_CLICKS | Não | 5,660281 all_conversions | 18,175496 all_conversions | Possível fluxo paralelo/teste; conferir dedup |

Histórico Ads `WEB Conamore Offline ERP`: `all_conversions` com registros desde jan/2025, mas `conversions` primária só aparece a partir de mai/2025 na série extraída; isso **não determina data de criação nem de ativação exata**. GA4 `purchase_erp` já existia em 25/09/2024, mas `compra_erp` somente desde 24/06/2025. Conta Ads com 47 ações não removidas em 08/11.

## Melhorias prioritárias

1. **Diagnóstico Ads (Increazy/MyMetric):** ler tela de Diagnóstico de conversões otimizadas e de uploads, erros/rejeições, `job_id`, match rate, status de user-provided data e logs de envio; validar 1 lead e 1 pedido com e-mail/telefone hash e consentimento, sem expor PII. Configuração ON não é teste end-to-end. Separar ECL (lead offline) de enhanced conversions for web.
2. **Conciliação de vendas:** ligar `order_id`/pedido do link Increazy a um evento único e testar reconciliação com pagamento confirmado. Escopo aprovado anteriormente: links sim; venda física `F_MOVTO` não; boletos depois. O diagnóstico DEBX de setembro identificou checkout órfão `i1764011093`, tags paralelas e GCLID não persistido; **revalidar no ambiente atual antes de corrigir**.
3. **Higienizar metas:** revisar por campanha Casa/Hotelaria/Hospitalar que ação primária alimenta Smart Bidding; investigar por que `[SERVERSIDE] ... Purchase` virou primária enquanto `01092024` deixou de ser, e quais eventos sobrepõem `compra_erp`, `purchase_erp` e `purchase`. Não desativar nem alterar primárias sem Sérgio/DigitalCEO — mudaria lances.
4. **GA4 Hotelaria:** investigar `compra_erp` não marcado como key event e `source/medium=(not set)`; não marcar automaticamente como key event antes de resolver deduplicação/atribuição com `purchase_erp`. Capturar `client_id`/`session_id` e GCLID com consentimento adequado; depurar webhook → Stape → GA4/Ads.
5. **Monitorar 7 dias** após correção com amostra de pedidos pagos, logs de webhook, DebugView, GA4 e atribuição Ads por ação/segmento. Matias/Increazy nas tags e captura; Adrian na base legal/consentimento.

**Limites:** GA4/GAQL não expõem payload hash recebido nem taxa de match em consulta usada; nenhuma compra real/lead de teste foi enviada nesta auditoria. Contagens Ads sob DDA são frações atribuídas a anúncios, não total de vendas. Histórico do Oracle/Firestore citado é de setembro, não foi reconsultado nesta análise.
