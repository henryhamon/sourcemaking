# Remover Intermediários
## Problema
Uma classe tem muitos métodos que simplesmente delegam a outros objetos.

![Antes](https://sourcemaking.com/images/refactoring/Remove%20Middle%20Man%20-%20Before.png)

## Solução
Deletar estes métodos e forçar o cliente a chamar os métodos finais diretamente.

![Depois](https://sourcemaking.com/images/refactoring/Remove%20Middle%20Man%20-%20After.png)

## Porque Refatorar
Existem dois tipos de problemas:
1. A classe servidora não faz nada ela mesma e simplesmente cria complexidade desnecessária. Neste caso, deve-se pensar se esta classe é mesma necessária.
2. Toda vez que uma funcionalidade é adicionada a classe delegada, você precisa criar um método de delegação para isso na classe servidora. Se muitas mudanças são feitas, isto será bastante cansativo.

## Como Refatorar
1. Crie um _getter_ para acessar o objeto da classe delegada da classe servidora.
2. Substitua as chamadas aos métodos de delegação na classe servidora com chamadas diretas para os métodos na classe delegada.