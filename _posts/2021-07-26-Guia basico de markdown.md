
# Guia básico de Markdown em português

## Sumário

1. [Introdução](#introdução)
2. [Sobre a linguagem Markdown](#sobre-a-linguagem-markdown)

    * [O que é a linguagem Markdown](#o-que-%C3%A9-a-linguagem-markdown)
  
    * [Como a linguagem Markdown funciona](#como-funciona-a-linguagem-markdown)
  
3. [Headers](#headers)

    * [O que são Headers](o-que-são-Headers)
  
    * [Como utilizar os Headers](oomo-utilizar-os-Headers)
  
4. [Listas](#listas)

    * [O que são listas em Markdown](#o-que-são-listas)
  
    * [Listas não ordenadas](#listas-não-ordenadas)
  
    * [Checklists](#checklists)
  
    * [Listas ordenadas](#listas-ordenadas)
  
5. [Links](#links)
    * [Como criar links em Markdown](#como-criar-link-em-markdown)
    * [Links de imagens](#links-de-imagens)
    * [Emails e links rápidos](#emails-e-links-rápidos)

6. [Códigos](#códigos)
    * [Inline Code](#inline-code)
    * [Fenced code](#fenced-code)
8. [Tabelas](#tabelas)
    * [Alinhamento padrâo](#alinhamento-padrão)
    * [Alinhamento à direita](#alinhamento-à-direita)
    * [Alinhamento centralizado](#alinhamento-centralizado)
9. [Recursos Textuais](#recursos-textuais)
    * [Blaquotes](#blaquotes)
    * [Textos diferenciados](#textos-diferenciados)
    * [Rodapés](#rodapés)

## Introdução

Este é um artigo para leitura que descreve funcionalidades e  [regras](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md) que na verdade são *boas práticas* na linguagem **Markdown**.
O objetivo é, além de servir como um guia, introduzir conceitos e princípios da mesma de forma clara e objetiva.

---

## Sobre a linguagem Markdown

### O que é a linguagem Markdown
O Markdown é uma linguagem de marcação usada para formatar documentos de todos os tipos, criada por [John Gruber](https://daringfireball.net/projects/markdown/) e Aaron Swartz em 2004, hoje é uma das linguagens mais populares entre programadores.
Um arquivo Markdown ou MD é composto por texto simples, é fácil de entender e não tem toda aquela marcação HTML poluindo o conteúdo.

### Como funciona a linguagem Markdown
Para escrever um código markdown, você só precisa de um editor de texto funcional, a partir daí, basta salvar esse arquivo com a extensão _.md_ então seu arquivo estará pronto para rodar em qualquer processador de Markdown.
    
    **Nota: Processadores de Markdown convertem o código escrito em Markdown, em um arquivo html,
    
      que por sua vez pode ser visualizados por qualquer navegador funcional.

---

## Headers

### O que são Headers

Headers podem ser traduzidos como cabeçalhos, mas não se deve confundir com eles. Na linguagem markdown headers funcionam como 

separadores de conteúdos, mas sua principal função é delimitar a ordem de importância de títulos.

### Como utilizar Headers

* Para utilizar basta utilizar os caracteres **"#"**, eles criam _headers_ e seus níveis se dão de acordo com a quantidade de **"#"** que você coloca antes do título.
  exemplo: ## Meu exemplo de título.
* Ao criar *headers* deve-se seguir a ordem de headers utilizados não podendo pular do **nível 1 (#)** para o **nível 3 (###)** como diz a regra [md001](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md001)

* Também podemos criar _headers_ utilizando **"=========" para nível 1**, e **"---------" para nível 2**, _headers_ de nível 3 continuam utilizando **###**.

---

## Listas

### O que são listas
Existem na nossa cultura, diversos tipos de listas, para as mais diferentes formas de aplicação. Uma lista pode ser uma lista de compras, mas também pode ser um passo a passo de uma receita de bolo. Fundamentalmente quando se trata de listas, os arquivos gerados na linguagem markdown tratam de apenas dois tipos de listas possíveis, as listas *_Ordenadas_* e as listas *_Não-Ordenadas_*.

### Listas não-ordenadas

listas não ordenadas são criadas a partir dos caracteres **"- ","+ ","\* "(ou traço espaço,mais espaço,asterísco espaço)**.

* A regra [md004](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md004) , explica que listas não ordenadas não devem mesclar símbolos diferentes para a mesma lista.
  * Isso vale também para os subníveis.
  * As regras [md005](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md005), e  [md007](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md004) relacionam a identação da lista, determinando a diferença de espaços para cada subnível como 2 espaços e a quantidade em um mesmo subnível não pode ser diferente.

## CheckLists

 Um caso especial de lista não ordenada são as checklists, elas são utilizadas para destacar tópicos com *checkbox*.

- [ ] Caixa sem seleção

- [x] Caixa selecionada

### Listas ordenadas

As listas ordenadas são compostas pela sintaxe (**"" `number`. ""** **(ou número ponto espaço")**.
1. esse é um exemplo de lista ordenada
1. Nessa lista eu utilizei o inicio de todos os itens como *"1. "*.

    1. Sub-lista ordenada.
    2. Aqui eu enumero a lista como 1.2.3.... em cada item da lista.

1. Utilizar 1->3-> 2 como índice de uma lista ordenada fere a regra [md029](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md029).

---

## Links

Não convém, no âmbito deste artigo explicar o que são links ou porque
utiliza-los, pois considero trivial, mas caso você queira saber um
pouco mais sobre, eis um ótimo artigo feito pelo [Professor Diego](https://prof-web-diego.webnode.pt/) sobre
[O que são links ou hiperlinks](https://prof-web-diego.webnode.pt/products/o-que-e-link-ou-hyperlink-/).
### Como criar links em markdown

Para criar links se deve utilizar a sintaxe:

>
>        (texto do link)+[endereço do link].
>
ou:
>
>        "(texto do link)"+[ref]
>
>        "[ref]":link
Para adicionar um título ao link, basta adicionar um texto entre aspas duplas nos parênteses do link após o link


        Exemplo: [Google](www.google.com "este é 
        um link para o site da google")

[Google](www.google.com "Este é um link para o site da google")


Equivalente a :

```html
<a>href="www.google.com" Google title="Este é um link para o site da google"</a>
```

### links de imagens

* Para criar links com referências a imagens deve ser utilizada a sintaxe:
>
>       "![Alternate text]"+"(image.jpg)"
>
ou:
>
>        "![Alternate text]"+"[ref]"
>
>       "[ref]":image.jpg "Texto opcional"

Para adicionar um título ao link da imagem basta adicionar um texto entre aspas duplas nos parênteses do link após o link assim como no do texto.

### Emails e links rápidos

Para adicionar emails ou links rápidos basta colocá-los entre os caractéres **"<>"**

Envie um email para <tec.henriquedepaula@gmail.com>

        Equivalente a [tec.henriquedepaula@gmail.com](mailto:tec.henriquedepaula@gmail.com)

Para adicionar um link no próprio documento, basta utilizar o id do elemento no link utilizando **_("#" +"id_elemento")_**
**Exemplo:** [Capitulo 1](#id_headers)

   *Nota: Não é possível adicionar id, class ou outros aspectos de metadados em markdown, para solucionar isso basta definir o elemento em html.*

### Hipertextos em Headers e notas de rodapé

---

Hipertextos em headers podem ser utilizados em linguagens markdown e existem algumas formas de se fazer isso.

1. É colocado um id entre chaves referente ao título, dai pra frente é só referenciar esse id como se referencia links normais.

        ## TITULO 1{#id_titulo1}

        essa é uma referencia ao [título 1](#id_titulo1)
1. Substituindo o header com "#" pelo seu equivalente em html, e adicionando `id="id_anyHeader"` entre sua tag.
1. Mesclando o nível do header com sua tag html adicionando-a posteriormente ao header com o id sugerido: `## ANY HEADER H2 <h2>id="id_anyHeader"</h2>`.

[capítulo 6](#id_textos).

``` html

## capitulo 6<h2 id="id_textos"></h2>`
```

        [capítulo 6](#id_textos)

1. Referenciando o título em um link substituindo o id pelo titulo com hifens ao invés de espaços em branco.
[capítulo 1](#headers).

        [capítulo 1](#headers)

---

## Códigos

Existem três variedades de formas para mostrar códigos em Markdown.

Em geral elas estão separadas em _Fenced_, _Idented_ e _Mixed_. Mas foge do âmbito desse artigo explicar a diferença entre eles, entretanto, você pode descobrir a diferença entre eles bem [aqui](https://riptutorial.com/markdown/topic/553/code)
### Inline Code
Para adicionar códigos em uma única linha basta adicionar *crase* antes e depois do código.

Desse jeito:

        `var fruta="banana" //linha de código`
`var fruta="banana" //linha de código`
### Fenced code

Criar um _Fenced code_ produz um bloco de códigos no qual você pode especificar a linguagem utilizada colocando a abreviação da linguagem após os caractéres iniciadores **"```"** ou **"~~~"**

```js
fruta="banana";
doce="doce de banana";
vitamina="vitamina de banana";
```

>       ```js
>       fruta="banana";
>       ```

```html
<html>
   <head>
      <title>Meu titulo</title>
   </head>
</html>
```

---

## TABELAS

Para criar tabelas utilizando a linguagem markdown basta seguir o passo-a-passo a seguir:


1. Coloque os nomes das colunas da tabela e os separe utilizando o caractére " **|** ".

        Exemplo:
        Invocador | Posição | Winrate

1. Na próxima linha utilize os caractéres delimitadores para cada coluna, sendo necessária somente uma vez.

1. Agora basta adicionar os itens da tabela separando-os por "**|**" e sua tabela está criada.

### Alinhamento à esquerda

"**---|**" : Para alinhamento padrão.
"**:---**" : Para alinhamento à esquerda (padrão).

Invocador | Posição | Winrate
---|---|---
Pijack | top |10%
Jukes | top | 50%

---

### Alinhamento à direita

"**:---:**" : Para alinhamento centralizado.

Invocador | Posição | Winrate
---:|---:|---:
Pijack | lane do topo |10%
propositalmente | lane do topo | 50%

### Alinhamento centralizado

"**---:**" : Para alinhamento à direita.

Invocador | Posição | Winrate
:---:|:---:|:---:
Pijack | lane do topo |10%
propositalmente | lane do topo | 50%

## Recursos textuais

Para utilizar recursos textuais de destaque é muito simples, e trivial, provavelmente você já utilizou muitos desses recursos em alguns apps, então esse capítulo vai ser bem menos explicativo e bem mais demonstrativo.

### Blaquotes

---

 Normalmente utilizados para citar um texto inferior, os chamados blackquotes
>Aqui eu utilizo um ">"
>
> E utilizando um ">" numa nova linha em branco
>
> posso escrever outras linhas entre os blackotes, que começarem com >.

### Textos diferenciados

---

1. Dá pra cortar o texto usando ~~ no início e no final da frase
 ~~desse jeito~~

1. Dá pra mesclar efeitos de textos:
~~**Texto cortado em negrito**~~
1. Dá pra usar emojis :monkey: mas só em alguns interpretadores de markdown. Uma referência para alguns emojis está [Aqui](ref)

[ref]:https://gist.github.com/rxaviers/7360908
 Esse eu nem sei o nome mas ele é mais bonito, porém ele ignora espaços em branco e caracteres que não sejam alfanuméricos

  Não é afetado por efeitos em negrito ou itálico, mas dá pra colocar entre blackotes, para usar:"$\$texto$$"
  >$$Henrique$$

* Não funciona no github (24/07/2021)

* _é considerado um heading_

### Rodapés

Para criar um rodapé como esse
rodapé [²] ou esse outro  rodapé [³] basta seguir a seguinte sintaxe:'

        Sintaxe: Qualquer texto [^índice do rodapé] mais texto
        [^índice do rodapé]: Nota

[²]: like

[³]: that
