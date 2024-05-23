# Aprimorando configuração

[Arquivo anterior](/estudos/configuracaoBasicaCompilador.md)


[README](/README.md)


Bom, do jeito que as configurações estão agora, podemos apagar os arquivos `app.js` e `negociacao.js` que, ao compilar novamente, eles serão criados novamente.

Porém, se apagarmos alguma propriedade instancia de negociacão, como por exemplo a data, o typescript vai dar erro, e mesmo dando erro, ele vai compilar do mesmo jeito, e não queremos isso, queremos que só compile quando o programa não estiver dando erros. Para que isso acontença, iremos adicionar mais uma coisa no `tsconfig.json` logo embaixo do `target`, que é o `noEmitOnError`.

```json
{
  "compilerOptions": {
    "outDir": "dist/js",
    "target": "ES6",
    "noEmitOnError": true
  },
  "include": ["app/**/*"]
}
```

Agora os arquivos js serão  compilados apenas quando não houver erros.
Lembrand que se você vai resolver algum problema no seu código e você vai olhar o arquivo "js" ou "ts"? Você vai olhar o arquivo "ts", porque ele é o código-fonte, o "js" é gerado a partir dele, se você tem que fazer uma correção é no arquivo "ts".

[Continuação...](/estudos/automatizandoCompilacao.md)


[README](/README.md)