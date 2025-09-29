## Consumindo uma API com `fetch`

Nesta aula, você aprendeu a usar a função **`fetch`** para fazer requisições HTTP e consumir uma API diretamente do JavaScript, sem a necessidade de instalar bibliotecas adicionais.

### Como Fazer uma Requisição `GET` com `fetch`

O `fetch` é uma API nativa do navegador que lida com requisições de forma **assíncrona**. Para usá-lo, você fornece o endereço (URL) da API que deseja acessar.

1.  **Definir a URL:** Indique o endereço completo do recurso que você quer consumir.

      * **Exemplo:** `http://localhost:3333/products`

2.  **Lidar com a `Promise`:** O `fetch` retorna uma **`Promise`**, um objeto que representa o resultado de uma operação assíncrona. Para obter o resultado, você pode usar o método `.then()`.

    ```javascript
    fetch('http://localhost:3333/products')
      .then(response => {
        // ...
      });
    ```

      * O primeiro `.then()` recebe um objeto `Response`, que contém informações sobre a requisição (status, headers, etc.), mas ainda não os dados.

3.  **Converter a Resposta para JSON:** A resposta da API geralmente está no formato JSON. Para extrair o conteúdo e convertê-lo em um objeto JavaScript, use o método `.json()` do objeto `Response`. Este método também retorna uma `Promise`.

    ```javascript
    fetch('http://localhost:3333/products')
      .then(response => response.json())
      .then(data => {
        // 'data' agora contém os dados reais da API
        console.log(data);
      });
    ```

      * O segundo `.then()` recebe os dados já convertidos, prontos para serem usados na sua aplicação.

### Resumo do Fluxo

O fluxo completo para consumir uma API com `fetch` utilizando o método `GET` é:

1.  **Inicia a requisição:** `fetch(url)`.
2.  **Aguarda a resposta:** A primeira `.then()` aguarda a chegada da resposta HTTP.
3.  **Converte a resposta:** O método `.json()` converte o corpo da resposta em um objeto JavaScript.
4.  **Usa os dados:** A segunda `.then()` recebe o objeto de dados e permite que você trabalhe com ele na sua aplicação.

