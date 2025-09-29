### Configurando `targets` e Outros Presets no Babel

Nesta aula, você aprendeu a importância do arquivo **`babel.config.js`** para personalizar o comportamento do Babel. Além de apenas carregar o `preset-env`, é possível configurar opções específicas para atender às necessidades do seu projeto, como definir quais navegadores você quer dar suporte.

### Configurando Alvos (`targets`)

A principal configuração mostrada foi a propriedade **`targets`**. Ao envolver o preset `preset-env` em um array e adicionar um objeto de configurações, você pode especificar exatamente quais versões de navegadores sua aplicação deve suportar.

**Exemplo:**

```javascript
const presets = [
  [
    "@babel/preset-env",
    {
      "targets": {
        "edge": "17",
        "firefox": "60",
        "chrome": "67",
        "safari": "11.1"
      }
    }
  ]
];

module.exports = { presets };
```

Essas configurações instruem o Babel a transpilar o código apenas o suficiente para que ele funcione nos navegadores e versões especificadas, o que pode otimizar a velocidade da compilação e o tamanho do arquivo final.

### Otimizando Scripts no `package.json`

O instrutor também mostrou uma boa prática para organizar seus scripts no `package.json`:

  * **`build`:** Use este script para uma compilação única, sem o modo de observação (`--watch`).
  * **`dev`:** Use este script para o desenvolvimento, incluindo o modo de observação (`--watch`) para recompilar automaticamente a cada alteração.

**Exemplo:**

```json
"scripts": {
    "build": "babel main.js --out-dir dist",
    "dev": "babel main.js --out-dir dist --watch"
}
```

Isso torna o fluxo de trabalho mais claro e eficiente, permitindo que você escolha entre uma compilação de produção ou um ambiente de desenvolvimento rápido.

### O Poder da Documentação

A aula reforçou a importância de consultar a documentação oficial do Babel (`babeljs.io`). Ela é a fonte mais confiável para encontrar todas as propriedades e opções de configuração disponíveis, garantindo que você utilize as funcionalidades mais recentes e corretas. Embora não seja necessário saber todas as propriedades de cor, é crucial saber que elas existem e onde procurá-las.

