## O que é uma API?

**API** (Application Programming Interface) é uma interface que disponibiliza um conjunto de funcionalidades ou dados que podem ser utilizados por outras aplicações. Em termos simples, uma API atua como uma ponte que permite que diferentes softwares se comuniquem e troquem informações.

### Exemplos Práticos

As APIs são usadas em uma variedade de cenários para evitar que os desenvolvedores tenham que "reinventar a roda":

* **API de CEP:** Em vez de manter um banco de dados de endereços, uma aplicação pode usar uma API de CEP. Ao informar o CEP, a API retorna automaticamente o endereço completo (rua, bairro, cidade), simplificando a vida do usuário e do desenvolvedor.
* **API de Previsão do Tempo:** Uma aplicação pode integrar uma API de previsão do tempo para exibir a temperatura ou as condições climáticas de uma cidade em tempo real, sem precisar coletar esses dados por conta própria.
* **API de Cotação de Moedas:** Para uma aplicação financeira, uma API pode fornecer a cotação atualizada de moedas como Dólar ou Euro, garantindo que os valores estejam sempre corretos.

### Comunicação Cliente-Servidor e Métodos HTTP

APIs funcionam em um modelo **cliente-servidor**. A sua aplicação (o cliente) envia uma **requisição** (um pedido) para a API (o servidor), e a API retorna uma **resposta**.

Para que a API saiba o que fazer com a sua requisição, são utilizados os **métodos HTTP**. Cada método tem um propósito específico:

* **`GET`:** Usado para **ler ou obter dados**. Ex: buscar a lista de produtos.
* **`POST`:** Usado para **enviar dados e criar** um novo recurso. Ex: cadastrar um novo usuário.
* **`PUT`:** Usado para **atualizar** um recurso existente. Ex: atualizar todos os dados de um perfil.
* **`PATCH`:** Usado para **atualizar parcialmente** um recurso. Ex: atualizar apenas a foto de perfil.
* **`DELETE`:** Usado para **remover** um recurso. Ex: excluir um item do carrinho.

### Padrões de Comunicação: JSON

Para a troca de dados entre a sua aplicação e a API, é necessário um padrão de comunicação. O mais comum é o **JSON (JavaScript Object Notation)**.

O JSON é um formato leve e de fácil leitura, que representa dados em pares de **chave-valor**, similar a um objeto JavaScript. Ele é ideal para enviar e receber dados, garantindo que cliente e servidor "falem a mesma língua".


