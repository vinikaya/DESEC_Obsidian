## LAB01
Usado filtro no wireshark
	ip.src == 172.16.1.3 && tcp.flags.syn == 1
	Resposta: 33024,33054,43001,44289,49222


## LAB02
Ao rodar o script banner grab feito em pyton nas portas encontradas anteriormente foi retornamos um socket
	172.16.1.55:44905
	Ao conectar

## LAB03
O socket encontrado foi:
	172.16.1.55:44905
## LAB04
Traduzindo os bits de rede cheguei na resposta ICMP
## LAB08
Após interpretar o payload do bits de rede, eu cheguei no nome de um arquivo, e então peguei o endereço ip de destino que vi nos bits de rede e coloquei /malware.txt que é o nome do arquivo, logo cheguei na resposta final.
