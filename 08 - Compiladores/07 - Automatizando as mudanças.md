-----

### Automatizando as Mudanças com o Babel

Nesta aula, você aprendeu a automatizar o processo de compilação do seu código JavaScript. Em vez de executar o script de build manualmente a cada alteração, você pode configurar o Babel para "observar" seu código e recompilar automaticamente.

### Habilitando o Modo "Watch"

Para ativar essa automação, você precisa adicionar a flag `--watch` (ou simplesmente `-w`) ao comando do Babel no seu script de build. Isso faz com que o Babel, em vez de ser executado uma única vez, permaneça em execução, monitorando as alterações nos arquivos.

1.  **Edite o arquivo `package.json`**:
2.  **Adicione a flag `--watch`** ao script `build`.

<!-- end list -->

```json
"scripts": {
    "build": "babel main.js --out-dir dist --watch"
}
```

### Executando o Script Automatizado

1.  **Inicie o monitoramento**: No terminal, execute o script de build.
    ```bash
    npm run build
    ```
2.  **O Babel entra em modo de observação**: Você verá uma mensagem no terminal, como "The watcher is ready". Isso significa que o processo está em andamento, observando as mudanças.
3.  **Altere o código**: Agora, quando você fizer uma modificação e salvar o arquivo `main.js`, o Babel detectará a alteração e executará a compilação novamente, atualizando o arquivo na pasta `dist`.

Essa técnica aumenta significativamente a sua produtividade, pois o código compilado estará sempre atualizado, refletindo instantaneamente as alterações no seu código de desenvolvimento.

### Interrompendo o Processo

Para parar o Babel de observar os arquivos, vá até o terminal onde o script está em execução e pressione `Ctrl + C`. Isso encerrará o processo.

A automação com a flag `--watch` é um recurso poderoso que economiza tempo e esforço, permitindo que você se concentre na lógica da sua aplicação sem se preocupar com a compilação manual.
