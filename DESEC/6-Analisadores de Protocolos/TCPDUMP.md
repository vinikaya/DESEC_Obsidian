Analisador de protocolos em linha de comando.

Comando: 
	- tcpdump -v -i eth0  -- faz a captura da interface de rede 'eth0', 
		- -v = modo verbose(mostrar detalhes);
		- -i = indica interface de rede;
	- tcpdump -v -i eth0 -w nome.pcap  -- 
		- -w indica que ira salvar a captura em um arquivo com nome indicado a frente;
	- tcpdump -venr nome.pcap  -- 
		- -r indica a leitura de um arquivo de captura indicado na frente. 
		- -n troca o nome do servidor pelo endereço IP(para ver o nome é só tirar o "n").
		- -v entra no modo verbose mostrando mais detalhes dos pacotes como o protocolo e etc.
		- -e traz detalhes sobre o protocolo Ethernet
	- 
	
	
	