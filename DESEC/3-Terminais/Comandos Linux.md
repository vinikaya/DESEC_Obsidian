	add user  -adicionar usuarios
	/etc/passwd  -pasta onde ficam armazenados os usuarios
	passwd user  - Resetar senha do usuario
	locate acess.log  -Localiza arquivos, antes usar o "updatedb"
	find /root -name acess.log  - procura arquivos em pastas especificas, pode especificar a pasta /.
	whereis nmap - mostra os arquivos do programa
	grep  -para filtrar comandos de busca.
	cat /etc/passwd | grep "/bin/bash"  -só retorna as linhas que tenham o "/bin/bash"
	egrep  -usar o comando grep sem escrever tanto.
	egrap -v "root|desec" /etc/passwd  - traz somente linhas com root ou desec.
	awk  -imprimi o arquivo separado por algum item padrão.
	cut  - igual awk só q mais simples.
	cut -d : -f1,6 temshell  -mostra os itens 2 e 6 de todas as linhas separados por :
	sed  -altera linhas com erros.ç