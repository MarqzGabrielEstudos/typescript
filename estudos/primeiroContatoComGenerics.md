# Primeiro contato com Generics

[Arquivo anterior](/estudos/limpandoFormulario.md)


[README](/README.md)


## Resumo sobre a ideia de negociações

Vamos partir para mais uma parte aqui da especificação da nossa aplicação. Já temos a nossa negociação que após criada não pode ser modificada, tudo maravilhoso. Porém, na nossa aplicação no futuro vamos ter uma tabela onde vamos mostrar todas as negociações incluídas, inseridas pelo usuário.

Uma coisa importante é que nessa lista de negociação eu só posso incluir eu não posso remover. Porque eu criei a negociação e coloquei nessa lista eu não posso remover nenhum dado dessa lista. Porque não faz sentido eu ter a negociação do dia 10, uma lista de negociações e alguém chegar lá no dia depois e adicionar uma negociação nova nela.

Eu tenho que materializar isso no nosso código para garantir que a minha lista me permita adicionar, mas não remover itens.

Eu não posso utilizar, se voltarmos ao nosso código, uma *array* do JavaScript padrão porque o *array* me permite adicionar e remover. Eu vou criar um novo modelo chamado Negociações, no plural, e esse modelo vai encapsular essa lista de negociações.

Através da instância de negociações eu vou pedir: por favor, adicionar. Por favor, me dê uma lista das negociações. É nessa instância que vai um rap envolta do array de negociações que eu peço para ele adicionar, listar para mim o que ele tem. Com isso eu vou garantir que ninguém vai tocar, ninguém vai modificar a lista de negociações. 

Eu vou voltar lá para a nossa pasta “models”, não é js, lá dentro de ts da pasta “app”, vou criar um novo arquivo chamado `negociacoes.ts`. Eu tenho uma negociação, mas eu tenho uma função que representa uma lista de negociações. Como estou utilizando o sistema de modo do TypeScript eu vou escrever `export class Negociacoes {}`.

O que esse método vai ter? Vai ter que guardar de maneira privada uma lista de negociações. Sabemos que se eu quero tornar algo privado que o desenvolvedor não tenha acesso na hora que está programando, apenas a classe através de seus métodos, se eu pedir para ele adicionar, só ela pode pegar a negociação que eu passei para ele e adicionar na lista, como eu faço isso?

Eu vou colocar aqui: `private negociacoes = [];`e vai começar com um array vazio. Vou salvar. Esse método vai evoluir ainda, mas o mais importante é entender que ele guarda uma lista de negociações. Eu vou criar um método, que vamos ver lá na frente, adicionar negociação, lista negociações, mas é só uma instância de negociação que pode alterar e modificar essa lista do array, porque se eu deixasse exposto qualquer um poderia remover ou apagar.

## Iniciando com Generics

A primeira coisa que estamos entendendo é que o TypeScript está inferindo que esse *array* é do tipo *any*. Significa que você pode colocar qualquer coisa dentro desse *array*.

Em JavaScript eu faço isso aqui: `const lista = [];`, eu posso fazer: `lista.push(10);`, dentro de push vou colocar dentro dele um número. Agora posso fazer lista.push('10'); com o número em formato string. `lista.push(new Date());`. Uma lista em JavaScript padrão você pode colocar qualquer coisa lá dentro.

E se você tem uma lista que só é para ter um determinado tipo você só tem como saber se você cometeu um erro não colocando um tipo diferente em *runtime*, você não consegue descobrir em tempo de compilação.

Olha a sacada do TypeScript, eu vou dizer que esse método tem um tipo *array*. Quando eu coloco esse tipo *array* aqui o TypeScript está começando a reclamar e vai me dar essa mensagem, para quem nunca viu na vida parece uma coisa do outro do mundo, ele está dizendo: `Generic type 'array<T>'`, já faz esse diamante, e coloca um T no meio, esse T é *Type*.

Sempre que você ver esse T grande é *Type*. Ele está dizendo: `Generic type '*array*<T>' requires 1 type argument(s)`. Ele está dizendo que o tipo genérico *array* precisa de um tipo. Qual é a sacada? Você está dizendo que negociações é um *array*, quando você diz que é um *array* o TypeScript vai fazer o autocomplete, vai verificar seu código, tudo para que negociações siga os métodos e propriedades de um *array*.

O TypeScript está te perguntando qual é o valor que vai estar lá dentro. É uma lista de que? É uma lista de coelho, é uma lista de boi, é uma lista de vaca? Olha o que queremos, queremos que esse *array* seja uma lista de negociações.

Vou abrir o diamante que vale dinheiro e agora vou escrever negociação. `private negociacoes: *array*<Negociacao> = [];` Vou dar "enter", ele fez o import automático, se ele não fez você adiciona esse import e o js no final. `import { Negociacao } from './negociacao.js';`

Quando eu fiz isso eu não cometi mais nenhum erro na negociação. Por quê? Vou mostrar um exemplo para vermos. Vou criar uma lista `const list = [];`, uma lista em branco. Quando eu fiz isso aqui atribuindo o TypeScript está dizendo aqui que *array* não é uma propriedade de uma classe e ele está inferindo que é uma lista do tipo *any*.

Vou colocar `list.push('10');` em string, `list.push(11);`. Fiz isso porque eu atribuí o valor aqui, programaticamente ele adotou o *any* aqui. Se bem que era para ele reclamar, não sei porque não reclamou. Suponho que é porque estou fazendo esse teste fora do código.

O mais importante aqui é você ver o seguinte: eu posso colocar qualquer coisa, mas se eu disser que agora *list* é um *array* do tipo *string*, olha o que vai acontecer, você só pode colocar *string* lá dentro, não um número.

Ou se eu digo que listas é *number* você não pode colocar *string*. Em 99% dos casos, quase 100% você quer uma lista que tenha os mesmos tipos lá dentro. E olha que bacana, eu disse que essa aqui é uma lista de *string*, coloquei 10, `list.push('20');`, `list.push('Flavio');`, `list.push('Almeida');`. Agora vou fazer um for, `for (let nome of list) {;`.

Estou fazendo um `for of`. Se eu coloco `nome`. o TypeScript entende que se você está inteirando uma lista que é o do tipo *string* ele sabe que esse nome vai ser *string* e vai te fazer todo o autocomplete desse nome entendendo que ele é uma *string*.

Isso significa que se eu tentar fazer alguma outra coisa que não faz sentido operar com *string* eu não vou conseguir e vou ter um erro de compilação. Agora se eu coloco aqui para `number` nenhum desses aqui meu código vai passar. Vou passar aqui 10, vou passar 20 e agora aqui se eu coloco ponto `nome.`, ele mostra todos os métodos de alguém que é número.

O que acabamos de ver aqui é que em TypeScript ele tem suporte a *generics*, algo que linguagens como Java, C# tem. Significa que você diz que negociações é um *array*, é um *array*, vai ter um método *push*, vai ter um método *pop* e por aí vai.

Mas o que você vai gravar lá dentro? Eu preciso saber. Eu preciso saber o tipo porque senão você pode colocar qualquer coisa lá dentro, mas eu só quero que entre nesse *array* negociação, mas nada me impede de eu colocar *any*. Estou fazendo explicitamente.

Se eu coloquei *any* eu posso colocar agora qualquer coisa lá dentro, mas não é muito legal, você quer garantir que a lista seja uniforme, uma lista de um determinado tipo é aí que entram *generics*. Toda vez que você ver `array<T>`, esse T é que você está pedindo outro tipo para complementar esse tipo que você está trabalhando.

Está aqui, criei, meu código está compilando e eu tenho um *array* de negociação. O que eu preciso fazer agora é criar um método para adicionar uma negociação aí dentro, um método para eu poder listar, ter acesso a essa lista de negociações porque se eu faço isso daqui: `const negociacoes = new Negociacoes();`, se eu faço isso, se dou `negociacoes`. eu não vejo nada porque é privado.

Eu não quero colocar ele *public* para ele aparecer aqui porque se ele aparecer qualquer um pode pegar essa lista, pode apagar, pode remover. Eu quero que ela fique privada e através de um método que vamos ver tipo adiciona eu posso passar uma negociação e lá dentro ele vai fazer a adição para mim.

Código:

```javascript
//negociacoes.ts

import { Negociacao } from "./negociacao.js";

export class Negociacoes {
    private negociacoes: Array<Negociacao> = [];

}
```

[Continuação...]()


[README](/README.md)