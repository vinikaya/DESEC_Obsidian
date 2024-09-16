## BGP

https://bgpview.io/
https://bgp.he.net/
pode ser pesquisado por IP, domínio ou nome da empresa.

Caso a empresa alvo tenha um ANS é possível mapear e ver todos os netblocks por esses sites.


## Pesquisa pelo SHODAN

![[Pasted image 20240909171017.png]]
Shodan faz uma busca por IPS públicos e portas abertas, é possível fazer vários tipos de pesquisas, como por bloco de ip ou por um ip especifico ou pelo nome de uma empresa ou por serviço por localização e etc.


API SHODAN
	-NO site possui a sua shodan key, copiando ela é possível usar o shodan no terminal
	-shodan init key
	-shodan host 37.59.174.225 -- fazendo buscas.

## Censys
Parecido com shodan faz pesquisas por filtro
Exemplo:
![[Pasted image 20240909180017.png]]

## Pesquisa Domain Name System

![[Pasted image 20240909180228.png]]
	$ host -t A businesscorp.com.br  -- retorna o IPV4
	$ hosrt -t mx businesscorp.com.br  -- servidor de email


## Entendendo transferência de zona
Sempre que for buscar o name server de um endereço ip ou domínio ira retornar no minimo dois endereços de dns.
![[Pasted image 20240912152939.png]]
	O endereço secundário serve como backup e todos os endereços de dns devem estar sincronizados para manter o funcionamento dos dois.
	
A **transferência de zona DNS** (ou **DNS Zone Transfer**) é um processo no qual uma cópia de uma zona DNS (um conjunto de registros de DNS de um domínio) é replicada de um servidor DNS principal (mestre) para um ou mais servidores DNS secundários. Esse processo garante que os servidores DNS secundários tenham as informações atualizadas sobre os registros DNS de um domínio, permitindo redundância e maior disponibilidade.
É possivel fazer uma solicitação direto para um dominio e um endereço de dns para tentar puxar os dados dns, logicamente se o servidor estiver bem configurado não resultara em nada, porem em alguns casos pode retornar os dados do dns.
	host -l -a businesscorp.com.br ns1.businesscorp.com.br
	Dessa forma faz um solicitação para esse dns desse dominio e pode ser testados com todos os endereços de dns do dominio e caso existam muitos pode ser feito um script.

## Script para pesquisa direta(DNS)
É possível criar um bruteforce para descobrir os endereços de domínio de uma empresa pois existe um padrão quando pesquisamos por um endereço que não existe, logo podemos criar um script que faça centenas ou milhares de tentativas e excluir as respostas erradas.
	1- Deve criar uma lista com palavras que podem ser o nome de subdominios de uma site, exemplo: rh (rh.businesscorp.com.br).
	2- Criar um scrip que leia esse arquivo de texto e faça varias pesquisas usando o comando "host" e exclua as linhas com erro, dessa forma somente imprimindo os resultados positivos.
		`for p in $(cat list1.txt); do`
		`host $p.$1 | grep -v "(NXDOMAIN)"; done`


## Pesquisa reversa(DNS)
Pegar o rande de IP proprietario da empresa fazendo pesquisas usando o whois e crindo um script que faza uma pesquisa "host" com cada endereço de ip nesse range.

## SPF - Sender Policy Framework
![[Pasted image 20240912173957.png]]
 É possível verificar a configuração do servidor dns de texto com:
	 host -t txt businesscorp.com.br   -Ira retornar a configuração de texto e caso seja suscetível conforme imagem a cima então é passível de golpe.

Com a configuração suscetível e possível mandar emails com remetente desse domínio sendo fácil de falsificar emails de uma empresa caso esteja vulnerável. 

## Entendendo Subdomain Takeover

Quando você consegue pegar controle de um subdomínio de uma empresa, é uma falha gravíssima pois com o controle do subdomínio é possível criar fraudes com os clientes e até com os próprios funcionários da empresa.
![[Pasted image 20240912175646.png]]
	O subdomínio dev.businesscorp.com.br redireciona para o link susinesscorp.s3.amazon.com porem o mesmo foi desativado pela empresa, e caso um criminoso ciente dessa situação faça o registro do domínio na Amazon ele terá o controle do subdomínio da empresa.
	CNAME= um nome alias de um link.
	
![[Pasted image 20240912175820.png]]
	Porem nem todo serviço é passível de registrar um subdomínio desativado exemplo:wordpress.

Script para descobrir endereços CNAME redirecionados para saber se estão disponíveis para takeover.
	`#!/bin/bash`
		`for p in $(cat list1.txt); do`
		`host -t cname $p.$1 | grep "alias for"; done`
		
Quando retornar os endereços CNAME e um desses endereços estiver indisponível para acessar significa que é uma possibilidade de takeover, se for o endereço do wordpress pode ser tentado registrar esse domínio no próprio wordpress, caso consiga então você tem um subdominante takeover, podendo criar uma pagina web falsa e direcionando clientes ou funcionários sem levantar suspeitas por usar um domínio "valido" da empresa.

## Tomando controle de um subdominante

![[Pasted image 20240912182220.png]]
	Entrando na pagina da aws e criando um bucket com o domínio desativado e fazendo um upload de uma pagina web.


## Outra ferramenta de DNS

dig -- ferramenta que automatiza a busca por domínios e dns
	dig -t ns businesscorp.com.br +short
		Retorna uma resposta grande, usando o +short diminui

dnsenum -- ferramenta de pentets
	dnsenum --enum businesscorp.com.br
		Faz conhecimento do host e varias ações e também tentativa de transferência de zoa, e pode ser passado um arquivo para fazer bruteforce de domínios

dnsrecon -d businesscorp.com.br
	traz nameservers e varias outras infos

fierce
	Faz varias ações alem de transferência de zona e bruteforce

## Serviços online para coleta passiva
virustotal -- para verificar se um arquivo é ou possui vírus. Verifica se algum site foi violado
dnsdumpster -- faz enumeração, leitura de domínio e serviços, trás muitos detalhes.
securitytrails  -- trás informações de domínio e subdomínios.


## Coleta através de certificados digitais
Todo site que possui um certificado digital(cadeado) mostra que possui uma conexão segura, mas para possuir um certificado digital ele deve ser registrado e por questão de segurança existe um registro publico de certificados digitais.
Fazendo uma busca por um domínio no registro do certificado digital ele ira mostrar todos os subdomínios e/ou domínios expirados. Outra forma de achar subdomínios.
https://crt.sh/  -- Site que verifica certificado digital.
