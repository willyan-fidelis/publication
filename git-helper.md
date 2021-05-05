## Git Command Helper

Dicas de comandos git

#### Atualizando e baixando atualizções remotas.
Comando:  
git pull  

Descrição:  
Esse comando faz o fetch e depois o merge de um repositorio remoto para local.  
Referencias:  
https://pt.stackoverflow.com/questions/3231/qual-a-diferen%c3%a7a-entre-os-comandos-git-pull-e-git-fetch


#### Untrack arquivos já adicionados ao repositorio
Comandos:
Primeiro remove todos os arquivos do arquivo index:
git rm -r --cached .
Agora adiciona tudo, considerando o gitignore alterado:
git add .
Por fim commita:
git commit -m ".gitignore fix"

Descrição:  
Esses comandos realizam o Untrack de arquivos que ja estavam sendo traqueados, mas hoje faze parte do gitignore.  
Referencias:  
https://www.codeblocq.com/2016/01/Untrack-files-already-added-to-git-repository-based-on-gitignore/

