# Longa Lista de Parâmetros
## Sinais e Sintomas
Mais de três ou quatro parâmetros em um método.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/long-parameter-list-1.png)

## Causas do Problema
Uma longa lista de parâmetros pode surgir depois que vários algoritmos são unidos em um único método. A longa lista pode ter sido criada para qual e como o algoritmo irá rodar.

A longa lista de parâmetros pode também ser subproduto de tentativas de fazer as classes mais independentes uma da outra. Por exemplo, para criar objetos específicos, foi movida a chamada do método de criação para dentro de outro método. A classe original não vê mais a relação entre os objetos, e a dependência é diminuída. Mas, muito desses objetos são criados, e cada um deles tem seus próprios parâmetros, o que significa que surgirá uma longa lista de parâmetros.

É difícil entender tais listas, o que se torna contraditório e difícil de usar conforme elas crescem. Em vez de receber vários parâmetros, o objeto pode usar dados dele mesmo. Se o objeto atual não contém todos os dados necessários, outro objeto(o que irá usar os dados necessários) pode ser passado como parâmetro do método.

## Tratamento
* Verifique quais valores são passados como parâmetros. Se alguns deles são apenas resultados de chamadas de métodos de outro objeto, use _Replace Parameter with Method Call_. Este objeto pode ser colocado como campo de sua própria classe ou passado como um parâmetro de método.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/long-parameter-list-2.png)

* Em vez de passar um conjunto de dados recebido de outro objeto como parâmetro, passe o próprio objeto para o método, usando _Preserve Whole Object_.
* Se tem muitos elementos não relacionados, talvez possa juntá-los em um único objeto parâmetro via _Introduce Parameter Object_.

## Consequência
* Mais legivel, menos código.
* Refatorar pode mostrar código duplicado não visto anteriormente.

## Quando Ignorar
* Não altere a lista de parâmetros se isso causar dependência entre as classes.
