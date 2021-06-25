# AWS Lambda
Em tese a instalação consistem em:  
Instalação CLI SAM(serverless AWS command line interface)  
Configurando e criando usuario e permições em IAM  
Instalando Docker  
Instalando AWS Toolkit para o vscode  
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-linux.html  

# Videos/Teste Local
https://www.youtube.com/watch?v=DA3hlLxTl-8  
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-hello-world.html  

## Docker não inicia no WSL?:
https://github.com/MicrosoftDocs/WSL/issues/457  
sudo /etc/init.d/docker start  
https://stackoverflow.com/questions/44678725/cannot-connect-to-the-docker-daemon-at-unix-var-run-docker-sock-is-the-docker  
sudo dockerd  

## Problemas para rodar docker sem sudo e consequentemente problemas no vscode com debug?:
Voce deve adicionar o seu usuario ao grupo root para ter privilegios sem ter que utilizar sudo:  
https://docs.docker.com/engine/install/linux-postinstall/ 
