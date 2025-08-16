### Introdução ao método `map()`

O método `map()` é uma ferramenta poderosa em JavaScript para percorrer e manipular arrays. Sua principal característica é a capacidade de criar um **novo array** a partir de um array existente, sem modificar o original.

### Como funciona

O método `map()` recebe uma **função de callback** como parâmetro. Essa função é executada para cada elemento do array original, em ordem. O que a função de callback retorna em cada execução se torna o valor do novo array, na mesma posição.

**Estrutura básica:**

```javascript
// Array original
const produtos = ['teclado', 'mouse', 'monitor'];

// Usando o método map() com uma função de callback
produtos.map(item => {
  // Ações a serem realizadas para cada item
});
```

### Sintaxe e Uso

Existem duas formas principais de usar a função de callback:

1.  **Com chaves (`{}`):**
    Use esta opção quando precisar realizar uma lógica mais complexa ou várias operações antes de retornar um valor.

    ```javascript
    produtos.map(product => {
      // Lógica de manipulação
      return product.toUpperCase();
    });
    ```

2.  **Sintaxe reduzida (sem chaves):**
    Use esta opção para um retorno simples e direto.

    ```javascript
    produtos.map(product => product.toUpperCase());
    ```

### Criando um novo array com objetos

Um dos usos mais comuns do `map()` é transformar um array de strings em um array de objetos. Isso permite enriquecer os dados com novas propriedades, como um ID aleatório, uma descrição ou um preço.

**Exemplo:**

```javascript
// Array de strings
const produtos = ['teclado', 'mouse', 'monitor'];

// Transformando em um array de objetos
const produtosFormatados = produtos.map(produto => ({
  id: Math.random(),
  description: produto,
}));

// Resultado:
// [
//   { id: 0.12345, description: 'teclado' },
//   { id: 0.67890, description: 'mouse' },
//   { id: 0.54321, description: 'monitor' }
// ]
```

### Resumo

  - O método `map()` percorre cada elemento de um array.
  - Ele executa uma função de callback para cada elemento.
  - O retorno da função de callback é adicionado a um **novo array**.
  - É ideal para manipular dados de arrays e criar novas estruturas, como arrays de objetos.
