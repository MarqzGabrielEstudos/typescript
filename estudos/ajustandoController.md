# Ajustando nosso controller

[Arquivo anterior](/estudos/tipoImplicitoAny.md)


[README](/README.md)

Como resolvemos esse problema de compilação resultante da ativação do `noImplicitAny`? A maneira mais fácil é você chegar aqui e dizer que o tipo dele é *any*, eu estou explicitando que o tipo dele é *any*. `private inputDate: any; private inputQuantidade: any; private inputValor: any;`.

Você pode perguntar "Flávio, é tão simples assim?" É, mas qual é a ideia? A ideia é você evitar o tipo *any*. A primeira coisa é que como estou utilizando o tipo *any* qualquer coisa pode ser qualquer coisa e se eu tentar usar o autocomplete, se eu chegar aqui this.inputValor., por exemplo, eu não tenho nenhuma sugestão do compilador da IDE com base nas informações do TypeScript do que eu posso fazer com esse valor. Resolveu, mas resolveu meia boca.

Vamos colocar um tipo que faça sentido. Uma coisa importante para ressaltarmos aqui para vocês ficarem espertos, é que esse tipo *date* que eu coloquei, esses tipos *number*, o TypeScript já vem com eles, já vem dentro dele para a linguagem JavaScript todos os tipos padrões da linguagem JavaScript.

É por isso que tem um tipo *date*, tem um tipo *number* e por debaixo dos panos todos esses tipos vão me dar acesso a todos os métodos e propriedades que fazem sentido para esse tipo.

Tanto isso é verdade que, eu chego no `inputData:`, `this.inputData.`, não tem nada aqui, nenhum autocomplete que eu mostrei para vocês e agora se eu volto lá para negociação: `this._data.` é date quando eu dou ponto ele mostra todos os métodos relacionados a *date*.

Porque o TypeScript tem certeza que só pode entrar um *date* aí em tempo de compilação. Isso significa que em *runtime*, se você não fizer nenhuma mágica para tentar colocar algo diferente lá dentro, você só vai ter um *date*.

Voltando a falar nos tipos do TypeScript, o TypeScript também vem com tipos para elementos do dom. Essa data que estamos trabalhando aqui é do tipo *html input element*. Faz sentido porque o date, a quantidade e o valor se eu olho lá no meu html eles são *input number*, e *input date*, *type date*.

Como é que fazemos isso? Vamos voltar lá para a nossa “negociação controller”, vou dizer que data, quantidade e valor são do tipo `HTMLInputElement`. Não precisa importar porque isso aqui já é padrão do TypeScript.

Ele está reclamando que agora que ele sabe que esse input é um *html element*, todo *html element* eu tenho agora o `autocomplete: addEventListener`, `value`. Sabemos que de um html input element, de um elemento do dom do tipo input, eu pego o valor através de `.value`. Olha que lindo, o TypeScript está me dizendo que todo input `.value`, o retorno dele é uma string, você está tentando passar uma string como se fosse um valor de date.

O compilador está nos avisando, como eu tipei quantidade como html input element, ele está me lembrando que eu pegar data que é value. Porque todo input quando você dá `.value` é sempre uma *string*.

Eu tenho que arrumar algum jeito de converter antes de passar para negociação, um input value aqui como um date. E também para cá, quando eu resolver esse problema aqui vai pular para essa linha daqui porque value é uma string e o nosso construtor da quantidade se vermos da negociação, é *number*.

Precisamos fazer uma pré-conversão que graças ao TypeScript se tivéssemos fazendo todo ambiente configurado desde o início ele já me daria a dica que não é assim, que eu tenho que converter esses dados do elemento do dom para que seja possível passar para instância.

Código:

```javascript

import { Negociacao } from "../models/negociacao.js";

export class NegociacaoController {
    private inputData: HTMLInputElement;
    private inputQuantidade: HTMLInputElement;
    private inputValor: HTMLInputElement;

//resto do codigo omitido
```

[Continuação...]()


[README](/README.md)