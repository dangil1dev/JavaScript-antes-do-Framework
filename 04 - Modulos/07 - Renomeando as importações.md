## Renomeando Importações em JavaScript

Nesta aula, vamos aprender a renomear as funções que importamos de um módulo. Essa prática é extremamente útil para **evitar conflitos de nomes** com variáveis ou funções já existentes no seu código e para tornar o código mais claro e legível.

-----

### A Sintaxe para Renomear Importações

Para renomear uma importação, usamos a palavra-chave **`as`** (como). A sintaxe é a seguinte:

`import { nomeOriginal as novoNome } from './modulo.js';`

Vamos voltar ao nosso exemplo com `calc.js` e `main.js`. Assumindo que as funções `sum` e `multiply` são exportadas com seus nomes originais:

**`calc.js`**

```javascript
export function sum(a, b) {
    return a + b;
}

export function multiply(a, b) {
    return a * b;
}
```

**`main.js`**

Agora, vamos importar e renomear essas funções para evitar conflitos.

```javascript
// main.js

// Renomeia 'sum' para 's' e 'multiply' para 'mult'
import { sum as s, multiply as mult } from './calc.js';

console.log("4 + 6 =", s(4, 6));       // Usamos 's' em vez de 'sum'
console.log("4 * 6 =", mult(4, 6));     // Usamos 'mult' em vez de 'multiply'
```

Ao usar `sum as s`, estamos dizendo ao JavaScript para importar a função `sum` do módulo `calc.js`, mas para nos permitir acessá-la em `main.js` com o nome `s`. Isso é especialmente útil se você já tem uma função ou variável chamada `sum` no seu arquivo.

-----

### Por que Renomear Importações?

Renomear importações é uma prática importante em cenários como:

1.  **Evitar Conflitos de Nomes**: Se seu código já possui uma função ou variável com o mesmo nome daquela que você está importando, renomear a importação evita erros de declaração. Por exemplo, se você já tem uma função local chamada `multiply()`, pode importar a função do módulo como `import { multiply as calcMultiply } from './calc.js'`.

2.  **Melhorar a Clareza**: Você pode usar um nome mais curto ou mais descritivo no contexto do arquivo atual. Por exemplo, renomear `multiply` para `mult` pode ser mais conciso e legível.

3.  **Importação de Múltiplos Módulos**: Se você está importando funções com o mesmo nome de diferentes módulos, renomear cada uma delas garante que não haja conflitos.

A renomeação de importações é uma ferramenta poderosa para manter seu código organizado, legível e livre de erros, especialmente em projetos grandes onde a probabilidade de conflitos de nomes é maior.

