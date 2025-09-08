## Criando uma API de Exemplo com `json-server`

Nesta aula, você aprendeu a criar dados simulados para sua API local usando o **`json-server`**. Isso permite que você pratique o consumo de dados de uma API sem a necessidade de um servidor real.

### Estruturando os Dados da API

1.  **Crie o arquivo de dados:** O arquivo `server.json` funciona como seu banco de dados. Os dados são estruturados como um objeto JSON.
2.  **Defina os recursos:** As chaves principais do seu objeto JSON se tornam os "recursos" ou "endpoints" da sua API. Cada recurso deve ser um array de objetos.
      * **Exemplo:** A chave `"products"` se torna o endpoint `/products`.

**Exemplo de `server.json`:**

```json
{
  "products": [
    {
      "id": 1,
      "name": "Mouse",
      "price": 150.25
    },
    {
      "id": 2,
      "name": "Teclado",
      "price": 90
    },
    {
      "id": 3,
      "name": "Monitor",
      "price": 500
    }
  ]
}
```

### Testando a API no Navegador

Ao executar o `json-server` (`npm run server`), ele cria automaticamente os endpoints para você. Você pode acessá-los no navegador para testar as requisições **`GET`**.

  * **Para listar todos os produtos:**
    `http://localhost:3333/products`
  * **Para obter um produto específico por ID:**
    `http://localhost:3333/products/1` (substitua o `1` pelo ID desejado)

O `json-server` simula o comportamento de uma API real, retornando um objeto JSON com o produto correspondente ao ID ou um erro "not found" se o produto não existir. Isso facilita a compreensão de como as requisições funcionam na prática.
