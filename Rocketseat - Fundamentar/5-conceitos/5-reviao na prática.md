# Resumo

* criar repositório:

$ git init

pra ver o estado dos aruivos e se tem alterações pra serem enviadas:

$ git status 

para adicionar tudo:
 $ git add .

 para adicionar só um arquivo por vez:

 $ git add nome do arquivo.txt

 se eu adicionar tudo mas quiser continuar mexendo em um arquivo ainda, nesse caso tenho que remover ele desse estado e deixar ele em vermelho:

 $ git rm --cached file2.txt

 para colocar no repositório:

 $ git commit -m "initial commit"