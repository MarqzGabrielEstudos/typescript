# Convertendo os dados de entrada

[Arquivo anterior](/estudos/ajustandoController.md)


[README](/README.md)

Para converter os dados de entrada.
A primeira coisa que eu tenho que converter é essa string que representa uma data um objeto do tipo *date*. Vou fazer: `const date = new Date();`. Se eu faço isso ele vai criar uma data na data de hoje, eu não quero isso eu quero que ele crie uma data respeitando o que o usuário digitou.

Para fazer isso precisamos passar uma *string*, por exemplo, nesse formato: ano, mês e dia separados por vírgula. O construtor de date entende e cria uma data bonita representando essa data. Porém, quando estamos lendo do teclado, do *value*, do meu campo, da data, ele vem com hífen.

O que eu preciso fazer? Eu preciso substituir todos os hifens por vírgula e então passar a *string* para o date. Para fazer isso vou criar uma expressão regular, sabemos que toda expressão regular é feita com “barra barra”, “//”. O que vou dizer?

Encontra tudo que é hífen, mas não quero que você encontre só o primeiro não eu quero que você encontre todos, o primeiro, o segundo, o terceiro, o quarto, todas as ocorrências eu coloco um g de global. `const exp = /-/g;`.

Olha que bacana, se eu passo o mouse aqui em cima, de novo, como estou atribuindo essa variável pela primeira vez o TypeScript entende que essa é uma expressão regular. Se é uma expressão regular eu consigo chamar os métodos `exp.test` da expressão regular e por aí vai.

Criei a expressão regular e agora vou dizer que o date vai ganhar o valor de `this.inputData.value.`, como *value* é uma *string* ele também me mostrou todos os métodos relacionados da *string* e vou usar o *replace*.

O *replace* pode receber como parâmetro a primeira expressão regular e segundo o que você quer colocar no lugar quando a expressão regular encontrar o que você está procurando. Eu vou pedir para substituir com vírgula. `cont date = new Date(this.inputData.value.replace(exp, ','));` No construtor estou passando o resultado de replace e vai procurar todo mundo que tem hífen e vai substituir por vírgula e criar o meu *date*.

Segunda linha, eu vou ter a quantidade que conseguimos converter para inteiro através de `parseInt(this.inputQuantidade.value);`. E `const valor` eu vou usar o `parseFloat` porque esse valor pode ter decimais, vai ser `const valor = parseFloat(this.inputValor.value);`.

Agora que eu tenho todos os valores convertidos eu vou trocar aqui para o meu construtor, vou apagar aqui, vou passar. `const negociacao = new Negociacao(date, quantidade, valor);`.

Se eu pego agora aqui e coloco o date por último, `const negociacao = new Negociacao(quantidade, valor, date);`, vai ter erro de compilação porque estou tentando passar um *number* para o primeiro parâmetro do meu construtor que é um *date*. O TypeScript também te ajuda nisso.

O meu código está compilando, vou salvar. Nenhum erro. Volto para o navegador. Vou lá e coloco: 1/11/1111, coloco a quantidade 2 e o valor 111, clico em "incluir". Está lá perfeito, a minha data com o objeto data aqui representado, a quantidade numérica e o valor numérico.

Código:

```javascript

//codigo omitido

adiciona() {
    const exp = /-/g;
    const date = new Date(this.inputData.value.replace(exp, ','));
    const quantidade = parseInt(this.inputQuantidade.value);
    const valor = parseFloat(this.inputValor.value);
    const negociacao = new Negociacao(date, quantidade, valor);
}
```

[Continuação...](/estudos/organizandoCodigo.md)


[README](/README.md)