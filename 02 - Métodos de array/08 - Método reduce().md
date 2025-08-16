O método **`reduce()`** é uma ferramenta poderosa para "reduzir" um array a um **único valor**. O nome vem da sua função: ele processa cada elemento do array para, no final, retornar um resultado acumulado, como uma soma, um produto, ou até mesmo um novo objeto.

-----

### Entendendo os parâmetros

O `reduce()` recebe uma função de callback que tem os seguintes parâmetros:

  - **Acumulador (`accumulator`):** É o valor que está sendo "acumulado" a cada iteração. Ele armazena o resultado da iteração anterior.
  - **Valor Atual (`currentValue`):** É o valor do elemento do array que está sendo processado na iteração atual.
  - **Índice (`index`):** (Opcional) A posição do elemento atual.
  - **Valor Inicial (`initialValue`):** (Opcional) Um valor com o qual o acumulador deve começar. Se não for fornecido, o acumulador começará com o primeiro elemento do array.

A sintaxe básica é:
`array.reduce(callback(acumulador, valorAtual, indice), valorInicial)`

-----

### Exemplo prático: Somando valores

O uso mais comum do `reduce()` é para somar todos os números em um array.

```javascript
const valores = [1, 2, 3, 4, 5];

const soma = valores.reduce((acumulador, valorAtual) => {
  return acumulador + valorAtual;
}, 0); // O valor inicial é 0

console.log(soma);
// Saída: 15
```

Vamos entender o processo passo a passo com o **valor inicial 0**:

1.  **Iteração 1:**

      - `acumulador` = 0 (valor inicial)
      - `valorAtual` = 1
      - Retorno = `0 + 1` = **1**

2.  **Iteração 2:**

      - `acumulador` = 1 (resultado da iteração anterior)
      - `valorAtual` = 2
      - Retorno = `1 + 2` = **3**

3.  **Iteração 3:**

      - `acumulador` = 3
      - `valorAtual` = 3
      - Retorno = `3 + 3` = **6**

4.  **Iteração 4:**

      - `acumulador` = 6
      - `valorAtual` = 4
      - Retorno = `6 + 4` = **10**

5.  **Iteração 5:**

      - `acumulador` = 10
      - `valorAtual` = 5
      - Retorno = `10 + 5` = **15**

O método termina, e o valor final **15** é retornado.

O `reduce()` é uma ferramenta versátil para qualquer operação que precise consolidar os elementos de um array em um único resultado.
