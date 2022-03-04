
Essas são notas de aprendizado anotadas referentes ao capítulo 6 do livro [Programação web com Node e Express.](https://github.com/EthanRBrown/web-development-with-node-and-express-2e)

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
