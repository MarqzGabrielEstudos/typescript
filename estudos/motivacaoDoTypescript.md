# Motivação do Typescript

[Arquivo anterior](/estudos/finalizandoModeloNegociacao.md)


[README](/README.md)

Vamos primeiro checar. Uma negociação não pode ser modificada depois de criada. Vimos que quando eu adiciono aqui uma propriedade privada da minha classe e eu coloco um `get` que tem um nome igual ao da minha propriedade eu não consigo chegar no meu código.

Se eu fizer `negociacao.quantidade = 10;` este código não vai funcionar. Eu vou salvar, vou voltar para o navegador e quando olho lá ele gera essa mensagem de erro dizendo que eu não posso atribuir nada a um `get`. Não modifiquei a quantidade, parece que está tudo ok.

Não está. Primeiro: na hora que estou escrevendo meu código será que nada me impede de eu chegar agora e dizer que quantidade é igual a 10 e eu só vou saber que eu cometi um erro em *runtime*, significa que eu só vou saber que meu código não funcionou depois que eu estou rodando.

Mas é tarde demais. Imagina se esse código vai para a produção ou vai até para um ambiente de homologação, um ambiente de testes. Você vai rodar, vai estar com problema, você vai ter que voltar, alterar seu código, colocar de novo no ambiente de testes ou de produção.

Segundo: nada me impede de eu adicionar agora, chegar aqui em negociação e eu colocar `quantidad = 10;`, comi um "e". Vocês sabem o que vai acontecer, o JavaScript vai criar dinamicamente nessa instância a propriedade quantidade. E se o programador pegar onda, se ele chamar de quantidade e ele quiser fazer `console.log(negociacao.quantidad);` e ele quer ver o resultado, ele vai fazer isso daqui.

Volto lá para o navegador, vou recarregar, tem que fazer refresh nos arquivos do JavaScript. Ele vai ver que o código dele rodou, funcionou, mas ele não está considerando a quantidade lá da negociação. Ele colocou por engano essa propriedade e está considerando em todo o código essa propriedade adicionada dinamicamente.

Isso não está legal, isso vai gerar problema. E mais ainda exige essa regra que diz que uma negociação obrigatoriamente tem uma data, uma quantidade e um valor. Vamos voltar para o nosso código e olha o que eu vou fazer, removi isso aqui.

Agora vou colocar uma data `new Date()` e esqueci de colocar a quantidade. E agora vou pedir para ele calcular negociação, o volume para mim. `const negociacao = new Negociacao(new Date() ); console.log(negociacao.volume);`.

Salvo, vou lá no navegador, vou fazer um refresh e “NaN, not a number. Porque o meu código na hora que estou desenvolvendo está passando, não tem nenhuma indicação visual que eu cometi um erro, ninguém me obriga a passar esses parâmetros para o construtor da minha classe negociação e eu só vou saber que meu código está com problema em *runtime*, quando meu código está rodando no navegador.

E isso é muito tarde, queremos falar rápido, queremos descobrir se o nosso código está com defeito no momento em que estamos desenvolvendo. É aí que entra a linguagem TypeScript.

A linguagem TypeScript é um Superset do ECMAScript, significa que tudo que tem em JavaScript tem em TypeScript e o TypeScript nos traz mais coisas que, inclusive vamos ver no próximo vídeo, nos ajuda a capturar erro em tempo desenvolvimento e não em *runtime*.

Ou seja, eu não vou ter que testar a minha aplicação: escrevo o código, vou para o navegador e recarrego para saber se ela está funcionando ou não. Eu quero saber no momento que eu estou desenvolvendo.

[Continuação...](/estudos/instalandoTypescript.md)


[README](/README.md)