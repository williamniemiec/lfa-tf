
# Automaton reader
![](https://github.com/williamniemiec/Automaton-Reader/blob/master/media/automatonReader.png?raw=true)


This is a project about automata. It consists of an application that allows you to perform certain operations on automata.

## Warnings
Unfortunately I didn't have time to develop a GUI for the application. If you like the project and know how to create a Python GUI feel free to develop one. Furthermore, if you know a better algorithm that those that this project uses, do not hesitate to commit it to the project.
In addiction, <b>no automaton can contain the symbol '&' in the name of its states</b>, as it is a reserved symbol of the application ('&' represents the empty word and '&&' symbolizes the state artificially created by the application [function 'convertDFAToTtf'])

## Available methods
- Display automaton information
- Generate regular grammar from a DFA
- Generate minimal DFA
- Compare two automata and see if they are equivalent
- Given a list of words, check if they are accepted by the automaton

## File formats
#### [in] Automaton
<pre>
&lt;M&gt;=({&lt;q0&gt;,...,&lt;qn&gt;},{&lt;s1&gt;,...,&lt;sn&gt;},&lt;ini&gt;,{ &lt;f0&gt;,...,&lt;fn&gt;})
Prog
(&lt;q0&gt;,&lt;s1&gt;)=&lt;q1&gt;
...
(&lt;qn&gt;,&lt;sn&gt;)=&lt;q0&gt;
where:
&lt;M&gt;: automaton name;
&lt;qi&gt;: for 0 &le; i &le; n, with n &isin; N and n &ge; 0, represents a state of the automaton;
&lt;si&gt;: for 1 &le; i &le; n, with n &isin; N and n &ge; 1, represents a symbol of the language alphabet recognized by the automaton;
&lt;ini&gt;: indicates the initial state of the automaton, where ini is a state of the automaton;
&lt;fi&gt;: for 0 &le; i &le; n, with n &isin; N and n &ge; 0, represents a final state of the automaton, where fi is a state of the automaton;
(&lt;qi&gt;,&lt;si&gt;) =&lt; qj &gt;: describes the transition function applied to a qi state and an input symbol si that takes computing to a qj state.

<blockquote>
<h2>Example</h2>
AUTOMATON=({q0,q1,q2,q3},{a,b},q0,{q1,q3})
Prog
(q0,a)=q1
(q0,b)=q2
(q1,b)=q2
(q2,a)=q3
(q2,a)=q2
(q3,a)=q3
(q3,b)=q2
</blockquote>
</pre>
#### [in] Words file
Words files must meet in the following standards:
- Each word must be on a different line
- Each symbol must be separated by spaces or quotes or commas
- It is possible for a symbol to contain more than one character - to separate one symbol from another use a separator mentioned above
<pre>
<blockquote>
<h2>Example</h2>
"on""off"
"on""clean""batLow""ecoBat""off"
a b c
a,b,c
'a''b''c'
"a""b""c"
"a" "b" "c"
</blockquote>
</pre>
#### [out] Regular grammar
When generating the grammar of an automaton, the output file will contain the following format:
<pre>
&lt;G&gt;=({&lt;V0&gt;,...,&lt;Vn&gt;},{&lt;s1&gt;,...,&lt;sn&gt;},&lt;S&gt;,&lt;Prod&gt;)
&lt;Prod&gt;
&lt;S&gt; -&gt; &lt;s1&gt; &lt;V0&gt;
...
&lt;Vn&gt; -&gt; &lt;sn&gt; &lt;V2&gt;
where:
&lt;G&gt;: name given to RG;
&lt;Vi&gt;: for 0 &le; i &le; n, with n &isin; N and n &ge; 0, represents a RG variable;
&lt;si&gt;: for 1 &le; i &le; n, with n &isin; N and n &ge; 1, represents a symbol of the alphabet of the language generated by the RG (terminals);
&lt;S&gt;: indicates the initial symbol, such that S is a RG variable;
&lt;Prod&gt;: is the name of the RG production set;
&lt;Vi&gt; -&gt; &lt;si&gt;&lt;Vj&gt;: describes the production that replaces the variable Vi by the symbol si followed by the variable Vj. Symbol '&' indicates empty production.

<blockquote>
<h2>Example</h2>
G = ({S, A, B},{a,b},S,P)
P
S -&gt; a A
A -&gt; a A
A -&gt; b B
B -&gt; &
</blockquote>
</pre>

## How the application works?
To run the application, just run the file <code>releases/automaton.exe</code>
After executing the file, the program's initial menu will open. Choosing the option to open an automaton, a window will open to open the file containing the automaton (must be in the format specified above).

![](https://github.com/williamniemiec/Automaton-Reader/blob/master/media/1.InitialMenu.png?raw=true)

 Once the file is opened, the main program menu will open, as shown in the image below.
 
![](https://github.com/williamniemiec/Automaton-Reader/blob/master/media/2.MainMenu.png?raw=true)

Now just choose the desired option.


## Project organization

### /
|Name | Type| Function
|------- | --- | ----
| releases | Directory| contains project executables
| media | Directory| Contains photos used in readme&#46;md
| examples | Directory| Contains files that can be used to test the application (contains automata and files with words)
| src | Directory| Contains the classes responsible for running the application
| tests | Directory | Contains application class tests

### /tests
|Name | Type | Function
|------- | --- | ----
| media | Directory | Contains the files used in the tests (automata and word file)
| AutomatonFileManagerTest&#46;py | File | Contains tests related to the 'AutomatonFileManager' class
| AutomatonListHelperTest&#46;py | File | Contains tests related to the 'AutomatonListHelper' class
| AutomatonTest&#46;py | File | Contains tests related to the 'Automaton' class

## References
- [Paulo Blauth Menezes - Linguagens Formais e Autômatos: Volume 3 da Série Livros Didáticos Informática UFRGS](https://books.google.com.br/books?id=OEBJ5ga7nvUC&dq=minimiza%C3%A7%C3%A3o+de+automato+ufrgs&hl=pt-BR&source=gbs_navlinks_s)
- [Prof. Juan Moises Mauricio Villanueva - Conversão de Autômatos Finitos Não Determinísticos (AFND) para
Autômatos Finitos Determinísticos (AFD) ](http://www.cear.ufpb.br/juan/wp-content/uploads/2016/08/Aula-4b-Convers%C3%A3o-de-AFND-para-AFD.pdf)

 
<hr>

# --{ Português }--


Esse é um projeto sobre autômatos. Consiste em uma aplicação que permite realizar certas operações sobre automatos

## Aviso
Por questões de tempo eu não desenvolvi uma interface gráfica para a aplicação; se você gostar do projeto e quiser desenvolver uma fique a vontade. Além disso, se você achar um algoritmo melhor do que aqueles que esse projeto utilize, não hesite em fazer um commit com ele.

Além disso, nenhum autômato pode conter o símbolo '&' no nome de seus estados, pois é um símbolo reservado da aplicação (& representa a palavra vazia e && simboliza estado criado artificialmente pela aplicação - função 'convertDFAToTtf')

## Métodos disponíveis
- Exibir informações do autômato
- Gerar gramática regular de um AFD
- Gerar AFD minimo
- Comparar dois automatos e ver se eles são equivalentes
- Dada uma lista de palavras, verifica se elas são aceitas pelo autômato

## Formato dos arquivos
#### [in] Automato
<pre>
&lt;M&gt;=({&lt;q0&gt;,...,&lt;qn&gt;},{&lt;s1&gt;,...,&lt;sn&gt;},&lt;ini&gt;,{ &lt;f0&gt;,...,&lt;fn&gt;})
Prog
(&lt;q0&gt;,&lt;s1&gt;)=&lt;q1&gt;
...
(&lt;qn&gt;,&lt;sn&gt;)=&lt;q0&gt;
onde:
&lt;M&gt;: nome dado ao autômato;
&lt;qi&gt;: para 0 &le; i &le; n, com n &isin; N e n &ge; 0, representa um estado do autômato;
&lt;si&gt;: para 1 &le; i &le; n, com n &isin; N e n &ge; 1, representa um símbolo do alfabeto da linguagem reconhecida pelo autômato;
&lt;ini&gt;: indica o estado inicial do autômato, sendo que ini é um estado do autômato;
&lt;fi&gt;: para 0 &le; i &le; n, com n &isin; N e n &ge; 0, representa um estado final do autômato, sendo que fi é um estado do autômato;
(&lt;qi&gt;,&lt;si&gt;)=&lt;qj&gt;: descreve a função programa aplicada a um estado qi e um símbolo de entrada si que leva a computação a um estado qj.

<blockquote>
<h2>Exemplo</h2>
AUTÔMATO=({q0,q1,q2;,q3},{a,b},q0,{q1,q3})
Prog
(q0,a)=q1
(q0,b)=q2
(q1,b)=q2
(q2,a)=q3
(q2,a)=q2
(q3,a)=q3
(q3,b)=q2
</blockquote>
</pre>
#### [in] Arquivo de palavras
Os arquivos de palavras devem estar no seguinte formato:
- Cada palavra deve estar em uma linha diferente
- Cada símbolo deve estar separado por espaço ou aspas ou vírgulas
- É possível que um símbolo contenha mais que um caracter - para separar um símbolo do outro usar um separador citado acima
<pre>
<blockquote>
<h2>Exemplo</h2>
"ligar""desligar"
"ligar""limpar""batFraca""ecoBat""desligar"
a b c
a,b,c
'a''b''c'
"a""b""c"
"a" "b" "c"
</blockquote>
</pre>
#### [out] Gramática regular
Ao gerar a gramática de um autômato, o arquivo de saída conterá o seguinte formato:
<pre>
&lt;G&gt;=({&lt;V0&gt;,...,&lt;Vn&gt;},{&lt;s1&gt;,...,&lt;sn&gt;},&lt;S&gt;,&lt;Prod&gt;)
&lt;Prod&gt;
&lt;S&gt; -&gt; &lt;s1&gt; &lt;V0&gt;
...
&lt;Vn&gt; -&gt; &lt;sn&gt; &lt;V2&gt;
onde:
&lt; G &gt;: nome dado a GR;
&lt; V i &gt;: para 0 &le; i &le; n, com n &isin; N e n &ge; 0, representa uma variável da GR;
&lt; si &gt;: para 1 &le; i &le; n, com n &isin; N e n &ge; 1, representa um símbolo do alfabeto da
linguagem gerada pela GR (terminais);
&lt; S &gt;: indica o símbolo inicial, tal que S é uma variável da GR;
&lt; Prod &gt;: é o nome do conjunto de produções da GR;
&lt; Vi &gt; -&gt; &lt; si &gt;&lt; Vj &gt;: descreve a produção que substitui a variável Vi pelo
símbolo si seguido da variável V j. Símbolo & indica produção vazia

<blockquote>
<h2>Exemplo</h2>
G = ({S, A, B},{a,b},S,P)
P
S -&gt; a A
A -&gt; a A
A -&gt; b B
B -&gt; &
</blockquote>
</pre>

## Como funciona?
Para executar a aplicação, basta executar o arquivo <code>releases/automaton.exe</code>
Após a execução do arquivo será aberto o menu inicial do programa. Escolhendo a opção de abrir um autômato será aberta uma janela para abrir o arquivo que contém o autômato (deve estar no formato especificado acima).

![](https://github.com/williamniemiec/Automaton-Reader/blob/master/media/1.InitialMenu.png?raw=true)

 Aberto o arquivo, será aberto o menu principal do programa, como mostra a imagem abaixo.
 
![](https://github.com/williamniemiec/Automaton-Reader/blob/master/media/2.MainMenu.png?raw=true)

Agora basta escolher a opção desejada.


## Organização do projeto
### /
|Nome | Tipo | Função
|------- | --- | ----
| releases | Diretório | Contém executáveis do projeto
| media | Diretório | Contém fotos usadas no readme&#46;md
| examples | Diretório | Contém arquivos que podem ser usados para testar a aplicação (contém automatos e arquivos com palavras)
| src | Diretório | Contém as classes responsáveis pelo funcionamento da aplicação
| tests | Diretório | Contém os testes das classes da aplicação

### /tests
|Nome | Tipo | Função
|------- | --- | ----
| media | Diretório | Contém os arquivos utilizados nos testes (autômatos e arquivo de palavras)
| AutomatonFileManagerTest&#46;py | Arquivo | Contém os testes relativos a classe 'AutomatonFileManager'
| AutomatonListHelperTest&#46;py | Arquivo | Contém os testes relativos a classe 'AutomatonListHelper'
| AutomatonTest&#46;py | Arquivo | Contém os testes relativos a classe 'Automaton'

## Referências
- [Paulo Blauth Menezes - Linguagens Formais e Autômatos: Volume 3 da Série Livros Didáticos Informática UFRGS](https://books.google.com.br/books?id=OEBJ5ga7nvUC&dq=minimiza%C3%A7%C3%A3o+de+automato+ufrgs&hl=pt-BR&source=gbs_navlinks_s)
- [Prof. Juan Moises Mauricio Villanueva - Conversão de Autômatos Finitos Não Determinísticos (AFND) para
Autômatos Finitos Determinísticos (AFD) ](http://www.cear.ufpb.br/juan/wp-content/uploads/2016/08/Aula-4b-Convers%C3%A3o-de-AFND-para-AFD.pdf)
