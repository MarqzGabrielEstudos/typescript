# Negociação, Modelagem e Regras

[Arquivo anterior](carregamentoModulos.md)


[README](/README.md)

## Entendendo as regras do produto

Se formos para o mundo real, para o mundo da bolsa de valores, sabemos que uma negociação possui regras. Por exemplo, uma negociação não pode ser modificada depois de criada, obrigatoriamente tem que ter uma data, quantidade e valor, o volume de uma negociação calculado multiplicando-se a quantidade negociada do dia pelo valor negociado.

Todas essas regras que existem no mundo real têm que ser materializadas no meu código, no meu modelo de negociação para que ela se aproxime o mais perto no real. Inclusive, no nome de métodos de propriedade que fique escrito em alto nível para quem leia o código entenda de que domínio se trata e no nosso caso é um domínio de negociação.

## JS first

Vamos escrever primeiro em JavaScript para depois comparar com TS.

A primeira coisa que vou fazer, vou lá em "App", vou tirar esse `alert` daqui e todos os modelos que vamos criar da nossa aplicação ficarão dentro da pasta `models`. Aqui dentro eu vou clicar com o botão direito do mouse, "New File", vou criar `negociacao.js`.

Vou modelar este arquivo usando classes do ECMAScript, vou dizer que: `class Negociacao {}`. Que vai ter uma quantidade, uma data e um valor.

E eles não podem ser modificados depois que uma instância de negociação é criada. Já vou lançar um melhor da linguagem JavaScript, criando atributos privados, atributos que quando eu defina em uma classe eu só consigo definir os valores deles através do construtor ou por métodos da própria classe. Se alguém fora da classe tentar alterar essas propriedades, não vai conseguir.

Para fazer isso eu uso tralha, ‘#’.

Agora eu preciso, no momento que estou criando uma negociação, passar a data, quantidade e valor. Sabemos que fazemos isso através de um construtor, vou receber uma data, uma quantidade e vou receber um valor `constructor(data, quantidade, valor) { }`.

E aqui vou dizer `constructor(data, quantidade, valor) { this.#data = data; this.#quantidade = quantidade; this.#valor = valor; }`.

Agora exportamos a classe, importamos em `app.js`.

Se eu vier na aba Network e a recarrego, você vai ver que o App foi carregado e como eu fiz o import de negociação, ele também carregou o módulo da negociação sem eu precisar explicitar dentro do Index.html. Só bastou eu colocar o App que o navegador vai resolver isso tudo para mim.

Agora que tenho minha negociação importada eu vou criar uma instância de negociação, vou dizer: `const negociacao = new Negociacao()`, vou passar aqui com a ordem dos parâmetros do construtor que são data, quantidade e valor, vou passar `new date()`, a quantidade que eu vou passar é 10 e o valor que eu vou passar é 100. `const negociacao = new Negociacao(new Date(), 10, 100);`.

Passei para o meu construtor e vou fazer um `console.log` da negociação para vermos. `console.log(negociacao)`;. Vou tentar `negociacao.quantidade = 1000;`, tentar alterar. E vou dá um outro `console.log(negociacao)` para podermos ver o resultado.

Vou salvar, vou voltar no navegador, vou olhar na aba do console. Quando eu vejo aqui, olha só, ele criou com a data, com a quantidade e com o valor. A quantidade continua 10, não mudou. O que meu JavaScript fez foi adicionar dinamicamente uma propriedade quantidade de mesmo nome dinamicamente com esse valor que eu coloquei.

Não consegui alterar o valor original, mas também eu consegui adicionar essa propriedade aqui quantidade dinamicamente na minha instância da classe negociação. Não parece que o JavaScript está nos ajudando a não alterar a propriedade da classe negociação.

O que precisamos agora é implementar os getters para que eu possa ler cada negociação. A data, se eu quiser só ler a data, se eu ler a quantidade, se eu quiser o volume eu preciso criar esses getters para que eu possa imprimir aqui e também ver o resultado antes de fazermos uma grande revelação.

[Continuação...](/estudos/finalizandoModeloNegociacao.md)


[README](/README.md)