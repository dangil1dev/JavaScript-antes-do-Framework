## O que são Pacotes em JavaScript?

Em JavaScript, **pacotes** (também conhecidos como **bibliotecas**) são coleções de código pré-escrito e reutilizável. Eles fornecem funcionalidades prontas que você pode adicionar ao seu projeto, economizando tempo e esforço, já que não precisa "reinventar a roda".

---

### Por que usar Pacotes?

* **Acelerar o Desenvolvimento:** Em vez de escrever tudo do zero, você pode usar um pacote para adicionar rapidamente funcionalidades complexas, como manipulação de datas, validação de formulários ou requisições de rede.
* **Código de Qualidade:** A maioria dos pacotes populares é mantida pela comunidade de desenvolvedores. Isso significa que eles são frequentemente atualizados, têm bugs corrigidos, e o desempenho é otimizado ao longo do tempo.
* **Gerenciamento de Dependências:** Quando você usa um pacote, sua aplicação passa a depender dele. Os **gerenciadores de pacotes** (como o npm) são ferramentas que ajudam a instalar, atualizar e remover esses pacotes, mantendo o controle das dependências do seu projeto.

### Formas de Incluir Pacotes

Existem duas maneiras principais de incluir um pacote em seu projeto:

1.  **Injetando um Script:** Você pode incluir um pacote adicionando uma tag `<script>` no seu arquivo HTML, que aponta para o arquivo JavaScript do pacote. Essa abordagem é simples, mas pode se tornar difícil de gerenciar à medida que o número de pacotes aumenta.

2.  **Usando um Gerenciador de Pacotes:** A maneira mais moderna e recomendada é usar um gerenciador como o **npm** (Node Package Manager). Com o npm, você pode instalar pacotes através da linha de comando, e ele cuida de todas as dependências automaticamente, garantindo que seu projeto funcione corretamente.


