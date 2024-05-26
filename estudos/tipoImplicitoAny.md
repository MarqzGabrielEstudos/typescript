# O tipo implicito any

[Arquivo anterior](/estudos/supresaAoInstanciarNegociacao.md)

[README](/README.md)

Ao mouse por cima de data, qual é o tipo que o Visual Studio Code está inferindo a partir do compilador TypeScript?

Any, quantidade, valor, any. Você sabe que any em inglês é qualquer coisa, isso significa que a minha negociação, o construtor da minha negociação está aceitando qualquer coisa que você passar. Se você passar um abacaxi como data esse abacaxi vai entrar. Eu não tenho checagem nenhuma.

O TypeScript adota o tipo any implicitamente. Isso é legal porque você consegue escrever um código rápido que você não precisa pensar muito, mas isso causa problemas no seu código como acabamos de ver. O que vamos fazer? A primeira coisa antes de tiparmos esse construtor, dizer que data tem que ser sempre date, quantidade tem que ser sempre número e valor tem que ser sempre número.

Eu vou alterar uma configuração no compilador que eu sugiro quando você está começando um projeto do zero, você ativar. É que é para dizer para o TypeScript para ele não adotar o tipo any implicitamente, só se você por algum motivo do seu código você quiser que aquele campo seja any, por algum motivo de compatibilidade, ou seja o que for.

Como fazemos isso? Vamos lá no meu "tsconfig", estou dentro do meu “tsconfig” tenho uma propriedade logo aqui que é `"noImplicityAny"` e eu vou colocar aqui `true`. Se segurem na cadeira porque quando eu ativar isso, o nosso programa vai parar de funcionar. Salvei. Já começou a ter erro de compilação em vários lugares. Vamos começar por partes.

Vou lá para o meu "negociacao.ts" e vamos ver o que precisamos resolver. Já está mostrando aquele ponto que deu problema no construtor. O parâmetro data tem um tipo implícito `any`, eu tenho que dizer qual é o tipo correto. Qual é o tipo correto? Eu quero que seja `date`. Qual é o tipo da quantidade? Aí você sempre faz assim: `quantidade: number`. Qual é o tipo valor? `valor: number`. `constructor(data: Date, quantidade: number, valor: number)`.

Para ficar claro garanta, coloque o tipo aqui também: `private _data: Date; private _quantidade: Number; private _valor: Number;`. Quem está olhando a definição da sua classe vai ver number, o que não pode é que se aqui é number e aqui é string não vai encaixar, por isso você faz isso. E temos como simplificar isso, mas ainda não é a hora de lidar com simplificação é a hora de entendermos os fundamentos.

Código:

```javascript
//negociacao.ts

export class Negociacao {
    private _data: Date;
    private _quantidade: number;
    private _valor: number;

    constructor(data: Date, quantidade: number, valor: number){
        this._data = data;
        this._quantidade = quantidade;
        this._valor = valor;
    }

//resto do código omitido
```

```json
//tsconfig.json

{
  "compilerOptions": {
    "outDir": "dist/js",
    "target": "ES6",
    "noEmitOnError": true,
    "noImplicitAny": true //essa linha que foi adicionada
  },
  "include": ["app/**/*"]
}
```

[Continuação...](/estudos/ajustandoController.md)

[README](/README.md)