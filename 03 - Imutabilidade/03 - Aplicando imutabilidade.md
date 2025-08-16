Na programação, é crucial entender a diferença entre **referência** e **cópia**. Quando você trabalha com objetos e arrays em JavaScript, uma atribuição simples (`=`) cria uma referência, não uma cópia independente.

-----

### O Problema da Referência

Quando você atribui um objeto a uma nova variável, ambas as variáveis passam a apontar para o mesmo objeto na memória. Isso significa que qualquer alteração feita em uma variável irá, inadvertidamente, afetar a outra.

**Exemplo com objetos:**

```javascript
let endereco1 = { rua: 'Avenida Brasil', numero: 20 };
let endereco2 = endereco1; // Referência, não cópia

endereco2.number = 30;

console.log(endereco1.number);
// Saída: 30 (valor alterado inesperadamente)
```

Nesse caso, ao mudar `endereco2`, você também alterou `endereco1`, pois ambos compartilhavam o mesmo local na memória.

**Exemplo com arrays:**

```javascript
let lista1 = ['apple', 'banana'];
let lista2 = lista1; // Referência

lista2.push('watermelon');

console.log(lista1);
// Saída: ['apple', 'banana', 'watermelon']
```

Adicionar um item a `lista2` afetou `lista1` pelo mesmo motivo: ambas as variáveis se referem ao mesmo array.

### A Solução: Aplicando a Imutabilidade

Para evitar esse problema, você deve criar uma **cópia explícita** do objeto ou array antes de fazer qualquer modificação. A forma mais moderna e recomendada de fazer isso é com o **Spread Operator (`...`)**.

#### Para objetos:

Você pode criar um novo objeto e "espalhar" as propriedades do objeto original nele. Em seguida, adicione as novas propriedades ou sobrescreva as existentes.

```javascript
let endereco1 = { rua: 'Avenida Brasil', numero: 20 };
let endereco2 = { ...endereco1, number: 30 }; // Cria uma cópia e modifica

console.log(endereco1.number);
// Saída: 20 (inalterado)

console.log(endereco2.number);
// Saída: 30 (novo valor)
```

#### Para arrays:

Da mesma forma, o Spread Operator permite criar uma nova lista com os elementos da original e adicionar novos itens.

```javascript
let lista1 = ['apple', 'banana'];
let lista2 = [...lista1, 'watermelon']; // Cria uma nova lista com o novo item

console.log(lista1);
// Saída: ['apple', 'banana'] (inalterado)

console.log(lista2);
// Saída: ['apple', 'banana', 'watermelon']
```

Ao aplicar a imutabilidade, você garante que as variáveis originais permaneçam intocadas, tornando seu código mais previsível e livre de efeitos colaterais indesejados.
