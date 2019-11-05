# Principais comandos do GNU e UNIX
Esta secção é destinada a exemplificar e discutir os principais comandos dos sistemas operacionais linux, independente de sua distribuição.

### O que é um comando?
Podemos definir comandos como **palavras de ação** do Sistema operacional, onde executaremos uma determinada ação para a palavra que for escrita no terminal.
Podemos ter alguns tipos de comandos:
* Comando interno do *shell*
* Programa externo

##### Comando interno do *shell*
Comandos internos do *shell*, são ações que executamos de forma nativa no terminal, ou seja, comandos que são predefinidos no *shell* do seu Sistema Operacional (S.O.) e executam ações também já definidas. como por exemplo o comando *'echo'*, que escreve algo na sua saída padrão.

```
echo "Bem vindo!"
```

#### Programa externo
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
