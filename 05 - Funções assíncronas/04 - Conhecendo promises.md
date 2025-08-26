## Conhecendo Promises em JavaScript

Nesta aula, vamos colocar em prática o que aprendemos sobre **Promises**. Promises são objetos que representam a conclusão (ou falha) de uma operação assíncrona.

Vamos criar uma função que retorna uma Promise para simular uma operação que leva tempo, como uma requisição de rede.

-----

### Criando uma Promise

Uma Promise é criada usando o construtor `new Promise()`, que recebe uma função com dois parâmetros: `resolve` e `reject`.

  * **`resolve`**: Uma função a ser chamada quando a operação assíncrona é concluída com sucesso.
  * **`reject`**: Uma função a ser chamada quando a operação assíncrona falha.

**Exemplo em Código:**

```javascript
function asyncFunction() {
  return new Promise((resolve, reject) => {
    // Simula uma operação assíncrona que leva 3 segundos
    setTimeout(() => {
      const success = true; // Simula o sucesso ou falha da operação

      if (success) {
        resolve("A operação foi concluída com sucesso.");
      } else {
        reject("Algo deu errado.");
      }
    }, 3000); // 3000 milissegundos = 3 segundos
  });
}
```

Neste exemplo, a função `asyncFunction` retorna uma nova Promise. Dentro dela, usamos `setTimeout()` para simular um atraso de 3 segundos. Após o atraso, verificamos a variável `success`:

  * Se for `true`, chamamos `resolve()` com uma mensagem de sucesso.
  * Se for `false`, chamamos `reject()` com uma mensagem de erro.

-----

### Lidando com a Promise: `then()`, `catch()` e `finally()`

Quando uma função retorna uma Promise, você pode usar métodos encadeados para lidar com o resultado:

  * **`.then()`**: Executa uma função se a Promise for **resolvida**. Recebe o valor passado por `resolve()`.
  * **`.catch()`**: Executa uma função se a Promise for **rejeitada**. Recebe o valor passado por `reject()`.
  * **`.finally()`**: Executa uma função **independentemente** do resultado (seja sucesso ou falha).

**Exemplo Prático de Uso:**

```javascript
console.log("Executando a função assíncrona...");

asyncFunction()
  .then(response => {
    // Executado se a promise for resolvida (success = true)
    console.log("SUCESSO:", response);
  })
  .catch(error => {
    // Executado se a promise for rejeitada (success = false)
    console.log("ERRO:", error);
  })
  .finally(() => {
    // Executado sempre, no final da operação
    console.log("Fim da execução.");
  });
```

Ao executar este código, o console exibirá "Executando a função assíncrona...", aguardará 3 segundos e, em seguida, mostrará o resultado e a mensagem final:

  * **Se `success` for `true`**: O `.then()` será executado, mostrando a mensagem de sucesso, seguido pelo `.finally()`.
  * **Se `success` for `false`**: O `.catch()` será executado, mostrando a mensagem de erro, seguido pelo `.finally()`.

-----

### Por que não podemos pegar o retorno direto?

Se você tentar obter o valor de retorno de uma função assíncrona diretamente, como em `const response = asyncFunction()`, você não terá o valor final, mas sim o objeto `Promise` em si, que estará no estado **`pending` (pendente)**. Isso ocorre porque o JavaScript não espera a Promise ser concluída; ele continua a execução do código.

Para "esperar" pelo resultado, você precisa usar os métodos `.then()`, `.catch()` e `.finally()`, ou, como veremos na próxima aula, a sintaxe `async/await`.
