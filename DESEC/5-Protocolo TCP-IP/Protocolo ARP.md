ARP tem a habilidade de descobrir qual MAC está associado a um endereço IP especifico.
Ultiliza o ARP Request e ARP Reply
	ARP Request: pergunta para a rede toda (Broadcast) quem tem determinado IP a resposta é o ARP Reply.
	ARP Reply: é a resposta enviada pelo host que tem o IP requisitado com seu endereço MAC.
	O host que recebe a resposta armazena o IP e o MAC por um tempo.
	Só funciona na rede local, quem faz o broadcast é o gateway(roteador).
	Ao olhar a requisição ARP feita para um servidor da internet sempre ira retornar o MAC do roteador(gateway) pois ele faz o roteamento dos pacotes com a internet.


ESTRUTURA ARP
![[Pasted image 20240719155239.png]]

![[Pasted image 20240719155721.png]]
Existe essa divisão do endereço MAC na terceira linha de azul pra quarta pois o ARP tem 4 bytes de largura, o mesmo para as linhas de amarelo com IP e a linha roxa com o MAC. cada linha tem no máximo 4 bytes.

![[Pasted image 20240719160425.png]]
	Opcode informa se é um ARP Request ou ARP Reply, 1 = request e 2 = Reply.
	Target MAC address está com zeros 00:00:00... pois é o servidor a ser descoberto
	Target IP address é o IP do alvo que respondera com seu MAC address
	
![[Pasted image 20240719160750.png]]
	ARP Reply com o Target MAC Adress preenchido com o MAC servidor.