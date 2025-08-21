## Manipulando Objetos com Imutabilidade em JavaScript

Nesta aula, exploraremos a manipulação de objetos em JavaScript utilizando o princípio da **imutabilidade**. Essa abordagem foca em **não modificar o objeto original diretamente**, mas sim criar um **novo objeto** com as alterações desejadas. Isso garante que o objeto original permaneça intacto, o que é fundamental para a previsibilidade e manutenção do código, especialmente em aplicações complexas.

-----

### Preservando Propriedades Existentes com Spread Syntax

Para atualizar propriedades de um objeto sem alterar o original, utilizamos a **spread syntax (`...`)**. Essa sintaxe permite copiar todas as propriedades de um objeto existente para um novo objeto, facilitando a alteração de propriedades específicas.

**Exemplo:**

Imagine que temos um objeto `book` com informações de um livro:

```javascript
const book = {
  title: "A Jornada do Desenvolvedor",
  category: "JavaScript",
  author: {
    name: "João Silva",
    email: "joao.silva@example.com"
  }
};
```

Para atualizar o título e a categoria do livro sem modificar o objeto `book` original, criamos um novo objeto `updatedBook`:

```javascript
const updatedBook = {
  ...book, // Copia todas as propriedades de 'book'
  title: "Criando um Front-End Moderno com HTML", // Sobrescreve o título
  category: "HTML" // Sobrescreve a categoria
};

console.log("Livro Original:", book);
console.log("Livro Atualizado:", updatedBook);
```

Observe que o objeto `book` permanece inalterado, enquanto `updatedBook` contém as novas informações. As propriedades `author` (nome e e-mail) foram mantidas, pois foram copiadas pelo spread syntax e não foram sobrescritas.

-----

### Adicionando Novas Propriedades

Podemos adicionar novas propriedades a um objeto imutável da mesma forma que atualizamos as existentes: simplesmente declarando a nova propriedade no novo objeto criado com a spread syntax.

**Exemplo:**

Para adicionar uma propriedade `type` ao `updatedBook`:

```javascript
const updatedBookWithType = {
  ...updatedBook, // Copia todas as propriedades de 'updatedBook'
  type: "Programação" // Adiciona a nova propriedade 'type'
};

console.log("Livro Atualizado com Tipo:", updatedBookWithType);
```

-----

### Removendo Propriedades com Desestruturação e Rest Operator

A remoção de propriedades de um objeto de forma imutável é feita utilizando a **desestruturação de objetos** combinada com o **rest operator (`...`)**. Isso nos permite "extrair" a propriedade que desejamos remover e coletar todas as demais propriedades em um novo objeto.

**Exemplo:**

Para remover a propriedade `category` do objeto `book` original:

```javascript
const { category, ...bookWithoutCategory } = book; // Desestrutura 'category' e coleta o restante em 'bookWithoutCategory'

console.log("Livro Sem Categoria:", bookWithoutCategory);
```

Neste exemplo, a propriedade `category` é extraída para uma variável separada (que pode ser ignorada, se desejado), e todas as outras propriedades do objeto `book` são coletadas em `bookWithoutCategory`. O objeto `book` original permanece inalterado.

Da mesma forma, podemos remover outras propriedades:

```javascript
const { author, ...bookWithoutAuthor } = book;
console.log("Livro Sem Autor:", bookWithoutAuthor);
```

-----

### Conclusão

A manipulação de objetos utilizando o princípio da imutabilidade é uma prática recomendada em JavaScript para garantir a integridade dos dados e facilitar a depuração. Ao invés de modificar diretamente os objetos existentes, criamos novas versões com as alterações desejadas, utilizando a spread syntax para copiar propriedades e a desestruturação com o rest operator para remover. Essa abordagem promove um código mais previsível e robusto.
