Responsável por entrega de pacote entre maquinas.
Não é confiável por somente entregar os pacotes sem realizar verificações.
Para confiabilidade associa o Protocolo IP ao Protocolo TCP.
Para velocidade Protocolo IP ao Protocolo UDP
	IP + TCP = Confiabilidade
	IP + UDP = Velocidade

![[Pasted image 20240719161437.png]]
![[Pasted image 20240719161622.png]]
	Versão: 4 (ipv4)
	IHL: tamanho do Protocolo.
	DSF(type of service): qualidade de serviço(não muito ultilizado).
	Total length: tamanho total do pacote (64bytes é um pacote pequeno, pacotes grandes devem ser fraguimentados).
	Indentification: funciona quando fraguimenta um pacote(por ser grande), indentifica cada parte do pacote.
	Flags: algumas infos sobre o pacote.
	Time to live(TTL): cada sistema operaciona define um valor padrão (linux = 64), Pode ser alterado.
	Protocolo: 6(codigo TCP).
	 Source: IP de origem.
	 Destination: endereço IP de destino.


FRAGMENTAÇÃO PACOTE IP
	Um fragmento ethernet aceita por padrão somente 1500 bytes, se o pacote IP tiver mais de 1500 bytes ele devera ser dividido em diversos pedaços, oque é chamado de fragmentação de pacotes.

![[Pasted image 20240719172913.png]]
		Identitification: gera um numero aletorio que será a identificação dos pacotes fraguimentados, todos os fraguimentos do mesmo pacotes terão o mesmo numero.
		Flags: tem infos da fraguimentação, exemplo MF(more flags) indica que tem mais fragmentos.
			Flag - Fragment offset: mostra a ordem do pacote, 0(zero) é o primeiro pacote o segundo é 185 pois será incrementado ao seguir os pacotes. terceiro pacote é 378. Ordem crescente.
		
		
		
		