## Conhecendo o `Event Loop` em JavaScript

Nesta aula, vamos desmistificar o conceito de **`Event Loop`** e como ele é a chave para entender a natureza assíncrona e não bloqueante do JavaScript.

---

### O Modelo de Concorrência do JavaScript

Para compreender o `Event Loop`, é crucial entender as características do JavaScript:

* **Single-Thread**: O JavaScript executa uma única tarefa por vez. Imagine uma fila de banco com apenas um atendente: cada pessoa deve esperar sua vez.
* **Non-Blocking**: O JavaScript não "trava" ou "bloqueia" a execução quando encontra uma operação demorada (como uma requisição de rede). Em vez disso, ele a delega e continua com a próxima tarefa.
* **Assíncrono**: Para lidar com a natureza não bloqueante, o JavaScript usa um modelo assíncrono. Isso significa que ele não espera o retorno de uma operação demorada, permitindo que outras tarefas sejam executadas enquanto a primeira é processada em segundo plano.
* **Concorrência**: Múltiplas tarefas podem estar "concorrendo" por processamento, e o `Event Loop` é o mecanismo que gerencia essa concorrência.

O **`Event Loop`** é o motor que gerencia a execução de código assíncrono em uma única thread, garantindo que o JavaScript seja não bloqueante.

---

### As Engrenagens do `Event Loop`

O funcionamento do `Event Loop` pode ser visualizado em três componentes principais:

1.  **`Call Stack` (Pilha de Chamadas)**: É a estrutura de dados onde o JavaScript rastreia a execução das funções. As funções são adicionadas ao topo da pilha e removidas quando a execução é concluída. O código síncrono é executado diretamente aqui, de cima para baixo.

2.  **`Web APIs` (APIs do Navegador)**: Funções assíncronas como `setTimeout()`, `fetch()`, e eventos do DOM (como cliques) são gerenciadas pelas `Web APIs` do navegador. Quando o `Call Stack` encontra uma dessas funções, ela é enviada para a API correspondente, que a processa em segundo plano.

3.  **`Callback Queue` (Fila de Retornos)**: A `Callback Queue` é uma fila onde as funções assíncronas (os "retornos" ou "callbacks") são colocadas após serem processadas pelas `Web APIs`.

**O Papel do `Event Loop`**: O `Event Loop` é um processo constante que monitora a **`Call Stack`** e a **`Callback Queue`**. Sua única função é verificar se a `Call Stack` está vazia. Se estiver, ele pega o primeiro callback da `Callback Queue` e o move para a `Call Stack` para ser executado.

---

### Prioridades: `Microtasks` vs. `Macrotasks`

A `Callback Queue` na verdade é composta por duas filas com diferentes prioridades:

* **`Microtasks` (Alta Prioridade)**: Tarefas como `Promise.then()`, `Promise.catch()`, e `async/await` são consideradas `Microtasks`. O `Event Loop` prioriza a execução de todas as `Microtasks` na fila antes de sequer considerar uma `Macrotask`.
* **`Macrotasks` (Baixa Prioridade)**: Tarefas como `setTimeout()`, `setInterval()`, e eventos do DOM (como `onclick`) são consideradas `Macrotasks`.

**A Ordem de Execução**: O `Event Loop` segue a seguinte sequência:
1.  Executa todo o código síncrono na `Call Stack`.
2.  Após a `Call Stack` ficar vazia, verifica a fila de `Microtasks` e executa todas elas.
3.  Só depois que a fila de `Microtasks` estiver vazia, ele verifica a fila de `Macrotasks` e move a primeira para a `Call Stack`.
4.  O ciclo se repete.


