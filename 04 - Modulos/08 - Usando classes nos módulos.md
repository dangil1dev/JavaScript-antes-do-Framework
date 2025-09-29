## Usando Classes em Módulos JavaScript

Nesta aula, vamos ver como usar **classes** em módulos JavaScript. Classes são uma maneira poderosa de agrupar funcionalidades relacionadas e podem ser exportadas e importadas exatamente como funções ou variáveis.

Vamos refatorar nosso exemplo anterior para usar uma classe chamada `Calc`.

-----

### Refatorando para uma Classe em `calc.js`

Em vez de exportar as funções `sum` e `multiply` individualmente, vamos encapsulá-las dentro de uma classe `Calc`.

**Conteúdo de `calc.js`:**

```javascript
// calc.js

// Exporta a classe Calc para ser usada em outros módulos
export class Calc {
  // O construtor é opcional aqui, mas pode ser usado para inicializar propriedades
  constructor() {
    console.log("Calculadora inicializada.");
  }

  // Método para somar dois números
  sum(a, b) {
    return a + b;
  }

  // Método para multiplicar dois números
  multiply(a, b) {
    return a * b;
  }
}
```

Neste código:

  * Usamos `export class Calc` para **criar e exportar a classe** simultaneamente. A convenção é sempre nomear classes com a primeira letra maiúscula.
  * Os métodos `sum` e `multiply` são definidos diretamente dentro da classe, **sem a palavra-chave `function`**.

-----

### Usando a Classe em `main.js`

Para usar a classe `Calc`, precisamos primeiro **importá-la** e, em seguida, **instanciá-la** para criar um objeto.

**Conteúdo de `main.js`:**

```javascript
// main.js

// Importa a classe Calc do módulo './calc.js'
import { Calc } from './calc.js';

// Instancia a classe para criar um objeto 'calculator'
const calculator = new Calc();

// Acessa os métodos da instância usando a notação de ponto
console.log("4 + 6 =", calculator.sum(4, 6));         // Saída: 4 + 6 = 10
console.log("4 * 6 =", calculator.multiply(4, 6));    // Saída: 4 * 6 = 24
```

Neste código:

1.  **`import { Calc } from './calc.js';`**: Importamos a classe `Calc` como uma exportação nomeada.
2.  **`const calculator = new Calc();`**: Criamos uma nova **instância** (um objeto) da classe `Calc`.
3.  **`calculator.sum(4, 6)`**: Acessamos o método `sum` através do objeto `calculator`. A sintaxe para acessar métodos de uma classe é `nomeDoObjeto.nomeDoMetodo()`.

-----

### Vantagens de Usar Classes em Módulos

  * **Organização de Código**: As classes permitem agrupar métodos e propriedades que estão logicamente relacionados. Isso torna seu código mais organizado e fácil de entender.
  * **Encapsulamento**: Você pode ter métodos e propriedades que são privados para a classe, limitando a exposição da sua lógica interna.
  * **Reuso e Herança**: Classes podem ser estendidas (herança), o que permite criar novas classes com base em funcionalidades existentes, promovendo o reuso de código.

Tanto a abordagem baseada em funções quanto a baseada em classes são válidas para modularizar seu código. A escolha depende da complexidade e da natureza das funcionalidades que você está agrupando. Se as funcionalidades estão intimamente relacionadas e você precisa de um "molde" para criar objetos, usar uma classe é uma excelente opção.

