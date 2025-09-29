### Criando um Script para Compilar

Nesta aula, você aprendeu uma técnica essencial para melhorar a produtividade: a criação de scripts personalizados no arquivo **`package.json`**. Isso permite automatizar tarefas repetitivas, como a compilação do seu código.

### Automatizando a Compilação com um Script

Em vez de digitar o comando completo do Babel no terminal a cada alteração de código, você pode criar um script simples que executa o comando por você.

1.  **Edite o `package.json`**: Abra o arquivo e adicione a seção `"scripts"`.
2.  **Crie o script `build`**: O nome `build` é um padrão comum para o script de compilação.
3.  **Defina o comando**: Coloque o comando completo do Babel como o valor da string. O **NPM** (Node Package Manager) é inteligente o suficiente para saber onde encontrar o executável do Babel dentro da pasta `node_modules`, então você não precisa incluir o caminho completo.

<!-- end list -->

```json
{
  "name": "projeto-exemplo",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build": "babel main.js --out-dir dist"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@babel/cli": "^7.24.6",
    "@babel/core": "^7.24.6",
    "@babel/preset-env": "^7.24.6"
  }
}
```

### Executando o Script

Para executar o seu novo script, use o comando `npm run` seguido do nome do script.

```bash
# Executa o script 'build' definido no package.json
npm run build
```

Ao executar `npm run build`, o NPM automaticamente executa o comando `babel main.js --out-dir dist` para você. Essa prática não só economiza tempo, mas também evita erros de digitação e padroniza o fluxo de trabalho para toda a equipe de desenvolvimento.


