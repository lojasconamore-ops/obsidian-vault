# Banco de Dados e Oracle

## Missão do Matias aqui

Oracle é o coração técnico de muitas operações da Conamore. O Matias precisa dominar administração, performance, backup, recuperação e segurança do banco.

## O que ele precisa saber muito bem

### Administração Oracle
- Estrutura de instâncias, bancos, schemas e usuários
- Tablespaces, datafiles, redo logs e control files
- Gestão de permissões, roles e privilégios mínimos
- Criação e manutenção de objetos: tabelas, views, índices, sequences, procedures, packages e triggers
- Leitura de `ORA-` errors e triagem rápida de incidentes

### Performance e estabilidade
- Identificar consultas lentas e gargalos de I/O
- Avaliar índices, estatísticas e planos de execução
- Observar sessões bloqueadas, contenções e deadlocks
- Monitorar crescimento de tabelas, segmentos e tablespaces
- Evitar alteração sem medir impacto

### Backup e recuperação
- Backup consistente e com rotina testada
- Restore e point-in-time recovery quando necessário
- Estratégia de retenção e validação periódica
- Separação entre backup de banco, backup de arquivos e backup de aplicação

### Segurança
- Privilégios por menor acesso possível
- Auditoria de acessos e alterações críticas
- Proteção de credenciais e conexões
- Separação entre ambiente de produção, homologação e testes

## Rotina prática

1. Verificar saúde geral do banco
2. Checar jobs falhos e alertas
3. Conferir crescimento de espaço
4. Revisar consultas problemáticas e bloqueios
5. Validar backup e janela de manutenção
6. Registrar qualquer incidente ou correção no Obsidian

## Janela operacional do DEBX

- O Oracle DEBX fica disponível diariamente das **08:00 às 18:00 (BRT)**.
- Fora dessa janela, o ambiente pode estar em manutenção ou encerramento de sessão.

## Regra de ouro

Se o banco estiver degradando, a empresa inteira sente. Oracle não é só banco — é operação.

## Referência prática

- [[Projetos/Lojas Conamore/Oracle e DEBX - Treinamento de Agentes]] — guia compartilhado único para conectar no Oracle do DEBX e executar consultas seguras.
