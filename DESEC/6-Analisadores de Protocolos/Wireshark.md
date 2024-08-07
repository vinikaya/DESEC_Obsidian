Analisador de protocolo com interface gráfica, um dos mais usados no mundo gratuito.

Filtro no wireshark(pesquisar mais formas de usar o filtro):
	ip.dist == 192.168.0.200  -- busca somente os pacotes com ip destino mensionado;
	Possivel fazer varios tipos de filtro.
	tcp contains "PASS"  -- forma de pesquisar por palavras na resposta do pacote.
	https://wiki.wireshark.org/DisplayFilters  -- filtros de visualizar e procurar.
	https://wiki.wireshark.org/CaptureFilters  -- filtros de capturas.

Clicar com botão direito em um pacote TCP(ou qualquer outro) e "FOLLOW" Mostra de forma organizada e em ordem as respostas dos pacotes TCPs.

(Aula analise de trafego - Exploit  - boa para ter noção da analise dos pacotes no wireshark)
