O método **`findIndex()`** é uma função de array que retorna o **índice** do primeiro elemento que satisfaz uma condição específica. Se nenhum elemento atender à condição, ele retorna **-1**.

-----

### Como funciona

O `findIndex()` também utiliza uma função de callback que é executada para cada item do array. Dentro dessa função, você define a condição que o elemento deve satisfazer.

  - Se a condição for verdadeira para um elemento, o método para de procurar e retorna o índice desse elemento (lembre-se que os índices começam em 0).
  - Se a condição for falsa para todos os elementos após percorrer o array inteiro, o método retorna **-1**.

### Exemplos práticos

#### Encontrando o índice de um valor

Imagine que você tem um array de números e quer saber a posição do primeiro número maior que 4.

```javascript
const valores = [4, 6, 8, 12];

const indiceEncontrado = valores.findIndex(valor => valor > 4);

console.log(indiceEncontrado);
// Saída: 1
```

  - O método começa no índice 0, onde o valor é 4. A condição `4 > 4` é falsa.
  - Ele avança para o índice 1, onde o valor é 6. A condição `6 > 4` é verdadeira.
  - O método para e retorna o índice 1.

#### Quando o elemento não é encontrado

Se a condição não for satisfeita por nenhum elemento, o `findIndex()` retorna -1.

```javascript
const valores = [4, 6, 8, 12];

const indiceNaoEncontrado = valores.findIndex(valor => valor > 20);

console.log(indiceNaoEncontrado);
// Saída: -1
```

Neste caso, não há nenhum número no array que seja maior que 20, então o método retorna -1, indicando que a busca não teve sucesso.

### Resumo

O `findIndex()` é uma ótima ferramenta para encontrar a posição do primeiro elemento que corresponde a um critério no seu array. Use-o para saber a **localização** de um item, em vez do próprio item.
