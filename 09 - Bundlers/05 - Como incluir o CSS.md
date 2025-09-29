### Passo 1: Criar o arquivo CSS

Primeiro, organize seu código CSS. Dentro da pasta **`src`**, crie uma nova pasta chamada **`css`** e, dentro dela, um arquivo **`styles.css`**. Adicione alguns estilos para testar, como:

```css
body {
  background-color: #000;
  color: #fff;
}

h1 {
  text-transform: uppercase;
}
```

### Passo 2: Importar o CSS no JavaScript

Para que o Webpack reconheça o arquivo CSS, você deve importá-lo em seu arquivo JavaScript principal (por exemplo, **`src/js/index.js`**). Isso permite que o Webpack inclua o CSS em seu grafo de dependências.

```javascript
import '../css/styles.css';
```

Ao fazer isso, o Webpack tentará processar o arquivo CSS. No entanto, por padrão, ele não sabe como lidar com esse tipo de arquivo, e é por isso que precisamos dos **loaders**.

### Passo 3: Instalar os Loaders necessários

Para que o Webpack consiga ler e empacotar arquivos CSS, você precisa instalar os loaders `css-loader` e `style-loader` como dependências de desenvolvimento.

  * **`css-loader`**: Este loader interpreta o `@import` e o `url()` em arquivos CSS, como se fossem `require()` do JavaScript.
  * **`style-loader`**: Este loader injeta o CSS no DOM da página, usando tags `<style>`.

Abra o terminal e execute o comando de instalação:

```bash
npm install --save-dev css-loader style-loader
```

### Passo 4: Adicionar a regra de CSS no `webpack.config.js`

Agora, no seu arquivo **`webpack.config.js`**, você precisa adicionar uma nova regra para que o Webpack saiba o que fazer com os arquivos CSS. Você faz isso dentro de uma nova propriedade chamada `module`.

A regra deve incluir:

  * `test`: Uma expressão regular que identifica os arquivos `.css`.
  * `use`: Um array que especifica quais loaders usar para esses arquivos. A ordem é importante — o Webpack executa os loaders da direita para a esquerda, então o `css-loader` deve vir antes do `style-loader`.

Seu arquivo de configuração deve ficar assim:

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
    new HtmlWebpackPlugin()
  ],
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
};
```

Você também pode usar a propriedade `exclude` para evitar que o Webpack processe arquivos CSS da pasta `node_modules`, o que pode otimizar o processo de build:

```javascript
// ...
module: {
  rules: [
    {
      test: /\.css$/,
      exclude: /node_modules/,
      use: ['style-loader', 'css-loader'],
    },
  ],
},
// ...
```

### Passo 5: Executar o Build

Com tudo configurado, basta rodar o comando de build no terminal:

```bash
npm run build
```

Agora, o Webpack vai empacotar seu JavaScript e seu CSS. Você não verá um arquivo **`styles.css`** na pasta `dist` porque o `style-loader` injeta o CSS diretamente no DOM, dentro do arquivo `main.js`. Ao abrir o **`index.html`** da pasta `dist`, você verá os estilos aplicados na sua página.
