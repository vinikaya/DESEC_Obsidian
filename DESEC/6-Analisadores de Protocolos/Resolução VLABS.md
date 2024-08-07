Arquivo  disponivel no link : [https://desecsecurity.com/academy/down/scan_interno.pcap](https://desecsecurity.com/academy/down/scan_interno.pcap)

## Vlabs - Scan interno
### vlab 1
Endereço fisico invasor:

Usando o comando:
	tcpdump -vnr scan_interno.pcap | grep request
Foi filtrado somente os pacotes com a palavra request logo retornou qual o IP do Invasor. depois:
	tcpdump -venr scan_interno.pcap src 192.168.0.150 
Esse filtro retorna somente os pacotes com a fonte ip 192.168.0.150, as informações do começo do pacote são do protocolo Ethernet onde mostra as informações do endereço MAC da fonte e do destino. Assim foi possivel descobrir o endereço fisico(MAC) do atacante.
Usando wireshark é muito mais facil de indentificar.
### Vlab 2
Marca do fabricante da interface de rede do invasor:

Usando os 3 primeiros bytes(6 numeros) do endereço MAC em site de consulta;
Pelo wireshark é possível visualizar essa informação nas infos do protocolo.

vlab 3 endereço logico(IP) atacante.
vlab 4 endereço logico do alvo.

# Vlabs - PortScan

## Vlab 1
Portas abertas:

Usando o comando:
	tcpdump -vnr scan_interno.pcap src host 192.168.0.23 | cut -d "," -f1 | grep -v IP | grep -v "R" | sort -un
foi possível filtrar os pacotes com host fonte do IP indicado e usando a ferramenta "cut" cortei só as informações desejadas, com o grep -v IP removi a linha desnecessária e com o "grep -v "R" " removi os pacotes com com a Flag R que significa erro, assim retornou somente os pacotes que fizeram sincronização com aquelas portas do servidor.
Formas de encontrar portas abertas:
	pacotes TCP com flags FIN, pois se finalizou a conexão significa que foi conectado e se foi conectado é pq a porta estava aberta,
	pacotes TCP com Flags SYN e ACK(ACK = " . " ), pois foram conectados com o servidor e retornaram a flag ACK.

# Vlabs Acesso
Descobrir o serviço que foi logado pelo invasor:
	Usado o wireshark, foi analisado as portas abertas descoberta no vlab anterior, foi observado os pacotes TCP com a Flag PSH que significam que possui payload no pacote TCP. foi observado usando a ferramenta "follow" do próprio wireshark uma comunicação com o servidor e o login bem sucedido no serviço proftpd.

# Vlab Suporte
Procurar troca de mensagem entre um cliente e suporte, para isso foi analisado os pacotes TCP que fizeram conexão nas portas abertas encontrado anteriormente, foi analisado os pacotes TCP com Flags PSH(push) que carregam um payload, dentro desse payload se encontrava a troca de mensagem e com a ferramenta "follow" foi possível observar de maneira facil e organizada a troca de mensagens.

# Vlab - Analise bytes I
Analise de Bytes de rede, solicitando o socket de origem, socket e o conjunto IP:Porta, exemplo: 192.0.0.1:80.

