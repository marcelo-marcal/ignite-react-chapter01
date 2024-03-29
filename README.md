<h1 align="center">
    <img src="./img/img000.png" />
</h1>

# ignite-react-chapter01

### Trilha ReactJS

## Fundamentos do ReactJS

### 1 Criando estrutura do projeto

## 1 Configurando Ambiente:

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


Agora na pasta src, vamos criar um aquivo: `index.js`

E escrever o seguinte código:

<h1 align="center">
    <img src="./img/img002.png" />
</h1>

E vamos execulta:

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

### Webpack Dev Server

Vamos instalar webpack-dev-server como dependencia

```yarn add webpack-dev-server -D```

E vamos configura dentro do arquivo `webpack.config` uma variavel `devServer` para ele ficar escultado cada alteração na aplicação:

<h1 align="center">
    <img src="./img/img015.png" />
</h1>

E vamos execulta o comando:

```yarn webpack serve```

Dica: Caso não fucione sera nescessario mudar a versão da instalação do `yarn add webpack-dev-server -D` = `"webpack-dev-server": "^4.11.1"` para: `"webpack-dev-server": "3.11.2"`.

E vamos execulta o comando:

```yarn add webpack-dev-server@3.11.1```

E vamos execulta o comando:

```yarn webpack serve```

<h1 align="center">
    <img src="./img/img016.png" />
</h1>

Agora todas as vezes que for salvo uma alteração no codigo ele vai gera um `bundle`

### Utilizando source maps
## Importante:
Configura uma funcionalidade chamada source maps, que e uma forma de visualizar o codigo original da nossa aplicação mesmo quando ele está no `bundle.js`. Que ira ajudar quando for encontra o erro.

Vamos no arquivo `webpack.config.js`, e acrecentar a seguinte linha no codigo:

```
devtool: 'eval-source-map',
```

<h1 align="center">
    <img src="./img/img017.png" />
</h1>

Pauso o webpack `Ctrl + C`

E vamos execulta o comando:

```yarn webpack serve```

### Ambiente dev e produção

Vamos configura um ambiante de desenvolmineto e um de produção.
E dentro do aquivo `webpack.config.js`, e acrecentar a seguinte linha no codigo:

```const isDevelopment = process.env.NODE_ENV !== 'development';```

```mode: isDevelopment ? 'development' : 'production',```

```devtool: isDevelopment ? 'eval-source-map': 'source-map',```

<h1 align="center">
    <img src="./img/img018.png" />
</h1>

Para execulta a aplicação:
Mac e Linux

```NODE_ENV=production yarn webpack```

No windows
Vamos precisa instalar uma variavel de ambiente e funciona para definir variavel de ambiente independe do sistema:

```yarn add cross-env -D```

E dentro do arquivo `package.json` adicionar encima das dependencias alguns scripts:
Um script para ambiente de desenvolmineto:

```"dev": "webpack serve",```

Um script para ambiente de produção:

```"build": "cross-env NODE_ENV=production webpack"```

<h1 align="center">
    <img src="./img/img019.png" />
</h1>

Salva

E vamos execulta o comando para ambiente de desenvolmineto:

```yarn dev```

E vamos execulta o comando para ambiente de produção:

```yarn build```

### Importando arquivos CSS

Vamos criar uma pasta `styles` e dentro dela um arquivo `global.css`.

<h1 align="center">
    <img src="./img/img020.png" />
</h1>

E dentro do App vamos importa o arquivo:

`import './styles/global.css'`

E dentro do arquivo `webpack.config.js` vamos criar uma nova regra para que ele possa ler arquivos css.

<h1 align="center">
    <img src="./img/img021.png" />
</h1>

E estalar dois loaders:
Vamos instalar o `style-loader` e `css-loader` como dependencia

```yarn add style-loader css-loader -D```

E vamos execulta o comando:

```yarn dev```

### Utilizando SASS

Que vem ser um pre processador, que nos da algumas funcionalidades a mais no projeto.

Vamos instalar o `sass-loader` como dependencia.
Para entender arquivos sass

```yarn add sass-loader -D```

```yarn add node-sass -D```

Se precisa desistalar:

```yarn remove sass```

E dentro do arquivo `webpack.config.js` vamos alter a nova regra para que ele possa ler arquivos.

<h1 align="center">
    <img src="./img/img022.png" />
</h1>

Troco arquivo `global.css` para `global.scss`.

E no arquivo `App.jsx`
Troco arquivo `import './styles/global.css';` para `import './styles/global.scss';`.

E vamos execulta o comando:

```yarn dev```

Fim da Configuração de Ambiente:

## 2 Conceitos Importantes:

### Primeiro componente React

Criar pasta components dentro src:

E dentro da pastqa um arquivo `RepositoryList.jsx`

E vamos contruir nosso componente.
<h1 align="center">
    <img src="./img/img023.png" />
</h1>

E vamos altera o arquivo `App.jsx`
<h1 align="center">
    <img src="./img/img024.png" />
</h1>

E fazer uma pena alteração no stilo dentro do arquivo `global.scss`.
<h1 align="center">
    <img src="./img/img025.png" />
</h1>

E vamos execulta o comando:

```yarn dev```

### Propriedades no React

Os tres conseitos basico do react: Componete, Propiedade e Estado

Vai criar um arquivo `RepositoryList.jsx` com essa estrutura:

<h1 align="center">
    <img src="./img/img026.png" />
</h1>

E para acessa o componete eu vou usa um argumento `props` e chamar a propriedade que tem o nome `repository` eu acesso o `props` com o nome `{props.repository}` onde as chaves representa uma variavel javascript dentro do html.

E dentro do arquivo `RepositoryItem.jsx`  
<h1 align="center">
    <img src="./img/img027.png" />
</h1>

Sendo possivel fazer uma verificação dentro do repositorio.
Caso o repositorio esteja vazio `??` ele me retorna um nome: tipo Default
<h1 align="center">
    <img src="./img/img028.png" />
</h1>

`??` = e parecedo com o sinal `||` que e ou, mais essa nova funcionalidade Desconsidera que o zero e um valor invalido.

Seguindo pode estrutura a lista com as informações para o `RepositoryItem` no `RepositoryList` da seguinte forma.
<h1 align="center">
    <img src="./img/img029.png" />
</h1>

E dentro do arquivo `RepositoryItem.jsx` e para poder acessa o nome do reposito eu vou adiciona `?.nome` onde o `?` vai verifica com o repositorio está nulo ou não, e estive nulo ele não ira procura e retorna logo o Default.
<h1 align="center">
    <img src="./img/img030.png" />
</h1>

Outra forma de resolver e colocar o `repository={repository}` em todos eles.
<h1 align="center">
    <img src="./img/img031.png" />
</h1>

E dentro do arquivo `RepositoryItem.jsx` vamos uses as outras informações:
<h1 align="center">
    <img src="./img/img032.png" />
</h1>

### Estado do componente

Criar um componete para explicação:
Criar um arquivo `Counter.jsx` dentro da pasta components.

<h1 align="center">
    <img src="./img/img033.png" />
</h1>

`useState` Vai monitora e vai trazer atraves de um arrey

E no `App.jsx` vamos rederizar com as alterações:

<h1 align="center">
    <img src="./img/img034.png" />
</h1>

### A imutabilidade no React

Conceito:
E que uma variavel nunca podera ter seu valor alterado, mais sim sempre ira receber um novo valor.

### Fast Refresh no Webpack

E uma forma de altera o codigo da aplicação e salvar, porem mantendo o estado do componete no Browse.

Vamos instalar React Refresh Webpack Plugin como dependencia

```yarn add -D @pmmmwh/react-refresh-webpack-plugin react-refresh```

E vamos no no arquivo `webpack.config.js`

E vamos importa `const ReactRefreshWebpackPlugin = require('@pmmmwh/react-refresh-webpack-plugin')`

E chamar ele somente em ambiente de desenvolvimento
<h1 align="center">
    <img src="./img/img035.png" />
</h1>

`&&` Se eu estive em desenvolvimento ele ira execulta a segunda parte do if, e se não, ele ira retorna falso.
E para não gera error vamos usar `.filter(Boolean),` para tudo for falso ele remover o falso de dentro do if.

Vamos para `yarn dev` com `Ctrl + C`

E vamos rodar `yarn dev`

## 3 Chamadas HTTP:

### Estilização da listagem

Vamos apagar o arquivo `Counter.jsx` pois não ira ser usado.
No arquivo `App.jsx` vamos remover a parte do counter e deixa so o `<RepositoryList />`

E na pasta `styles` vamos criar um arquivo `repositories.scss` que vai ser a estilização dos repositorios.

Em no arquivo `RepositoryList.jsx`. 
E vamos importa `import '../styles/repositories.scss';`

E no arquivo `repositories.scss` vamos fazer alguns estilos.

<h1 align="center">
    <img src="./img/img036.png" />
</h1>

```
li {
    & + li {
       margin-top: 20px;
    }
```
`& + li { }` = Toda vez que tive uma `li` devera fazer alguma coisa.


### Utilizando o useEffect

Vamos pucha o repositorio de dentro da API do github:

`api.github.com/users/Diego3g`

<h1 align="center">
    <img src="./img/img037.png" />
</h1>

mais vamos usa uma lista de repositorio da rocketseat

`api.github.com/orgs/rocketseat/repos`

E depois de copia a url de deixa comentada dentro do arquivo `RepositoryList.jsx`

E vamos criar um estado `const [] = useState([]);`para armazena a listagem de repositorios. E vamos adicionar as seguintes variaves: `repositories , setRepositories`.

 Vamos usar o `useEffect()` que tem a finalidade de esta escultado alguma alteração.
 E vai receber dois parametros:
 1 - Qual função eu quero execultar. `{},`
 2 - Quando eu quero execultar a função. `[]` como dependecias, ou seja quais as informações que quando mudarem o `useEffect()` vai execulta de novo.

 Ex: Toda vez que o repositories for atualizado ele ira execulta o useEffect().

 ```
  useEffect(() => {

  }, [repositories]);
 ```

Mais se passa o arrey dessa dependencia vazio ele vai execulta uma unica vez, assim que componete for exibido em tela.
OBS: Cuidado para não deixa sem o segundo parametro, pois ele ira entra loop!

No primeiro paramentro vamos fazer um `fetch()` e vamos busca os nosso repositorio no github.
E quando esse `fetch()` me devolver um resposta `.then()`.
Eu vou converte essa resposta para `json`. 
Assim: `.then(response => response.json())`.

E quando a resposta pra `json` termina de ser convertida, eu vou ter os dados do meu repositorio.
Assim: `.then(data => response.json())`.

Vamos um exemplo:

<h1 align="center">
    <img src="./img/img038.png" />
</h1>
O console.log() e so para podemos ver oque esta trazendo.

No Browse, vamos dar um inspecionar > Console e vou lipar o console e dar um F5.

<h1 align="center">
    <img src="./img/img039.png" />
</h1>

Agora vamos salva o `data` dentro da variavel de repositorio:
Onde eu vou dar `setRepositories(data)` passando o data.
Ficando assim: `.then(data => setRepositories(data))`


### Listando repositórios

Agora so precisamos pegar o `repositories` e mostrar em tela de forma dinamica.
Vamos começa deletando a variavel:

```
const repository = {
  nome: 'unform',
  description: 'Forms in React',
  link: 'https://github.com/unform/unform'
}
```
E para mostra no vetor em cada um coisa diferente.
Dentro do HTML:
Eu vou percorre cada um repositorio, e para cada um dos repositorio eu quero retorna alguma coisa.
`forEach` = Ele percorre cada um dos repositorios execulte uma fulção.
`map` = Ele percorre cada um dos repositorios e retorna alguma coisa.

Para cada repositorio eu quero retornar um repositorio item

```
{repositories.map(repository => {
    return <RepositoryItem repository={repository}/>
})}
```

Ou eu posso colocar parentes e omitir o return

```
{repositories.map(repository => (
    <RepositoryItem repository={repository}/>
))}
```
E quando o retorno tem uma linha só ou um retorno pequeno:

```
{repositories.map(repository => <RepositoryItem repository={repository}/>)}
```

Mais vamos usar a seguinte:

<h1 align="center">
    <img src="./img/img040.png" />
</h1>

E la no `RepositoryItem.jsx` vamos trocar de `link` para `html_url` 
E podemos ate remover o `?? 'Default'`.

E todas as vez que eu fizer um `map` em minha aplicação, eu priciso informa ao React atraves de uma propriedade, que o proprio React cria, chamada `key={}` qual e a informação unica entre cada repositorio. Por exempro eu não posso ter um repositorio com o nome repetido, então se eu usar o nome do repositorio como chave: `key={repository.name}`. Ele deixa de aprensentar o error no developer tools.

```
{repositories.map(repository => {
    return <RepositoryItem key={repository.name} repository={repository}/>
})}
```

## 4 Usando TypeScript:

### Fundamentos do TypeScript

E um super sete, sendo um conjunto de funcionalidades que adicionamos em cima de uma linguagem.

Exemplo:

Imagine que você tem uma função que vai retorna uma mensagem de boas vindas ao usuario:
Onde o nome dela e: `showWelcomeMessage`.
E ela recebe um parametro: `(user)`. que teria os dados do usuario.
E retornaria uma mensagem: `return`.
Com o texto: ` `Welcome ${user.name}, your e-mail is ${user.email}`; `

```
function showWelcomeMessage(user) {
    return `Welcome ${user.name}, your e-mail is ${user.email}`;
}
```

E para evitar error adicionamos uma tipagem, como qual o formato que estamos esperando dentro da minha função:

Exemplo:
Definir um tipo para o usuario, e sempre definimos com a primeira letra maiuscula. e definindo o tipo de objeto com `type`.
E se quiser dizer que o estado não e obrigatorio eu uso `?` do lado de state `state?`.
E vou falar para meu `(user)` da função precisa segui o formato do User do `type` ficando assim `(user: User)`.

```
type User = {
    name: string
    email: string
    address: {
        city: string
        state?: string
    }
}

function showWelcomeMessage(user: User) {
    return `Welcome ${user.name}, your e-mail is ${user.email}, your city is ${user.address.city}, and your state is ${user.address.state}`;
}
```

Mais não precisamos tipar todas as variaves da aplicação, pois o typescript tem inferencia de tipos conseguindo indentifica qual a variavel na maioria dos casos.

### TypeScript no ReactJS

Configura o typescript para ser usado na aplicação.
tem a finalidade de tipar as propriedade que um componete pode ter.

Vamos instalar TypeScript n aplicação como dependencia de desenvolvimento:

```yarn add typescript -D```

Logo apos instalado vamois rodar um comando:

```yarn tsc --init```

Que ira inicia o typescript na aplicação.

Agora vamos configura o arquivo criado `tsconfig.json`
Vamos descomentar o `"lib":[],`
E adicionar nele tres biblioteca.

```
"lib": ["dom", "dom.iterable", "esnext"],
```

Vamos selecionar todas `/*` com `Ctrl + Shit + L` ele ira selecionar todos.

Ai podemos ir ate final da linha e deletar.

Vamos descomentar o `"allowJs": true,`

Vamos descomentar o `"allowSyntheticDefaultImports": true,`

Vamos descomentar o `"skipLibCheck": true `

Vamos descomentar o `"esModuleInterop": true,`

Vamos descomentar o `"strict": true, `

Vamos descomentar o `"forceConsistentCasingInFileNames": true,`

Vamos descomentar o `"moduleResolution": "node",`

Vamos descomentar o `"resolveJsonModule": true,`

Vamos descomentar o `"isolatedModules": true,`

Vamos descomentar o `"noEmit": true,`

Vamos descomentar o `"jsx": "preserve",` e troca o nome `"jsx": "react-jsx",`

Agora podemos remove o restante e a função `"target": "es2016",` , `"module": "commonjs", ` que elas não serão usadas.

Fica assim:

<h1 align="center">
    <img src="./img/img041.png" />
</h1>

Agora vamos continuar a configuração dontro do `webpack.config.js` porque o `'babel-loader'` não consegui interpleta codigo typescript.
E para o `'babel-loader'` entenda codigos typescript, vamos adiciona mais uma configuração:

Vamos instalar o @babel/preset-typescript como dependencia de desenvolvimento:

```yarn add @babel/preset-typescript -D```

Agora vamos no arquivo `babel.config.js` e adiciona `'@babel/preset-typescript',`

<h1 align="center">
    <img src="./img/img042.png" />
</h1>

E dentro do `webpack.config.js` vamos mudar para que seja compreendido tanto o `javascript` quanto `typescript` e em `test: /\. tsx$/,` vamos fazer a seguinte alteração: `test: /\. (j | t)sx$/,` dentro de uma expresão regular onde essa `|` que dizer ou.

E no `resolve` precisamos acrescentar o `'.ts', '.tsx'` dentro do `extensions: ['.js', '.jsx', '.ts', '.tsx'],`. 

E mudar o `entry:` mudando ele para `'index.tsx'`.

<h1 align="center">
    <img src="./img/img043.png" />
</h1>

E agora mudar o arquivo `index.jsx` para `index.tsx`.

Essa mudança vai gera um error, porque quando instalamos o typescript em nossa aplicação por não incluir umas definições de tipo do typescript, ou seja ela não inclui toda a parte do typescript precisa para entender como a blioteca funciona.

Vamos instalar o @types/react-dom como dependencia de desenvolvimento:

```yarn add @types/react-dom -D```

```yarn add @types/react -D```

E vamos execulta a aplicação pra ver se tudo esta funcionando:

`yarn dev`

### Componentes com TypeScript

Configura os componetes que estão em jsx para tsx.

Vamos começa com `App.jsx` porque e so tranforma em `tsx`, assim: `App.tsx`.

Agora vamos para o `RepositoryItem.jsx`, `tsx` assim: `RepositoryItem.tsx`.

E ja apresentou um erro, mostrando que o `props` recebe um any, `any` segnifica qualquer tipo, e que dizer que ele não sabe o tipo de desse `props`.

<h1 align="center">
    <img src="./img/img044.png" />
</h1>

Vamos começas fazendo uma `interface` com o nome do componete `RepositoryItemProps` com o Props no final.

E vou receber dentro do props: 
```
repository: {
    name: string;
    description: string;
    html_url: string;
  }
```

E vamos copiar o `RepositoryItemProps` e colocar no `props`.
Como `(props: RepositoryItemProps)`, falando que o formato do props e o fomato que esta dentro do `RepositoryItemProps`.

<h1 align="center">
    <img src="./img/img045.png" />
</h1>

E dentro do `RepositoryList.jsx`, vamos começa alterando para `tsx` ficando `RepositoryList.tsx`.

Vamos fazendo uma `interface` com o nome do componete `Repository`.
e adicionar dentro de useState o nome da interfaces `Repository[]`, ficando assim: `useState<Repository[]>([])`.

<h1 align="center">
    <img src="./img/img046.png" />
</h1>

## 5 Finalizando Aplicação:

### Utilizando React DevTools

Vamos ate as Extensões do Browser e procura por React DevTools.
Essa extençao vai me ajudar no DevTools:

`Components` ver a arvore react.

`Profiler` anotar todos os componetes exibidos em tela, quanto tempo demora para exibir.

### Finalização do módulo