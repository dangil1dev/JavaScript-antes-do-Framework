## Instalando e Utilizando o `json-server`

Nesta aula, aprendemos a usar o **`json-server`**, uma ferramenta que permite simular uma API RESTful completa de forma rápida e local. Isso é ideal para focar na lógica de consumo de dados em JavaScript sem depender de uma API real na internet.

### Instalação do `json-server`

Para instalar o `json-server`, você precisa ter o Node.js e o NPM instalados.

1.  Abra o terminal do seu projeto.
2.  Execute o comando `npm install json-server`. Isso instalará o pacote na pasta `node_modules` e o adicionará como uma dependência no seu arquivo `package.json`.

### Configurando e Executando a API Local

Após a instalação, você precisa criar um arquivo JSON com os dados que deseja simular e configurar um script no seu `package.json` para rodar o servidor.

1.  **Crie o arquivo de dados:** Crie um arquivo na raiz do seu projeto, por exemplo, `server.json`. Este arquivo servirá como seu banco de dados. Você pode adicionar dados JSON dentro dele.

    ```json
    {
      "test": {}
    }
    ```

2.  **Crie o script de execução:** No seu `package.json`, adicione um script para executar o `json-server`.

    ```json
    "scripts": {
      "server": "json-server --watch server.json"
    }
    ```

      * `--watch server.json`: Essa flag faz com que o servidor reinicie automaticamente sempre que você fizer uma alteração no arquivo `server.json`.

3.  **Execute o servidor:** No terminal, rode o comando que você definiu no script.

    ```bash
    npm run server
    ```

    O servidor será iniciado, por padrão, na porta `3000`. Você pode acessá-lo no seu navegador em `http://localhost:3000`. As "chaves" do seu arquivo JSON se tornam os "recursos" da sua API. Por exemplo, a chave `"test"` cria o endpoint `http://localhost:3000/test`.

### Personalizando a Porta

Você pode alterar a porta padrão do servidor usando a flag `--port`.

  * **No script do `package.json`:**
    `"server": "json-server --watch server.json --port 3333"`
