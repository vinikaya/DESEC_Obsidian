## Condições
(exemplo de como um script deve ser escrito).
	`#! /bin/bash`
	`echo "Qual a cor do semaforo?"`
	`read  cor`
	`if [ "$cor" == "verde" ]`
	`then`
        `echo "siga em frente"`
	`else`
        `echo "Pare!!"`
	`fi`

![[Pasted image 20240807160533.png]]
	if [ "$idade" == "18" ]  -- o sinal "=" é uma condição de igual e pode ser usada qualquer uma mostrada acima no lugar
	then
		echo "Pode dirigir"
	else
		echo "não pode"

	if [ "$idade" -gt "18"]  ---gt greater than(maior que) = ">"
	then
		echo "Pode dirigir"

![[Pasted image 20240807161115.png]]
	Condição de caso no bash script

## Argumentos 
Os argumentos são passados no terminal na frente do script e são gravados seguindo a ordem.
	exp:
		 :~/ ./script.sh vinicius joao   -- ao executar esse script no terminal foi passado dois argumentos o "$1"=vinicius e o "$2=joao.

Exemplo de script:
	`#! /bin/bash`
	`if [ "$1" == "" ]`
	`then`
	        `echo "DESEC"`
	        `echo "Modo de uso: $0 192.168.0.20 80"`
	`else`
	        `echo "varrendo host: $1 e porta: $2"`
	`fi`
	-- Nesse script ele caso seja executado sem nenhum argumento ele ira imprimir o modo de uso.
	Ao passar o argumento 1 e 2 ele ira imprimir na ultima frase.

## Repetições

Comando "echo" consegue imprimir sequencias:
	echo {1..10}  -- ira imprimir de 1 a 10.
	echo {a..z}  --ira imprimir da letra a aletra z(alfabeto completo e em ordem)
	echo {1000..2000}  -- ira imprimir os numeros de 1000 a 2000.
Comando "seq":
	seq 1 10  -- ira imprimir de 1 a 10 na vertical.

Comando "for";
	for ip in {1..10};do echo 192.168.0.$ip;done  -- ira criar uma lista de 1 a 10 e imprimir na variavel "ip", gerando uma lista de endereços IPs.
	Exemplo de uso:
		`#! /bin/bash`
		`for ip in $(seq 1 10);`
		`do`
		`echo 172.16.0.$ip;`
		`done`

Comando "while":
wilhe true;do echo "pronto";done  --habilitar um script para ficar escultando algo no host.

# Criando um Script
`#! /bin/bash`
`if [ "$1" == "" ]`
`then`
        `echo "DESEC - PingNet"`
        `echo " Modo de uso : $0 REDE(192.168.0)"`
`else`
`for host in {1..245};`
`do`
`ping -c1 $1.$host | grep "64 bytes" | cut -d " " -f 4 | sed  's/.$//';`
`done`
`fi`

-- Nesse Script ele ira pegar o endereço de rede informado e ira gerar pings de rede em Hosts com final 1 a 255 e ira retornar os endereços que foram pingados, após o "| grep" todo o comando foi feito para limpar o resultado da varredura para mostrar somente os endereços IPs.

## Script PortScan de Rede
hping3 - ultilitario q serve para enviar pacotes para um host e receber uma resposta, usando o protocolo e para a porta q quisermos.
	hping3 -S -p 80 -c 192.168.0.1 2> /dev/null   -- no final o "2>" redireciona o log de erro para o "/dev/null"(Lixo) e imprimi na tela somente o resultado, é uma forma de limpar a saida do comando.

Exemplo:                       
	`#! /bin/bash`
	`if [ "$1" == "" ]`
	`then`
	        `echo "Desec - PortScann"`
	        `echo "Modo de uso: $0 REDE PORTA"`
	`else`
	`for ip in {seq 1..255};`
	`do`
	`hping3 -S -p $2 -c 1 $1.$ip 2> /dev/null | grep "flags=SA" | cu>`
	`done`
	`fi`
	--(pode conter erros) Esse script usa a ferramenta hping3 que permite pingar uma porta especifica de um determinado host, é uma forma silenciosa de varrer a rede pois pinga somente na porta especificada.
	