# Limpando o formulário

[Arquivo anterior](/estudos/organizandoCodigo.md)


[README](/README.md)

Antes de irmos para o próximo capítulo, vamos fazer uma melhoria na nossa aplicação. O que está acontecendo? Eu vou lá no meu formulário, eu digito uma data, digito uma quantidade, digito um valor, clico em "incluir". Em teoria eu teria que incluir em uma tabela, fazer alguma coisa, mas estamos exibindo no console.

O esperado é que se você acabou de incluir, vamos limpar o formulário e colocar o *focus* diretamente no campo da data para que o usuário já possa sair digitando e cadastrando uma nova negociação. Como vamos fazer isso? É JavaScript puro, mas o TypeScript nos ajuda a lembrar muita coisa sem precisarmos ir lá consultar a documentação do JavaScript e por aí vai.

Eu vou criar um método `limparFormulario()`, esse método vai ser `void`, não vai fazer nada. Qual é a ideia? Ele não está pronto ainda, mas eu sei que após exibir a minha negociação, assim que eu criei uma negociação, exibe em uma tabela ou exibe no `console.log` eu quero limpar formulário. `this.LimparFormulario();`

Esse método vai ter que chegar aqui, pegar cada *input* começando pelo data, `this.inputData.value = ' '` e vou limpar, vou passar uma *string* em branco. Vou chegar no segundo `this.inputQuantidade.value = ' ';` e vou passar uma *string* em branco.

Olha só o TypeScript me ajudando, esqueci de colocar `value` e ele está dizendo que *string* não pode ser atribuído para html *input element*. Vou colocar agora `this.inputValor.value - ' ';` também vai ser uma *string* em branco.

Eu sei que após limpar todos esses métodos o `inputData` eu quero colocar o focus. Para fazer o focus no elemento do dom você coloca `.f` e como o TypeScript sabe que *focus* é um elemento do dom já te mostra o método `focus`, `this.inputData.focus();`.

Toda vez que eu adicionar uma negociação eu vou primeiro exibir no console, depois eu limpo e vai ser isso. Vou salvar, meu método é `void`, por isso não retorna nada, vou salvar. Vou voltar para o navegador, deu *refresh*, vou digitar aqui, vou clicar em "incluir". Cliquei, exibiu, limpou meu formulário e já colocou o foco no data. Muito melhor que a experiência do usuário.

O que eu queria ressaltar aqui é que como esse *input* data, o *input* valor são elementos do dom o TypeSript sabe, porque você tipou com html *input* element, ele sabe que `inputData` é um elemento dom por isso te dá um monte de opções, até `querySelector`. Ele vai te dar todos os métodos e propriedades desse elemento do dom.

Está chegando a hora de puxarmos um pouco mais no curso e vamos lá, vamos continuar.

Código: 
```javascript
//código omitido
    adiciona(): void {
        const negociacao = this.criaNegociacao();
        console.log(negociacao);
        this.limparFormulario();
    }

//código omitido

    limparFormulario(): void {
        this.inputData.value = '';
        this.inputQuantidade.value = '';
        this.inputValor.value = '';
        this.inputData.focus();
    }
```

[Continuação...](/estudos/primeiroContatoComGenerics.md)


[README](/README.md)