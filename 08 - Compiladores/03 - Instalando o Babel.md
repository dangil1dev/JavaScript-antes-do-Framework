## Instalando o Babel

Nesta aula, você aprendeu a instalar e a gerenciar os pacotes do **Babel**, o compilador JavaScript mais popular do mercado. O Babel é essencial para garantir que seu código moderno seja compatível com a maioria dos navegadores.

### Instalação do Babel

A instalação do Babel é feita via **NPM** (Node Package Manager). O comando a seguir instala as dependências necessárias para usar o Babel como um compilador para o ambiente de desenvolvimento.

```bash
npm install --save-dev @babel/core @babel/cli @babel/preset-env
```

  * `npm install`: Comando para instalar pacotes.
  * `--save-dev`: Essa flag especifica que os pacotes são **dependências de desenvolvimento**. Isso significa que eles são necessários para o desenvolvimento e a compilação do código, mas não serão incluídos na versão final da aplicação, que será executada pelo usuário.
  * `@babel/core`: O pacote principal do Babel, contendo todas as funcionalidades essenciais.
  * `@babel/cli`: O pacote que fornece a interface de linha de comando para rodar o Babel a partir do terminal.
  * `@babel/preset-env`: Um conjunto de configurações pré-definidas (presets) que permitem transpilar o JavaScript moderno para uma versão compatível com a maioria dos navegadores.

### Gerenciando as Dependências

Ao executar o comando de instalação, três arquivos e pastas importantes são criados ou atualizados:

1.  **`node_modules`:** Esta pasta armazena todos os pacotes instalados. Ela pode ficar grande, pois o Babel e seus plugins têm suas próprias dependências. Por ser uma pasta gerada, ela não precisa ser incluída em repositórios de código (como o GitHub). Você pode simplesmente deletá-la e recriá-la com o comando `npm install` a qualquer momento.
2.  **`package.json`:** Este arquivo registra as dependências do seu projeto. Com o `--save-dev`, os pacotes do Babel são listados em `devDependencies`.
3.  **`package-lock.json`:** Este arquivo garante que qualquer pessoa que clone seu projeto e rode `npm install` terá exatamente as mesmas versões de pacotes que você. Ele armazena uma "foto" exata das dependências, garantindo consistência.

Agora que o Babel está instalado, na próxima aula você vai aprender a configurá-lo para transpilar seu código JavaScript.
