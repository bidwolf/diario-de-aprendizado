Nas linguagens de programação, entende-se como tipos de variáveis, como sendo formas diferentes de se compreender e interpretar os dados
fornecidos pelo computador e pelos programas criados pelos programadores, esses dados nada mais são que conjuntos de informações binárias 
que são convertidas em padrões estabelecidos pela linguagem de programação para definir o que é um determinado tipo de dado.
Nesse sentido, convém a nós, estudantes de programação nos reiterar na *Forma como o Javascript lida com seus tipos de dados*.
## Tipos de variáveis em Javascript

Como foi citado no post [Básico de Javascript](https://bidwolf.github.io/diario-de-aprendizado/2021/07/28/Javascript-b%C3%A1sico.html)
Javascript é uma linguagem não tipada, o que significa dizer que não é necessário especificar explicitamente o tipo de uma variável como
é feito em c, ou java, pois o próprio interpretador de código Javascript já é capaz de deduzir o tipo de variável se está querendo utilizar naquele determinado momento. O que nos leva a seguinte questão:

### Como estão classificados os tipos de dados em Javascript

Os tipos de dados em javascript podem ser classificados tipos primitivos e objetos, onde tipos primitivos em geral, são imutáveis, e seus dados são comparados por valor. Já objetos, possuem maior flexiblidade, são mutáveis, possuem métodos, e são comparados por referência.

Tipo de dado| Flexiblidade | Possui métodos | Comparação
:---:|:---:|:---:|:---:
Number|Imutável|*true*|Por Valor
Boolean|Imutável|*true*|Por Valor
String|Imutável|*true*|Por Valor
Null|Imutável|*false*|Por Valor
Undefined|Imutável|*false*|Por Valor
Object|Mutável|true|Por referência

### O que é um tipo imutável

Dizer que um dado é imutável significa na verdade dizer que não é possível alterar o significado de uma expressão, por exemplo, dizer que 3 agora vale 5, não faz sentido, mas no caso de strings pode-se pensar que faria sentido alterar uma letra de uma palavra, mas Javascript o trata como tipo imutável, e qualquer tentativa de alterar o valor de seu conteúdo falha silenciosamente.
ex:

~~~js

var palavra="banana";
palavra[2]='t'; // falha silenciosamente
palavra // -> banana
~~~ 

Isso acontece por que em Javascript ao invés de tentar fazer uma alteração diretamente na variável, o que ele faz é criar uma instância de um objeto empacotador do tipo que se está alterando, a alteração então ocorre em um objeto 'temporário' e a informação não persiste.
todos os tipos excetuando null e undefined possuem métodos empacotadores(Wrappers) que criam uma instância de objeto com métodos únicos para cada tipo, por isso que podemos utilizar alguns métodos herdados de Object.prototype ou métodos como toUpperCase das Strings.
