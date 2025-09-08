-----

### Utilizando o Arquivo Compilado

Nesta aula, você aprendeu a usar o arquivo JavaScript compilado pelo **Babel** e entendeu a importância de recompilar o código a cada alteração. Isso garante que a versão da sua aplicação seja sempre compatível com a maioria dos navegadores.

### A Conexão com o HTML

Para que o navegador use o código transpilado, você deve alterar o atributo `src` da tag `<script>` no seu arquivo `index.html`. Em vez de apontar para o arquivo de desenvolvimento (`main.js`), você deve apontar para o arquivo compilado que está na pasta de saída (`dist/main.js`).

**Exemplo:**

```html
<script src="./dist/main.js"></script>
```

### O Ciclo de Compilação

Ao fazer uma alteração no seu arquivo de desenvolvimento (`main.js`), essa mudança **não será refletida** automaticamente no navegador. O navegador está executando a versão que está na pasta `dist`.

Para que a mudança seja aplicada, você precisa seguir o seguinte ciclo:

1.  **Altere o código:** Modifique o seu arquivo JavaScript de desenvolvimento (`main.js`).
2.  **Compile o código:** Execute o script de build para que o Babel transpile o código e gere uma nova versão na pasta `dist`.
    ```bash
    npm run build
    ```
3.  **Visualize no navegador:** O navegador, que está usando o arquivo de `dist`, irá carregar a nova versão do seu código. Se você estiver usando uma extensão como o Live Server, a página será atualizada automaticamente.
