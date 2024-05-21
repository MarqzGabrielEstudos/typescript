# Finalizando o modelo de negociação

[Arquivo anterior](/estudos/negociacaoModelagemRegras.md)

[README](/README.md)

Vamos criar *getters*. Somente leitura pra quem quiser ler data, quantidade e valor individualmente.

Porque se eu fizer agora assim, chegar agora e colocar `negociacao.data`, se eu salvo e volto no meu navegador vai dar undefined, por a data ser privada, eu não tenho acesso a ela. Preciso criar alguém que me retorne essa data. Nem se eu fizer isso: `negociacao.#data`, vai dar erro de sintaxe.

Como eu crio um *getter*? Eu vou chegar na minha classe de JavaScript, vou criar `get data() {}`, essa função vai me retornar `return this.#data;`. Eu vou criar `get quantidade() {}` que vai me retornar `return this.#quantidade; }`. Porque o *get*, assim como o método tem a acesso, sabe acessar os atributos privados da minha classe. Então `get valor() {}` e vou retornar `return this.#valor;`.

Fiz isso, vou salvar. Volto em "App", quando eu crio o `get` eu consigo acessar a propriedade como se o `get` fosse uma propriedade classe, como se não fosse o método. O `get` é como se fosse o método, mas ele me dá um acesso como se fosse uma propriedade de classe. Fazendo isso agora tem que ser capaz. Salvei, vou voltar no navegador, recarregar.

Eu consigo ver, ler a data. Está legal, eu consigo criar uma negociação, essa negociação se eu tenho de mudar as propriedades privadas dela eu não consigo, eu não criei nenhum método na minha classe que me permita fazer essa alteração.

Contudo eu consigo a ler a data, eu consigo ler a quantidade e se eu tentar fazer isso aqui também não vai rolar. Se eu tentar fazer `negociacao.data = Flavio;`, quando executo o meu código, não dá, porque é `get`, eu não posso atribuir nada a um `get`, só ler.

Está faltando o nosso volume. O volume vou criar como `get: get volume(] { return this.#quantidade * this.#valor; }`. Quantidade vezes valor. Salvei, vou voltar em App, eu quero imprimir o volume, como é um `get` eu acesso como se fosse uma propriedade ele tem que imprimir para mim 1000.

A coisa não está 100% e vamos ver que não é por nossa culpa, é por uma questão da limitação da linguagem JavaScript.

[Continuação...](/estudos/motivacaoDoTypescript.md)


[README](/README.md)