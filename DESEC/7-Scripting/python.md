PortScan em python
	![[Pasted image 20240816171344.png]]
		-Modulo Socket é usado para criar conexões de rede e trabalhar com sockets
		-Modulo sys permite acessar argumentos passados na linha de comando
		-Um novo socket é criado. `socket.AF_INET` indica que o endereço da família é IPv4, e `socket.SOCK_STREAM` indica que é um socket de fluxo, usado para conexões TCP.
		-"meusocket.connect_ex(())..." tenta se conectar à porta especificada em um endereço IP (ou hostname) que é passado como argumento na linha de comando (`sys.argv[1]`).
		-A função `connect_ex()` retorna 0 se a conexão for bem-sucedida, o que significa que a porta está aberta.
		-"socket.close()" O socket é fechado após cada tentativa de conexão para liberar recursos.