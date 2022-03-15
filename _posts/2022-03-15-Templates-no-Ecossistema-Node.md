# Templates no ecossistema Node

Este artigo fala sobre o capítulo 7 do livro ***Programação web com Node e Express*** que aborda como assunto principal o tema de templating no server side que hoje é um conceito que foi substituído na nossa área pelos frameworks front-end  utilizando ferramentas como ***Vue, Angular e React***.

## Contextualizando

A primeira coisa que você deve se perguntar, e com razão,  é :

* O que é templating pra que serve e porque eu deveria aprender se na introdução do artigo você já disse que é uma tecnologia ultrapassada?

### O que é Templating

O ***Templating*** nada mais é que uma técnica para a construção e formatação do conteúdo afim de exibi-lo para o usuário.

### Pra que serve

Para responder essa pergunta vamos a um exemplo:

Suponhamos que você tenha que criar diversos artigos para o seu blog, e entre um artigo e outro você repara uma coisa, existe um padrão na introdução de cada artigo que você escreve, e esse padrão está tão claro que em grande parte você apenas copia e cola essa parte do artigo e segue em frente.

Bom meu jovem gafanhoto, você acaba de descobrir o que um template busca solucionar : ***Reusabilidade***.

### Porque aprender

Para responder o porque você deveria aprender a utilizar o templating no server side basicamente porque tanto ***Angular*** quanto ***Vue*** usam uma abordagem semelhante à dos templates para criar *HTML*.

### Como um template se apresenta no código

Começando com o que o template está substituindo considerando a maneira mais óbvia e simples de gerar scripts de uma linguagem a partir de outra (HTML com Javascript).

```js
//No código Javascript
document.write('<h1>Por favor não faça isso!</h1>')
document.write('<p><span class = "code">document.write</span> é ')
document.write('impertinente e deve ser evitado a todo custo. <p/>')
document.write('<p>Hoje é dia'+new Date()+'.<p/>')

```

E como o código acima sugere, esse tipo de coisa jamais deve ser feito, e deve ser evitado arduamente, porque ***Emitir HTML em Javascript é problemático***.

### Problemas de se emitir HTML em código Javascript

1. **Mudar de contexto é problemático**:

    Se você tiver codando muitas linhas em javascript será confuso adicionar HTML no meio do código, porque não é algo usual.

2. **Preocupação com escape de caracteres**:

    Você provavelmente já teve que escrever uma string em que precisou utilizar as famosas contra-barras antes para que o caractere seja adicionado à ela corretamente, agora imagine ter que fazer isso a todo momento.

3. **Usar Javascript que gera HTML que também inclua Javascript leva rapidamente qualquer pessoa à loucura**:

    Já ouviu falar em loops certo? basicamente é como um loop infinito, onde o fim é o começo e o começo é o fim, ou algo do tipo, você não gostaria de ter que escrever nem mesmo uma tag *script* sequer nesse contexto.

4. **Perdemos o realce da sintaxe, e outros recursos úteis como intellisense, snippets úteis e quaisquer outros recursos do editor utilizado:**

    Convenhamos, perder aquela coloração diferente pra ajudar a identificar funções ou variáveis, ou mesmo ver tudo como se fossem strings deixa o ato de programar um pouco mais difícil e até mesmo massivo. Sem contar as dificuldades para **analisar o código ou entender**.

### Como o templating resolve esses problemas

Permitindo que escrevamos o código na linguagem de destino fornecendo ao mesmo tempo a possibilidade de inserção de dados dinâmicos. Veja o exemplo anterior reescrito como um template do Mustache:

```HTML
<!-- No código HTML-->
<h1>Muito melhor</h1>

<p>Hoje é dia {{today}}.</p>
```

E tudo que precisamos fazer agora é fornecer um valor para {{today}} no server side.

## Selecionando uma engine de template

No ecossistema do node existem muitas engines de templating para escolher, e responder qual é a melhor é algo complicado de se fazer, mas eis aqui alguns critérios que se deve levar em conta.

### Desempenho

Quanto mais rápido seu site for melhor, portanto desempenho é sim um requisito muito importante.

### Client-side ou Server-side

A maioria das engines de templating está disponível para atuar tanto no server-side quanto no client-side. Se você precisar de templates nos dois lados, é recomendado selecionar algo que seja igualmente eficaz em ambos os casos.

### Abstração

Você deseja algo familiar ao HTML ou prefere algo diferente disso? Os templates (principalmente server-side) oferecem mais opções em casos como esse.

Em resumo os templates evoluíram muito e provavelmente você não escolherá mal independente de qual selecionar.

O **Express** nos permite usarmos o engine de templating que quisermos, portanto, será muito fácil migrar de um para o outro caso seja necessário.
