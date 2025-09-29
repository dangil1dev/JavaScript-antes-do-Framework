### Passo 1: Instalar o Plugin

Primeiro, você precisa instalar o `html-webpack-plugin` como uma **dependência de desenvolvimento**. Abra seu terminal na pasta do projeto e execute o seguinte comando:

```bash
npm install --save-dev html-webpack-plugin
```

### Passo 2: Importar o Plugin

Agora, abra seu arquivo de configuração do Webpack, o **`webpack.config.js`**, e adicione a importação do plugin no topo do arquivo. É importante usar a sintaxe `require()` pois estamos no ambiente do Node.js.

```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin'); // Importação do plugin

module.exports = {
  // ...
};
```

### Passo 3: Adicionar o Plugin à Configuração

Dentro do objeto que você exporta em **`webpack.config.js`**, adicione a propriedade `plugins`. Essa propriedade é um **array** onde você pode listar todos os plugins que o Webpack deve usar. Para o `html-webpack-plugin`, você cria uma nova instância dele.

```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/js/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
  mode: 'development',
  plugins: [
    new HtmlWebpackPlugin() // Adicionando o plugin ao array
  ],
};
```

### Passo 4: Executar o Build

Com a configuração feita, é só rodar o comando de build. No terminal, execute:

```bash
npm run build
```

O Webpack vai empacotar seu código JavaScript, e graças ao plugin, ele também vai gerar um arquivo **`index.html`** dentro da pasta `dist`. A melhor parte é que o `script` com a referência para o seu `main.js` já estará magicamente inserido nesse HTML.

Agora você pode abrir o `index.html` da pasta `dist` no seu navegador para ver o resultado final do seu projeto empacotado, com HTML e JavaScript funcionando juntos.
