# Controller de negociação

[Arquivo anterior](/estudos/modificadorPrivate.md)


[README](/README.md)

Vamos usar o conceito *controller*.
Um *controller* vai uma classe, vamos criar uma instância dessa classe, ela que vai controlar a interação desse *form* e quando eu clicar em incluir é essa negociação *controller* que vamos criar que vai pegar os dados do formulário e criar o meu modelo.

Esse *controller* vai ser a ponte entre as interações do usuário na minha página e a criação de modelos, ele vai ser o meio de campo. Ele vai ter uma dependência de elementos de UI, a minha data, a minha quantidade, o meu valor, e vai fazer a comunicação disso com o nosso modelo.

Vou voltar para o meu projeto, dentro de "App" eu tenho a pasta "controllers > New File" e vou criar um novo arquivo que eu vou chamar de `negociacao-controller.ts`. Cuidado, não é “js” é “ts”. Eu tenho a minha negociação controller aqui. Vou começar porque vou querer usar isso em algum outro lugar da minha aplicação, por isso vou começar com: `export class Negociacaocontroller {`.

O que essa negociação *controller* vai ter? Eu preciso, assim que ela for instanciada, ela tem uma referência para o input da data, da quantidade e do valor. De começo o que vou colocar é o seguinte: vou criar `private inputData; private inputQuantidade; private inputValor; }`.

No momento quando o meu construtor for inicializado dessa classe, olha o que vou fazer: `constructor() { this.inputData =`. Precisamos ter um conhecimento de JavaScript, lá na pasta "dist" vou abrir o html, sabemos que o campo data tem o `id` data, que o campo valor tem o `id` valor e que o campo quantidade tem o `id` quantidade.

Preciso usar o `document.querySelector` para pegar essa função e colocar aqui no meu código. Vou fazer: `document.querySelector`, isso aqui é JavaScript puro não tem nada de TypeScript, vou pegar o elemento que tem data, `this.inputQuantidade` vai ser `document.querySelector (‘#quantidade)`, para pegar o *input* da quantidade.

E `this.inputValor = document.querySelector (‘#valor’)`. Então: `constructor() { this.inputData = document.querySelector('#data'); this.inputQuantidade = document.querySelector('#quantidade'); this.inputValor = document.querySelector('#valor'); }.`

Isso significa que no momento que eu criar a instância de negociação *controller*, se estou criando uma instância de negociação *controller* o constructor vai ser executado. Aí vou ao DOM e pego esses elementos do dom atribuo aqui nessas propriedades do construtor da minha classe.

Porque quando eu chamar o método adiciona, `adiciona()`, esse método tem que primeiro fazer: `console.log(this.inputData);`. Só para sabermos se realmente pegamos essas funções quando eu chamar.

Na verdade, sabemos que eu tenho que criar uma negociação pegando a data, a quantidade e valor. Inicialmente vou dar um `console.log` para vermos como as coisas se encaixam. `adiciona() { console.log(this.inputData); console.log(this.inputQuantidade); console.log(this.inputValor); }`.

Por aqui não tem mistério nenhum, a única novidade olhando aqui de TypeScript para nós é o modificador private aqui. Quando a minha negociação controller for criada ela vai guardar o `inputValor`, `inputQuantidade` e o `inputData` em uma propriedade da classe e toda vez que eu chamar o método adiciona ele vai imprimir no console esses elementos do dom que eu peguei.

Código:

```javascript
//negociacao-controller.ts

export class NegociacaoController {
    private inputData;
    private inputQuantidade;
    private inputValor;

    constructor() {
        this.inputData = document.querySelector('#data');
        this.inputQuantidade = document.querySelector('#quantidade');
        this.inputValor = document.querySelector('#valor');

    }

    adiciona() {
        console.log(this.inputData)
        console.log(this.inputQuantidade)
        console.log(this.inputValor)
    }
}

```

[Continuação...](/estudos/integracaoFormulario.md)


[README](/README.md)