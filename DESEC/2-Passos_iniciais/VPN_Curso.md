VPN do curso

Baixar arquivo da VPN no site, descompactar e acessar pelo terminal com o comando "openvpn arquivo.ovpn" 

Para conectar sem autenticação, criar um arquivo nano "conecta"  com o usuario na primeira linha e a senha na segunda e salvar. Editar o arquivo de acessa da vpn ".ovpn" na linha escrito "auth-user-pass" dar um espaço e escrever o nome do arquivo com as credenciais "conecta" salvar. Após não pedira mais senha.

Fechar o terminal com a vpn rodando não encerra a vpn, para descobrir se a vpn está rodando usa o comando "ps auxwww | grep openvpn" para fechar usa o comando "kill" ou "killall" com o ID do processo ou o nome do programa "openvpn" exemplo: "killall openvpn" fechara todos os processos rodando do open vpn.

