
## Iniciando com Requisições HTTP e o `fetch`

Nesta etapa, você aprenderá a fazer **requisições HTTP** para uma API e consumir os dados usando a função **`fetch`**, que é a forma padrão de se fazer requisições em JavaScript.

Você não apenas aprenderá a **ler dados** de uma API, mas também a **enviar informações** para ela. Isso é fundamental para interações como cadastrar um novo produto, fazer login ou atualizar dados.

---

### O que é uma Requisição HTTP?

Uma requisição HTTP é a forma como um cliente (como o seu navegador) se comunica com um servidor para pedir ou enviar dados. É o protocolo fundamental da internet. Existem diferentes tipos de requisições, chamadas de "métodos HTTP", sendo os mais comuns:

* **GET**: Para solicitar e ler dados de um servidor.
* **POST**: Para enviar dados ao servidor para criar um novo recurso.
* **PUT/PATCH**: Para enviar dados para atualizar um recurso existente.
* **DELETE**: Para solicitar a remoção de um recurso do servidor.

### O que é o `fetch`?

O **`fetch`** é uma API nativa do JavaScript (e do navegador) que oferece uma maneira moderna e flexível de fazer requisições de rede. Ele retorna uma **`Promise`**, o que significa que podemos usar `async/await` ou `.then()` e `.catch()` para lidar com o sucesso ou a falha da requisição.
