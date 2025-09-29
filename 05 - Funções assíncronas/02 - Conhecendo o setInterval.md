-----

## Conhecendo o `setInterval()` em JavaScript

Nesta aula, vamos explorar o **`setInterval()`**, uma função em JavaScript muito similar ao `setTimeout()`, mas com uma diferença crucial: enquanto o `setTimeout()` executa uma função uma única vez após um tempo, o `setInterval()` a executa **repetidamente** em intervalos definidos.

-----

### O Que É `setInterval()` e Como Usá-lo?

A função **`setInterval()`** é ideal para tarefas que precisam ser repetidas, como um relógio digital, uma animação ou um contador. Ela recebe os mesmos dois parâmetros do `setTimeout()`:

1.  Uma **função** a ser executada.
2.  O **tempo** de intervalo em **milissegundos**.

A função fornecida no primeiro parâmetro será executada continuamente a cada intervalo de tempo especificado.

**Sintaxe:**

```javascript
setInterval(() => {
  // Código a ser repetido
}, tempoEmMilissegundos);
```

**Exemplo Prático: Um Contador Regressivo**

Para ilustrar o uso do `setInterval()`, vamos criar um contador regressivo simples.

```javascript
let value = 10;

// Inicia o intervalo que executa a função a cada 1 segundo (1000ms)
const interval = setInterval(() => {
  console.log(value);
  value--; // Decrementa o valor em 1

  // Condição para parar o contador
  if (value < 0) {
    console.log("Feliz Ano Novo!");
    clearInterval(interval); // Interrompe o intervalo de execuções
  }
}, 1000);
```

Neste código, a função dentro do `setInterval()` é executada a cada segundo. A cada execução, o valor de `value` é exibido e decrementado.

-----

### Controlando o `setInterval()` com `clearInterval()`

Diferentemente do `setTimeout()`, que para automaticamente, o `setInterval()` continuará a ser executado indefinidamente até que seja interrompido manualmente. Para isso, usamos a função **`clearInterval()`**.

Para interromper um intervalo, você precisa:

1.  Armazenar a referência do `setInterval()` em uma variável (neste exemplo, `interval`).
2.  Chamar **`clearInterval()`** e passar a variável como argumento.

No nosso exemplo do contador, a contagem para quando `value` chega a zero, evitando que o contador continue em números negativos.

-----

### `setInterval()` vs. `setTimeout()`: A Diferença Chave

  * **`setTimeout()`**: Executa a função **uma vez** após o tempo especificado. Pense nele como um "atraso".
  * **`setInterval()`**: Executa a função **repetidamente** em intervalos regulares. Pense nele como um "relógio".

Ambas as funções são essenciais para agendar tarefas em JavaScript, mas são usadas para propósitos diferentes: uma para atrasos únicos e outra para execuções recorrentes.
