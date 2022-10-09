# Criando chave SSH

Descrição
O que é uma chave SSH?

É uma espécie de conexão que temos que fazer com a máquina e o servidores do GitHub, sendo encriptada, para identificarmos que nossa máquina pode usar o GitHub.

Para criarmos, clicaremos na bolinha do usuário, ir na parte de configurações, e nela iremos até a opção SSH and GPG keys, mas antes vamos para o terminal.

Abrindo o terminal, no caso esse é o do macOS, digitamos ssh-keygen, para gerar a chave ,-t rsa, para dizer o tipo de encriptação, -b 4096, a força da encriptação, -C "maykrbrito@gmail.com", o email que estamos criando, isso tudo na mesma linha, dando enter ele vai pedir algumas coisas que não precisamos, apenas dando enter.

No windows precisaremos do Git instalado, ao instalar você terá um terminal diferente, que podemos criar a chave da mesma forma que no macOS.

Agora com a chave precisamos pegar ela para colocarmos ela no botão verde, ainda pelo terminal, damos um cd ~/.ssh/ , teremos algumas opções como id_rsa e id_rsa.pub, que é o que queremos, mas não conseguimos navegar, fazer um cd nele, mas conseguimos dar um cat para mostrar tudo que há no arquivo, dando enter, vamos copiar tudo desde o ssh até o .com e voltar ao GitHub, clicando no botão verde de nova chave, colocar um título e colar a chave e adicionar ela.


como configurar:
vai no terminal e digita: 
$ ssh-keygen -t rsa -b 4096 -C "mesmo email da conta da do git hub"

$ cat ~/.ssh/id_rsa.pub

copia a chave ssh que aparece (tudo que retornar) e cola lá no github.

pra colar: vai nas configurações do github e vai na parte de SSH e clica em new SSH:
vai pedir um nome pra essa chave (coloca o nome do seu pc). vc coloca e abaixo cola a chave copiada.

# Adicionando chaves ao gerenciador local SSH Agent

Descrição
Para este passo, vamos abrir o navegador, entrando neste link https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key-for-a-hardware-security-key você será direcionado a uma página no GitHub que irá nos ajudar, lembrando que para que executemos este processo, precisamos saber que o windows funciona de uma forma diferente do que macOS e o linux, então por isso para cada processo há uma página diferente, para todos esses sistemas operacionais.

Para o windows é bem simples, abriremos o terminal, iniciaremos ssh agent no background digitando ou apenas copiando do link, depois colaremos a linha já no terminal diferente que já tem o Git, eval "$(ssh-agent -s)", então mostrará para você o processo que está sendo executado e depois apenas rodar esta linha no terminal, ssh-add ~/.ssh/id_rsa.

No mac há alguns processos a mais do que o windows, iremos começar com a mesma linha eval "$(ssh-agent -s)", irá mostrar novamente o processo executado, então daremos um .ssh/config, veremos que não tem, então precisaremos dar um vim para criar, vim ~/ .ssh/config, assim criamos o config, agora tudo que precisamos é copiar:
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
Por fim copiaremos ssh-add -K ~/.ssh/id_rsa.

Pronto assim sua máquina está funcionando junto com a do GitHub.

# Linkando um repositório remoto com local



Descrição
Fizemos nosso primeiro repositório apenas online, mas agora criaremos seguindo um outro caminho.

vamos em new para criar um novo repositório, colocamos o nome, descrição, mesmo opcional é bem importante, escolhemos se é privado ou público para as outras pessoas, pularemos essa etapa de adicionar coisas pela nuvem, pois faremos ele todo manualmente, criado, estaremos vendo os passos que deveremos seguir.

Estaremos criando um repositório escrevendo no terminal mkdir nome do diretório , cd nome do diretório , damos um git init para iniciarmos o nosso git, damos o vim [README.md](http://readme.md) no caso estaremos escrevendo algumas coisas como nome e descrição, saímos e damos um git status para apenas darmos uma olhada, o arquivo não está sendo rastreado, então vamos dar um git add . , git commit -m ":tada: first commit" o nosso primeiro commit o  é apenas um ícone, agora precisaremos adicionar nosso repositório remoto, usando a parte de ssh que é muito mais seguro do que HTTPS, estaremos escrevendo add origin git@github.com:maykrbrito/demo.git este é somente um exemplo, já que o de cada um será diferente apenas copie ao lado do SSH, agora que adicionamos podemos dar um git remote -v para vermos os repositórios que estão na nuvem, mas por enquanto apenas estamos a focar em somente 1, que é no GitHub, damos um git branch -M main , pois ainda não temos a branch main, da forma com que estamos a trabalhar de padrão a branch vem na master, então mudamos o padrão para o main.

Agora damos um git push -u origin mainpara enviarmos nossos repositórios para nuvem, damos um yes para liberar a conexão, as chaves foram adicionada.

Voltando para parte code vemos que foi criado e linkado, olha que legal.

# Modificando arquivos local e enviando para repositório remoto



Descrição
Agora estaremos fazendo uma alteração, no terminal, acessamos o nosso arquivo README que fizemos na aula passada escrevendo vim[README.md](http://readme.md) , damos um enter e modificamos o que queremos, saindo dando um git status podemos ver que ele não foi colocado no stage area, precisamos colocar, mas como o arquivo já está sendo rastreado pelo git, não precisaremos fazer o git add . , faremos o git commit -am ":sparkles: changing readme" m sendo a mensagem e o a ele vai adicionar a modificação que não está na stage area automaticamente junto ao commit tudo em uma linha só, isso somente funcionaria caso você já tenha posto na stage area alguma vez. não vamos precisar fazer o git remote, pois a nuvem já existe, dando o git push não vamos precisar fazer o -u origin , porque estamos na branch main já que a branch já existe aqui para o git.

# Modificando arquivos remotos e puxando para repositório local



Descrição
Se alterarmos o arquivo e dermos commit changes, estaríamos fazendo direto online, mas se fizermos um git log --oneline, veremos que está a faltar um commit, sendo que na nuvem há mais, como faremos para puxar alteração da nuvem para máquina é bem simples, apenas damos um git pull e só, e se vermos novamente estará atualizada.

# Entendendo o histórico remoto


Descrição
O histórico funciona da seguinte forma, se formos para um dos repositórios e clicarmos em commits com o sinal de relógio poderemos ver o histórico de modificações, podemos navegar por todos os pontos da história, ou seja clicando no ultimo ícone, vemos que o repositório que está sendo mostrado é o do momento da modificação, mas como faço para voltar é bem simples, mudamos a branch para main.

# Corrigindo conflitos de merge


Descrição
Nesta aula estaremos fazendo uma configuração e corrigir conflito e erros por causa de um processo.

Entrando no diretório cd demo/ como exemplo, quando dermos um git pull ele vai avisar que está havendo um conflito, para corrigir apenas faremos o padrão pedido pelo git que é git config --global pull.rebase false que é o padrão merge, dando novamente o git pull estará tudo certo.

Agora forçaremos um erro para criarmos uma situação, vamos supor que nós tenhamos feito uma alteração no repositório e demos commit apenas na nuvem e esquecemos de dar git pull e quando chegamos em casa, nós fazemos uma alteração no local, quando formos dar um git pull vai mostrar que deu erro, se abrirmos pelo vim[README.md](http://readme.md) , poderemos ver que é possível escolher entre a alteração local e pela remota, e para fazermos isso apenas apagamos a cabeça, os ====== e os >>>>>> e dizemos qual alteração que queremos, mas existe outro modo usando o VSCode, abrindo ele, no terminal damos um open . e colocamos ele no VSCode, ele automaticamente irá perceber o conflito e irá lhe dar certas opções, como a de aceitar as alterações locais ou as da nuvem, aceitando qualquer uma automaticamente o VSCode vai alterar de acordo com a escolha, então damos um git commit -am "mensagem" , agora o git pull e depois por fim o git push, atualizando vemos as alterações no GitHub.

#