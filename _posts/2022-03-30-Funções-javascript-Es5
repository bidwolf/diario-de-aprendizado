# Capítulo 8 - Funções

Uma função nada mais é que um bloco de código Js definido uma vez e que pode ser executado quantas vezes forem requisitadas. As funções também são conhecidas como *sub-rotinas* ou *procedimentos*, e são *Parametrizadas*, onde ao se definir uma função é possível atribuir um identificador a ela, passar uma lista de identificadores (parâmetros) que funcionarão como variáveis locais para o corpo da função, e podem ou não possuir um valor de *retorno*.

O valor de retorno torna-se o valor da expressão da chamada da função.

ex:

```js
let somar=function(numero,incremento){
    return numero+incremento;
}
somar(3,4);// retorna 7
//também pode ser escrito como:
let subtrair=(numero,decremento)=>numero+decremento;
subtrair(3,4);// retorna 7
//Outra forma:
function soma(numero,incremento){
    return numero+incremento;
}
soma(3,4);// retorna 7
// As vezes as funções são definidas e chamadas imediatamente
let sixPlusThree((x,y)=>(x*y))(6,3);
```

As definições de funções podem ser aninhadas em outras definições de funções e essas têm acesso a qualquer variável que estejam no escopo onde são definidas.

Lembrando, em javascript, qualquer declaração de função é **içada** para o início do programa. Entretanto, o mesmo não vale para funções definidas como expressões. Nesse caso, apenas a variável que as contém é içada, mas o conteúdo atribuído não. O que pode causar erro de tipo.

## Nomes de funções

Nomes de funções devem ser bem escolhidos para melhorar a legibilidade do código, e por consequência, sua legibilidade, e em geral devem ser verbos. Funções que devem ser internas ou ocultas(e não parte de uma API pública) às vezes recebem nomes que começam com sublinhado.

## Chamando Funções

O código js contido no corpo de uma função não é executado até que a mesma seja chamada, e as funções podem ser chamadas de ***quatro formas***:

* Como funções

* Como métodos

* Como Construtoras

* Indiretamente utilizando métodos ***call( )*** e ***apply( )*** do objeto global.

### Chamada de função

As funções são chamadas como funções ou como métodos utilizando expressões de invocação, que consiste em uma expressão de função avaliada como um objeto função, seguida de um parêntese de abertura, uma lista de argumentos separadas por virgula e um parêntese de fechamento.

Se a expressão de função é uma expressão de acesso à propriedade(a função é propriedade de um objeto ou elemento de um array) então ela é uma invocação de um método.

Na chamada, cada expressão de argumento é avaliado e então se tornam argumentos da função que se tornam variáveis locais do escopo da função.

Normalmente, as funções escritas para serem chamadas como funções não usam a palavra-chave ***this***.

### Chamada de método

Nada mais é que uma função definida como propriedade de um objeto, e diferem de uma chamada de função normal por causa do contexto da chamada.

As expressões de acesso à propriedade consistem em duas partes, objeto e um nome de propriedade. E nesse caso o objeto se torna o contexto da chamada e o corpo da função pode se referir a esse objeto usando a palavra-chave ***this***(palavra reservada importantíssima para POO).

Ao contrário das variáveis, a palavra ***this*** não possui escopo, e as funções aninhadas não herdam o valor de this em suas chamadoras.

Se uma função aninhada é chamada como método, seu valor de this é o objeto em que foi chamada. Se uma função aninhada é chamada como uma função, então this vai ser o objeto global ou undefined no modo restrito.

Se quiser armazenar o valor de this na função externa, é comum utilizar uma variável chamada **self**.

Exemplo:

`let self=this;`

### Chamada de construtora

Se uma chamada de função ou de método é precedida pela palavra-chave ***new***, então ela é uma chamada de função chamada de construtora.

```js
let valorDaAresta=2;
let quadrado = new Quadrado(valorDaAresta);
let figuraVazia = new Figura;// new Figura();
```

As chamadas de construtoras se diferem das chamadas de função e de método normais na forma que como tratam os argumentos, o contexto da chamada e o valor de retorno.

Se uma função construtora não possui parâmetros, então a chamada da função pode omitir os parênteses.

Uma chamada de construtora cria um novo objeto vazio e então faz com que esse objeto herde propriedades ***prototype*** da construtora. Funções construtoras se destinam a inicializar objetos, sendo que o objeto recém criado é utilizado como contexto da chamada, de modo que a função construtora possa se referir a ela com a palavra-chave ***this***.

*Dica:*

> Mesmo que a chamada da construtora pareça uma chamada de método, o objeto utilizado como contexto é o objeto recém criado.

```js

function Quadrado(lado){
    this.lado=lado;
}
Quadrado.prototype = {
    area : () => this.lado * this.lado,
    baricentro : new ponto(this.lado / 2 , this.lado / 2)
}
let baricentro = new Quadrado(3).baricentro;

```

As funções construtoras em geral usam a palavra-chave return.
Elas normalmente inicializam o novo objeto e então retornam implicitamente ao chegarem no final dos seus corpos. Nesse caso, o novo objeto é o valor da expressão de invocação da construtora. No entanto, se uma construtora usa explicitamente a instrução return para retornar um objeto, então esse objeto se torna o valor da expressão de invocação do construtor. Entretanto se return retornar um valor nulo ou um valor primitivo, então esse valor é ignorado.

### Chamada indireta

As funções são objetos, e como todo objeto, possuem métodos e propriedades, como exemplo de propriedade de funções, temos os argumentos da função, e como exemplo de método, estaremos relacionando às chamadas indiretas, que são os métodos ***apply*** ( ) e ***call*** ( ).
Esses dois métodos permitem especificar os argumentos da chamada.

* O método ***call*** ( ) utiliza sua própria lista de argumentos como argumentos para função, enquanto ***apply*** *( ) espera que um array de valores seja usado como argumentos.

## Argumentos e parâmetros de função

As definições de funções não especificam um tipo esperado para os parâmetros, e nem mesmo verificam a quantidade de argumentos passados, podem ser mais argumentos do que o pedido, ou menos. Entretanto é sim possível testar o tipo dos argumentos da função, caso seja necessário garantir que uma função não seja chamada com argumentos incompatíveis.

### Parâmetros opcionais

Em js na ES5, para criar funções com argumentos opcionais deve-se colocar-los por ultimo na lista de argumentos e também especificar que aquele parâmetro é opcional na definição da função para prevenir equívocos.

### Callee

Método das funções que se refere à função que está sendo executada no momento, o que é útil para permitir que funções não nomeadas chamem a si mesmas recursivamente.

```js
let factorial=(numero)=>numero*arguments.callee(numero-1);
```

### Caller

Esse método faz referência a função que a chamou, ou seja, dá acesso a pilha de chamada.

### Usando propriedades de funções como argumentos

Para casos em que se tem muitos argumentos possíveis em uma mesma função, fica difícil de lembrar a ordem dos argumentos passados para ela, e nesse caso convém utilizarmos propriedade de objeto como argumentos para que o programador não tenha que ler a documentação toda vez que tiver que utilizar essa função.

Podemos passar os argumentos como pares key/value em qualquer ordem, e para implementar esse estilo de chamada de método, devemos definir a função de modo a esperar um único objeto como argumento e fazer com que quem a utilize passem um objeto que defina os pares key/value exigidos.

```js
//Função difícil de lembrar dos parâmetros
function hardWebScrapper(pageName,inputSelector,buttonSelector,hasContentInPage){
    //implementação
}
// Não é necessário lembrar dos parâmetros
function webScrapper(config){
    hardWebScrapper(
        config.pageName,
        config.inputSelector || 'input',
        config.buttonSelector,
        config.hasContentInPage || false
    )
}
// Usando a função webScrapper
const Leroy = webScrapper({buttonSelector:'btn.btnInput',pageName:'Leroy Merlim',})
```

### Tipos de argumento

Os parâmetros de método em js não possui tipos declarados, e não é feita verificação de tipo nos valores passados para a função. Você pode ajudar a auto-documentação do seu código escolhendo nomes descritivos para argumentos de função e incluindo seus tipos como comentários.

Uma abordagem diferente sera aprendida quando estivermos aprendendo ***react.js***.

## Definindo suas próprias propriedades de funções

Em javascript, funções não são valores primitivos, e sim um tipo de objeto especializado, logo, eles podem possuir propriedades, e quando uma função precisa de uma variável "*estática*" cujo valor persiste entre as chamadas, muitas vezes é conveniente utilizar uma propriedade de uma função, em vez de congestionar o espaço de nomes definindo uma variável global.

Por exemplo, suponha que se queria escrever uma função que ao ser chamada , retorne um único valor inteiro. A função nunca deve retornar o mesmo valor duas vezes. Para conseguir isso, a função precisa monitorar os valores já retornados de forma que essa informação persista entre as chamadas de função.

Você poderia armazenar essa informação em uma variável global, mas isso não é necessário, já que é usada apenas pela própria função.
É melhor armazená-la em uma propriedade do objeto *Function*.

## Funções como espaço de nomes

Em **ES5** não havia forma de declarar variáveis com escopo léxico, de forma que as variáveis eram sempre declaradas utilizando `var`, o que não seria um problema, se elas não criassem variáveis globais quando estão fora do corpo de uma função. Essa característica de javascript se torna um problema quando você cria módulos que vão ser importados para outras aplicações, ou em javascript do lado do cliente, várias páginas web, que por sua vez podem possuir variáveis globais internas que provocariam resultados inesperados na sua aplicação.

Para solucionar esse problema, você caro gafanhoto deve se lembrar de ao invés de criar seus módulos js dentro de uma função, e então chamar essa função, tornando as variáveis globais, locais à função.

```js
function meuMódulo(){
    // O código do módulo
    // Todas as variáveis se tornam locais a essa função
    // Evitando assim variáveis globais
}
meuMódulo();
```

Também é possível utilizar uma função auto-executável, evitando inclusive a criação de uma variável em tese não utilizada para outro propósito.
Essa técnica é tão utilizada que se torna idiomática.

```js
(() => {
    //Código do módulo aqui
})();
```

A abertura e o fechamento dos parênteses é utilizada para evitar que o compilador interprete como uma instrução de declaração de função, e com o parêntese ele o reconhece como uma expressão de definição de função.

## Closures e propriedades de  função

Assim como a maioria das linguagens de programação modernas, javascript utiliza escopo léxico, onde as funções são executadas usando o escopo de variável que estava em vigor ao serem definidas e não o escopo de quando foram chamadas.
Para implementar escopo léxico, o estado interno de uma *function object* em js deve incluir não apenas o código da função mas também uma referência ao encadeamento de escopo concorrente. Essa combinação chamada de vínculos de variável, no qual as variáveis da função são solucionadas, é chamado de *closure* na literatura da ciência da computação.

Tecnicamente, todas as funções são closures em js, pois são objetos e possuem encadeamento de escopo associado. A maioria das funções é chamada usando o mesmo encadeamento de escopo que estava em vigor quando foi definida, e essa característica torna-se não tão relevante. As closures são interessantes quando são envolvidas em um encadeamento de escopo diferente do que estava em vigor quando foi definida.

Isso acontece mais comumente quando um function object aninhado é retornado da função dentro da qual foi definida.
Existem várias técnicas de programação poderosas que envolvem esse tipo de closures de função aninhada, e seu uso se tornou relativamente comum na programação js.

As closures podem parecer confusas quando você as encontra pela primeira vez, mas é importante entendê-las bem para utiliza-las com segurança.

Existem várias técnicas de programação poderosas que envolvem esse tipo de closure de função aninhada e seu uso se tornou relativamente comum na programação javascript.

No exemplo contido nesse diretório a função ***checarEscopo*** declara uma variável local e então define e chama a função **f** que retorna o valor dessa variável

Já na função checarEscopo2 temos exemplificado o conceito de closure, onde, não importa onde ***f*** é chamada, o encadeamento de escopo a que ela pertence que é levado em consideração, e nesse encadeamento, a variável escopo possui valor "escopo-local" pois essa captura os vínculos de variável local e o parâmetro da função externa dentro da qual são definidas.

## Call e Apply

Os métodos call() e apply() permitem chamar uma função indiretamente como se fosse um método de algum outro objeto.
O primeiro argumento de *call e apply* é o objeto em que a função será chamada: esse argumento é o contexto da chamada e se torna o valor da palavra-chave *this* dentro do corpo da função.

Para chamar uma função calcularPreçoReal() como um método do objeto produto sem passar argumento nenhum, você poderia usar call ou apply

```js

calcularPreçoReal.apply(produto);
calcularPreçoReal.call(produto);
```

A diferença entre eles aparece quando se adiciona argumentos, o primeiro argumento de call e apply se torna o valor de this, caso seja um valor primitivo que é substituído pelo objeto empacotador, caso seja `null` ou `undefined` e esteja no modo restrito, este se torna o objeto global.
Já os argumentos seguintes se tornam argumentos da função chamada, e no método call eles são passados de forma sequencial:

```js
calcularPreçoReal.call(produto,país,frete);
```

Enquanto que no método apply, é passado um array e objetos semelhantes a um array como argumento:

```js
let IRPJ = new Imposto(12);
let INPI = new Imposto(2,0.12);
let listaDeImpostos[INPI,IRPJ];
calcularPreçoReal.apply(produto,listaDeImpostos);

```

Se uma função é definida para aceitar um número arbitrário de argumentos, o método apply se sai melhor. Por exemplo para mostrar o valor máximo em um conjunto de valores, voce pode utilizar o método apply em conjunto com Math.max().

E a função trace() contida no exemplo do capítulo 8.7 recebe um objeto e um método, substituindo o método especificado por um método novo que empacota uma nova funcionalidade em torno do método original.

### O método bind()

O objetivo é vincular uma função a um objeto, e quando é chamado em uma função e um objeto é passado à ela o método retorna uma nova função. Chamar a nova função chama a função original como método de o. Os argumentos passados para a função são passados para a nova função são passados para a função original.

```js
function f(y){return this.x + y;}
let objeto = {x:2};
let g = f.bind(objeto);
console.log(g(2)) // imprime 4
```

O método *bind()* faz mais do que simplesmente vincular uma função a um objeto. Ele também faz aplicação parcial: os argumentos passados para bind() após o primeiro são vinculados junto com o valor de this.

A aplicação parcial as vezes é chamada de *currying*.

### A construtora Function()

As funções normalmente são definidas com a palavra-chave function, ou na forma de uma instrução de função ou de uma expressão de função literal. Mas as funções podem ser definidas com a construtora Function().Que cria uma função anônima  que não utiliza o escopo local criado por ela e sim o escopo exterior.

## Programação Funcional

As seções a seguir demonstram técnicas de programação funcional em js que se destinam a ser uma exploração para aumentar a conscientização sobre o poder das funções de js.

### Processamento de arrays utilizando funções

Suponha que temos um array de números e queremos calcular a média e o desvio padrão desses valores. Poderíamos fazer isso no estilo não funcional, como segue:

### Funções de alta ordem

Uma função de alta ordem é uma função que opera sobre funções, recebendo uma oou mais funções, recebendo uma ou mais funções como argumentos e retornando uma nova função:

```js
function not(f){
    return function(){
        let result=f.apply(this,arguments);
        return !result;
    };
    let isPar=(x)=>x%2==0;
    let isImpar=not(isPar);
    [1,2,3,4,5].every(isImpar)
}
```

A função not() anterior é uma função de alta ordem, pois recebe como argumento uma função e retorna outra função. Como outro exemplo, considere a função mapper contida no diretório ***lib/functionalExamples.js***

### Aplicação parcial de funções

O método bind() de uma função f retorna uma nova função que chama f em um contexto especificado e com um conjunto de argumentos especificado. Dizemos que ele vincula a função a um objeto e aplica os argumentos parcialmente. O método bind() são colocados no início da lista de argumentos passada para a função original. Mas também é possível aplicar parcialmente os argumentos da direita
