## Prioridade e Ordem de Execução no JavaScript

Nesta aula, faremos um experimento prático para comprovar a prioridade de execução do **Event Loop** que estudamos anteriormente.

O objetivo é entender como o JavaScript, sendo single-thread e non-blocking, lida com diferentes tipos de tarefas, como código síncrono, **Microtasks** (promessas) e **Macrotasks** (temporizadores).

-----

### O Experimento

Vamos escrever um código com diferentes tipos de tarefas e, em seguida, analisar a ordem em que elas são executadas. Tente adivinhar a ordem de saída antes de ver o resultado final\!

**Código:**

```javascript
// Ação 1
console.log('1: Código síncrono');

// Ação 2: Adiciona uma Microtask diretamente à fila
// `queueMicrotask` é uma API moderna para agendar Microtasks
queueMicrotask(() => {
    console.log('2: Microtask (queueMicrotask)');
});

// Ação 3: Macrotask
setTimeout(() => {
    console.log('3: Macrotask (setTimeout)');
}, 1000); // 1 segundo de atraso

// Ação 4: Outra execução síncrona
console.log('4: Outro código síncrono');

// Ação 5: Promise, que é uma Microtask
Promise.resolve().then(() => {
    console.log('5: Microtask (Promise)');
});
```

-----

### Análise da Ordem de Execução

Ao executar o código, a saída no console é:

```
1: Código síncrono
4: Outro código síncrono
2: Microtask (queueMicrotask)
5: Microtask (Promise)
3: Macrotask (setTimeout)
```

**Vamos entender o porquê:**

1.  **Código Síncrono (`1` e `4`):** O JavaScript sempre prioriza o código síncrono. As linhas `1` e `4` são executadas imediatamente, na ordem em que aparecem. A pilha de chamadas (`Call Stack`) processa essas tarefas primeiro, antes de qualquer coisa assíncrona.

2.  **Microtasks (`2` e `5`):** Após a pilha de chamadas ficar vazia (ou seja, todo o código síncrono ter sido executado), o **Event Loop** verifica a fila de **Microtasks**. Ambas, `queueMicrotask` e a Promise, são Microtasks. Elas são executadas em alta prioridade, na ordem em que foram adicionadas à fila.

3.  **Macrotask (`3`):** Somente depois que a fila de Microtasks está completamente vazia, o **Event Loop** passa para a fila de **Macrotasks**. O `setTimeout()` (uma Macrotask) é a última a ser executada. O atraso de 1 segundo não altera a prioridade de execução, apenas o momento em que a tarefa é adicionada à fila de Macrotasks.

Esse experimento visualiza a hierarquia de execução do JavaScript:

1.  **Código Síncrono** (executado na `Call Stack`).
2.  **Microtasks** (executadas da fila, após a `Call Stack` estar vazia).
3.  **Macrotasks** (executadas da fila, após a fila de Microtasks estar vazia).

Compreender essa ordem de execução é fundamental para escrever código assíncrono previsível e para depurar problemas relacionados a temporização e concorrência.
