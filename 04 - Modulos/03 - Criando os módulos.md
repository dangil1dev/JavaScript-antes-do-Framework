## Criando Nosso Primeiro Módulo JavaScript

Nesta aula, vamos colocar a mão na massa e criar nosso primeiro módulo em JavaScript, entendendo na prática como organizar o código em arquivos separados e como compartilhar funcionalidades entre eles usando **ES Modules (ESM)**.

-----

### Estrutura do Projeto

Vamos começar com uma estrutura de projeto simples, que inclui um arquivo HTML e um arquivo JavaScript principal:

  * **`index.html`**: O arquivo principal da nossa aplicação web.
  * **`main.js`**: Nosso arquivo de script principal. Para facilitar a organização e indicar sua função central, vamos **renomear** o arquivo de `scripts.js` para `main.js`.

**Conteúdo de `index.html`:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Módulos JavaScript</title>
</head>
<body>
    <h1>Primeiro Módulo JavaScript</h1>

    <script src="main.js" type="module"></script>
</body>
</html>
```

**Importante:** Observe a adição do atributo `type="module"` na tag `<script>` que carrega o `main.js`. Isso é **essencial** para que o navegador entenda que o arquivo `main.js` (e, consequentemente, todos os módulos que ele importar) deve ser tratado como um módulo JavaScript. Sem isso, as sintaxes `import` e `export` não funcionarão e você verá erros no console.

-----

### Criando o Módulo `calc.js`

Para demonstrar a modularização, vamos criar um novo arquivo chamado `calc.js`. Este módulo será responsável por funcionalidades de cálculo.

**Conteúdo de `calc.js`:**

```javascript
// Função para somar dois números
function sum(a, b) {
    return a + b;
}

// Função para multiplicar dois números
function multiply(a, b) {
    return a * b;
}

// Exportando as funções para que possam ser usadas em outros módulos
export { sum, multiply };

// Alternativamente, você poderia exportar individualmente:
// export function sum(a, b) {
//     return a + b;
// }
// export function multiply(a, b) {
//     return a * b;
// }
```

No `calc.js`, definimos duas funções simples: `sum` e `multiply`. Para que essas funções possam ser utilizadas fora deste arquivo (ou seja, em outros módulos como `main.js`), precisamos **exportá-las**. A palavra-chave `export` sinaliza quais funcionalidades de um módulo estão disponíveis para o mundo exterior. Você pode exportar funções individualmente ou agrupá-las em um único `export` no final do arquivo.

-----

### Utilizando o Módulo em `main.js`

Agora que criamos e exportamos as funções do nosso módulo `calc.js`, vamos importá-las e utilizá-las no nosso arquivo principal, `main.js`.

**Conteúdo de `main.js`:**

```javascript
// Importa as funções 'sum' e 'multiply' do módulo './calc.js'
import { sum, multiply } from './calc.js';

console.log("4 + 6 =", sum(4, 6));         // Saída: 4 + 6 = 10
console.log("4 * 6 =", multiply(4, 6));    // Saída: 4 * 6 = 24
```

No `main.js`, usamos a palavra-chave `import` para trazer as funções `sum` e `multiply`.

  * `import { sum, multiply }`: Indica quais funcionalidades específicas queremos importar do módulo. As chaves são usadas porque estamos importando **exports nomeados**.
  * `from './calc.js'`: Especifica o caminho para o módulo de onde queremos importar. O `./` indica que o arquivo `calc.js` está no mesmo diretório que `main.js`.

Se você abrir o `index.html` no seu navegador, deverá ver os resultados das operações no console do desenvolvedor. Isso demonstra que as funções definidas no `calc.js` foram importadas e executadas com sucesso no `main.js`.

-----

### Pontos Chave para Lembrar:

  * **`export`**: Usado no arquivo do módulo (`calc.js`) para tornar funções, variáveis ou classes disponíveis para outros módulos. Se algo não é exportado, ele permanece privado dentro do módulo.
  * **`import`**: Usado em outro arquivo (`main.js`) para acessar as funcionalidades exportadas de um módulo.
  * **`type="module"`**: **Crucial** no HTML, na tag `<script>` que carrega o script principal. Isso diz ao navegador para tratar o arquivo como um módulo e habilitar as sintaxes `import` e `export`.
  * **Caminho do Módulo**: Ao importar, você precisa especificar o caminho correto para o arquivo do módulo (`./calc.js` para arquivos no mesmo diretório, ou caminhos relativos/absolutos, dependendo da estrutura do seu projeto).

Com essa configuração, você deu o primeiro passo na modularização do seu código JavaScript, tornando seus projetos mais organizados e escaláveis\!
