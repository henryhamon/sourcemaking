# Método Longo
## Sinais e Sintomas
Um método que contém muitas linhas de código. Geralmente, qualquer método que possua mais de dez linhas, deve fazer você começar a se questionar.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/long-method-1.png)

## Causas do Problema
Como no Hotel California, alguma coisa sempre está sendo adicionado no método, mas nunca retirado. Como é mais fácil escrever código do que lê-lo, este _"smell"_ permanece silencioso até que o método se torne feio e grande.

Mentalmente, é mais difícil criar um novo método do que adicionar código em um já existente: "Mas é só duas linhas, não é necessário criar um método pra isso...". Isso significa que mais algumas linhas são adicionadas, e depois mais algumas, dando origem a um código macarrônico.

## Tratamento
Como regra, se você sentir necessidade de comentar alguma coisa dentro do método(para explicá-lo), você deve pegar esse trecho de código e colocar em outro método. Mesmo se for uma única linha, pode e deve ser colocado em um método separado. E se o método tem um nome descritivo, ninguém vai precisar olhar dentro do método para saber o que ele faz.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/long-method-2.png)

* Para reduzir o tamanho do corpo do método utilize _Extract Method_.
* Se variáveis locais e parâmetros são interferidos durante o método de extração, use _Replace Temp with Query_, _Introduce Parameter Object_ ou _Perseve Whole Object_.
* Se nenhuma das opções anteriores funcionar, tente mover o método todo para um objeto separado através do _Replace Method with Method Object_.
* Operadores condicionais e laços de repetição são alguns indícios que algum código pode ser movido para outro método. Onde houver condições utilize, _Decompose Conditional_. Se encontrar laços de repetição, tente  _Extract Method_.

## Consequência
* Através de todos os tipos de código orientado a objeto, classes com pequenos métodos duram mais. Quanto maior o método ou a função, mais difícil de entender e manter os mesmos.
* Além disso, os métodos muito grandes oferecem um bom lugar para conter código duplicado desnecessário.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/long-method-3.png)

## Performance
Um acréscimo no número de métodos atinge a performance como as pessoas dizem? Em quase todos os casos o impacto é tão insignificante que nem vale a pena se preocupar com isso.

Além disso, agora com um código limpo e de fácil entendimento, é mais provável que encontre métodos que valem a pena reestruturar, para ganhos reais se houver necessidade.
