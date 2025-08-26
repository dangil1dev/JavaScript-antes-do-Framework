## Renomeando Exportações em JavaScript

Nesta aula, vamos ver como renomear as exportações de um módulo JavaScript. Essa técnica é útil quando você precisa evitar conflitos de nomes ou simplesmente deseja usar um nome mais descritivo no arquivo de importação.

Para demonstrar, continuaremos usando os arquivos `calc.js` e `main.js` da aula anterior.

-----

### Renomeando uma Exportação Nomeada

Em uma **exportação nomeada**, a sintaxe `export { nome as novoNome }` permite que você altere o nome da função (ou variável/classe) no momento em que ela é exportada.

**Exemplo em `calc.js`:**

Vamos voltar a exportar nossas funções no final do arquivo e renomeá-las.

```javascript
// calc.js

function sum(a, b) {
    return a + b;
}

function multiply(a, b) {
    return a * b;
}

// Renomeia as funções 'sum' e 'multiply' no momento da exportação
export {
  sum as sumTwoNumbers,
  multiply as multiplyTwoNumbers
};
```

Neste código, a função `sum` é exportada com o nome `sumTwoNumbers`, e a função `multiply` com o nome `multiplyTwoNumbers`.

**Importação em `main.js`:**

Agora, no arquivo `main.js`, não podemos mais importar usando os nomes originais (`sum` e `multiply`). Precisamos usar os novos nomes definidos na exportação.

```javascript
// main.js

// Importa as funções usando os novos nomes definidos na exportação
import { sumTwoNumbers, multiplyTwoNumbers } from './calc.js';

console.log("4 + 6 =", sumTwoNumbers(4, 6)); // Agora usamos o novo nome
console.log("4 * 6 =", multiplyTwoNumbers(4, 6)); // Agora usamos o novo nome
```

Se você tentar importar `sum` ou `multiply`, o JavaScript gerará um erro, pois esses nomes não são mais exportados pelo módulo.

-----

### Observação sobre a Importação Padrão (`default`)

A exportação padrão já possui essa flexibilidade por natureza. Como vimos na aula anterior, você pode dar qualquer nome a ela na importação, sem precisar renomeá-la no momento da exportação.

```javascript
// calc.js (exemplo de exportação default)
export default function sum(a, b) {
    return a + b;
}

// main.js
import mySum from './calc.js'; // Renomeamos 'sum' para 'mySum' na importação
console.log(mySum(5, 5));
```

-----

### Resumo das Formas de Renomeação:

  * **Exportação Nomeada**: Renomeie a exportação no arquivo de origem usando a sintaxe `export { originalName as newName }`. O nome importado deve ser o `newName`.
  * **Exportação Padrão**: Renomeie a importação no arquivo de destino, dando a ela o nome que desejar.

