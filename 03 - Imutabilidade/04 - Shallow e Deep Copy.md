### Cópia Superficial (Shallow Copy)

Uma cópia superficial cria uma nova instância do objeto, mas **apenas para o primeiro nível de propriedades**. Se o objeto original contiver outros objetos ou arrays aninhados, a cópia superficial apenas copiará as referências para esses objetos.

Isso significa que ambos os objetos (o original e a cópia) continuarão a apontar para o mesmo objeto aninhado na memória. Portanto, qualquer alteração nesse objeto aninhado afetará ambos.

**Exemplo:**

```javascript
const cursoHTML = {
  nome: 'HTML',
  alunos: [{ nome: 'Rodrigo', email: 'rodrigo@email.com' }]
};

// Cópia superficial (shallow copy)
const cursoJS = { ...cursoHTML, nome: 'JavaScript' };

// Adicionando um novo aluno ao cursoJS
cursoJS.alunos.push({ nome: 'João', email: 'joao@email.com' });

console.log(cursoHTML.alunos);
// Saída: [{nome: 'Rodrigo'}, {nome: 'João'}]
// O aluno "João" foi adicionado aqui também!
```

O problema: embora o `cursoJS` seja um novo objeto, a propriedade `alunos` é apenas uma referência à lista de alunos do `cursoHTML`. Ao adicionar um novo aluno à lista de `cursoJS.alunos`, você também modifica a lista original `cursoHTML.alunos`.

-----

### Cópia Profunda (Deep Copy)

Uma cópia profunda resolve esse problema. Ela cria uma **cópia completa e independente** de todo o objeto, incluindo todos os objetos e arrays aninhados. Isso garante que a manipulação da cópia não afete o objeto original.

A forma recomendada de realizar um deep copy é usar uma abordagem que copia o objeto aninhado também. Você pode usar o **Spread Operator (`...`)** em cada nível de aninhamento.

**Exemplo:**

```javascript
const cursoHTML = {
  nome: 'HTML',
  alunos: [{ nome: 'Rodrigo', email: 'rodrigo@email.com' }]
};

// Cópia profunda (deep copy)
const cursoJS = {
  ...cursoHTML,
  nome: 'JavaScript',
  alunos: [...cursoHTML.alunos] // Cria uma nova cópia do array de alunos
};

// Adicionando um novo aluno ao cursoJS
cursoJS.alunos.push({ nome: 'João', email: 'joao@email.com' });

console.log(cursoHTML.alunos);
// Saída: [{nome: 'Rodrigo'}]
// O objeto original está intacto!
```

Neste caso, ao usar `[...cursoHTML.alunos]`, você cria um novo array de alunos para o objeto `cursoJS`. Agora, a lista de alunos do `cursoHTML` e a de `cursoJS` são completamente independentes.

-----

### Quando usar cada tipo de cópia?

  * **Shallow Copy**: Use para objetos com propriedades de valores primitivos (strings, números, booleanos) ou quando você não se importa que os objetos aninhados sejam compartilhados.
  * **Deep Copy**: Use para objetos mais complexos com **arrays ou objetos aninhados**. É a melhor prática para garantir a imutabilidade completa e evitar efeitos colaterais indesejados, especialmente em frameworks como o React.
