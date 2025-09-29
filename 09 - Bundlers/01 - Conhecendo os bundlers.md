### O Que São Bundlers e Por Que Eles São Essenciais?

Nesta aula, você aprendeu o conceito de **bundlers** e sua importância no desenvolvimento web. Um bundler é uma ferramenta que **agrupa e empacota diversos arquivos e suas dependências** em um ou mais arquivos de saída, com o objetivo principal de **otimizar o carregamento da página**.

### Como os Bundlers Funcionam

O processo de um bundler pode ser dividido em duas etapas principais:

1.  **Geração do Gráfico de Dependências:**

      * O bundler começa com um arquivo de entrada (geralmente o arquivo principal da sua aplicação).
      * Ele analisa este arquivo em busca de outras importações e dependências.
      * Em seguida, ele segue essas dependências, construindo um **mapa completo de relacionamentos** entre todos os arquivos do projeto. Esse mapa é conhecido como **gráfico de dependências**.

2.  **Empacotamento (`Packing`):**

      * Com o gráfico de dependências em mãos, o bundler percorre o mapa, unindo todos os arquivos em um ou mais pacotes.
      * Ele integra o código de cada arquivo em um único pacote de saída (por exemplo, `bundle.js`), que o navegador pode processar de forma mais eficiente.
      * Em vez de fazer múltiplas requisições para carregar cada arquivo individualmente, o navegador precisa carregar apenas o pacote final, reduzindo o tempo de carregamento da página.

**Exemplo Prático:**

Em um projeto com múltiplos arquivos JavaScript (`file1.js`, `file2.js`, `file3.js`), em vez de referenciar cada um no seu HTML, você usa o bundler para combiná-los em um único arquivo de saída (`bundle.js`).

**Sem Bundler:**

```html
<script src="file1.js"></script>
<script src="file2.js"></script>
<script src="file3.js"></script>
```

**Com Bundler:**

```html
<script src="bundle.js"></script>
```
