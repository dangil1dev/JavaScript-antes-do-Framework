## Conhecendo `async` e `await` em JavaScript

Nesta aula, você aprenderá a usar as palavras-chave **`async`** e **`await`** para trabalhar com funções assíncronas de uma forma mais limpa e legível. Essa sintaxe é uma alternativa moderna e mais intuitiva ao encadeamento de `.then()` e `.catch()` que vimos anteriormente.

-----

### O Que é uma Função `async`?

Para usar o `await`, você precisa estar dentro de uma **função assíncrona**. Você define uma função como assíncrona simplesmente colocando a palavra-chave `async` antes de sua declaração. Uma função `async` sempre retorna uma `Promise`, mesmo que você retorne um valor simples.

**Sintaxe:**

```javascript
// Função de seta assíncrona
const minhaFuncaoAssincrona = async () => {
  // ... código assíncrono
};

// Função declarada assíncrona
async function minhaOutraFuncaoAssincrona() {
  // ... código assíncrono
}
```

-----

### Usando `await` para Esperar por uma `Promise`

A palavra-chave `await` pode ser usada dentro de uma função `async` para **pausar a execução do código** até que uma `Promise` seja resolvida ou rejeitada. Isso permite que você escreva um código assíncrono que se parece com código síncrono, tornando a lógica mais fácil de seguir.

**Exemplo:**

Vamos refatorar o exemplo da aula anterior, usando `async` e `await` para obter o resultado de nossa `Promise` de forma mais direta.

```javascript
// Nossa função que retorna uma Promise (do exemplo anterior)
function asyncFunction() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = true;
      if (success) {
        resolve("A operação foi concluída com sucesso.");
      } else {
        reject("Algo deu errado.");
      }
    }, 3000);
  });
}

// Uma função assíncrona que consome a Promise
const runAsyncCode = async () => {
  console.log("Executando a função assíncrona...");

  // O 'await' pausa a execução aqui até a Promise ser resolvida
  const response = await asyncFunction();

  // Este console.log só será executado após 3 segundos
  console.log("SUCESSO:", response);
  console.log("Fim da execução.");
};

runAsyncCode();
```

Neste código, a linha `const response = await asyncFunction();` aguarda que a `Promise` retornada por `asyncFunction()` seja resolvida. Apenas quando isso acontecer, o valor de sucesso será atribuído à variável `response`, e a execução do código continuará.

-----

### Lidando com Erros: `try...catch`

Como uma `Promise` pode ser rejeitada, precisamos lidar com possíveis erros. Com `async/await`, a maneira mais comum de fazer isso é usando um bloco **`try...catch`**, que funciona de forma semelhante ao tratamento de exceções em outras linguagens de programação.

  * **`try`**: Contém o código que pode gerar um erro (como uma chamada `await`).
  * **`catch`**: Se um erro ocorrer no bloco `try`, a execução é transferida para o bloco `catch`, que recebe o objeto de erro.
  * **`finally`**: Este bloco, opcional, é executado sempre, independentemente de haver um erro ou não, sendo útil para a limpeza de recursos.

**Exemplo com `try...catch`:**

```javascript
const runAsyncCodeWithErrors = async () => {
  try {
    const success = false; // Simula uma falha

    // O 'await' vai aguardar, mas a Promise será rejeitada
    const response = await asyncFunction(success);

    // Este código não será executado se houver um erro
    console.log("SUCESSO:", response);

  } catch (error) {
    // A execução vem para cá se a Promise for rejeitada
    console.log("ERRO:", error);

  } finally {
    // Este código sempre será executado
    console.log("Fim da execução.");
  }
};

runAsyncCodeWithErrors();
```

Ao usar `async/await` com `try...catch`, a sintaxe para lidar com Promises se torna muito mais parecida com o código síncrono, o que simplifica a leitura e a manutenção de sua aplicação.
