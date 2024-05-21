# Entendendo carregamento de modulos do JS

[README](/README.md)

Quando trabalhamos com sistema de módulos nativos do navegador, vamos importar um único módulo que é um script de JavaScript, um único módulo em Index html e é o navegador que vai ler esse módulo e vai descobrir o que ele necessita para funcionar e vai baixar para nós automaticamente outros módulos.

Removendo a responsabilidade de ter que colocar vários scripts da nossa página e ter que lembrar a ordem de dependência entre eles. Isso é muito interessante. Podemos fazer isso nativamente no navegador.

Como vamos fazer isso? Vamos lá dentro da pasts "js", dentro dela, clicamos em `js/models` ele vai estar com a seta para baixo, eu vou clicar com o botão direito, "New File", eu vou criar o App `app.js`. Cuidado na hora de criar porque ele não pode ficar dentro da pasta models, tenha a certeza que ele é filho direto da pasta js.

Criei este humilde módulo porque não vamos falar script, porque trabalhando no sistema de módulos todo arquivo `.js` chamamos de módulo. Vou colocar aqui aquele humilde `alert` que aprendemos no curso de lógica de programação, coloquei o `alert`, vou voltar para o Index html e vou fazer isso uma única vez. Vou colocar aqui a tag `<script type="module" src=>`, para dizer que não é um script é um módulo.

Onde está esta função? É só lembrarmos que a pasta "dist" é compartilhada na raiz do meu navegador quando eu abro o localhost 3000. Tenho que colocar a subpasta `<script type="module" src="js/app.js"></script>`. Vou fechar a tag script, vou salvar.

Salvei, vou voltar ao navegador e automaticamente ele já recarregou e já me mostrou o alerta provando que a função está sendo carregada pelo sistema de módulos do ECMAScript. Então importei o módulo principal da aplicação e é dentro dele que toda a aplicação vai ser inicializada e por aí vai. Agora que entendemos isso vamos partir para a modelagem da nossa negociação que é o que interessa.

[README](/README.md)


[Continuação...](/estudos/negociacaoModelagemRegras.md)