## Como Instalar Versões Específicas de Pacotes

Nesta aula, foi enfatizada a importância de instalar a mesma versão de um pacote que o instrutor está utilizando. Isso garante a compatibilidade do código e evita problemas que possam surgir de atualizações que mudam a forma de usar a biblioteca.

### Por que Instalar Versões Específicas?

  * **Evitar Incompatibilidade:** Alterações entre as versões de um pacote (especialmente em atualizações "major") podem quebrar o código.
  * **Acompanhar o Curso:** Utilizar a mesma versão garante que seu projeto se comporte exatamente como o do instrutor, facilitando o aprendizado e a resolução de eventuais problemas.

### Verificando Versões Disponíveis

Você pode encontrar o histórico de versões de qualquer pacote no site oficial do NPM (`npmjs.com`). Ao pesquisar por um pacote, a aba **"Versions"** mostra todas as versões publicadas, incluindo a data de lançamento e o número de downloads, o que pode indicar a popularidade de cada versão.

### Comando para Instalar uma Versão Específica

Para instalar uma versão exata de um pacote, use o comando `npm install` seguido do nome do pacote e da versão, separados por um símbolo de arroba (`@`).

A sintaxe é:

```bash
npm install [nome-do-pacote]@[versao]
```

**Exemplo:**

Para instalar a versão `1.1.0` do `json-server`, o comando seria:

```bash
npm install json-server@1.1.0
```

Ao executar este comando, o NPM instalará precisamente a versão especificada e atualizará a referência no arquivo `package.json` do seu projeto. Essa prática é recomendada para manter o ambiente de desenvolvimento consistente e garantir que você consiga acompanhar todas as aulas sem contratempos.
