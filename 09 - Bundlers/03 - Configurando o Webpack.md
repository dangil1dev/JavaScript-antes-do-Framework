## Configurando o Webpack: Um guia prático

A configuração padrão do Webpack é feita através de um arquivo chamado **`webpack.config.js`**, que deve ser criado na raiz do seu projeto. Separar as configurações neste arquivo torna seu script **`build`** no **`package.json`** mais limpo e permite um controle mais detalhado sobre o processo de empacotamento.

### 1\. Limpando o script no `package.json`

Primeiro, remova a configuração inline do Webpack no seu arquivo **`package.json`**. O script **`build`** deve ficar mais simples, apenas chamando o comando **`webpack`**:

```json
"scripts": {
  "build": "webpack"
}
```

Dessa forma, ao executar `npm run build`, o Webpack buscará automaticamente o arquivo de configuração na raiz do projeto.

### 2\. Criando o arquivo de configuração

Crie um novo arquivo na raiz do projeto chamado **`webpack.config.js`**. O nome é crucial, pois o Webpack procura por ele por padrão.

Dentro desse arquivo, você exportará um objeto com as configurações. Você pode fazer isso utilizando a sintaxe `module.exports = {}`.

```javascript
module.exports = {
  // Propriedades de configuração
};
```

### 3\. Definindo as propriedades de configuração

Dentro do objeto exportado, você pode definir as principais configurações para o Webpack.

#### **`entry` (Entrada)**

Essa propriedade define o arquivo JavaScript principal do seu projeto, a partir do qual o Webpack começará a construir o gráfico de dependências.

**Exemplo:**

```javascript
module.exports = {
  entry: './src/js/index.js'
};
```

#### **`output` (Saída)**

Esta propriedade determina onde e com qual nome o Webpack deve gerar o arquivo de saída empacotado. É um objeto que pode conter as seguintes subpropriedades:

  * **`filename`**: O nome do arquivo de saída. É comum usar nomes como `main.js` ou `bundle.js`.
  * **`path`**: O caminho do diretório onde o arquivo de saída será salvo. Para garantir compatibilidade entre diferentes sistemas operacionais (Windows, Linux, macOS), use o módulo **`path`** do Node.js.

**Exemplo:**

```javascript
const path = require('path');

module.exports = {
  entry: './src/js/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  }
};
```

O `path.resolve(__dirname, 'dist')` garante que o caminho para a pasta `dist` seja resolvido corretamente, independentemente do sistema operacional.

#### **`mode` (Modo)**

Essa propriedade informa ao Webpack o ambiente em que você está trabalhando, o que otimiza o empacotamento. As duas opções principais são:

  * **`'development'`**: Otimiza para velocidade de construção e oferece ferramentas úteis como debugging.
  * **`'production'`**: Otimiza o código para o menor tamanho possível, utilizando minificação e outras técnicas.

**Exemplo:**

```javascript
module.exports = {
  // ... outras configurações
  mode: 'development'
};
```

Se você não definir o modo, o Webpack emitirá um aviso no console.

### 4\. Resumo da configuração completa

Ao final, seu arquivo **`webpack.config.js`** ficará parecido com isso:

```javascript
const path = require('path');

module.exports = {
  entry: './src/js/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
  mode: 'development'
};
```

Com este arquivo configurado, basta executar `npm run build` no terminal. O Webpack usará as configurações que você definiu para empacotar seu código. O resultado será um arquivo `main.js` dentro da pasta `dist`, pronto para ser usado no seu projeto.
