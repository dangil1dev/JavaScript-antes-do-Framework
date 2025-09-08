### Organização de Projeto

Uma convenção comum para organizar projetos é usar a pasta **`src`** (de *source*) para armazenar todos os arquivos de desenvolvimento. Isso ajuda a separar o código que você cria dos arquivos de configuração do projeto, que geralmente ficam na pasta raiz.

Dentro de `src`, você pode criar subpastas para organizar seus arquivos por tipo, como a pasta `js` para os arquivos JavaScript.

### Instalando o Webpack

Para instalar o Webpack, você usará o NPM (Node Package Manager).

1.  Abra o terminal na pasta raiz do seu projeto.
2.  Execute o comando:

<!-- end list -->

```bash
npm install --save-dev webpack webpack-cli
```

  * `webpack`: O pacote principal do Webpack.
  * `webpack-cli`: Fornece a interface de linha de comando para executar o Webpack.
  * `--save-dev`: Sinaliza que esses pacotes são dependências de desenvolvimento, ou seja, são necessários para o processo de build, mas não para a aplicação final.

### Empacotando com o Webpack

Para que o Webpack funcione, você precisa criar um script de `build` no seu arquivo `package.json`. Esse script dirá ao Webpack qual é o arquivo de entrada da sua aplicação.

1.  **Crie o script `build`**:

    ```json
    "scripts": {
      "build": "webpack ./src/js/index.js"
    }
    ```

      * `webpack`: Inicia o processo de empacotamento.
      * `./src/js/index.js`: Este é o seu arquivo de entrada. É a partir dele que o Webpack constrói o gráfico de dependências, identificando e agrupando todos os arquivos importados.

2.  **Execute o script**:

    ```bash
    npm run build
    ```

### O Resultado da Compilação

Após executar o comando, o Webpack irá:

1.  Analisar o arquivo `index.js` e todas as suas dependências.
2.  Agrupar todo o código em um único arquivo de saída, chamado **`main.js`**, que ele cria dentro de uma nova pasta chamada **`dist`**.

A pasta `dist` é o diretório de distribuição. É nela que o Webpack coloca a versão final e otimizada do seu projeto, pronta para ser usada em produção.

Ao inspecionar o `main.js` na pasta `dist`, você verá que todo o código dos seus arquivos de origem (como `index.js` e `components.js`) foi combinado em um único arquivo. Isso demonstra como o Webpack resolve as dependências e empacota seu código para otimizar o carregamento no navegador.

