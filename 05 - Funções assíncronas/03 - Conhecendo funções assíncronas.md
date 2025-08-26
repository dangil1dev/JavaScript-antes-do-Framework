---

## Conhecendo as Funções Assíncronas em JavaScript

Nesta aula, você irá compreender o conceito de **funções assíncronas** e por que elas são essenciais para o desenvolvimento moderno em JavaScript. Diferente de uma função síncrona, que executa e retorna um valor imediatamente, uma função assíncrona lida com operações que podem levar tempo, como requisições a APIs externas ou acesso a um banco de dados.

---

### A Promessa de um Retorno (`Promise`)

Quando uma função assíncrona é chamada, ela **não retorna o valor esperado imediatamente**. Em vez disso, ela retorna uma **`Promise`** (promessa). Pense nisso como uma garantia: "Eu prometo que vou processar sua solicitação e, assim que terminar, vou te dar uma resposta."

Essa promessa pode ter dois resultados:

* **`resolved` (resolvida):** A operação foi concluída com sucesso e o valor esperado foi retornado.
* **`rejected` (rejeitada):** Ocorreu um erro durante a operação (por exemplo, o banco de dados está indisponível) e a promessa foi rejeitada.

O uso de `Promises` permite que seu código continue a ser executado sem ficar "travado" esperando o retorno de uma operação demorada.

---

### O Papel do `await` em Funções Assíncronas

Em uma função assíncrona, você pode usar a palavra-chave **`await`** para "pausar" a execução do código e esperar que uma `Promise` seja resolvida. Isso é útil quando você precisa do resultado de uma operação assíncrona para continuar com as próximas etapas.

**Exemplo:**

Imagine que você precisa buscar uma lista de produtos em um banco de dados e, em seguida, exibi-la na tela. Se você não usar `await`, seu código pode tentar exibir os produtos antes que a busca no banco de dados seja concluída, resultando em um erro.

Ao colocar `await` antes da chamada da função de busca, você garante que o código só continue após a `Promise` de busca ser resolvida e os dados dos produtos serem retornados.

**Lembre-se:** A palavra-chave `await` só pode ser usada dentro de uma **função assíncrona**.
