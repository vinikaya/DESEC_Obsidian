Transmission Control Protocol

Protocolo confiável para transmissão de dados, pois garante a entrega dos dados.
Orientado a transmissão, só transmite se a conexão for estabelecida.(Three-way Handshake)
Segmento TCP se comunica com Portas.

![[Pasted image 20240729160059.png]]
![[Pasted image 20240729160126.png]]
Source Port: porta de origem do cliente.(porta aleatoria, numero alto)
Destination Port: porta do servidor.
Sequence number: indentifica o seguimento TCP.
Acknowledgment number: numero da proxima sequencia de dados, importante pois garante oque está sendo enviado.
Data offset: tamanho do header.
Flags: informações sobre o protocolo.
Windows size: tamanho maximo do proximo seguimento.
Checksun: faz uma verificação completa da estrutura do protocolo.
Urgent Pointer: define uma prioridade ao conteudo.
Option:
Padding:

	Flags:
		SYN: indica sincronizar(conexão entre os lados envolvidos)
		FIN: indica finalizar(conexão deve ser fechada)
		RST: indica resetar(comunicação n entendida ou erro)
		PSH: indica que possui dados no payload TCP
		ACK: faz a confirmação indicando que sabe o proximo numero de sequencia.
		URG: indica urgencia(conteudo deve ser priorizado)


3WHS - Three-way Handshake
	TCP é orientado a conexão logo só transmite se garantir que uma conexão foi estabelecida com sucesso.
	O estabelecimento dessa conexão inicial se chama Three-way Handshake.
	![[Pasted image 20240729161606.png]]
	Tem esse nome devido as 3 interações com o servidor e o host para estabelecer a conexão, após estabelecer a conexão 3WHS começa a transmissão de dados com o protocolo TCP carregando outros protocolos em seu payload.
	As 3 primeiras interações(3WHS) não possui payload pois é somente para garantir a conexão entre o cliente e o servidor.


Encerrando conexão TCP
	Quando o host deseja encerrar conexão veremos a flag FIN.
	![[Pasted image 20240729162318.png]]
	Nesse pacote é setado as Flags FIN e ACK, pois indica que deseja finalizar a conexão e ACK confirmando.
	Após a maquina cliente manda um pacote com a Flag ACK confirmando e encerrando a conexão. 


Problema na conexão
	Quando não estabelece conexão veremos a Flag RST.
	![[Pasted image 20240729162744.png]]
	O cliente manda um pacote TCP com a Flag SYN tentando estabelecer uma conexão(dois pacotes acima no print ao final da linha mostra as Flags SYN e RST, ACK)
	Nesse caso o servidor não está com a porta 80 aberta.