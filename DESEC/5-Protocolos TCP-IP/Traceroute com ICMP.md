![[Pasted image 20240730153131.png]]
![[Pasted image 20240730153604.png]]
	O roteador envia um pacote ICMP para o cliente com type 11 e code 0 informando que o tempo de vida do pacote excedeu, dessa forma é possível descobrir o IP do roteador.
	Ao mandar um ICMP com TTL 3 ele ira passar por 3 roteadores e o terceiro roteador ira retornar um pacote informando que excedeu
	o TTL com a informação do IP do roteador e depois se enviar um pacotes ICMP com TTL 4 o quarto roteador ira retornar o pacote informando o IP e assim por diante, dessa forma é possivel fazer até chegar ao servidor final fazendo todo o traceroute.
		Exemplo:
			ping -c -t 1 www.google.com  -- ira retornar um pacote "time to live exceeded" enviado pelo primeiro roteador.
			ping -c -t 2 www.google.com -- mensagem enviada pelo segundo roteador e assim por diante.