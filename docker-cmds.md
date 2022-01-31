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

Stop docker:  
docker stop container_id  

Expor porta 80 do container na porta 8080 ao rodar:  
docker run -i -t -p 8080:80 ubuntu:14.10 /bin/bash  
  
Uma vez container rodando em modo interativo vc pode instalar qq coisa, como um servidor nginx:  
apt install nginx  
Para ver se ta rodando:  
ps -ef  
Nõa ta rodando então execute:  
/etc/init.d/nginx start  
Agora ta rodanod:  
ps -ef  
  
Outra opção é baixar a imagem do nginx diretamente(ref: https://linuxways.net/ubuntu/how-to-install-docker-in-ubuntu-20-04-and-run-nginx-container/):  
sudo docker pull nginx  
sudo docker run -d --name nginx-server -p 8080:80 nginx  
  
Vc pode ver as alteração da ultima vez que seu container rodou com(onde f7ff26213666 é o id do container):  
docker diff f7ff26213666  
  
Uma coisa super utel é deixar instalações/alterações salvas no container, afinal ao desligar tudo sera perdido e o container fica nas condições inicias.  
Para isso faça um commit dessas alterações, que salvar um conaiter, onde f7ff26213666 é o id do container, fidelis/nginx-ubuntu é o nome e 1.0 é a versao que vc esta dando para esse novo container, com um estado salvo:  
docker commit f7ff26213666 fidelis/nginx-ubuntu:1.0  
docker commit f7ff26213666 fidelis/nginx-ubuntu -> Assim o docker não save e nao gerencia as versoes, e sera considerada a last!
Bora testar essa imagem com outra porta no host?:  
docker run -i -t -p 6660:80 fidelis/nginx-ubuntu:1.0 /bin/bash  
Depois vc mesmo tem ainda que inciar o serviço, afinal o commit salva as instalações mas não starta o servico sozinho:  
/etc/init.d/nginx start  
Ou iniciar ja com serviço nginx-server de pé:  
sudo docker run -d --name nginx-server -p 6660:80 fidelis/nginx-ubuntu:1.0  
  
Rodando um processo de um container por fora do mesmo:  
docker exec 88c686ec529f /etc/init.d/nginx start  
Onde 88c686ec529f é o container_id e etc/init.d/nginx start é o comando solicitado para o container.  
  
Mais comandos:  
docker inspect 88c686ec529f ->inspeciona detalhes, como ip interno e afins  
Por fora do container com nginx: curl 172.17.0.2:80 -> retona a pagina de boas vindas do nging  
docker stats 88c686ec529f -> status de consumo de memoria, rede e processamento que o container esta utilizando do host.  
docker stop 88c686ec529f -> Para um container, mas nao remove. Vc visualiza ele com docker ps -a
docker start 88c686ec529f -> Inicia um container  
docker rm 88c686ec529f -> Remove, mas so com container parado  
docker rm -f 88c686ec529f -> Força a remoção, mesmo com container rorando.  
O mesmo vale para apagar imagens:  
docker rmi image_id -> Remove, mas so com container parado  
docker rmi -f image_id -> Força a remoção, mesmo com container rorando.  
Todos os containers com esse imagem tbem serao removidos.  
docker images -> listta todas as imagens  
  
Fazendo dois container com nginx se comunicar.  
Primeiro inciar o primeiro container, de preferencia passando um nome como option, senao o nome sera gerado de forma random e vc precisa saber o nome mais tarde:  
docker run --name first-webserver -i -t -p 6660:80 fidelis/nginx-ubuntu:1.0 /bin/bash
Agora iniciamos o segundo dando um nome qualquer nesse caso web2, fazendo um link com o first-webserver que agora tem um nickname web1:  
docker run -it --name web2 --link first-webserver:web1 fidelis/nginx-ubuntu:1.0

Probelmas comuns:  
comandos ps não recochecido, necessario instalar(https://www.vivaolinux.com.br/dica/Docker-ps-command-not-found-Resolvido):  
apt update && apt install -y procps  
Comando ping nao reconhecido:  
apt install iputils-ping  
  
---------------- Dockerfile ----------------  
Coloca cada passo para criar uma imagem de container  
  
Bora criar o primeiro Dockerfile!  
Em uma pasta crire um arquivo com o vim:  
vim Dockerfile  
Depois digite linha a linha no vim:  
FROM ubuntu:14.04  
MAINTANCE willyan_fidelis@hotmail.com  
RUN apt-get update && apt-get install -y apache2 && apt-get clear  
Ou:  
FROM fidelis/nginx-ubuntu  
MAINTANCE willyan_fidelis@hotmail.com  
RUN apt-get update && /etc/init.d/nginx start && apt install -y procps
  ------  
O vim é chato, ao abrir edite a vontade, depois aperte ESC, depois :x para salvar ou :qa! para sair!  
Bom, agora buildar passando .(ponto), ou seja, o diretorio atual:  
docker build .  
Pronto, veja suas imagens e tera uma nova! So que nao deu nenhum nome nem tag(execute docker images e veja), que é importante!  
Faca assim(paase -t para tag + versao):  
docker build -t fidelis/server_test:1.0 .
Agora ja podemos usar essa imagem normalmente:  
docker run -it fidelis/server_test:1.0 /bin/bash  


2020.01.30: 
Algumas das principais pastas do docker: 
/var/lib/docker 
/var/lib/docker/volumes 
/var/lib/containerd 

