### Passo 1: Instalar as dependências do Babel

Primeiro, você precisa instalar os pacotes necessários do Babel como **dependências de desenvolvimento**. Cada um tem uma função específica:

  * **`@babel/core`**: O motor principal do Babel que realiza a transpilação.
  * **`@babel/preset-env`**: Um "preset" que agrupa vários plugins para transpilar o JavaScript moderno (ES2015+) para o ES5, com base nos ambientes de destino que você especificar.
  * **`babel-loader`**: O loader que o Webpack usa para integrar o Babel ao processo de empacotamento.

Abra o terminal e execute o seguinte comando:

```bash
npm install --save-dev @babel/core @babel/preset-env babel-loader
```

### Passo 2: Adicionar a regra do Babel no `webpack.config.js`

Agora, no seu arquivo de configuração do Webpack, o **`webpack.config.js`**, adicione uma nova regra no array `rules` dentro da propriedade `module`. Esta regra vai instruir o Webpack a usar o `babel-loader` em todos os seus arquivos JavaScript.

  * `test`: Uma expressão regular para identificar os arquivos `.js`.
  * `exclude`: Uma regra para ignorar a pasta `node_modules`, que geralmente não precisa de transpilação.
  * `use`: Um objeto com as configurações do loader.
      * `loader`: Especifica que você quer usar o `babel-loader`.
      * `options`: Um objeto que passa configurações para o Babel, como o `presets` que você instalou. O `@babel/preset-env` é o mais comum, e `targets` como `'defaults'` garantem compatibilidade com a maioria dos navegadores.

Sua configuração deve ficar parecida com esta:

```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  // ...
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env'],
          },
        },
      },
    ],
  },
};
```

### Passo 3: Executar o Build

Com a configuração completa, basta rodar o comando de build no terminal.

```bash
npm run build
```

O Webpack vai empacotar sua aplicação, passando todos os arquivos JavaScript pelo Babel antes de gerar o código final. Se o processo for concluído com sucesso, o terminal exibirá uma mensagem de "Completed" e seu código estará pronto para rodar em diversos navegadores\!
