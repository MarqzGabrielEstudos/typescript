# Surpresa ao instanciar uma negociação

[Arquivo anterior](/estudos/integracaoFormulario.md)


[README](/README.md)

Agora que estamos com tudo pronto, “com a faca e o queijo na mão”, vimos que quando eu coloco as datas, a quantidade, o valor e clico em incluir eu tenho acesso aos elementos do dom. Sabemos que todo input tem a propriedade `.value`, que eu tenho acesso ao valor desse input, eu tenho os insumos para criar a minha negociação. Vamos voltar para lá.

Eu vou fazer isso: `const negociao = new Negociacao();`, dentro de `adiciona()`.

Agora eu vou passar os valores que a minha negociação está esperando. O primeiro é a data, `( this.inputData.value, this;inputQuantidade.value, this.inputValor.value); }` e por fim tenho uma negociação criada Não há nenhum erro de compilação, parece que meu código vai funcionar em *runtime*.

Agora vou fazer um `console.log(negociacao);`. Vou salvar, vou esperar compilar. Tudo bonito, tudo maravilhoso. Verifique se você colocou o js aqui. Vou voltar para o navegador, vou dar um clear aqui, tirar esse “preserve log” e dar um clear. Vou colocar qualquer data, quantidade e valor, vou clicar em incluir e vemos nossa negociação que foi criada.

Felicidade? Não. Não é felicidade nenhuma é tristeza porque se você olhar essa negociação, primeiro, a data tinha que ser um date e não essa *string*. Segundo, a quantidade está como *string*, o valor está como *string*. Isso faz parte da definição da nossa classe, eu espero que a quantidade seja um número, espero que o valor seja um número, espero que a data seja uma data.

O que aconteceu? Por que o TypeScript não está brilhando aqui? Não está brilhando porque o nome já diz: TypeScript, faltou dizermos quais são os tipos dessas propriedades da minha negociação para que o TypeScript me diga que não posso colocar *string* porque não fará sentido.

Então teremos que adicionar tipos.

Código: 

```javascript
//negociacao-controller método adiciona()

import { Negociacao } from "../models/negociacao.js";

//código da classe omitido

    adiciona() {
        const negociacao = new Negociacao(
            this.inputData.value,
            this.inputQuantidade.value,
            this.inputValor.value
        );
    }
```

[Continuação...](/estudos/tipoImplicitoAny.md)


[README](/README.md)