# Javascript básico
Este é um resumo de aprendizado referente aos capítulos 1-4 do livro **"Javascript the definitive Guide"** por David Flanagan
em sua 6ª edição sobre Javascript Uma ótima recomendação para aqueles que desejam aprender a fundo os aspectos da linguagem 
javascript nos padrões ES5.

## Características da linguagem
Javascript é repleto de características que merecem destaque, e que obviamente devem ser conhecidas pelos desenvolvedores
para que suas fraquezas e forças estejam bem definidas, pois, esses pontos podem definir se javascript é a melhor linguagem a ser
utilizada no desenvolvimento do projeto que o programador está envolvido.

### Tipos primitivos
Em Javascript existem 5 tipos primitivos, sendo eles:
* _Number_:  Que contempla os tipos numéricos, não diferenciando tipos inteiros ou tipos flutuantes.
* _String_:  Que contempla os tipos de texto, e podem ser declarados entre "", '' ou ``.
* _Boolean_: Que contempla os tipos lógicos, _true_ e _false_.
* _Object_:  Que é um conjunto de propriedades definidos por nome-valor sendo esses conjuntos nome-valor, ordenados ou não.
* _null_: Que é uma palavra reservada que é usada para indicar falta de referência, ou referência nula a um objeto (nenhum objeto aqui=null).
* _undefined_: Tem significado parecido com null, mas é bem mais fundamental, este indica ausência de valor( valor indefinido).

### Linguagem não tipada
Dizer que uma linguagem é não tipada, não quer dizer que não existam tipos primitivos na linguagem, e sim que ao definir *variáveis*
não é necessário dizer para o interpretador de código javascript, o tipo da variável atribuido, o próprio interpretador é capaz de
determinar qual o tipo primitivo relacionado a variável, ao utilizar certas _expressões e operadores_.
```js
var numero=6; //cria uma variável que contém o número seis
typeof(numero); // -> number
numero="6";// modifica o valor da variável para uma string contendo o caractere 6
typeof(numero);//-> string
```
