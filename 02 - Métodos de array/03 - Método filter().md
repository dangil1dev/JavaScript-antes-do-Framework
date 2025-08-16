O método `filter()` é usado para criar um **novo array** contendo apenas os elementos do array original que atendem a uma condição específica. Ele não modifica o array original.

-----

### Como funciona

O `filter()` recebe uma função de callback que é executada para cada elemento do array. Essa função deve retornar um valor `boolean` (`true` ou `false`).

  - Se a função de callback retorna `true`, o elemento atual é incluído no novo array.
  - Se a função retorna `false`, o elemento é descartado.

A estrutura é semelhante a outros métodos de array, como o `map()`:

```javascript
array.filter(elemento => {
  // Lógica de condição
  return condicao; // Retorna true ou false
});
```

-----

### Exemplos práticos

#### 1\. Filtrando por comprimento de string

Vamos supor que você tem um array de palavras e quer um novo array com apenas as palavras que têm mais de 3 letras.

```javascript
const palavras = ['JavaScript', 'HTML', 'CSS', 'web'];

const resultado = palavras.filter(palavra => palavra.length > 3);

console.log(resultado);
// Saída: ['JavaScript', 'HTML']
```

Neste exemplo, 'JavaScript' e 'HTML' foram incluídas porque a condição `palavra.length > 3` é verdadeira para elas. 'CSS' e 'web' foram ignoradas, pois têm 3 letras ou menos.

#### 2\. Filtrando objetos em um array

Você pode aplicar o `filter()` em um array de objetos para selecionar itens com base em uma propriedade.

```javascript
const produtos = [
  { description: 'teclado', price: 150, promotion: true },
  { description: 'mouse', price: 70, promotion: false },
  { description: 'monitor', price: 900, promotion: true }
];

// Filtrando produtos em promoção
const produtosEmPromocao = produtos.filter(produto => produto.promotion === true);

console.log(produtosEmPromocao);
// Saída:
// [
//   { description: 'teclado', price: 150, promotion: true },
//   { description: 'monitor', price: 900, promotion: true }
// ]
```

Neste caso, a condição é `produto.promotion === true`. Somente os objetos onde essa propriedade é verdadeira são incluídos no novo array.
