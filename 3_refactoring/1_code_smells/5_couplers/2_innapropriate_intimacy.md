# Intimidade Inapropriada
## Sinais e Sintomas
Uma classe utiliza campos e métodos internos de outra classe

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/inappropriate-intimacy-1.png)

## Causas do Problema
Não enxergar classes que estão muito acopladas. Boas classes devem saber o mínimo possível sobre outras classes. Sendo assim elas se tornam mais fáceis de manter e reutilizar.

## Tratamento
* A maneira mais fácil é usar o _Move Method_ e _Move Field_ para mover partes de uma classe para a classe onde essas partes são mais utilizadas. Isso apenas funciona se a classe realmente não precisar dessas partes.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/inappropriate-intimacy-2.png)

* Outra solução é usar _Extract Class_ and _Hide Delegate_ na classe para fazer a relação entre os códigos "oficial".
* Se ambas as classes são interdependentes, você deve utilizar _Change Bidirectional Association to Unidirectional_.
* Se essa "intimidade" ocorre entre subclasses e superclasses, considere _Replace Delegation with Inheritance_.

## Consequência
* Torna o código mais organizado.
* Simplifica o uso do código e sua reusabilidade.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/inappropriate-intimacy-3.png)
