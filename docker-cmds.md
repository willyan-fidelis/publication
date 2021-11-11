## Docker
  
  
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
