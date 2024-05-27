# Organizando melhor nosso código

[Arquivo anterior](/estudos/convertendoDadosEntrada.md)


[README](/README.md)

Se você está lendo o método adiciona, o que você quer ler? Se você começar a ler esse método você vai ver expressão regular, pegou date, pegou quantidade, converteu valor para no final criar uma negociação. Se o adiciona a ideia é criarmos uma negociação, podemos deixar o nosso código um pouco mais claro.

Para isso vou criar um método `criaNegociacao();`. Esse método `criaNegociacao` eu vou mover esse código que cria a negociação para dentro dele. E agora que eu movi para dentro dele vou dar `return Negociacao`, se eu passo em cima sobre o nome do método vemos que o método retorna uma negociação do tipo negociação e agora vou fazer o seguinte: `const negociacao = this.criaNegociacao();`.

Fica mais claro eu isolando isso. Vou salvar. Volto para o navegador, vou criar a minha negociação, clico em "incluir" e está lá bonito, gerou a minha negociação.

Agora uma coisa que estamos falando aqui para organizar melhor o nosso código é o seguinte, vimos que é uma boa ideia tipar variáveis, trabalharmos com tipos, mas também podemos colocar tipos em retorno de métodos. Se eu passar o mouse em cima do adiciona, você vai ver que o adiciona o TypeScript está dizendo que o tipo de retorno desse método é `void` porque ele não retorna nada.

Se eu passo o mouse aqui em cima do `criarNegociacao`, qual o tipo de retorno? O JavaScript é inteligente o suficiente para entender que como você está retornando uma negociação, ele entende que o tipo de retorno do `criarNegociacao` é uma negociação.

Tanto é verdade que se eu disser que negociação é uma *string* vou ter um erro de compilação porque o *string* eu não posso atribuir uma negociação no tipo *string*, porque estou forçando o tipo *string* aqui.

É uma boa prática. Eu sugiro que não peguemos carona nessa inferência do TypeScript, vamos tipar os retornos, os métodos. Já que adiciona não retorna nada, vamos colocar `void`. Se `criarNegociacao` retorna `negociacao`, deixa isso mais claro.

Porque tem uma pegadinha, quando você está criando o método, olha o que eu poderia ter feito, eu poderia ter tirado o retorno daqui, eu poderia ter escrito o método ao invés de retornar a negociação, eu podia retornar um valor.

O que esse método está retornando agora? *Number*. É porque eu errei, não era para retornar valor era para retornar negociação. Se você já começa tipando o seu método quando você retornar algo que antes de você implementar o método você acabou de implementar algo que não condiz com o tipo do retorno, você já ver um erro. O que eu fiz? Não é valor é negociação, vou retornar a negociação.

Eu sugiro vocês fazerem isso. Vai começar a escrever o método a primeira coisa eu sei que quando eu terminar de executar esse método ou ele não vai retornar nada, ou ele vai retornar uma negociação, você já coloca o tipo. E olha que legal, o tipo está aqui e eu não dei retorno nenhum, o TypeScript está falando que não retornei nada e se não retorno nada tenho que retornar um valor ou coloco `criarNegociacao` como `void`, já que *void* não retorna nada.

Você está blindado antes de escrever o seu método de que você tem certeza que você não vai comer uma gafe e que você sempre vai retornar uma negociação como retorno. E se eu omitir o retorno de novo o TypeScript vai me dizer que eu esperava retornar uma negociação, mas não retornou. Vamos usar isso daqui, vou tipar todos os métodos da nossa aplicação. Negociação, `void`, `constructor` não tipamos.

Vou voltar para a negociação. Meu `get` implicitamente está retornando um date, mas vou colocar explicitamente que retorna `Date`, que quantidade retorna `number`, que valor retorna `number` e que o volume retorna `number`. Se eu tivesse cometido um erro aqui, o TypeScript iria me indicar. Vamos fazer isso, evitar o tipo any. Você só usa o tipo Any se realmente for preciso, tipa as propriedades de classe e os métodos que recebem os `constructor`.

Se for uma variável que você está criando você pode deixar uma variável dentro de um método, você pode deixar que o TypeScript infira esse tipo de variável para você. Parâmetro de método, parâmetro de `constructor`, retorno de método e propriedades de classe vai lá e coloca o tipo que você está esperando.

Mesmo que você queira usar *any* você vai lá e diz que você quer usar *any*. Fica essa dica. Vou salvar e tudo continua funcionando, está uma beleza. Vamos para o próximo assunto.

Código:

```javascript

//negociacai-controller.ts
//inicio do código omitido
    adiciona(): void {
        const negociacao = this.criaNegociacao();
        console.log(negociacao);
    }

    criaNegociacao(): Negociacao {
        const exp = /-/g;
        const date = new Date(this.inputData.value.replace(exp, ','));
        const quantidade = parseInt(this.inputQuantidade.value);
        const valor = parseFloat(this.inputValor.value);
        return new Negociacao(date, quantidade, valor);
    }
```

```javascript
//negociacao.ts
//inicio do código omitido
    get data(): Date {
        return this._data;
    }

    get quantidade(): number {
        return this._quantidade;
    }

    get valor(): number {
        return this._valor;
    }

    get volume(): number {
        return this._quantidade * this._valor;
    }
```

[Continuação...](/estudos/limpandoFormulario.md)


[README](/README.md)