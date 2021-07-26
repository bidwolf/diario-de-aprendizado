
# Guia básico de Markdown em português

Entenda primeiramente, que existem [regras](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md) que na verdade são *boas práticas* na linguagem **Markdown**.

Isso pode te assustar um pouco é claro, mas saiba que ela continua funcionando mesmo que você cometa alguns erros.

## Headers</h2>

---

* Para começar saiba que utilizar caracteres # criam _headers_ e seus níveis se dão de acordo com o número de # que você coloca no arquivo.
* Ao criar *headers* deve-se seguir a ordem de headers utilizados não podendo pular do **nível 1 (#)** para o **nível 2 (##)** como diz a regra [md001](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md001)

* Também podemos criar _headers_ utilizando **"=========" para nível 1**, e **"---------" para nível 2**, _headers_ de nível 3 continuam utilizando **###**.

## 2. Listas</h2>

---

* Existem basicamente 2 tipos de listas possíveis, *_Ordenada_* e *_Não-Ordenada_*. As listas ordenadas são utilizadas com os caracteres **"1. (ou número ponto espaço")** e listas não ordenadas são criadas a partir dos caracteres **"- ","+ ","\* "(ou traço espaço,mais espaço,asterísco espaço)**

### Listas não-ordenadas

---

* A regra [md004](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md004) , explica que listas não ordenadas não devem mesclar símbolos diferentes para a mesma lista.
  * Isso vale também para os subníveis.
  * As regras [md005](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md005), e  [md007](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md004) relacionam a identação da lista, determinando a diferença de espaços para cada subnível como 2 espaços e a quantidade em um mesmo subnível não pode ser diferente.

## CheckLists

---

 Um exemplo de lista não ordenada são as checklists, elas são utilizadas para destacar tópicos com *checkbox*.

- [ ] Caixa sem seleção

- [ ] Caixa selecionada

### Listas ordenadas

---

1. esse é um exemplo de lista ordenada
1. Nessa lista eu utilizei o inicio de todos os itens como *"1. "*.

    1. Sub-lista ordenada.
    2. Aqui eu enumero a lista como 1.2.3.... em cada item da lista.

1. Utilizar 1->3-> 2 como índice de uma lista ordenada fere a regra [md029](https://github.com/DavidAnson/markdownlint/blob/v0.23.1/doc/Rules.md#md029).

## 3. Links, imagens e coisinhas a mais</h2>

---

* Para criar links se deve utilizar a sintaxe:
>
>        (texto do link)+[endereço do link].
>
ou:
>
>        "(texto do link)"+[ref]
>
>        "[ref]":link

* Para criar links com referências a imagens deve ser utilizada a sintaxe:
>
>       "![Alternate text]"+"(image.jpg)"
>
ou:
>
>        "![Alternate text]"+"[ref]"
>
>       "[ref]":image.jpg "Texto opcional"
> <img src="kaminari.jpg" width= "200" description="Imagem contendo o personagem de boku no hero Academy Kaminari sorrindo">

* Para adicionar um título ao link da imagem ou link normal, basta adicionar um texto entre aspas duplas nos parênteses do link após o link

        Exemplo: [Google](www.google.com "este é 
        um link para o site da google")

[Google](www.google.com "Este é um link para o site da google")

* Equivalente a :

```html
<a>href="www.google.com" Google title="Este é um link para o site da google"</a>
```

* Para adicionar emails ou links rápidos basta colocá-los entre os caractéres **"<>"**

Envie um email para <tec.henriquedepaula@gmail.com>

        Equivalente a [tec.henriquedepaula@gmail.com](mailto:tec.henriquedepaula@gmail.com)

* Para adicionar um link no próprio documento, basta utilizar o id do elemento no link utilizando **_("#" +"id_elemento")_**
**Exemplo:** [Capitulo 1](#id_headers)

   *Nota: Não é possível adicionar id, class ou outros aspectos de metadados em markdown, para solucionar isso basta definir o elemento em html.*

---

## 4. Códigos</h2>

---

Para adicionar códigos basta adicionar *crase*.

        `var fruta="banana" //linha de código`
`var fruta="banana" //linha de código`

```js
fruta="banana";
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

## 5. TABELAS</h2>

---

1. Coloque os nomes das colunas da tabela e os separe utilizando o caractére " **|** ".

        Exemplo:
        Invocador | Posição | Winrate

1. Na próxima linha utilize os caractéres delimitadores para cada coluna, sendo necessária somente uma vez.
   1. "**---|**" : Para alinhamento padrão.
   2. "**:---**" : Para alinhamento à esquerda (padrão).
   3. "**:---:**" : Para alinhamento centralizado.
   4. "**---:**" : Para alinhamento à direita.

1. Agora basta adicionar os itens da tabela separando-os por "**|**" e sua tabela está criada.

---

### Exemplo 1: Alinhamento à esquerda ou padrão

Invocador | Posição | Winrate
---|---|---
Pijack | top |10%
Jukes | top | 50%

---

### Exemplo 2: Alinhamento à direita

Invocador | Posição | Winrate
---:|---:|---:
Pijack | lane do topo |10%
propositalmente | lane do topo | 50%

---

### Exemplo 3: Alinhamento centralizado

Invocador | Posição | Winrate
:---:|:---:|:---:
Pijack | lane do topo |10%
propositalmente | lane do topo | 50%

---

## 6. Mexendo com textos <h2 id="id_textos"></h2>

---

Para utilizar recursos textuais de destaque é muito simples, e trivial, provavelmente você já utilizou muitos desses recursos em alguns apps, então esse capítulo vai ser bem menos explicativo e bem mais demonstrativo.

### Blackotes

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
[capítulo 6](#textos-diferenciados).

        [capítulo 6](#textos-diferenciados)

### Rodapés

Para criar um rodapé como esse
rodapé [²] ou esse outro  rodapé [³] basta seguir a seguinte sintaxe:'

        Sintaxe: Qualquer texto [^índice do rodapé] mais texto
        [^índice do rodapé]: Nota

[²]: like

[³]: that
