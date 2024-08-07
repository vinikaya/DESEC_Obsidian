Um script que faça a leitura de uma pagina da Web e encontre possíveis hosts no domínio.

wget businesscorp.com.br

grep href index.html | cut -d "/" -f 3 | grep "/." | cut -d '"' -f 1 | grep -v "<li>" > lista 

host www.businesscorp.com.br   -- retorna o endereço ip
