## Docker + WSL

Primeiros passos

#### Steps

Siga esses passos:  
https://docs.docker.com/engine/install/ubuntu/

Resumo:  
- Instale atraves do script que faz toda magica(não indicado para produção): 
curl -fsSL https://get.docker.com -o get-docker.sh  
sudo sh get-docker.sh  
- Geralmente o serviço não inicia sozinho, faça isso na mao(referencia: https://phoenixnap.com/kb/cannot-connect-to-the-docker-daemon-error):  
sudo service docker status  
sudo service docker start  
  
- Bora melhorar isso e colocar para rodar no startup?(Referencia: https://blog.nillsf.com/index.php/2020/06/29/how-to-automatically-start-the-docker-daemon-on-wsl2/):  
Execute:
sudo visudo
Ira abrir o arquivo para vc retirar a necessidade de pedir senha com o comando docker, adiconando n ultima linha esse conteudo:
nome_usuario ALL=(ALL) NOPASSWD: /usr/bin/dockerd
Por fim crie um script que adiona o codigo a inicalização. Basta criar esse arquivo e executa-lo:
#!/bin/bash

echo '# Start Docker daemon automatically when logging in if not running.' >> ~/.bashrc
echo 'RUNNING=`ps aux | grep dockerd | grep -v grep`' >> ~/.bashrc
echo 'if [ -z "$RUNNING" ]; then' >> ~/.bashrc
echo '    sudo dockerd > /dev/null 2>&1 &' >> ~/.bashrc
echo '    disown' >> ~/.bashrc
echo 'fi' >> ~/.bashrc
