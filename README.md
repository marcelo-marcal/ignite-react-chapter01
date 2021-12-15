# ignite-react-chapter01

### Trilha ReactJS

## Fundamentos do ReactJS

### 1 Criando estrutura do projeto

1.1 Vamos criar o arquivo package.json

```yarn init -y``` 

Vamos instalar a biblioteca react

```yarn add react```

Vamos instalar a biblioteca react-dom
E a arvore de elemento da nossa aplicação. em outras palavras e o HTML convertido em sintasse de objeto como javascript.
Permitido que react se comunique com a arvore de elementos do HTML.

```yarn add react-dom```

Agora vamos criar as estrutura de pastas do projeto
Pasta na raiz do projeto:
  src
  
Pasta na raiz do projeto:
  public

Onde vai ficar os aquivos publicos que precise ser acessado do meio externo.

Dentro do public:
  index.html

  E entramos digitando e selecionado html5, pois ele ja ira criar uma estrutura inicial.


### 2 Configurando Babel

Vamos configura o Babel, que tem a função de converter o codigo para que todos os Browser possa entender nossos códigos.

site: https://babeljs.io/

Vamos instalar a Babel, como dependencia de desenvolvimento:

```yarn add @babel/core @babel/cli @babel/preset-env -D```

Despois de instalado vamos criar um arquivo na raiz do projeto:
  babel.config.js

<h1 align="center">
    <img src="./img/img001.png" />
</h1>


Agora na pasta src, vamos criar um aquivo:
  index.js

E escrever o seguinte código:

<h1 align="center">
    <img src="./img/img002.png" />
</h1>

E vamos execulta
```yarn babel src/index.js --out-file dist/bundle.js```

<h1 align="center">
    <img src="./img/img003.png" />
</h1>

O mesmo codigo gerado dentro do site do Babel.

Vamos instalar a biblioteca @babel/preset-react -D como dependencia de desenvolvimento:

```yarn add @babel/preset-react -D```

E dentro do babal.config.js adicionar uma nova linha.

<h1 align="center">
    <img src="./img/img004.png" />
</h1>

E vamos execulta.

```yarn babel src/index.js --out-file dist/bundle.js```


vamos trasformar a extenção do nosso arquivo index.js em index.jsx
E porque jsx? Porque e quando ultilizamos HTML dentro do JavaScript

```yarn babel src/index.jsx --out-file dist/bundle.js```

### Configurando Webpack

Vai ensina atraves de uma serie de configurações que se chama loaders em nossa aplicação como ela deve tratar cada tipo de arquivo seja .js, .sass, .png, 
Ai o webpack vai tranforma os aquivos em uma forma que sera entendido pelo Browser.

Vamos instalar Webpack

```yarn add webpack webpack-cli webpack-dev-server -D```

Vamos criar na raiz do projeto um aruivo de configuração webpack.config.js
Vamos usar o `require` pois o node consegue intender ele desta forma ele vai colocar o caminha conforme o sistema operacional.

<h1 align="center">
    <img src="./img/img005.png" />
</h1>

E vou configura o caminho e que tipo de aquivo ele ira ler em uma expressão regular:

<h1 align="center">
    <img src="./img/img006.png" />
</h1>

Vamos instalar babel-loader como dependencia

```yarn add babel-loader -D```

Que ira fazer a integração entre o `loader` e `webpack`

Agora apenas para testar o codigo se já esta funcionado, vamos criar dentro src/ um arquivo App.jsx

<h1 align="center">
    <img src="./img/img007.png" />
</h1>

E no arquivo index.jsx, vamos fazer as senguintes importações:

<h1 align="center">
    <img src="./img/img008.png" />
</h1>

E vamos execulta o webpack no terminal:

```yarn webpack```

E se acessa a pasta dist ele geral em nosso `bundle.js` o nosso novo aquivo.


### Estrutura do ReactJS

O React tem a finalidade de criar toda a interfeice da aplicação atraves do javascript.

E vamos colocar dentro do arquivo index.html o seguinte codigo dentro do `body` ai toda a aplicação react sera contruida dentro da div.
```
<body>
  <div id="root"></div>  
</body>
```

E dentro do arquivo index.jsx mais fazer a seguinte alteração, para teste:
Onde o `getElementById` vai procura dentro da aplicação pelo id, que nesse caso e root.

<h1 align="center">
    <img src="./img/img009.png" />
</h1>

E vamos execulta o comando:
```yarn webpack```

E dentro do arquivo `index.html` adicionar o script:

<h1 align="center">
    <img src="./img/img010.png" />
</h1>

E vamos abri o arquivo html

Mas pra não precisa import o React dentro `index.jsx`,vamos fazer uma alteração no arquivo `babel.config` e adicionar o seguinte codigo: `runtime: 'automatic'`

<h1 align="center">
    <img src="./img/img011.png" />
</h1>

E vamos execulta o comando:
```yarn webpack```

E posso tambem busca as informações dentro do `App.jsx`

<h1 align="center">
    <img src="./img/img012.png" />
</h1>

Assim conseguimos intender como ele funciona.

### Servindo HTML estático

Uma melhoria que podemos fazer em nosso codigo html para não fica com a tag ` <script src="../dist/bundle.js"></script>`:
Vamos removela do codigo.

<h1 align="center">
    <img src="./img/img013.png" />
</h1>

E instalar:
```yarn add html-webpack-plugin -D```

E dentro do arquivo `webpack.config.js`, mais importa ele.
Vamos adicionar o seguinte codigo: 
```const HtmlWebpackPlugin = require('html-webpack-plugin')```
E tambem:
```
plugins: [
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname, 'public', 'index.html')
    })
  ],
```

<h1 align="center">
    <img src="./img/img014.png" />
</h1>

E vamos execulta o comando:
```yarn webpack```

Ele ira gera um arquivo html dentro da pasta `dist`
Assim melhoramos o fluxo da aplicação.

