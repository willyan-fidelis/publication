## Docker
  
Principal referencia:  
https://www.youtube.com/watch?v=0cDj7citEjE  
  
-Rodando um container em modo de iteração(-i):
docker run -i -t ubuntu /bin/bash  
onde ubuntu é imagem com a versao mais atual do ubuntu e /bin/bash é o processo que sera inicalizado  
Ja com o container aberto no terminal podemos testar se o processo bash esta aberto mesmo:  
ps -ef  
Podemos testar o terminal pedindo a versao do ubuntu:  
cat /etc/issue  
Para matar e sair do container:  
ctrl + D  
Para apenas sair do container, deixando o mesmo aberto:  
ctrl P + ctrl Q
Para voltar a atachar:
docker attach containerID

Listar containers rodando:  
docker ps  
Ou para ver all com  sudo ainda:  
sudo docker ps -a  
  
Listar imagens:  
docker images  

Expor porta 80 do container na porta 8080 ao rodar:  
docker run -i -t -p 8080:80 ubuntu:14.10 /bin/bash  
  
Uma vez container rodando em modo interativo vc pode instalar qq coisa, como um servidor nginx:  
apt-get install nginx  
Para ver se ta rodando:  
ps -ef  
Nõa ta rodando então execute:  
/etc/init.d/nginx start  
Agora ta rodanod:  
ps -ef  
  
Outra opção é baixar a imagem do nginx diretamente(ref: https://linuxways.net/ubuntu/how-to-install-docker-in-ubuntu-20-04-and-run-nginx-container/):  
sudo docker pull nginx  
sudo docker run -d --name nginx-server -p 8080:80 nginx  
