# Cadeia de Mensagens
## Sinais e Sintomas
No código ocorre várias chamadas encadeadas _$a->b()->c()->d()_.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/message-chains-1.png)

## Causas do Problema
Uma cadeia de mensagens ocorre quando um cliente chama um objeto, que chama outro, que chama outro, por ai vai. Estas cadeias significam que o cliente é dependente da navegação através da estrutura de classes. Qualquer mudança nessas relações necessitam mudança no cliente.

## Tratamento
* Para acabar com uma cadeia de mensagens, utilize _Hide Delegate_.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/message-chains-2.png)

* As vezes é melhor pensar como o objeto final está sendo usado. Talvez, faça sentido utilizar o _Extract Method_ para que esse método seja utilizado no começo da cadeia, usando _Move Method_.

## Consequência
* Pode reduzir a dependência entre as classes da cadeia.
* Pode reduzir o código macarrônico.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/message-chains-3.png)

## Quando Ignorar
* Se utilizar demais o _Hide Delegate_, pode ficar difícil de ver onde as coisas estão acontecendo. Outra maneira de dizer isso, evite o _Middle Man smell_ também.
