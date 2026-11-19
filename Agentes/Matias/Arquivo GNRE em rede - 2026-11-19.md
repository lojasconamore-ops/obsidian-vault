# Arquivo GNRE em rede — 2026-11-19

A pedido do Sergio, realizada cópia de preservação dos artefatos locais GNRE anteriores a 2026-11-19 00:00 BRT para a subpasta restrita `\\172.169.0.3\dados\DEBX XML\DIFAL\ARQUIVO_GNRE_ATE_2026-11-18\`.

- `GNRE_ATE_2026-11-18.tar.gz`: **20.131.286 bytes**, SHA-256 `f005425e2ebc6c0a5fffad563b0b2aa52d3fe507537b3262598f9b17b5c7162e`.
- `SHA256.txt` na mesma pasta; seu conteúdo foi lido de volta e comparado com o original.
- O pacote contém **514 entradas**: 384 arquivos `archive/` (XML de requisição/resposta/resultado e PDFs), 81 XMLs `inbox/`, 46 XMLs `normalized/` e três itens em `metadata/` (snapshot consistente de `state.db` via API de backup do SQLite e dois JSONs de eventos). Inclui `MANIFEST.json` com tamanho e SHA-256 por entrada e corte BRT.
- Criado sob `automatic.lock`, sem envio fiscal. Conferidos hash de cada entrada do pacote local, upload para nome temporário e promoção a nome definitivo, download integral de volta da pasta SMB, SHA-256 total **idêntico** e revalidação dos 514 hashes internos. O primeiro upload expirou após 8 MiB; a tentativa seguinte com timeout SMB de 180 s terminou corretamente; o parcial de 8 MiB foi removido. Temporários locais do empacotamento e download foram removidos após a verificação.
- ACL herdada inicialmente era insegura (`Everyone: FULL`). Corrigida **somente na nova subpasta** e nos dois arquivos internos: permissões exclusivas `CON\sergiol: FULL` e `CON\Domain Admins: FULL`, sem `Everyone` ou `Domain Users`. ACL conferida após a gravação; outros arquivos/pastas da DIFAL não foram alterados.
- **Nenhum XML/PDF fiscal local apagado nesta etapa.** Verificação após o arquivo: 384 arquivos em `archive/`, 81 em `inbox/`, 46 em `normalized/`; SQLite `PRAGMA quick_check = ok` e relatório `guide-status.txt` presente. O fluxo legado usa existência do PDF local para classificar conclusão (`_complete`); apagar agora sem adaptar esse teste e reconciliação produziria diagnóstico incorreto. O inbox é sincronizado automaticamente de SMB e seria repovoado. A cópia de rede é agora uma recuperação íntegra, não uma liberação já concluída de espaço local.

## Recuperação

Na pasta da rede, conferir `SHA256.txt` contra o pacote antes de extrair. `MANIFEST.json` contém a lista de arquivos originais e hashes; os caminhos dentro do pacote são relativos ao diretório `runtime/production/` e `metadata/` separa o snapshot do banco e os eventos. Restaurar o SQLite somente sob manutenção controlada, nunca sobre o banco ativo com WAL aberto. O arquivo de rede é um único ponto de armazenamento, não substitui política de backup e retenção fiscal aprovada.
