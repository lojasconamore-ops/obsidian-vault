# Validação do catálogo Conamore 2026 - links

Data da rechecagem: 2026-06-13

## Resultado geral
- Links testados: 191
- OK: 183
- Com problema: 8

## Problemas encontrados

### Página 20 — Cobertor Flannel
1. `https://www.conamore.com.br/cobertor-hotelaria/linha-de-produto/cobertores-para-hptelaria-flannel?q=cobertores_tamanho.value:799`
2. `https://www.conamore.com.br/cobertor-hotelaria/linha-de-produto/cobertores-para-hptelaria-flannel?q=cobertores_tamanho.value:800`
3. `https://www.conamore.com.br/cobertor-hotelaria/linha-de-produto/cobertores-para-hptelaria-flannel?q=cobertores_tamanho.value:801`
4. `https://www.conamore.com.br/cobertor-hotelaria/linha-de-produto/cobertores-para-hptelaria-flannel?q=cobertores_tamanho.value:802`
5. `https://www.conamore.com.br/cobertor-hotelaria/linha-de-produto/cobertores-para-hptelaria-flannel?q=cobertores_cores.value:927\r`
6. `https://www.conamore.com.br/cobertor-hotelaria/linha-de-produto/cobertores-para-hptelaria-flannel?q=cobertores_cores.value:926`
7. `https://www.conamore.com.br/cobertor-hotelaria/linha-de-produto/cobertores-para-hptelaria-flannel?q=cobertores_cores.value:802`
8. `https://www.conamore.com.br/cobertor-hotelaria/linha-de-produto/cobertores-para-hptelaria-flannel?q=cobertores_cores.value:804\r`

## Observações
- O erro está concentrado na mesma linha de produto.
- Há typo no slug: `hptelaria` → `hotelaria`.
- Há URLs com `\r` no final, que viram `%0D` na requisição.
- Na rechecagem atual, os problemas anteriores das páginas 5, 6, 7, 21, 34 e 38 não apareceram mais.

## Ação recomendada
- Corrigir o slug da página 20.
- Remover caracteres de quebra de linha invisíveis nas URLs.
- Reexportar o catálogo e fazer uma nova passada rápida antes de publicar.
