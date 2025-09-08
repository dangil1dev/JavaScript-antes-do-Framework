Ótimo\! Você concluiu a instalação e configuração do Babel, entendendo o papel crucial do compilador na garantia de compatibilidade do código.

-----

## Configurando e Executando o Babel

Para que o Babel funcione, ele precisa saber quais regras de transpilação (ou **presets**) usar.

### 1\. Configurando o Babel

Você cria o arquivo de configuração **`babel.config.js`** na raiz do seu projeto. O Babel o identifica automaticamente e aplica as configurações definidas.

1.  **Crie o arquivo:** `babel.config.js`
2.  **Defina a configuração:** Use o `@babel/preset-env`.

<!-- end list -->

```javascript
const presets = [
  "@babel/preset-env" // Transpila código JS moderno para versões mais compatíveis (Ex: ES5).
];

// Exporta as configurações para o Babel
module.exports = {
  presets
};
```

### 2\. Executando a Compilação

Para executar o Babel e compilar seu código, você usa o comando CLI (Command Line Interface) do Babel diretamente no terminal.

1.  **Estrutura do comando:** Você aponta o executável do Babel, o arquivo de entrada (`main.js`) e especifica a pasta de saída (`--out-dir dist`).

<!-- end list -->

```bash
# Executa o Babel para compilar o main.js e salvar o resultado na pasta dist
./node_modules/.bin/babel main.js --out-dir dist
```

  * **`./node_modules/.bin/babel`**: Este é o caminho para o executável do Babel que foi instalado dentro da sua pasta `node_modules`.

### 3\. Visualizando o Resultado (Transpilação em Ação)

Ao executar o comando, o Babel cria a pasta **`dist`** e o arquivo compilado **`main.js`** dentro dela.

**Código de Entrada (Moderno em `main.js`):**

```javascript
class User {
  constructor(email) {
    this.email = email;
  }
}

let user = new User("rodrigo@email.com");
```

**Código de Saída (Compilado em `dist/main.js`):**

O Babel transforma a `class` (recurso moderno do ES6/ES2015) em uma função construtora do tipo ES5 e adiciona códigos de suporte (`use strict` e outras abstrações), garantindo que navegadores mais antigos possam executar o código sem problemas.

**Ponto Chave:** Você não precisa entender o código gerado\! O objetivo é apenas **entender o que o compilador faz**: ele pega seu código limpo e moderno e o transforma em algo compatível, automatizando o processo de retrocompatibilidade.

-----

Com o compilador configurado, o próximo passo é otimizar o carregamento do seu código, o que nos leva ao conceito de *bundlers*.
