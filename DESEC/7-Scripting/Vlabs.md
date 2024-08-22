## Scripting like a pro

> [!NOTE]
> 	Execute seu script na rede 172.16.1.0/24 (este vlab precisa de VPN, ative sua VPN e conecte para ter acesso a essa rede)  
> 	  
> 	Qual o endereço IP do host infectado na rede?

Para resolver primeiro fiz uma varredura na rede 172.16.1 para saber quais são os hosts da rede usando o script "pingnet.sh" que retorna os endereços pings que recebem pacotes ou seja mostram sinal de vida.
	![[Pasted image 20240819172925.png]]
Após juntei os endereços Ips e criei outro script para fazer o portknock em todos os endereços com a sequencia de portas estabelecida anteriormente em outro desafio. E deixei o wireshark capturando os dados da rede.
	![[Pasted image 20240819173222.png]]
Após o wireshark capturar todos os dados, criei um filtro para mostrar somente os pacotes TCP com Flags = SYN, e observei qual pacote com a rede de origem do alvo enviou esse pacote.
```
tcp.flags.syn == 1
```

Percebi que o pacote de origem Ip 172.16.1.55 e porta 1337 enviou um pacote com flag SYN ou seja a porta estava aberta.
Após rode o comando nmap para verificar se a porta estava aberta e retornar informações dessa porta como o serviço.
```
nmap -p 1337 -sV 172.16.1.55 -Pn
```
	Este comando retorna o servisso rodando nessa porta

		![[Pasted image 20240819173941.png]]
Percebi que é um servidor Web http apache, então rodei o comando Wget no Ip e porta e foi feito o download do html da pagina rodando nesse servidor.
```
	wget http://172.16.1.55:1337
```
![[Pasted image 20240819174213.png]]
