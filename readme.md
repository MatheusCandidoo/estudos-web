# Principais comandos do GNU e UNIX
  
  Esta secção é destinada a exemplificar e discutir os principais comandos dos sistemas operacionais linux, independente de sua distribuição.

### O que é um comando?
  
  Podemos definir comandos como **palavras de ação** do Sistema operacional, onde executaremos uma determinada ação para a palavra que for escrita no terminal.
Podemos ter alguns tipos de comandos:
* Comando interno do *shell*.
* Programa externo.

##### Comando interno do *shell*
  
  Comandos internos do *shell*, são ações que executamos de forma nativa no terminal, ou seja, comandos que são predefinidos no *shell* do seu Sistema Operacional (S.O.) e executam ações também já definidas. como por exemplo o comando *'echo'*, que escreve algo na sua saída padrão.

```
echo "Bem vindo!"
```

##### Programa externo
  
  São programas instalados no seu sistema operacional que realizam uma determinada ação. Por exemplo o comando Tar, que compacta arquivos, não é um comando interno do *shell*, mas sim um programa de compactação de arquivos que foi instalado no seu sistema operacional.

```
Exemplo de como usar o comando tar
```

##### Como diferenciar os tipos de comandos

  Existe uma forma de identificar se um comando é interno ou um programa externo, utilizado o comando interno ***type***.

```
type echo
```

  Desta forma será impresso uma mensagem dizendo o tipo de comando. Executando o comando acima, temos a seguinte mensagem *'echo is a shell builtin'*, que nos diz que o comando echo é um comando construído no *shell*, ou seja, um comando interno, predefinido no *shell*. Mas se executarmos o seguinte comando:

```
type tar
```

  Teremos como resultado a seguinte mensagem *'tar is /bin/tar'*, *'/bin/tar'* é o diretório onde se encontra o programa que sera executado, desta forma podemos diferenciar os tipos de comandos interno e programa externo pelo retorno do comando *type*, que retorna uma mensagem de que o comando é construído no *shell* (*'echo is a shell builtin'*) para comandos internos e um diretório de onde está o programa para programas externos (*'tar is /bin/tar'*).

  O comando *type* pode retormais uma outra mensagem, que diz que o comando foi hasheado. Por exemplo, se utilizarmos o type no comando *clear*, que é um comando utilizado para limpar a tela do teminal.

```
type clear
```

  Teremos como resposta a mensagem *'clear is hashed (/urs/bin/clear)'*, isto significa que o comando foi alocado para uma *hash*  (Memória) interna do Sistema Operacional para ser executado de forma mais rápida, o S.O aloca na hash alguns comandos que são muito utilizados. Mas também podemos observar que no final da mensagem temos um diretório (*'...(/urs/bin/clear)'*), que nos informa que este comando é um comando de programa externo.

### Variável *PATH*
  
  Como discumitmos anteriormente, os comandos internos do *shell* são comandos nativos, então nosso S.O. não tem muita dificuldade para executa-los. Já os comandos de programas externos, necessitam que o Sistema Operacional encontre o diretório onde ele será executado, então tomemos como exemplo o comando *tar* que nos retornou um diretório quando utilizamos o comando *type* (*'/bin/tar'*). Mas como o S.O. enconrou o arquivo a ser executado? A variável *PATH* armazera alguns caminhos onde o sistema busca os arquivos a serem executados, vamos executar o comando *echo* para imprimivar o valor de *PATH*.

```
echo $PATH
```
  Lembrando que sempre que formos manipupar uma variável, precisamos utilizar o sifrão (*$*). Após executarmos o comando acima, temos a seguinte mensagem *'/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
'*. Simplificando para que possamos entender a mensagem, são vários diretórios, separando-os pelo uso dos *':'*. Bom nos sabemos que agora temos uma lista de locais onde o sistema pode procurar os arquivos, mas e como ele os acha? A partir desta lista, ele vai vasculhando cada diretório até achar o arquivo a ser executado, ou seja, quando utiizarmos o comando *'tar'*, o sistema ira vasculhar cada diretório até chegar no diretório *'/bin'* da variavel *PATH* e assim encontrar o arquivo a ser executado.

### Principais Comandos Linux

  Nesta seção iremos discutir e exemplificar os principais comandos linux pra conseguirmos navegar e avançar nos nossos estudos. Vamos começar com os dois comandos mais importantes de navegação no linux, os comandos *cd* e *ls*.
  
 #### Comando *cd*
  
  O comando *cd* é o comando que possibilida a navegação entre diretórios no windows. Sua sintaxe é extremamente simples, usamos o comando seguido de um diretório que desejamos ir, da seguinte maneiroa:
  
  ```
  cd /home
  ```
  Supondo que estivessemos no diretório raiz do windows, neste momento teriamos avançado para a pasta/diretório home. Caso você não entenda o que é o diretório raiz, vou colocar aqui uma imagem que demonstra a estrutura básica dos diretórios no Linux que eu retirei do site [linux training academy](https://www.linuxtrainingacademy.com/wp-content/uploads/2014/03/linux-directory-tree.jpg).
  ![Estrutura de diretórios](https://www.linuxtrainingacademy.com/book/)
  
  Como podemos notar, o diretório home está dentro do diretório '/', que é o diretório que chamamos de raiz, e dentro do diretório home temos *jason* e *pat*, que representam os diretórios dos usuários existentes no computador. Mas voltemos ao comando *cd* nós nos movemos da pasta '/' para a pasta */home*, podemos dizer que nós descemos um nível na nossa arvoré de diretórios, casso quissemos subir um nível e voltar para a pasta '/' podemos utilizar:
  
```
cd ..
```
  
  Este comando faz com que agora estejamos no diretório '/', que é o diretório pai do nosso "/home", portando este comando sempre retorna ao diretório pai de onde você digita-lo. Mas agora vamos nos mover até o diretório *documents* (caminho: */home/jason/Documents*), existem duas formas de nós chegarmos até lá com o comanod *cd*, utilizando o caminho relativo e o caminho absoluto.
  O caminho absoluto é o mais fácil de entendermos, ele é o caminnho completo da raiz até o nosso destino, por exemplo, o caminho absoluto  de *Documents* é */home/jason/Documents*, então para chegar até o nosso destino precisariamos digitar no terminal apenas:
  
```
cd /home/jason/Documents
```

  Já o caminho relativo, como o próprio nome sujere, vai depender de onde você está na árvore. O caminho relativo é o caminho da sua posição até o seu destino, desta forma, qual seria o caminho relativo de *Documents* para *Music*? Seria necessário que retornassemos até o diretório pais de *Documents* e depois fossemos até *music*. Algo como:

```
cd ../Music
```
  É um pouco mais simples chegar a um diretório por caminho absoluto, porém é extremamente inviável ficar decorando o caminho dos diretórios, por isso usamos muito mais o caminho relativo e muitas vezes um diretório por vez, onde entramos numa pasta, vemos o seu conteúdo e decidimos se estamos indo pro local certo ou não. Por exemplo, poderiamos ter ido até o diretório *Documents* por passo a passso:
  
```
cd /
cd home
cd jason
cd Documents
```
  Dessa forma fomos diretório por diretório até chegar no nosso destino. Existem alguns simbolos que ajudam a dar dinamicidade na navegão, basta escrever na frente de *cd* por exemplo:
  * / para navegar diretamente até o diretório raiz.
  * ~ para navegar diretamente até o diretório *home* do usuário atual.
  * - para voltar ao último diretório em que esteve (esse fica pra você testar e atiçar a curiosidade).
  
#### Comando *ls*

  Este é o comando de listagem de conteúdo, utilizamos ele para podermos ver os arquivos dentro de uma pasta (neste momento traremos tudo como arquivos, os diretórios/pastas serão arquivos do tipo diretório/pasta). Sua sintaxe também é bem simples, basta digitar *ls* no terminal que ele trará os resultados. Porém existem formas de refinar sua busca, ou exibir mais conteúdo sobre os arquivos encontrados, para isso vamos acrescentar alguns caracteres (chamaremos de opções) na frente do nosso comando, por exemplo:
  * ls -a: Exibe também os arquivos ocultos na saída (aqui, arquivos ocultos são os arquivos que tem sou nome iniciando com '.' (ponto), via de regra o comando ls não os exibe, com está opção, eles passam a ser visiveis).
  * ls -l: Exibe o conteúdo em forma de uma lista e com 9 colunas (são muitas mas vamos falar delas), da esquerda para a direita elas nos informam:
    1. Tipo de arquivo e permissões.
    2. Usuário dono do arquivo.
    3. Grupo dono do arquivo.
    4. Tamanho em BYTES do arquivo.
    5. Os próximos 3 formam juntos a data da ultima modificação sendo então:
       1. Mês
       2. Dia
       3. Hora e minuto
    6. Nome do arquivo.
  * ls -lh: exibe o mesmo conteúdo de ls -l, porém com a coluna de tamanho em bytes se ajustando para exibir em KiloBytes, MegaBytes e etc, quando necessário
  * ls -r: acessa de forma recursiva o conteúdo do diretório, mostando o contéudo dos diretórios filhos também.
  * podemos usar o ls combinando vários dessas opções, por exemplo, ls -lhar, vai exibir todos os conteúdos, inclusive os ocultos, em formato de lista, com o tamanho dos arquivos sendo adapatados quando necessário e de todos os diretórios subsequentes ao que se encontra.
  * A opção -t faz com que a lista seja ordenada pela data de modificação, da mais antiga para a mais recente, pode ser misturada com outros comando, por exemplo ls -ltr
  * Por fim, podemos passar também um diretório para o comando ls, por exemplo, ls -ltr /home, iremos exbir o conteúdo da pasta home mesmo não estando localizado neste diretório.
  Com isso podemos navegar pelo terminal do linux e facilitar o andamento do curso a seguir, então vamos lá!
  
  #### Comandos sequênciais
    
  Existem formas de executar comando de forma sequêncial no Linux, de forma a executarmos vários comandos em uma única linha de código, para isso nós usamos os caracteres ; (ponto e vírgula), || (pipe pipe) ou && (E comercial, e comercial). Qual a diferença de cada um deles, com o uso do ; os comandos são executados sem se importar com a sáida do comando anterior
    
```
cd /home/usuario/Desktop; ls -ltr
```

  Já ao usarmos || ou && significa que vamos impor condições para execurtarmos os comandos seguintes, de que forma? Quando usamos || nós só irememos executar o segundo comando, caso o primeiro retorne erro. E com && comerciais, será justamente o contrário, só executara caso o primeiro comando tenha sucesso.

``` 
cd /Diretorio_Inexistente || echo "Diretório não encontrado"
cd /home && ls -ltrh  
```
  
  O primeiro comando é um exemplo de que como utilizar ||, tente executar e note que o terminal irá retornar um erro de que não encontrou um arquio ou diretório com o nome e depois exibiu a mensagem que escremos com o comando *echo*, caso queira trocar por || por && neste exemplo, irá ver que o retorno será somente a mensagem de erro do linux. Já no segundo exemplo, temos uma forma de utlizar && para realizar comandos sequênciais, ao usar, verá que foi redirecionado ao diretório */home* e então foi listado seu conteúdo. Desta forma conseguimos executar muitos comundos de forma mais ágil, ao invés de executarmos um, esperar o retorno, executarmos outro.
  
### Buscando Ajuda

  O próprio S.O. tem documentação sobre os comandos, e nesta seçao vamos apresentar algumas formas de como utilizar essa documentação para entender os comandos. Entre os comandos que aprenderemos temos o *man, o *whatis*, *apropos* e a opção *--help*.
  
##### O Comando *man*

  É um comando para exibir um manual acerta do comando que deseja, usamos ele *man* e o comando que queremos ver o manual:
  
```
man ls
```
  Mas agora temos um manual dizendo o que o comando faz e opções que podemos acrescentar ao comando. Para navegar nas informações que apareceram, utilize *page down* para descer uma página, *page up* para subir uma página e as setas do teclado, para sair da visualização, pressione *q*. Outra forma de utilizar o man é com a opção *-k*, onde passamos uma *string* de busca e ele nos retornará uma lista de comandos que estejam relacionados à *string* de busca, dessa forma:
  
 ```
man -k system
```

  Outra forma de executar a mesma coisa é trocar *man -k* por *apropos"
  
#### O Comando *whatis*
  
  Funciona de forma semelhante ao comando *man -k*, porém, aqui ao invés de pesquisarmos por algo e econtrar um comando, nós pesquisamos o comando e ele nos retorna uma breve descrição, exemplo:

```
whatis ls
```
#### A Opção *--help*
  
  Todo comando possui está opção, ela é como uma versão simplificada do *man* e exibe uma documentação resumida e foca nas opções que podemos acrescentar o comando, seguido de uma descrição, muito recomandado para quando queremos sanar uma pequena dúvida e de forma rápida de um comando, sua sintaxe é "comando -- help", exemplo:
  
```
ls --help
cd --help
```

#### O Comando *alias*
  Usamos para criar atalhos e vamos encontrar muitas vezes comandos que já estão disponíveis com um *alias*, inclusive o próprio *ls* vem algumas vezes como um alias de uma opção mais avançada do *ls*. Mas é um comando bem útil, já que assim consiguimos "encurtar" comandos muito longo. Comumente ao digitarmos somente '*alias*' no *shell*. Mas vamos ao como criar:
  
 ```
 alias NomeAtalho='comando a ser executado'
 ```
  Mas vale lembrar que isso irá criar um atalho temporário, caso feche o *shell* irá perder o atalho, para tornar definitivo, terá que adicionar em um arquivo, o *.bashrc*. Para isso acesso o diretório */home*, e digite: 

```
vi .bashrc
```
  Aqui você ira inserir o comando do *alias* e depois de salvar o arquivo digite no *shell*:
  
```
source .bashrc
```
  Agora todos os seus atalhos estarão salvos permanentemente, ou até que você os altere ou exclua.
  
 #### O comando *which*
  É o comando que localiza o arquivo de execução dos programas externos que estão instalados no nosso sistema. A busca é feita a partir do diretório raiz. Vamos ao exemplo:
  
 ```
 which echo
```
  O retorno será */bin/echo* 
  
#### *Quoting*
  Aqui defineremos como o uso de certos caracteres para de certa forma proteger outros caracteres. Alguns caracteres reprensentam funções dentro de *shell*, como \* (asterisco), $ (cifrão), \` (crase) e \ (barra inversa). Os caracteres que vamos ver para realizar essa proteção são as " (aspas duplas), ' (aspas simples ou apóstrofo) e a \(barra inversa). Vamos a algumas diferenças entre cada um desses caracteres. A ' (aspas simples) protege todos os caracteres, sem exceção. As " (aspas duplas) protegem quase todos os caracteres, exceto o $, \` (crase) e \ (barra inversa). Já \ (barra inversa) protege somente o próximo caractere, ou seja o da direita. Vamos a alguns exemplos: `echo *` isso somente irá retornar todos o conteúdo do diretório, semelhante ao comando `ls`. Mas caso usemos as aspas duplas por exemplo: `echo "*"`, será impresso somente o asterisco na tela.  
