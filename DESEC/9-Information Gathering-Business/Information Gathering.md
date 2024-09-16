
## Mapeando Informações

![[Pasted image 20240902144500.png]]


## Vagas de emprego
![[Pasted image 20240902145402.png]]
	Olhando as vagas de emprego oferecidas pela empresa é possivel descobrir programas usados pela empresa, possibilitando fazer um ataque de engenharia social.
	É possivel descobrir informações muito importantes, como serviços usados e até o firewall e ainda mais a versão dos softwares.

## Coletando endereços de E-mail

https://hunter.io/
Com o site hunter.io é possível encontrar emails de empresas, encontrar pessoas, validar emails, descobrir o padrão de emails de uma empresa e etc. 

## Vazamento de dados(Leaks)
![[Pasted image 20240902150549.png]]

Sites para fazer pesquisas de vazamentos

have i been pwned
	Verifica se teve vazamento de dados de emails, pelo banco de dados do site, pode ser que esse site não mostre vazamento porem outro site mostre.


## Consulta de Leaks na dark web

https://dehashed.com/   - Site para ver informações de contas vazadas porem pagando(não muito recomendando e necessário).

pwndb2am4tzkvoid.onion - Site da deep web para checar leaks, pode não estar mais disponivel ou mudado de link, procurar em foruns mais sites parecidos.

Instalando tor no kali linux e configurando.
	apt install tor proxychains

configurar proxychain
	nano /etc/proxychains.conf
	Setas dynamic_chain e tirar o static_chain
	Adicionar linha
		socks5 127.0.0.1 9050
Configurar o navegador para rodar o proxy no socks5 e habilitar para dns socks5


## Script para consulta de Leaks
[https://github.com/limkokhole/karma](https://github.com/limkokhole/karma)
	Scrip que automatiza consulta de leaks na deep web, na pagina do github é explicado com instalar e como ultizar.


## Coleta de dados no Pastebin
Site para trocar de informação de forma rapida, uma outra forma de procurar leaks.
- Forma de pesquisar sem entrar no site
	site:pastebin.com "businesscorp.com" - pesquisar no proprio google
	

Na conta free pode criar alertas para caso aparece algo de um dominio, uma forma de monitorar um dominio


## Coleta de dados no trello
Existe uma falha quando algumas pessoas deixam os projetos publicos por falta de atenção, logo é possivel acessar fazendo buscas pelo google.
	usando a linha no google:
		site:trello.com "businescorp.com.br"
		site:trello.com ".com.br" backup
		site:trello.com "senhas"
!!!!! TRELLO NÃO INDEXA MAIS PROJETOS NO GOOGLE
disponiveis
## Buscando domínios similares
O atacante pode registrar um dominio similiar para direcionar um ataque a uma empresa ou cliente,
	Exmp: businesscorp, businescorp, busnesscorp.

urlcrazy - é uma ferramenta que monta domínios similares e verifica se cada dominio já foi registrado, bom para verificar fraudes e criar domínios para ataques. 

## Pesquisa cache de sites
web.archive.org  - Site que mapeia os caches, serve para ver versões passadas dos sites.

Analisar versões passadas do site do alvo, é possível ver informações que não estão mais disponíveis, usando o robots.txt é possivel ver arquivos q era aparentes e não são mais, as vezes esses arquivos ainda existem.

## NDN - Non-Delivery Notification

Técnica de coleta de informações utilizando email.

Enviar um email inexistente para o alvo, caso o servidor de email do alvo possua o NDN, ira retornar um email com informações.

## Thehavister
Ferramenta que faz pesquisa geral, em dominios, ips, portas, emails e etc.

## Metadados

![[Pasted image 20240905171609.png]]

Ferramenta "exiftool"  -- lê os metadados de arquivos, exemplo: ver informações da criação de um pdf como o programa usado pra criar e até a versão do sistema operacional usado.


