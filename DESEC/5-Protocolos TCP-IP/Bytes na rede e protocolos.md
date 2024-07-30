Cada byte é formado por dois numeros.
Em hexadecimal e deve ser traduzido.

![[Pasted image 20240730155552.png]]
![[Pasted image 20240730164904.png]]
	O protocolo Ethernet está carregando o IP em seu payload e o IP carregando o TCP em seu Payload e assim por diante.


Protocolo Ethernet
![[Pasted image 20240730155706.png]]
	Ferramentas de rede como Wireshark captura esse bytes na rede e interpreta oque significa cada byte para melhor entendimento do visualizador.
	O Mac de destino é o Mac do Roteador(gateway) por se tratar de uma requisição para um site externo.

![[Pasted image 20240730155923.png]]

# Bytes na rede - Protocolo IP
Bytes do IP está començando no penúltimo byte da primeira linha.
Cada linha da estrutura abaixo posui 4 bytes(cada byte são 2 numeros ou letras), logo a primeira linha se entende por:
	version: metade de um byte( 1 numero ou 1 letra);
	IHL: meio byte;
	Versio e IHL juntos formam 1 byte;
	Type of Service: 1 byte;
	Total lenght: 2 bytes;
	Total: 4 bytes(uma linha).
	
![[Pasted image 20240730160235.png]]
	Version: versão 4 informado por meio byte(em laranja "45");
	IHL: tamanho do Header IP informado por meio byte(azul "45") 5, cada linha do header IP tem 4 bytes logo são 5x4 igual a 20 bytes o tamanho do header. Até a linha 3 e segundo byte está o header com informações mais detalhadas do pacote(TTL, TOS Flags e etc);
	ToS(type of service): 00 pois n tem informação;
	Total lenght: tamanho total do pacote informado por dois bytes: "01 81"(hexadecimal, deve ser traduzido).
	
![[Pasted image 20240730161112.png]]

# Bytes na Rede - Protocolo TCP

Cada linha 4 bytes.
![[Pasted image 20240730163829.png]]
	Bytes TCP começa em verde;
	Source port: dd 84;
	Destination Port: 00 50;
	Os 4 proximos Bytes são referentes ao 
	Sequence Number;
	Data offset: informa o tamanho total do header desde o inicio.
		![[Pasted image 20240730165326.png]]
		Data offset: 8 linhas de 4 bytes = 32 bytes desde o primeiro byte "dd"(verde) acabando no "94"(segundo byte ultima linha).
		
	![[Pasted image 20240730165842.png]]

# Bytes na Rede - Payload

![[Pasted image 20240730172856.png]]
![[Pasted image 20240730173057.png]]
	Esse payload é uma requisição HTTP;
	Os bytes em vermelho significam: "GET / HTTP/1.1" 
	
![[Pasted image 20240730173219.png]]
