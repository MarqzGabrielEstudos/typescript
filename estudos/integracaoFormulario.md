# Integração com formulário

[Arquivo anterior](/estudos/controllerNegociacao.md)


[README](/README.md)

Vamos importar o `negociação controller` no `app.ts`, mas precisamos colocar `.js` no caminho do arquivo.

Criei meu *controller*. A sacada é que todas as vezes que você submete o formulário, olha aqui eu tenho o form e aqui eu tenho o botão, *button primary*.

Toda vez que você submeter esse formulário eu quero chamar o método adiciona do meu *controller*, para isso eu preciso pegar esse formulário que está na minha página e colocar no meu código. Vou fazer: `const form = document.querySelector('.form');`, peguei o *form* e sabemos que se é um form vou colocar: `form.addEventListener`.

Olha como o TypeScript é legal, eu fiz o `querySelector` e ele está me dizendo que está retornando algo do tipo `element`, que ganhou um tipo implícito `element` e por ser isso entende que todo `element` tem o `addEventListener`.

Se você submeter *form*, `submit`, vou pegar o evento, vou passar o evento, pego o evento e vou chamar `controller.adiciona();`. `form.addEventListener('submit', event => { controller.adiciona(); })`.

> Vamos recapitular, quando a minha aplicação inicia vai criar uma instância de negociação controller, ela tem dentro dela uma referência por input da quantidade, por input da data, input do valor. E eu peguei o form e disse que toda vez que você submeter esse form eu vou chamar o adiciona.

Sabemos que se eu fizer isso com a minha página ela vai recarregar.

Quando eu olho no console, você vai ver que eu vou clicar em incluir, a minha página está fazendo *refresh*. Ela está até exibindo no console, mas está fazendo *refresh* e não pode porque sabemos que todo formulário quando você submete, ele faz um *refresh* da página.

Como a nossa aplicação tenta copiar uma *single page application*, que é uma página que não recarrega durante o seu uso, eu preciso cancelar o evento padrão do formulário que é submissão, vou fazer: `event.preventDefault();`.

O TypeScript já inferiu que *form* é do tipo *event*, é como se eu já tivesse colocado o *event* aqui, mas como é parâmetro tem que está entre parênteses. O TypeScript automaticamente, como ele sabe que esse daqui é uma Arrow Function para o `addEventListener`, ele automaticamente infere que *form* é um *event* do tipo *submit* e vai fazer o *auto complete* para mim.

Prontin!

Código:

```javascript
//app.ts

import { NegociacaoController } from "./controllers/negociacao-controller.js";

const controller = new NegociacaoController();
const form = document.querySelector('.form');
form.addEventListener('submit', event => {
    event.preventDefault;
    controller.adiciona();
})
```

[Continuação...](/estudos/supresaAoInstanciarNegociacao.md)


[README](/README.md)