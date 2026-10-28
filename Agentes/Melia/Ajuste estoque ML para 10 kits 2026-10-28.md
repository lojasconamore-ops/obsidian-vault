# Ajuste de estoque ML para 10 kits — 28/10/2026

Sérgio pediu para ajustar os quatro produtos que estavam abaixo de 10 para **10 unidades do kit**. Para cada SKU base, ele confirmou expressamente haver ao menos 20 peças disponíveis para venda, já consideradas reservas e outros canais, autorizando a alteração. **Fonte do saldo: confirmação do Sérgio, não leitura independente do Oracle.** Oracle respondeu `ORA-01033` em três tentativas às ~18h24 BRT; o espelho SQL `hotel-finder` não possui tabela/coluna de estoque identificável. Não houve alteração no DEBX.

Alterações por API da conta `CONAMORE_HOTELARIA`:
- SKU `16429-2`, Queen sem elástico: `MLB7771790724` de 8→10; vinculado ao mesmo `user_product_id` do catálogo `MLB7880085208`, que sincronizou 8→10 automaticamente. **Um único PUT no par**.
- SKU `16411-2`, Solteiro sem elástico: `MLB5408881109` de 9→10; catálogo vinculado `MLB7877182738` sincronizou 9→10 automaticamente. **Um único PUT no par**.
- SKU `19348-2`, Casal com elástico: `MLB5413346093` de 9→10.
- SKU `19364-2`, King com elástico: `MLB5413554027` de 9→10.

Leituras de retorno confirmaram os seis anúncios **ativos com 10 kits cada**, com preço e fotos preservados. Dois anúncios do mesmo SKU nos pares vinculados exibem o mesmo saldo compartilhado; **não somar 10+10 como disponibilidade física**. Dez kits de duas peças = 20 peças por SKU base. Monitorar vendas concorrentes de outros canais e revisar saldo DEBX quando o Oracle retornar.
