## Deep Freeze em JavaScript

Nesta aula, exploraremos o conceito de **Deep Freeze** em JavaScript, que consiste em congelar um objeto de forma profunda, percorrendo recursivamente cada propriedade. Aprenderemos a criar uma função recursiva para congelar todas as propriedades de um objeto, garantindo um congelamento completo.

-----

### Entendendo a Limitação do `Object.freeze()`

Primeiro, vamos criar um objeto de exemplo para entender a diferença entre o congelamento raso e o profundo.

```javascript
const book = {
  title: 'Objetos Imutáveis',
  category: 'JavaScript',
  author: {
    name: 'Rodrigo',
    email: 'rodrigo@email.com'
  }
};
```

Quando usamos o `Object.freeze()` diretamente, ele realiza um **congelamento raso**. Isso significa que apenas as propriedades do primeiro nível do objeto são congeladas. Propriedades que são objetos aninhados não são afetadas.

```javascript
Object.freeze(book);

// Tentativa de alterar uma propriedade de primeiro nível:
book.category = 'CSS'; // Não funciona

// Tentativa de alterar uma propriedade de um objeto aninhado:
book.author.name = 'João'; // Funciona!
```

Como podemos ver no exemplo acima, a propriedade `category` não pode ser alterada, mas a propriedade `name` dentro do objeto `author` pode. O congelamento raso protege o primeiro nível de propriedades, mas não os objetos aninhados.

-----

### Criando a Função `deepFreeze()`

Para resolver essa limitação, precisamos criar uma função recursiva que percorra todas as propriedades, incluindo as aninhadas.

```javascript
function deepFreeze(obj) {
  // Obtém todas as chaves (propriedades) do objeto
  const props = Reflect.ownKeys(obj);

  // Itera sobre cada propriedade
  for (const prop of props) {
    const value = obj[prop];

    // Verifica se o valor da propriedade é um objeto ou função
    if ((value && typeof value === 'object') || typeof value === 'function') {
      // Chama a função deepFreeze recursivamente para o objeto aninhado
      deepFreeze(value);
    }
  }

  // Congela o objeto atual
  return Object.freeze(obj);
}
```

#### Passo a Passo da Função

1.  **Obter as propriedades**: `Reflect.ownKeys(obj)` retorna um array com todas as chaves (nomes das propriedades) do objeto.
2.  **Iterar sobre as propriedades**: Um loop `for...of` é usado para percorrer cada propriedade no array `props`.
3.  **Obter o valor**: Dentro do loop, `obj[prop]` obtém o valor associado à propriedade atual.
4.  **Verificação recursiva**: A condição `(value && typeof value === 'object') || typeof value === 'function'` verifica se o valor é um objeto ou uma função.
      - Se for, a função **`deepFreeze()` é chamada novamente (recursivamente)**, passando o objeto aninhado como parâmetro. Isso garante que todos os níveis de objetos e funções sejam processados.
5.  **Congelar o objeto**: Após o loop terminar (ou seja, todas as propriedades aninhadas já tiverem sido processadas), `Object.freeze(obj)` é chamado para congelar o objeto atual.

-----

### Testando o `deepFreeze()`

Agora, vamos aplicar a nossa nova função ao objeto `book`.

```javascript
deepFreeze(book);

// Tentativa de alteração de propriedade de primeiro nível:
book.category = 'HTML'; // Não funciona

// Tentativa de alteração de propriedade de objeto aninhado:
book.author.name = 'João'; // Não funciona!
```

Ao executar o código, você verá que nenhuma das alterações é aplicada. O `deepFreeze()` garantiu que todas as propriedades, em todos os níveis do objeto, fossem completamente imutáveis.

### Resumo

  - O **`Object.freeze()`** padrão em JavaScript realiza um **congelamento raso**, protegendo apenas as propriedades de primeiro nível de um objeto.
  - Para obter um **congelamento profundo**, é necessário criar uma função recursiva, como a **`deepFreeze()`**, que percorre todas as propriedades de um objeto e chama a si mesma para congelar os objetos aninhados.
  - Essa técnica é fundamental para garantir a **imutabilidade completa** de estruturas de dados complexas, prevenindo alterações indesejadas e bugs.
