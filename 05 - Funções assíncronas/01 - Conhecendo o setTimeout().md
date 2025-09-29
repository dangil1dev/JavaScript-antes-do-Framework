## Conhecendo o `setTimeout()` em JavaScript

Nesta aula, você aprenderá a usar a função **`setTimeout()`**, uma ferramenta fundamental em JavaScript para agendar a execução de código. O `setTimeout()` executa uma função uma única vez, após um intervalo de tempo específico.

-----

### O Que É `setTimeout()` e Como Usá-lo?

A função **`setTimeout()`** recebe dois parâmetros principais:

1.  Uma **função** a ser executada.
2.  O **tempo** de espera em **milissegundos** antes da execução.

Tudo o que estiver dentro da função do primeiro parâmetro será executado somente depois que o tempo especificado no segundo parâmetro for atingido.

**Sintaxe:**

```javascript
setTimeout(() => {
  // Código a ser executado
}, tempoEmMilissegundos);
```

**Exemplo Prático:**

Vamos criar um exemplo simples que exibe uma mensagem no console após um intervalo de tempo.

```javascript
console.log("Aguardando 3 segundos...");

setTimeout(() => {
  console.log("Olá, tudo bem?");
}, 3000); // 3000 milissegundos equivalem a 3 segundos
```

Neste código, a mensagem "Aguardando 3 segundos..." será exibida imediatamente. No entanto, a mensagem "Olá, tudo bem?" só aparecerá no console após a espera de 3 segundos.

Você pode ajustar o valor do tempo em milissegundos para controlar exatamente quando a função será executada. Por exemplo, para um segundo, use `1000`. Para meio segundo, use `500`.

-----

### Exemplo com Função Nomeada

Embora a notação de "arrow function" seja comum, você também pode passar uma função nomeada como primeiro parâmetro:

```javascript
function exibirMensagem() {
  console.log("Esta mensagem apareceu após o tempo!");
}

setTimeout(exibirMensagem, 2000); // Executa a função 'exibirMensagem' após 2 segundos
```
