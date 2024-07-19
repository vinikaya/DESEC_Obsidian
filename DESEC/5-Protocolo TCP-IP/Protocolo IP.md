Responsável por entrega de pacote entre maquinas.
Não é confiável por somente entregar os pacotes sem realizar verificações.
Para confiabilidade associa o Protocolo IP ao Protocolo TCP.
Para velocidade Protocolo IP ao Protocolo UDP
	IP + TCP = Confiabilidade
	IP + UDP = Velocidade

![[Pasted image 20240719161437.png]]
![[Pasted image 20240719161622.png]]
	Versão: 4 (ipv4)
	IHL: tamanho do Protocolo
	DSF(type of service): qualidade de serviço(não muito ultilizado)
	Total length: tamanho total do pacote (64bytes é um pacote pequeno, pacotes grandes devem ser fraguimentados).
	Indentification: funciona quando fraguimenta um pacote(por ser grande), indentifica cada parte do pacote.
	Flags: algumas infos sobre o pacote.
	Time to live(TTL): cada sistema operaciona define um valor padrão (linux = 64), Pode ser alterado.
	Protocolo: 6(codigo TCP)
	 Source: IP de origem
	 Destination: endereço IP de destino.
	 
	