# Para quem é o curso?

Descrição
Começaremos essa aula explicando a diferença entre Git e GitHub,

O Git é um gerenciador de projeto, alterações, histórico, usado em uma máquina local.

Caso você queira tirar da sua máquina e colocar em um repositório remoto, o GitHub existe como essa solução, sendo uma das mais usadas.

Porém o GitHub não dá para usar sem o Git, pois ele serve para hospedar os repositórios. Ao invés de deixar só na máquina, coloca na nuvem.

O que aprenderemos neste curso é a primeira parte que vemos no site "Give your code a home in the cloud", ou seja, colocar o seu código na nuvem, poderemos colocar todo o seu código, ver todo histórico, criar repositório pelo GitHub, trabalhar online, então veremos como linkar sua máquina com o GitHub, e levar seu repositório local ao GitHub e vice-versa.


# Requisitos para o curso e revisão de Git

Descrição
Um dos requisitos que precisaremos para entender o curso é ter visto a parte de "Ambiente dev de outro mundo" do discover e também vai precisar do guia de Git.

De começo vamos revisar rapidamente algumas coisas sobre o curso de Git e ver qual o fluxo que teremos aqui e também veremos algumas palavras a mais que teremos no curso.

Abrindo o terminal, faremos um novo diretório com o comando mkdir, no caso colocaremos o nome de "revisao", após criarmos, entraremos no nele usando o comando cd revisao , manualmente seria come se estivéssemos criando uma pasta, colocando o nome e entrando nela, mas para nós é melhor controlar o computador via texto, com isso estamos já treinando a usar mais o terminal.

Ainda no terminal damos um git init para iniciarmos o repositório, será onde iremos guardar as modificações do nosso código, feito isso eu teria como criar um arquivo de texto usando o "vim" digitando: vim [README.md](http://readme.md) , apertaremos a letra I para inserir algo, md é uma extensão de Markdown , podemos alguns códigos específicos, podendo até usar alguns HTMLs. Daremos então Esc :wq, para sair, lembrando que isso é um comando do vim.

Agora se dermos um git status , podemos ver que estamos em uma branch master, ou seja, ramificação master, também que não há commits, os arquivos que não estão sendo rastreados, lembrando do processo do Git, ele está na nossa working area local e temos de passar o arquivo para nosa stage area, onde ele estará preparado para que possamos criar o commit.

E agora precisamos fazer mais dois processos, o primeiro sendo git add . para adicionar todas as nossas modificações e o git commit -m "first commit" , feito isso fizemos todo o processo de criar um ponto na história.

Depois disso, agora algo que vamos aprender é dar um git push para enviar ao GitHub até o nosso repositório, assim que linkarmos nossa máquina a máquina do GitHub, e git pull para trazer alterações lá da nuvem, ou também git clone para trazer um repositório novo até a nossa máquina através do Git.