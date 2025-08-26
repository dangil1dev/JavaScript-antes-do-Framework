## Utilizando o `day.js` no Navegador

Nesta aula, foi demonstrado como utilizar a biblioteca **`day.js`** em um projeto JavaScript diretamente no navegador. O principal método para isso é a inclusão de um script no seu arquivo HTML, permitindo o acesso às funcionalidades do pacote.

### Como Incluir o Pacote no Projeto

1.  **Consultar a Documentação:** A primeira etapa é sempre visitar a [documentação oficial do `day.js`](https://www.google.com/search?q=%5Bhttps://day.js.org/docs/en/installation/installation%5D\(https://day.js.org/docs/en/installation/installation\)).
2.  **Obter o Link do Navegador:** Na seção de instalação, você encontra a opção "Browser", que fornece um link de CDN (Content Delivery Network).
3.  **Injetar o Script:** Copie o link e adicione uma tag `<script>` no seu arquivo `index.html`, antes da tag do seu script principal (`main.js`). Isso garante que o `day.js` esteja carregado e disponível para uso no seu código.

### Usando as Funcionalidades do `day.js`

Após a inclusão do script, o objeto global `dayjs` fica disponível. Você pode usá-lo para:

  * **Criar um Objeto de Data e Hora:** Chame `dayjs()` para criar um objeto que representa a data e a hora atuais.
  * **Formatar a Data:** Use o método `.format()` para exibir a data e a hora no formato desejado. É essencial consultar a documentação para conhecer os caracteres de formatação (por exemplo, `DD` para o dia, `MM` para o mês, `YYYY` para o ano, e `HH:mm` para a hora e minuto).

A consulta à documentação é uma prática fundamental, pois ela serve como um guia completo para todos os métodos e opções disponíveis no pacote.

O uso de pacotes como o `day.js` acelera significou o desenvolvimento, pois permite que você utilize funcionalidades complexas já prontas e bem mantidas pela comunidade, em vez de criá-las do zero.
