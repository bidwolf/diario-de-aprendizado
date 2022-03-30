# Introdução

Este é um resumo de aprendizado referente ao livro **"Javascript the definitive Guide"** por David Flanagan
em sua 6ª edição sobre Javascript Uma ótima recomendação para aqueles que desejam aprender a fundo os aspectos da linguagem
javascript nos padrões ES5.

## Características da linguagem

Javascript é repleto de características que merecem destaque, e que obviamente devem ser conhecidas pelos desenvolvedores
para que suas fraquezas e forças estejam bem definidas, pois, esses pontos podem definir se javascript é a melhor linguagem a ser
utilizada no desenvolvimento do projeto que o programador está envolvido.

### Tipos em Javascript

Em Javascript existem 5 tipos primitivos, sendo eles:

* _Number_:  Que contempla os tipos numéricos, não diferenciando tipos inteiros ou tipos flutuantes.

* _String_:  Que contempla os tipos de texto, e podem ser declarados entre "", '' ou ``.

* _Boolean_: Que contempla os tipos lógicos, _true_ e _false_.

* _Object_:  Que é um conjunto de propriedades definidos por nome-valor sendo esses conjuntos nome-valor, ordenados ou não.

* _null_: Que é uma palavra reservada que é usada para indicar falta de referência, ou referência nula a um objeto (nenhum objeto aqui=null).

* _undefined_: Tem significado parecido com null, mas é bem mais fundamental, este indica ausência de valor( valor indefinido).

#### Como estão agrupados

Os tipos podem ser agrupados em :

* Primitivos e objetos
* Com métodos e sem métodos
* mutáveis (objetos) e imutáveis(tipos primitivos)
* Comparados por valor(tipos primitivos),comparação por referência (objetos).

Sendo que, objetos são mutáveis, mas os outros tipos primitivos não, todos os tipos excetuando null e undefined possuem métodos em seus objetos wrapper(null e undefined não possuem objetos empacotadores).

### Linguagem não tipada

Dizer que uma linguagem é não tipada, não quer dizer que não existam tipos primitivos na linguagem, e sim que ao definir _variáveis_
não é necessário dizer para o interpretador de código javascript, o tipo da variável atribuído, o próprio interpretador é capaz de
determinar qual o tipo primitivo relacionado a variável, ao utilizar certas _expressões e operadores_.

```js

var numero=6; //cria uma variável que contém o número seis
typeOf(numero); // -> number
numero="6";// modifica o valor da variável para uma string contendo o caractere 6
typeOf(numero);//-> string

```

### Escopo de variáveis

São definidas como a região do código onde se declara e acessa variáveis.
Em javascript existem basicamente dois tipos de escopo, o escopo _local_ e o escopo _global_.

#### Escopo local

O escopo local existe apenas dentro do corpo de funções não sendo possível acessar suas propriedades fora dela.

Variáveis em escopo local com mesmo nome que variáveis de escopo global ocultam as globais enquanto o interpretador estiver analisando o escopo local.

Também é possível aninhamento de escopos, de forma que cada função aninhada possua seu próprio escopo, e a nível de comparação
a função mais exterior interage com a função interior como se fosse um escopo global.

```js

var globalScope="global" // declara uma variável global que não pode ser deletada com o operador delete
function localizarEscopo(){
  var globalScope="local"; // declara uma variável local que oculta a variável global enquanto o interpretador estiver nesse escopo
  var localScope="escopo local exterior";
  function localizarEscopo2(){
    var localScope="escopo local aninhado";
    return localScope;
  }
  console.log(localizarEscopo2());
  console.log(localScope);
  return globalScope;
  }
console.log(localizarEscopo());
console.log(globalScope);

```

Você pode pensar nas variáveis locais como propriedades do objeto relacionado à chamada da função (registro declarado do ambiente de execução).

#### Escopo global

O escopo global, também referido como objeto global ou window, é o escopo superior do programa js, nele se encontram
todas as definições de tipos primitivos, constantes e classes predefinidas que não podem ser excluídas ou
editadas na execução do programa.

Também nela estão contidas todas as variáveis declaradas pelo programador sem as palavras
reservada var ou let, ou variáveis var declaradas no escopo global. Elas são criadas no momento em que o interpretador inicia a execução ou o navegador carrega uma nova página.

O objeto global pode ser acessado através da palavra reservada _this_ (this pode se referir a outra coisa em um paradigma de orientação a objetos).

Variáveis declaradas sem var são globais mas podem ser deletadas ou editadas, ao contrário das variáveis globais convencionais.
Além disso não é possível sobrescrever variáveis globais sem var, utilizando instruções de declaração de variável com var,let ou const.

```js

var globalScope="global" // declara uma variável global que não pode ser deletada com o operador delete.
var editableGlobal="global editável"
function localizaEscopo(){
  var globalScope="local"; // declara uma variável local que oculta a variável global enquanto o interpretador estiver nesse escopo.
  var editableGlobal="escopo global editada"; // não edita a variável global, apenas cria uma variável local com mesmo nome.
  return [globalScope,editableGlobal;
  }
console.log(localizaEscopo2()); // -> ["local","global editável"]
console.log([globalScope,editableGlobal]);// -> "global","global editável"
function localizaEscopo2(){
  var globalScope="local"; // declara uma variável local que oculta a variável global enquanto o interpretador estiver nesse escopo.
  editableGlobal="escopo global "; //  edita a variável global, sobrescrevendo-a.
  return [globalScope,editableGlobal;
  }
  
console.log(localizaEscopo2()); // -> ["local","global editável "]
console.log([globalScope,editableGlobal]); // -> "global","global editável "

```

Variáveis globais são definidas como propriedades do objeto global, fato que pode ser comprovado ao lançar console.log(this) no ambiente de execução.

#### Escopo de bloco

Originalmente javascript não possui escopo de bloco, ou seja blocos de instrução não podem possuir variáveis visíveis apenas em seu bloco, mas isso é da ES5 pra trás, a partir da ES6, com a criação a expressão de declaração de variável usando a palavra reservada _let_ podemos utilizar esse recurso útil para nós programadores.

### Encadeamento de escopo

Javascript é uma linguagem de escopo léxico onde o escopo de uma variável pode ser considerado o conjunto de linhas de código para as quais a variável está definida. GLobal-> pra todo mundo, Local -> para a função ou funções aninhadas, bloco -> para o bloco de instruções pertencente.

Mas Podemos pensar nas variáveis locais como propriedades de algum tipo de objeto definido pela implementação, pensando em cada trecho de código com um encadeamento de escopo associado. Esse encadeamento é uma lista que define as variáveis que estão no escopo para esse código.

Quando o interpretador  precisa pesquisar o valor de uma variável(solução de variável), ele começa examinando o primeiro objeto do encadeamento, e se  ele tiver a propriedade com o nome da variável, então o valor dessa propriedade é usado. Se não ele passa para o encadeamento de escopo anterior, e se não houver nenhuma propriedade com o nome da variável no programa js, então js lança um reference error.

Ou seja, quando criamos um programa, ele instancia o objeto global e inicializa suas propriedades(acima citadas) e adiciona em suas propriedades uma propriedade que referencia seu escopo. Quando criamos uma função ele cria uma propriedade de escopo para essa função também onde a primeira posição é referente as variáveis declaradas no seu escopo e a segunda é do escopo global e em funções aninhadas também, e por ai vai.

**OBS** Funções aninhadas são instanciadas toda vez que a função anterior é chamada, o que significa que na prática, apesar do conteúdo das funções aninhadas serem os mesmos, cada instância é ligeiramente diferente da outra pois sua propriedade de encadeamento de escopo muda em cada chamada.
