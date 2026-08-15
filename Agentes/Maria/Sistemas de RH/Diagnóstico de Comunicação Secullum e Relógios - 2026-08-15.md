# Diagnóstico de comunicação local — Secullum e relógios — 15/08/2026

> **Confidencial — infraestrutura interna.** Testes exclusivamente de leitura; nenhuma configuração foi alterada.

## Escopo

- Servidor do agente Secullum: `172.169.0.100`.
- Relógio ACL e entrada duplicada PRISMA: `172.169.3.121`.
- Relógio CONAMORE: `172.169.0.156`.
- Relógio GCL: `172.169.4.101`.
- Relógio FILIAL: `172.169.6.106`.

A imagem do Agente de Comunicação mostrava todos os equipamentos como **Conectado** e o Serviço de Comunicação como **Em execução** no momento da captura.

## Servidor 172.169.0.100

- Acessível por ICMP via VPN, aproximadamente 183 ms.
- Portas TCP identificadas: 7, 9, 13, 17, 19, 80, 135, 139, 445, 1433, 3389, 4040 e 7070.
- Porta 80: Microsoft IIS 10.0; raiz retorna HTTP 500 genérico.
- Porta 1433: Microsoft SQL Server 2012 identificado, sem tentativa de autenticação.
- Porta 4040: serviço HTTP Kestrel ativo; raiz e rotas públicas usuais testadas retornaram 404. Não foi possível atribuí-lo conclusivamente ao Secullum sem credenciais ou documentação local.
- Porta 5985: Windows Remote Management (WinRM/WS-Man) ativo, aceitando autenticação `Negotiate`; sem autenticação retorna HTTP 401.
- Porta 7070: serviço AnyDesk, confirmado pelo certificado TLS; exige certificado de cliente.
- Não há proxy HTTP/SOCKS exposto nas portas usuais 1080, 3128, 8080 ou 8888. IIS e Kestrel não encaminharam as requisições aos relógios.
- SMB/RPC/RDP estão acessíveis, mas não houve tentativa de login ou leitura autenticada.

**Conclusão:** o servidor está acessível e executa a pilha compatível com um agente local Windows (IIS, SQL Server e serviço Kestrel), porém a rede não expõe uma rota pública identificável do Agente Secullum que permita consultar seu estado interno sem autenticação.

## Relógio CONAMORE — 172.169.0.156

- Sem resposta ICMP, mas acessível por TCP via VPN.
- Porta 80 aberta: servidor `REP`, página `R WebServer`, formulário de login.
- Porta 3000 aberta: protocolo binário do equipamento.
- Nenhuma autenticação foi tentada e nenhum comando foi enviado ao protocolo do relógio.

**Conclusão:** a comunicação TCP direta com esse REP está funcionando.

## ACL, GCL e FILIAL

- `172.169.3.121`, `172.169.4.101` e `172.169.6.106` não responderam a ICMP nem às portas 80/3000 a partir do servidor Hermes.
- A VPN possui somente a rota `172.169.0.0/24` via `tun0`.
- Atenção: `172.169.0.0/16` não pertence à faixa privada RFC1918 (`172.16.0.0/12`); sem rota específica, o tráfego pode seguir a rota padrão. A TI deve revisar esse endereçamento e garantir que essas redes sejam alcançadas exclusivamente pelo túnel apropriado.
- As redes `172.169.3.0/24`, `172.169.4.0/24` e `172.169.6.0/24` estão seguindo a rota padrão, fora do túnel; portanto o resultado é **inconclusivo sobre os relógios** e conclusivo sobre a falta de alcance pela VPN atual.
- A imagem mostra ACL e PRISMA cadastrados com o mesmo IP `172.169.3.121`; confirmar se são dois nomes para o mesmo relógio ou duplicidade cadastral.

## Encaminhamento técnico

Solicitar ao Matias/TI que valide, sem alterar os relógios:

1. inclusão das rotas VPN `172.169.3.0/24`, `172.169.4.0/24` e `172.169.6.0/24` para o cliente Hermes;
2. se ACL e PRISMA representam o mesmo equipamento;
3. qual porta/rota local pertence oficialmente ao Agente de Comunicação Secullum no servidor `172.169.0.100`;
4. se as portas legadas 7, 9, 13, 17 e 19 precisam permanecer expostas.
