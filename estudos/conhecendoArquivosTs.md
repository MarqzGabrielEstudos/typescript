# Conhecendo arquivos TS

[Arquivo anterior](/estudos/instalandoTypescript.md)


[README](/README.md)

- Trocar `app.js` e `negociacao.js` para arquivos `.ts`.
- Mover `negociacao.ts` para a pasta `./app/models` e o `app.ts` para a pasta `./app`.
- A pasta `dist` precisa conter tudo aquilo que o navegador entende, mas o navegador não entende arquivos `.ts`.
- Então os arquivos `.ts` vão para a pasta `app` e precisaremos compilar esses arquivos para `.js`, onde ficarão na pasta `dist` e o navegador irá interpretá-los.

[Continuação...](/estudos/configuracaoBasicaCompilador.md)