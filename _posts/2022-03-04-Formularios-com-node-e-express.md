# Minhas Notas pessoais do capítulo 6

Essas são notas de aprendizado anotadas referentes ao capítulo 6 do livro [Programação web com Node e Express.](https://github.com/EthanRBrown/web-development-with-node-and-express-2e)

## Objetos de requisição e resposta

Quando estiver criando um servidor web com Express, grande parte do que você lidará será com os objetos de requisição e resposta provindos dos manipuladores de requisição. Os manipuladores de requisição nada mais são que funções que enviam requisições e resposta através de métodos http. Dito isso faz sentido abordarmos mais a fundo a respeito do que são, para que servem e como utilizar esses objetos tão importantes para o nosso aprendizado nesse livro.

### URL (Uniform Resource Locator)

Urls são parte chave para a internet, e estão tão presentes no nosso dia-a-dia que nem sequer pensamos no que significa ou pelo que ela é formada. Mas não se preocupe, a partir deste tópico, você saberá o básico para prosseguir com o aprendizado e de quebra poderá explicar para sua vó o que são todas aquelas letrinhas em cima das receitas que ela acabou de pesquisar.

A sigla URL pode ser traduzida como sendo *Localizador Uniforme de Recursos*, No nosso contexto, elas são acessadas por redes TCP/IP (Transmission Control Protocol/Internet Protocol) que são compostas por 6 partes,   sendo elas ***Protocol, Host , Port, Path, Querystring and Hash.***

#### Protocol

* Determina como a requisição será transmitida.

* Os mais conhecidos são http e https.

#### Host

* Identifica o servidor em que a aplicação ou site está hospedada

* Podem ser identificados por uma palavra chave ou um endereço IP

* Termina com um domínio de nível superior (TLD) como .com , .net

* Pode possuir subdomínios como www.

* Exemplo :

```http
http://google.com
```

#### Port

* Cada servidor tem uma coleção de portas numeradas

* Um servidor só pode estar associado a uma porta específica

* As mais comumente usadas são : 3000, 8080, 8088, 80 e 443 (a porta 80 para *http* e a porta 443 para *https* serão assumidas caso você omita a porta do servidor

#### Path

* É a parte principal da aplicação web, através dela que se deve identificar as páginas ou outros recursos da aplicação de maneira específica

* Exemplo :

```http
http://localhost:3000/home
```

#### Querystring

* Também chamada de string de pesquisa, ou search string.

* Formada por pares nome/valor

* Começa por ?, e os pares nome/valor são separados por &.

* Ambos devem ser codificados em URL, que o Js pode fazer a conversão usando a função do objeto global encodeURIComponent.

```js
Object.encodeURIComponent('Pesquisa válida') 
//retorna Pesquisa+válida
```

* Exemplo :

```http
http://google.com/search/q=?url&vid=438542asd
```

#### Hash

* Não é passado para o servidor, apenas o navegador o conhece.

* SPA utilizam para controlar a navegação da página.

* Originalmente sua finalidade era exibir uma parte específica do documento web marcada por uma tag de âncora como tags id ou class.

* Exemplo :

[Conectando Formulário a um servidor](#conectando-o-formulário-ao-servidor)

### Métodos de requisição HTTP

O protocolo HTTP define uma coleção de métodos de requisição (verbos HTTP) que um cliente usa para se comunicar com o servidor. Normalmente são utilizados os métodos ***GET*** (método usado pelo navegador por exemplo para acessar páginas web) e ***POST*** (usado por exemplo para processamento de formulários ).

 O método GET recebe informações do servidor, enquanto que o método POST primeiro envia algum tipo de informação e depois recebe uma resposta do servidor (em geral responde com o mesmo HTML que seria enviado pelo método GET).

#### Fluxo HTTP

Eis um Exemplo do fluxo http do método GET.

![Fluxo Http](../../public/img/fluxoHttp.png)

### Request Headers

Quando navegamos para uma página web, o navegador envia informações para o servidor sobre a requisição para que possa servir ao cliente da melhor foma possível.

Informações sobre o Agent User, sistema operacional, navegador utilizado, linguagem padrão, entre outras são enviadas para o servidor e podem ser acessadas pela propriedade headers do objeto de requisição. O arquivo que se encontra no diretório /lib/echo-headers.js  possui código capaz de mostrar todas as informações que o navegador está enviando.

### Request Body

Requisições GET comuns não possuem a propriedade body no objeto de requisição, entretanto, requisições POST possuem.

O tipo de mídia mais comum é application/x-www-form-urlencoded  , que se trata basicamente de pares key/value codificados e separados por & (mesmo formato de querystrings).

### Request Object

Inicialmente, o objeto de requisição (Primeiro parâmetro de um manipulador de requisição, comumente chamado de `req` ou `request`) é uma instância de `http.IncomingMessage`, que é um objeto básico do Node. O express por sua vez adiciona outras funcionalidades. Para mais informações sobre esses métodos consulte as Páginas 90, 91 e 92 do livro, ou mesmo o [repositório do capítulo 6](https://github.com/EthanRBrown/web-development-with-node-and-express-2e) no GitHub.

## Response Headers

Assim como o objeto de requisição possui a propriedade headers com informações "ocultas" que são enviadas para o servidor, quando o servidor responder ele também retornará informações que não serão necessariamente renderizadas ou exibidas pelo navegador.

As informações normalmente incluídas nos headers de resposta são metadados e informações do servidor.

Como por exemplo a propriedade `Content-Type` que informa ao servidor que tipo de conteúdo está sendo renderizado.

```js
res.type='text/plain'
```

Os metadados também podem conter dicas para o navegador sobre por quanto tempo ele pode armazenar conteúdo em cache (consideração importante para otimização) .

Também é comum que a propriedade headers do objeto de resposta contenha informações sobre o servidor o que dá vantagem para hackers para o comprometimento do site (servidores comprometidos com segurança frequentemente omitem essas informações ou fornecem informações falsas). Para desativar o header X-powered-by siga o exemplo contido no [repositório do capítulo 6](https://github.com/EthanRBrown/web-development-with-node-and-express-2e).

Para ver todos os cabeçalhos de resposta basta abrir o devTools do seu navegador na aba network e recarregar a página, em seguida clicar na aba Headers.

![Response Headers](../../public/img/responseHeaders.png)

## Response Object

Inicialmente, o objeto de resposta (segundo parâmetro de um manipulador de requisição, comumente chamado de `res` ou `response`) é uma instância de `http.ServerResponse`, que é um objeto básico do Node.

O express por sua vez adiciona outras funcionalidades. Para mais informações sobre esses métodos consulte as Páginas 92, 93 e 94 do livro, ou mesmo o [repositório do capítulo 6](https://github.com/EthanRBrown/web-development-with-node-and-express-2e) no GitHub.

## Formulários

Para se criar formulários utilizando express precisamos primeiramente de uma página web por onde se possa captar os dados desse formulário.
De forma que ao se preencher e posteriormente submeter esses dados, se possa fazer uma requisição dos dados enviados através do método POST e então utilizar esses dados da forma que for conveniente.

### Criando o Formulário

 Para criar um formulário será **extremamente necessário** utilizar conhecimentos de HTML (mas não se preocupe, podemos dar um pequeno spoiler nessa anotação do capítulo).

1. Uma vez que você tem o conteúdo base da página definido (vide o capítulo 5 que trata sobre layouts e handlebars), fica fácil criar um formulário. Para isso, crie um arquivo com o nome da página onde será acessado esse formulário com extensão *.handlebars*.

2. Criado esse arquivo começaremos explicando as tags e propriedades que compõem o formulário:

* Primeira parte

    ```html
    
        <form action = '/process-contact'method = 'post'></form>
    
    ```

    Nessa parte em questão temos 3 elementos importantes para criação do nosso formulário, a Tag:
    1. `<form></form>` : Tag que delimita os elementos que compõem o formulário.

    2. `action = '/process-contact'` : Propriedade que descreve URI do programa que processa a informação do formulário (utilizamos essa informação no parâmetro path do método post do express).

    3. `method = 'post'` : Propriedade que descreve qual método ***HTTP*** se é utilizado ao realizar o submit do formulário.
    Os dados do formulário são passados para o corpo da requisição e então enviados para o servidor.

* Segunda parte:

    ```html
     <form action = '/process-contact'method = 'post'>
         <div>
            <label>:Seu nome:
                <input name="name"/>
            </label>
            <label>:Seu email:
                <input email="email"type="email"/>
            </label>

         </div>
     </form>
    ```

    1. `<label></label>` : Tag que específica uma semântica ***HTML*** para um elemento de um formulário na interface do usuário que pode estar associado a um formulário específico para identificar seu atributo.

    2. `<input name="name"/> || <input name="email" type="email"/>` :
        * A Tag *input* indica a semântica de um elemento de entrada de dados no formulário.

        * A propriedade *name* indica a forma com que o elemento é referenciado no corpo de requisição (***`req.body.name || req.body.email`***) do formulário.

        * A propriedade *type* indica o tipo de dado que está sendo enviado pelo formulário, de forma a possibilitar que apenas alguns tipos de entradas sejam aceitos (No caso de type="email", apenas entradas que possuam texto seguido de @ seguido de mais texto podem ser enviadas), e que o formulário não possa ser submetido até que a entrada esteja em formato válido.

* Terceira parte

    ```html
    
  <div>
    <button type="submit">Submit</button>
  </div>
    ```

    1. `<button>` : Tag que indica a existência de um botão na interface do usuário
    2. `type="submit"` : Propriedade que identifica o tipo do botão que nos diz qual ação será chamada ao clicar nele(submit envia os dados do formulário para o servidor).

### Conectando o Formulário ao servidor

Para que haja conexão entre o formulário e o servidor são necessários alguns elementos anteriormente mencionados, mas não se preocupe, será tudo esclarecido nessa anotação.

* Primeiramente devemos fazer as importações dos módulos:

```js
const express = require ('express');

const expressHandlebars = require ('express-handlebars');

const bodyParser = require ('body-parser');

```

Onde o único que merece uma atenção especial nesse capítulo é o módulo ***body-parser***, este trata-se de um *middleware* feito para fazer o parsing do corpo codificado em URL.

* Instanciando e configurando o servidor Express:

```js
const app = express();

app.engine('handlebars' , expressHandlebars({
    defaultLayout:'main'
}));
app.set('engine' , 'handlebars');

//definindo o middleware bodyParser como parser para Url codificada no express

app.use(bodyParser.urlencoded({ extended : false }))

```

Nessa situação definimos a engine responsável por renderizar as páginas como sendo o middleware handlebars. E setamos o layout padrão como sendo o arquivo main.handlebars que se encontra no diretório : */views/layouts/main.handlebars* .

Também definimos o middleware bodyParser como parser para Url codificada no express.

* Criando o método post:

```js

app.get('/redirectPage', (req, res) => res.render('redirectPageName'));
app.get('/formPage', (req, res) => res.render('formPageName'));
app.post('/process-contact', (req, res) => {
    console.log(`Received contact from ${req.body.name}<${req.body.email}>`);
    res.redirect(303, '/redirectPage');
});

```

Acompanhando o processo de criação do método post vemos que se antecede por dois métodos get, isso se dá pelo simples motivo de se fazer necessária a conexão com as rotas das páginas do formulário e a página de redirecionamento serem válidas e estarem disponíveis na nossa aplicação.

Dito isso, o método post tem como primeiro parâmetro o path da q URI do programa que processa a informação do formulário, o segundo parâmetro é uma função de callback que possui como parâmetros os objetos de requisição e resposta fornecidos pelo método post.

Essa função de callback mostra no console os dados enviados pela requisição através da instrução de acesso à propriedade *(req.body.nome)* e em seguida envia como resposta, o redirecionamento da página com o ***código de status HTTP : 303***.
