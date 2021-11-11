## Docker + WSL

Primeiros passos

#### Steps

Siga esses passos:  
https://docs.docker.com/engine/install/ubuntu/

Resumo:  
- Instale atraves do script que faz toda magica(não indicado para produção): 
curl -fsSL https://get.docker.com -o get-docker.sh  
sudo sh get-docker.sh  
Geralmente o serviço não inicia sozinho, faça isso na mao(referencia: https://phoenixnap.com/kb/cannot-connect-to-the-docker-daemon-error):  
sudo service docker status  
sudo service docker start
