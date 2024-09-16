robots.txt -- arquivo que informa o navegador quais diretórios devem ser desabilitados, é interessante para ver possíveis diretórios sensíveis. 

## Listagem de diretorios
A frente do link colocar nomes de possiveis diretorios exmp: css, js, img
	businesscorp.com.br/css

## Mirror Website
Espelhar a pagina para facilitar a exploração da mesma.
	`wget -m businesscorp.com.br`  -- "-m" significa mirror baixa toda a estrutura do site.
	`wget -m  -e robots=off rh.businesscorp.com.br` -- Desabilita o wget de lever o arquivo "Robots.txt" e dessa forma consegue baixar todos os arquivos.

## Analise de erros, códigos e extensões
Fazer leitura de código e de anotações deixadas por programadores nos códigos e procurar por links e nomes de bibliotecas e APIS.
Verificar códigos de erros na pagina pois podem conter informações, exmp: businesscorp.com.br/kmmssmdcksm  -- Ao escrever qualquer coisa no URL do site ele ira retornar um erro e caso o servidor estiver mal configurado pode retornar informações dos servidor.

## Pesquisar via requisições HTTP
`nc -v businesscorp.com.br 80` 
`HEAD / HTTP/1.0`-- retorna informações do servidor

GET /index.php HTTP/1.0  -- solicita a pagina php que foi descoberta antes.

Descobrir os metodos que o site permite(GET,HEAD,POST e etc)--
	nc -v rh.businesscorp.com.br 80
	OPTIONS /qualquer HTTP/1.0
Dessa forma ira retornar as informações de métodos o "/qualquer" pode ser escrito qualquer coisa só para ver a resposta

Usando o protocolo HTTP/1.0 é possivel passar o host
	nc -v businesscorp.com.br 80
	HEAD / HTTP/1.0
	Host:businesscorp.com.br
Pode ser usado quando houver varios subdominios.

## Brute force - Arquivos e Diretórios

dirb http://businesscorp.com.br  -- Ferramenta com wordlist propria que faz um bruteforce de arquivo e diretorios em um site.

dirb http://businesscorp.com.br /usr/share/dirb/wordlists/small.txt -- dessa forma é possível acessar e escolher as wordlists disponibilizadas pelo dirb ou criar a própria. 

## Criar um script de bruteforce de site
Observando o retorno de paginas exmp: 200 OK, 404 NOT FOUND e etc
DEssa forma é possivel saber se uma pagina existe ou não
Pode usar o curl para verificar
	curl -s --head businesscorp.com.br/css | grep HTTP
curl -v -H "User-Agent: DesecTool" businesscorp.com.br  -- Forma de fazer uma requisição mudando o User Agent pois alguns servidores podem estar configurados com black-list então quando identifica o nome de um programa de varredura ou requisição faz o bloqueio.

Curl tem um modo de  code onde é possível solicitar somente a informação desejada passando uma variável:
	curl -s -o /dev/null -w "%{http_code}" businesscorp.com.br/qualquercoisa
	Faz a requisição e usa o -s e -o para fazer um retorno limpo somente do http_code.

Exemplo de script:
	![[Pasted image 20240916180729.png]]
		Onde o $2 é a extensão do arquivo para encontrar arquivos exemp: PHP, txt e etc.