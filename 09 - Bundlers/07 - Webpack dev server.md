### Passo 1: Instalar o Webpack Dev Server

Primeiro, você precisa instalar o pacote **`webpack-dev-server`** como uma dependência de desenvolvimento. Abra seu terminal na pasta do projeto e execute:

```bash
npm install --save-dev webpack-dev-server
```

### Passo 2: Configurar o `webpack.config.js`

Após a instalação, adicione a propriedade **`devServer`** ao seu arquivo **`webpack.config.js`**. Esta propriedade é um objeto que permite controlar o comportamento do servidor local.

Dentro de `devServer`, você pode definir as seguintes opções:

  * **`static`**: A partir de qual diretório o servidor deve servir os arquivos estáticos. O ideal é apontar para a sua pasta de saída (`dist`), pois é onde o Webpack compila todos os arquivos.
  * **`port`**: A porta em que o servidor irá rodar. Um valor comum é `3000`, mas você pode escolher qualquer porta disponível.
  * **`open`**: Uma flag booleana que, se definida como `true`, faz com que o navegador abra automaticamente a URL do servidor assim que ele for iniciado.

Seu arquivo de configuração deve ficar assim:

```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  // ... outras configurações (entry, output, mode, plugins, etc.)
  devServer: {
    static: {
      directory: path.join(__dirname, 'dist'),
    },
    port: 3000,
    open: true,
  },
};
```

### Passo 3: Criar um script de desenvolvimento

Para facilitar o uso, crie um novo script no seu arquivo **`package.json`**. Um nome comum para este script é **`dev`**. Ele deve executar o comando **`webpack serve`**.

```json
"scripts": {
  "build": "webpack",
  "dev": "webpack serve"
}
```

### Passo 4: Rodar o servidor

Agora, você pode iniciar o servidor de desenvolvimento a partir do terminal. Execute o seguinte comando:

```bash
npm run dev
```

Ao executar o comando, o Webpack Dev Server irá:

1.  Compilar seu código com as configurações do `webpack.config.js`.
2.  Iniciar um servidor local.
3.  Abrir o navegador automaticamente (se a opção `open` estiver como `true`).

A grande vantagem é que qualquer alteração nos seus arquivos de desenvolvimento (JS, CSS, etc.) será detectada e a página será recarregada automaticamente, sem a necessidade de rodar o `npm run dev` novamente. Isso torna o ciclo de desenvolvimento muito mais rápido e eficiente.
