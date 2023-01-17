# 1. Unix e o Terminal

Nessa seção vamos aprender sobre os conceitos básicos de sistemas operacionais, especialmente o Unix, e a camada de interação mais básica: o terminal.

## 1.1 Sistemas Operacionais

Computadores são ferramentas versáteis: os utilizamos para estudar, escrever e-mails, jogar, ver séries e muito mais. Entretanto, raramente paramos para pensar na infraestrutura que existe por trás de todos esses serviços e atividades.

Um computador nada mais é do que uma peça feita de vidro, plástico, metal e silício. Claro, todas essas partes tem um alto valor agregado. O silício, por exemplo, é organizado em milhões de transistors formando um processador capaz de realizar operações lógicas e matemáticas.

Para que essa peça, que chamamos de *hardware*, tenha qualquer utilidade, precisamos controlar seus processos e fluxo de informação de forma a nos permitir a executar tarefas e a receber respostas.

Esse controle é feito através do *software*, o conjunto de programas de um computador que fornecem ao usuário final uma experiência interativa, o que inclui o seu navegador web(Chrome, Firefox), editores de documentos(Word, PowerPoint), as redes sociais no seu celular(Instagram, Facebook) e outra infinidade de programas.

Todos esses programas não existem por si só, mas sim dependem de uma interface, um ponto de interação entre duas partes, chamado de *sistema operacional*, que permite a existência de outros programas mais complexos. O sistema operacional tem duas funções principais: gerenciar o hardware e oferecer abstrações que facilitem a vida dos programadores.

Por exemplo, sem o sistema operacional um pobre usuário que deseja criar um simples arquivo de texto precisaria utilizar linguagem de máquina e saber muito bem como funciona o armazenamento(HD, SSD) e a memória RAM para registrar todos os bits nos lugares corretos, e nem vamos falar de recuperar esse arquivo depois!

O sistema operacional abstrai toda a complexidade dos dispositivos físicos e oferece para o programador uma *chamada de sistema* ou system call, fazendo com que a tarefa do exemplo seja executada de forma bem mais simples com chamadas como creat(), para criar o arquivo, open(), para abrir, write() para escrever e close() para fechar.

São exatamente esses tipos de funções que são utilizadas no final das contas por um programa como o Word quando você cria um novo documento. O sistema operacional vai indexar esse arquivo dentro de um *sistema de arquivos*, para que ele possa ser recuperado facilmente depois pelo seu nome.

## 1.2 Origem do Unix

O sistema operacional Unix surgiu em uma época muito diferente da computação. A memória de semicondutores ainda não estava popularizada, os chamados "minicomptadores" eram do tamanho de um armário e caros. 

![[640px-Pdp7-oslo-2005.jpg]]
Figura 1. Computador PDP-7, onde a primeira versão do Unix foi escrita.

Em um artigo de 1974 onde é descrito os conceito básicos e a implementação de partes do sistema, uma das vantagens apresentadas é que "o Unix pode rodar em hardware custando tão pouco quanto $40.000(dólares, em uma época em que uma Coca-Cola custava 5 centavos de dólar)". Hoje em dia temos computadores milhares de vezes mais potentes por menos de RS1.000.

Essa restrição de poder de processamento e capacidade de armazenamento forçava programadores brilhantes como Ken Thompson, autor do Unix, sempre tivessem consciência de quanta memória seus programas utilizavam, e a utilizar técnicas inteligentes para alcançar seus objetivos. O Unix surgiu justamente nesses princípios, o que hoje é conhecido como "filosofia Unix". 

A primeira versão do Unix de 1969 foi escrita em assembly, uma linguagem de baixo nível que fazia com que o sistema fosse difícil de adaptar para outras máquinas. Em 1973 ele foi reescrito em C, uma linguagem de alto nível desenvolvida por Dennis Ritchie desde 1970, o que facilitou a portabilidade do sistema, aumentando a sua popularidade. Por ser escrito em C, mudar o sistema de uma máquina para outra era um problema de reescrever apenas um programa: o compilador, ao invés de adaptar todo o sistema em outro assembly.

![[899px-Ken_Thompson_(sitting)_and_Dennis_Ritchie_at_PDP-11_(2876612463).jpg]]
Ken Thompson (sentado) e Dennis Ritchie utilizando o PDP-11.

Note que computadores pessoais ainda não existiam. As máquinas eram compartilhadas entre vários usuários, cada um conectado a um terminal diferente. O terminal incluía uma entrada: um teclado, e uma saída: uma impressora em papel e depois displays gráficos. Essa metáfora é transportada para os SOs modernos, mas vamos entrar em mais detalhes adiante.

## 1.3 O Sistema de Arquivos

A principal função que queremos de um computador é criar, manipular e consumir informação. Isso inclui trabalhos em Word e PDF, filmes e músicas em MP3 e MP4 e outras funções. Todas essas atividades geram informações que precisam ser armazenadas de forma organizada em um sistema de arquivos para que possam ser recuperadas depois.

Mas o que é um arquivo? Parece óbvio: é uma folha de papel com um texto ou imagens. Essa metáfora é tão bem transferida para o mundo digital que nós nem percebemos a diferença: para um estudante trabalhando na sua pesquisa, um arquivo no Word é tão real quanto um arquivo de papel. Mas para entendermos como arquivos funcionam no sistema operacional, precisamos de uma definição mais detalhada.

Parte da filosofia Unix citada anteriormente é que na implementação do sistema operacional "tudo é um arquivo". Isso quer dizer que todas as partes do sistema são representados em arquivos, isso reduz o número de casos especiais e diminui a complexidade, fazendo com que seja mais fácil de trabalhar e programar.

Mas é necessário fazer mais uma abstração: tipos de arquivos diferentes. Isso permite que o sistema operacional proteja e esconda alguns arquivos(aqueles que o usuário nem quer saber que existem), e ofereça uma interface mais simples.

Ao ligar o computador, o usuário começa a trabalhar criando e editando os documentos que ele precisa, gerando *arquivos comuns*. Depois ele decide que os seus arquivos tratam de assuntos diferentes, e seria mais conveniente separá-los em pastas diferentes, chamadas de *diretórios*.

Na perspectiva do usuário essas duas abstrações são o suficiente para organizar o seu trabalho; ele nem tem que se preocupar que existem vários *arquivos especiais* por baixo dos panos garantindo a funcionalidade e os serviços que ele deseja.

## 1.4 O Terminal

Como citado anteriormente o terminal era o meio de comunicação de um usuário com uma máquina compartilhada. Esse tipo de interação do usuário com a máquina é chamado de *linha de comando*, ou seja o usuário escreve comandos para rodar programas, ao invés de clicar em um ícone com o mouse.

![[811px-DEC_VT100_terminal.jpg]]
Figura 2. VT100, lançado em 1978, se tornou um dos terminais mais populares.

Hoje em dia a tecnologia é barata o suficiente para que cada usuário tenha a sua própria máquina, e além disso é poderosa o suficiente para exibir interfaces gráficas elegantes que tornam a vida do usuário novato mais simples. Mas o terminal é uma ferramente tão útil e poderosa que temos programas chamados *emuladores de terminal* que emulam essa interação que pode ser considerada "defasada", mas que até na mão de um usuário intermediário pode ser bem mais eficiente para algumas tarefas.

O terminal executa um programa chamado Shell, que é um interpretador de linhas de comando. Na sua forma mais simples, um comando tem a forma:

> comando $arg_1$ $arg_2$ ... $arg_n$

Ou seja, o usuário digita o nome de um comando e, caso necessário, passa argumentos separados por espaço. Esses argumentos são utilizados pelo programa para alterar o seu comportamento.

Existem vários Shells, e o usuário pode facilmente trocar entre eles como Bash, Fish, Zsh, Csh e vários outros. O mais comum utilizado na maioria das distribuições Linux(Ubuntu, Mint, Fedora) é o Bash.

Além de ser um interpretador de comandos, o Shell nos permite agrupar comandos para serem executados de uma só vez, chamados de *scripts*, que seguem um dos princípios da filosofia Unix, que diz que programas devem ser executar apenas uma tarefa, mas executá-la muito bem.

No final das contas um script chama outros programas e os interliga com o poder das condições lógicas, aritmética, loops e pipes para realizar uma tarefa mais complexa, com a flexibilidade de poder ser facilmente alterado, ter programas substituídos e muito mais.

---
### Prática 1
Explorando a estrutura de diretórios.

Como mostrado anteriormente, o diretório é um tipo de arquivo que permite a organização de arquivos comuns. O sistema operacional cria por padrão uma estrutura própria para organizar os aplicativos instalados(que são arquivos comuns), os dispositivos conectados(arquivos especiais) e outras funções.

Vamos agora utilizar o terminal para explorar esses arquivos. Primeiro precisamos definir que existe um diretório raiz, o primeiro diretório que engloba todos os outros do sistema, chamado de "/".

Para listar o conteúdo desse ou qualquer outro diretório utilizamos o comando **ls**.
Abra agora o terminal no seu sistema. Por padrão, você começa localizado no seu diretório pessoal, e um *prompt* que aparece geralmente na forma:

> \[usuario@linux\]$ 

indica que o shell está pronto para receber comandos. Quando você passar um comando para ele, ele vai parar a sua própria execução para rodar o seu comando, e então retornar com o prompt.

Você pode customizar esse prompt para mostrar a mensagem que você quiser, mas vamos entrar nesses detalhes depois.

Nesse prompt você pode agora digitar o comando ls e pressionar Enter para ver o resultado. No meu sistema(Fedora Linux 37) a saída é assim:

![[Pasted image 20230117134917.png]]

Pronto, você executou o seu primeiro comando!

Agora para explorar os diretórios padrão, vamos passar um argumento para o comando ls(lembre-se da definição de comandos). O argumento que queremos passar é o nome do diretório raiz:

![[Pasted image 20230117134936.png]]

Se você rodou esse comando no Ubuntu, ou no Linux Mint, ou no Fedora, você pode ter visto alguns diretórios diferentes, mas a maioria são padrão para todos. Vamos trabalhar apenas dentro do diretório **home**, utilizado para guardar os diretórios pessoais de usuários.

Apesar disso, é útil saber sobre alguns diretórios como o **etc**, que guarda arquivos de configuração de programas instalados e o **usr**, onde são instalados os programas. Outros como o **proc**, que guarda programas que estão rodando e **dev**, que guarda os arquivos especiais relacionais a devices, dispositivos, são utilizados exclusivamente pelo sistema operacional.

---




















# Projeto GNU e Bash

# Linux e Distros

