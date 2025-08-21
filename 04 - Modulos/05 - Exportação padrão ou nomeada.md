## Exportação Padrão (`default`) vs. Exportação Nomeada (`named`) em JavaScript

Nesta aula, vamos aprofundar nossa compreensão sobre os ES Modules explorando a diferença crucial entre a **exportação padrão (`default`)** e a **exportação nomeada (`named`)** em JavaScript. Entender essas distinções é fundamental para organizar seu código de forma eficaz.

-----

### Exportação Nomeada (`named exports`)

A exportação nomeada é o que vimos nas aulas anteriores. Você exporta funcionalidades específicas por seus nomes. Para importar, você precisa usar o **mesmo nome exato** da funcionalidade, entre chaves `{}`.

**Exemplo em `calc.js`:**

```javascript
// calc.js

// Exportação nomeada da função 'sum'
export function sum(a, b) {
    return a + b;
}

// Exportação nomeada da função 'multiply'
export function multiply(a, b) {
    return a * b;
}
```

**Importação em `main.js`:**

```javascript
// main.js

// Importa as funções 'sum' e 'multiply' pelo seus nomes exatos
import { sum, multiply } from './calc.js';

console.log("4 + 6 =", sum(4, 6));
console.log("4 * 6 =", multiply(4, 6));
```

**Características da Exportação Nomeada:**

  * **Requer Chaves `{}` na importação:** Você precisa usar chaves e o nome exato da funcionalidade.
  * **Múltiplas exportações:** Um módulo pode ter várias exportações nomeadas.
  * **Nomes fixos:** O nome usado para exportar deve ser o mesmo usado para importar. Você pode renomeá-lo na importação com `as` (ex: `import { sum as add } from './calc.js';`), mas a referência original é pelo nome exportado.
  * **Boa para:** Exportar múltiplas funções, variáveis ou classes de um módulo, quando você quer que o consumidor do módulo escolha exatamente o que importar.

-----

### Exportação Padrão (`default export`)

Ao contrário das exportações nomeadas, um módulo pode ter **apenas uma exportação padrão**. Ela é usada para exportar o "principal" de um módulo. A forma como você importa uma exportação padrão é diferente: **não são necessárias chaves `{}`** e você pode dar a ela **qualquer nome** na importação.

**Exemplo em `calc.js`:**

Vamos supor que a função `sum` seja a funcionalidade principal do nosso módulo `calc.js`.

```javascript
// calc.js

// Exportação padrão da função 'sum'
export default function sum(a, b) {
    return a + b;
}

// Exportação nomeada da função 'multiply' (podemos ter nomeadas e uma padrão)
export function multiply(a, b) {
    return a * b;
}
```

**Importação em `main.js`:**

```javascript
// main.js

// Importa a exportação padrão (sum) como 'addFunction' e a exportação nomeada 'multiply'
import addFunction, { multiply } from './calc.js';

// Perceba que 'addFunction' é o nome que demos à função 'sum' no momento da importação
console.log("4 + 6 =", addFunction(4, 6));
console.log("4 * 6 =", multiply(4, 6));

// Exemplo mostrando que o nome na importação padrão não precisa ser o original
import batata from './calc.js'; // 'batata' agora se refere à função 'sum'
console.log("2 + 3 (usando 'batata') =", batata(2, 3));
```

**Características da Exportação Padrão:**

  * **Não requer Chaves `{}` na importação:** Importe-a diretamente pelo nome que você quiser dar a ela.
  * **Uma por módulo:** Somente uma exportação `default` é permitida por arquivo de módulo.
  * **Flexibilidade no nome:** Você pode nomeá-la como quiser no momento da importação. Isso pode ser útil para dar nomes mais descritivos no contexto de onde a função está sendo usada.
  * **Boa para:** Quando um módulo tem uma única funcionalidade principal ou uma classe que representa o propósito central do módulo.

-----

### Qual Abordagem Usar?

  * **Use Exportações Nomeadas:**

      * Quando um módulo exporta **várias funcionalidades** que são igualmente importantes ou que você quer que sejam importadas seletivamente.
      * Para garantir que as funcionalidades sejam referenciadas pelo **nome exato** em todo o projeto, o que pode facilitar a legibilidade e a refatoração.

  * **Use Exportação Padrão:**

      * Quando um módulo possui uma **única funcionalidade principal** ou uma classe que representa o cerne do módulo (ex: um módulo que exporta uma única classe `User` ou uma única função `createStore`).
      * Pode ser mais conciso ao importar, pois não usa chaves.

Embora a exportação padrão ofereça flexibilidade no nome da importação, muitos desenvolvedores preferem as exportações nomeadas por sua clareza e por forçarem o uso dos nomes originais das funcionalidades, o que pode evitar confusão em projetos maiores. No entanto, ambas são ferramentas válidas e amplamente utilizadas.

-----
