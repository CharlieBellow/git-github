# Tudo sobre como usar o GIT

 
# Git e Git HUb - Alura

- HEAD: Estado atual do nosso código, ou seja, onde o Git os colocou
- Working tree: Local onde os arquivos realmente estão sendo armazenados e editados
- index: Local onde o Git armazena o que será commitado, ou seja, o local entre a working tree e o repositório Git em si.
https://git-scm.com/book/pt-br/v2/Fundamentos-de-Git-Gravando-Altera%C3%A7%C3%B5es-em-Seu-Reposit%C3%B3rio

# Comandos no terminal

- vê os commits e alterações feitas
$ git log

- vê as informações resumidas
$ git log --oneline

- para ver as configurações que foram feitas linha por linha:
$ git log -p
    (aperta q pra sair )

- mais formas de mostrar o histórico:
    https://devhints.io/git-log 

- mostra só as hashs (aquele código grande de 40 dígitos)
$ git log --pretty="format:%H"

- mostra o início da hash e a mensagem do commit
$ git log --pretty="format:%h %s"

- mostra o início da hash, a mensagem do commit e o autor
$ git log --pretty="format:%h %s %ae"

# configura o nome e o email no projeto:

- de forma local (só para esse projeto):
$ git config --local user.name “nome que você quer”
$ $ git config --local user.email “email que você quer”

- de forma global (todas as sas configurações do git hub)
$ git config --global user.name “nome que você quer”
$ $ git config --global user.email “email que você quer”

---------------

- para ver qual é a configuração que está:
$ git config user.name
$ git config user.email

-----------------------------

- ignorando um arquivo:
cria o arquivo .gitignore e adiciona o nome do arquivo igual ao modo como o terminal reconhece (se tiver espaço ou acento coloca entre aspas ou a \ antes do espaço - é bom sempre conferir no terminal como seria a escrita do arquivo se não for igual o .gitignore não vai funcionar)

se for uma pasta coloca da mesma forma mas a / no final. ex.: pasta/

um commit é a forma de salvar um estado ou versão do nosso código;
# quando commitar?
sempre que o código for atualizado pra uma versão que funciona. 
sempre que uma nova funcionalidade for adicionada (e esteja funcionando)
quando bug for corrigido

# quando NÂO commitar?
nunca commitar um código que não funciona.
quando a alteração não é significativa e não causa impacto. (correção de identação, etc)

# criando o servidor:

o servidor é um diretório que vai armazenar e controlar as alterações. (repositório puro)

$ git init --bare

depois vai na pasta que estou trabalhando e adiciona esse repositório servidor:

$ git remote add local /home/charlie/Documentos/cursos online/Dev/Git  e GitHub/Alura/servidor/

esse endereço é pode ser um repositório remoto, uma pasta no computador, 

#  Branches (ramos) demarcando linhas de desenvolvimento 

- criando uma nova branch:

$ git branch nomedabranch

- listando as branches:
$ git branch 

- mudando de branch:
$ git checkout branch nomedabranch


- criando e já mudando pra branch
$ git checkout -b nome

- deletando uma branch:
(você não pode estar na branch que quer deletar)
$ git branch -D nomeDaBranch


*** trazendo as alterações da branch para a master

- se quiser unir a branch atual que eu estou com outro branch de nome titulo (aí ele cria um commit de junção de marge e abre o vim pra vc editar o texto do commit)

$ git merge titulo 

* obs: nesse caso ele "apaga " os commits anteriores e cria um só pra essa nova merge

#  atualizando a master com os commits da branch título (trazendo os commits do titulo para a master)

$ git rebase titulo

(nesse caso, se eu estiver na master e quero juntar o que fiz na master com a brach titulo que eu tava trabalhando antes, ele vai juntar os comits de cada branch em uma linha de desenvolvimento só, que nesse caso é a master onde eu já estou e o último commit fica sendo o da master que é o eu eu tô)

- mostrando todas as linhas de desenvolvimento:
(mostra o desenhos das linhas na lateral)
git log --graph

# *** trabalhando com modificações na mesma linha de código:
(resolvendo conflitos de código)

se fizer merge ou rebase vai dar o conflito, aí você cai ter que escolher qual o código que vai ficar e depois adiciona o arquivo que foi modificado com o git add e git commit e esse commit será um commit de merge (:x - pra sair do vim ou q ou wq)

- adicionar na servidor que controla as versões:
$ git push local(ou o mais comum é origin) master

- pegar do servidor
$ git pull local/origin master

antes de enviar é sempre bom puxar as informações pra ver se o código que eu tõ trabalhando é o mais recente (git pull local master) e depois git push local master

# ***** navegando no histórico do projeto

- desfazer uma alteração que acabou de fazer (sem ter adicionado ainda com git add)
$ git checkout -- arquivo.html

- desfazer depois de ter feito o git add (desmarca o arquivo que foi marcado pra ser commitado):
$ git reset HEAD arquivo.html (o HEAD significa o estado em que esto trabalhando) (as alterações ficam lá mas não estão marcadas pra commitar. se quiser descosiderar também as alterações faz o git checkout -- arquivo.html)

- desfazer depois de commitar: (ctrl + z no commit)
$ git revert 0687f04f2ac... (hash do commit) 

- salvando temporariamente a versão do código pra mexer depois: (pra quando você precisa parar de trabalhar no arquivo e o código ainda não funciona)

$ git stash 

- ver o que tá salvo lá na lista de coisas guardadas:
$ git stash list
(cada item da lista é mostrado e dentro das {} tem o número da stash)

- pegar o que tá salvo na stash list:

$ git stash apply 0 
(zero é número da stash que eu quero pegar)

- removendo a stash que tá lá:
$ gi stash drop

- pegando e removendo a stash:
$ git stash pop

pegando de volta uma stash
$ git fsck --unreachable

# ********** viajando no tempo:
- indo para um commit específico:
$ git checkout (7 primeitos digitos da hash)

mas para não perder as alterações é necessário criar uma nova branch. 

$ git checkout -b novo-branch


- diferença entre 2 commits

$ git diff dc59a31..d83b587

- pra ver o que alterei até agora (antes de adicionar pra commitação)

$ git diff

# ************ gerando uma versão de projeto entregável

-  criando uma versão de código que funciona: (esse ponto não pode ser modificado)
$ git tag -a v0.1.0 -m "mensagem sobre a versão que está sendo lançada"
(v0.1.0 - é o nome da versão)

- para ver as versões que tenho:
$ git tag

- enviando a versão para o servidor local:

$ git push local v0.1.0
$ git push origin v0.1.0


- git remote -v (ver os meus repositórios)

no github a versão vai ficar na aba relese
