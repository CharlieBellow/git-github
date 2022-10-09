# Iniciando um novo projeto


Até agora aprendemos as bases do git, mas vamos ver como usar o git num projeto mais real.

Primeiramente acesse o site https://github.com/rocketseat-education, e busque pelo nlw-03-discovery e baixe como zip.

Ache o diretório e abra-o no terminal, e inicie um novo repositório com o comando git init, logo após, faça um git add . e por fim um git commit.

# Adicionando e verificando alterações


Descrição
Nessa aula veremos sobre as modificações do nosso projeto, e como nós podemos ter melhores mensagens de modificação nos nossos commits.

faz a alteração no arquivo. e pra ver o que editei é só rodar o comando:

$ git diff --color-words

e nessa parte: @@ -31,6 +31,9 @@

mostra em qual linha está a alteração.


  # Staging e commits com atalho

Descrição
Agora que pelo git status temos a noção de que o arquivo foi alterado, vamos commitá-lo.

Porém, como nós já temos todos os arquivos desse projeto no repositório, podemos pular a etapa do git add, já que após a modificação ele vai direto para a stage area, pois já é um arquivo rastreado e vamos fazer a execução do comando git commit com a opção -a, da seguinte forma:
git commit -am "lembre que podemos usar várias opções na mesma declaração"

$ git commit -am "modify index"

só funciona com arquivos já rastreados, ou seja, com arquivos que já estavam no git. 


# Ver modificações em diversos pontos da história

Descrição
Nessa aula nos aprofundaremos nas modificações, em como vê-las e em tudo que já fizemos no histórico do projeto.

Podemos usar o comando git show e as letras iniciais da hash de um commit, da seguinte forma:

$ git show 7f121d7

Assim, veremos exatamente aonde essas mudanças ocorreram, e o que foi retirado ou adicionado, e podemos ser ainda mais específicos, usando a seguinte opção:

$ git show 7f121d7 --color-words

Essa opção vai nos permitir ver as palavras exatas que foram alteradas no nosso commit.

Podemos também ver as mudanças que houveram dentro de um diretório específico (nesse caso o diretório views, dentro do diretório src) através do --, usado da seguinte forma:

$ git show 7f121d7 -- src/views/*

Diferentemente do git diff, o git show serve como um atalho para mostrar exatamente o que há em um repositório em qualquer momento da história, enquanto o git diff vai apresentar as diferenças encontradas no working directory e stage area.

# Ignorando arquivos e diretórios indesejados

o git ignore é um arquivo oculto, pra ver ele tem que rodar esse comando:
$ cat .gitignore

Descrição
Veremos aqui como fazemos para ignorar arquivos e diretórios que não queremos no nosso repositório, através do .gitignore.

O primeiro passo é criar o arquivo .gitignore, adicionar o nome do arquivo ou diretório que desejamos ignorar, e adicionar o nosso .gitignore ao nosso repositório, primeiro com o comando git add, e depois o git commit.

O seu .gitignore já foi para dentro do repositório e está pronto para rastrear os arquivos.

Caso tenha algum arquivo no seu repositório que você tenha adicionado ao .gitignore, como no exemplo do vídeo, o .DS_Store, apenas rode o comando abaixo:
$ git rm -r --cached .
Esse comando vai fazer o git parar de rastrear todos os arquivos, deixando-os no working directory apenas.

Após isso, executaremos o comando git add . que vai colocar todos os arquivos novamente na stage area, exceto os que serão ignorados pelo nosso .gitignore.

Depois, apenas fazemos um commit com uma mensagem que reflita o que fizemos.