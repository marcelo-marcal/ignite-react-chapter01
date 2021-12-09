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


