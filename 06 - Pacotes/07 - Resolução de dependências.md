## Resolução de Dependências com Versionamento Semântico

Nesta aula, exploramos a importância da **resolução de dependências** para garantir a compatibilidade e a estabilidade dos projetos. O principal conceito abordado foi o **Versionamento Semântico**, um padrão que facilita a compreensão das mudanças entre as versões de um software.

### O Que é Versionamento Semântico?

O versionamento semântico utiliza uma convenção de três números (`MAJOR.MINOR.PATCH`) para comunicar o tipo de alteração em cada nova versão de um pacote.

* **`MAJOR` (Versão Principal):** Aumenta quando há **alterações incompatíveis** que podem quebrar o funcionamento do seu código.
* **`MINOR` (Versão Menor):** Aumenta quando novas funcionalidades **são adicionadas de forma retrocompatível**, ou seja, sem quebrar o código existente.
* **`PATCH` (Versão de Correção):** Aumenta quando **bugs são corrigidos** de forma retrocompatível, sem introduzir novas funcionalidades ou quebrar a compatibilidade.

### Símbolos de Resolução de Dependências do NPM

O NPM utiliza símbolos para definir como as dependências devem ser atualizadas automaticamente no arquivo `package.json`.

#### Símbolo `~` (Til)

* **Função:** Permite atualizações automáticas apenas para versões de **`PATCH`** (correções de bugs).
* **Exemplo:** `~1.2.3`
* **Significado:** O NPM pode instalar qualquer versão `1.2.x` (ex: `1.2.4`, `1.2.5`), mas não uma versão `1.3.x` ou `2.0.0`.

#### Símbolo `^` (Acento Circunflexo)

* **Função:** Permite atualizações automáticas para versões de **`MINOR`** e **`PATCH`**.
* **Exemplo:** `^1.2.3`
* **Significado:** O NPM pode instalar qualquer versão `1.x.x` (ex: `1.3.0`, `1.4.1`), mas não uma versão `2.0.0`. Esta é a convenção mais comum, pois garante que você receba novas funcionalidades e correções sem o risco de alterações incompatíveis.

#### Símbolo `@` (Arroba)

* **Função:** É usado para instalar uma **versão específica e fixa** de um pacote.
* **Exemplo:** `npm install dayjs@1.11.10`
* **Significado:** O NPM irá instalar exatamente a versão `1.11.10`, sem permitir nenhuma atualização automática. Isso garante que a dependência permaneça exatamente a mesma, o que é útil para projetos que requerem total controle sobre as versões.

