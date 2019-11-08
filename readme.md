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
  
 #### Comando cd
  
  O comando *cd* é o comando que possibilida a navegação entre diretórios no windows. Sua sintaxe é extremamente simples, usamos o comando seguido de um diretório que desejamos ir, da seguinte maneiroa:
  
  ```
  cd /home
  ```
  Supondo que estivessemos no diretório raiz do windows, neste momento teriamos avançado para a pasta/diretório home. Caso você não entenda o que é o diretório raiz, vou colocar aqui uma imagem que demonstra a estrutura básica dos diretórios no Linux que eu retirei do site [linux training academy](https://www.linuxtrainingacademy.com/linux-directory-structure-and-file-system-hierarchy/).
  ![Estrutura de diretórios](/imagens/linux-directory-tree.jpg)
  
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
  
#### Comando ls

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
  
  
