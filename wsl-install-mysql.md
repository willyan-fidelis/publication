## Instalar MySQL no Ununtu com WSL

Instalação foi testada na versão 5.7

#### Steps

Siga esses passos:  
https://computingforgeeks.com/how-to-install-mysql-on-ubuntu-focal/  

Unico detalhe que antes de avançar ao passo 'Step 3: Secure MySQL 5.7 Installation on Ubuntu 20.04' voce precisa iniciar o serviço do mysql no windowscom o comando:  
sudo service mysql start  

Agora com o mysql rodando no linux na WSL voce precisa de uma ferrameta para visualizar e editar. Vamos instalar o mysql workbench no windows, no meu caso testei com a versão 6.3:   
-Baixar: https://downloads.mysql.com/archives/workbench/  
-Instalar  
-Agora abra o workbench, basta criar uma nova conexão que enxerga o linux, o mais legal que basta usar as config padrão que o windows ja enxerga como se o server fosse local, com localhost e porta padrão.  
-Fim! 
