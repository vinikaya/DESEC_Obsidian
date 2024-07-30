Hypertext Transfer Protocol

Funciona através de trocas de requisições entre cliente e servidor.

![[Pasted image 20240730145905.png]]
![[Pasted image 20240730150027.png]]
	Toda requisição recebe um codigo de resposta conhecido como status
		200 ok
		301 Moved Permanetly
		403 Forbidden
		404 Not Found
		500 Internal Server Erro

HTTP Request:
	![[Pasted image 20240730150310.png]]
	Request Method: Metodo GET
		Request URI: endereço solicitado / normalmente é a pagina inicial.
		Request Version: versão da requisição.
	Host: Indica o host a ser comunicado(as vezes um mesmo server pode ter mais de um host)
	User-Agent: Informação do cliente, navegador e sistema OP.
	Accept: Oque ele espera receber de resposta.
	

HTTP Response:
	![[Pasted image 20240730150754.png]]
	Response version:
	Status code: 200 ok, significa que a requisição foi respondida corretamente.
	Date:
	Server: Detalhes do servidor, Depende de como o servidor foi configurado, caso bem configurado mostra menos informação ou nenhuma.
	Line-based text data(ultima linha): é o codigo html da pagina solicitada.
	