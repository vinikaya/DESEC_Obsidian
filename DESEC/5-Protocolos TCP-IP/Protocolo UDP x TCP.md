User Datagram Protocol - UDP
UDP assim como o TCP é um protocolo de transporte de dados.
UDP não é seguro e não é orientado a conexão.
UDP é um protocolo muito mais rápido porem menos seguro. 
![[Pasted image 20240729164204.png]]
![[Pasted image 20240729164340.png]]
	Source Port: porta de origem
	Destination Port: porta de destino.
	Length: tamanho completo dele.
	Checksun: 
	Gera 1 pacote com payload de 28 bytes com uma mensagem. SIMPLES E RAPIDO

![[Pasted image 20240729164822.png]]
	Pacote TCP enviou 9 pacotes para enviar a mesma mensagem, sendo estabelecer conexão 3WHS e mandando o pacote e confirmando o recebimento do pacote para ter certeza que foi entregue e depois finalizando a conexão com confirmação do servidor.
	 Gera 9 pacotes para enviar o mesmo dado enviado com UDP acima. SEGURO E GARANTIDO.