# Automatizando Compilação de Arquivos

[Arquivo anterior](/estudos/aprimorandoConfiguracao.md)


[README](/README.md)

Vamos deixar nosso ambiente mais profissional, em que sentido? No sentido de toda vez que eu alterar, bulinar, modificar, mexer nos meus arquivos "ts" que automaticamente o compilador do TypeScript escuta que eu mexi no arquivo e gere o processo de compilação sempre garantindo que a pasta "dist" vai estar atualizada após salvar qualquer arquivo "ts". Como fazemos isso?

Primeiro você vai voltar para o seu terminal, vou parar aqui o meu servidor, vamos lá para o "package.json", existe uma série de scripts aqui, temos um script `compile`. Eu vou criar aqui um script que eu vou chamar de `watch`, podia ser calopsita, tico tico, mas eu vou chamar de `watch`, que é de observar, de ver.

Ele vai chamar o compilador TypeScript com parâmetro `tsc -w`, esse parâmetro `tsc -w` você já deve imaginar que "w", "wacth", é para o compilador TypeScript ficar monitorando os arquivos.

Deixa eu salvar aqui. Recomendo ficar monitorando os arquivos das pastas que você adicionar dentro do include, será que isso vai funcionar? Vou chegar aqui no meu terminal, `npm run watch`. Quando eu executo esse comando, você vai ver que "Starting compilation in watch mode", ele primeiro dá uma compilada em tudo e depois ele fica olhando se algum arquivo mexeu para que você possa ver na sua aplicação.

Se eu chegar agora aqui no "app", eu vou colocar aqui um alert('oi'), vou salvar, fica olhando, salvei, quando eu salvo ele falou que detectou uma mudança e que fez uma compilação incremental. Se eu olho lá agora para pasta "dist > app", o alert estar lá.

Mas agora, temos um problema aqui, qual é o problema? Nós queremos que esse processo de compilação rode o tempo todo, mas eu também quero rodar o meu servidor web, por que qual é a sacada?

## Server e Watch

A sacada é que toda vez que eu alterar a minha pasta "app", a pasta "dist" vai ser modificada, o meu servidor web, que eu expliquei para vocês no início do curso que ele fica escutando quaisquer mudanças na pasta "dist", vai fazer o refresh no navegador.

Eu quero que isso aconteça, eu quero modificar um arquivo "ts", ele vai gerar o arquivo na pasta "dist", quando o meu servidor, o Live Server está disputando qualquer modificação na pasta "dist" ele automaticamente vai fazer o refresh no browser.

Olha maravilha, se alterou o arquivo "ts", esquece, o navegador vai fazer o refresh e você vai ter sempre o resultado final da compilação do arquivo TypeScript lá. Para fazer isso, eu preciso fazer o compilador TypeScript e o servidor rodarem ao mesmo tempo. Como eu faço isso?

Se você olhar aqui no "package.json" já tem adicionado aqui esse script aqui `start`, que usa esse módulo que já veio com o nosso projeto que permite que o node execute dois scripts em paralelo. Se você olhar aqui, ele vai executar o `npm run watch` e o `npm run server`.


Vamos vê-lo em ação? Vou chegar no terminal. Feche o seu navegador para que ele abra de novo, para fazer todo o processo, ficamos mais impressionados ainda. `npm run start`, é ele que vamos usar até o final do curso. Fiz isso, ele vai executar o compilador TypeScript e meu servidor aqui abriu.

Agora podemos fazer qualquer alteração, que automaticamente o `watch` e o `run server` irão rodar automaticamente.

[Continuação..](/estudos/modificadorPrivate.md)


[README](/README.md)