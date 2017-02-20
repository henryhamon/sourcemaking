# Classe Inline
## Problema
Uma classe não faz quase nada e não é responsável por nada, e não tem nenhuma responsabilidade adicional planejada para ela.

![Antes](https://sourcemaking.com/images/refactoring/Inline%20Class%20-%20Before.png)

## Solução
Mover todas as funcionalidades da classe para outra.

![Depois](https://sourcemaking.com/images/refactoring/Inline%20Class%20-%20After.png)

## Porque Refatorar
Geralmente esta técnica é necessário depois que as funcionalidades de uma classe são "transplantadas" para outras classes, deixando a mesma sem ter muito o que fazer.

## Benefícios
* Eliminar classes desnecessárias libera memória operacional no computador, e largura de banda.

## Como Refatorar
1. Na classe destinatária, crie os campos e métodos públicos presentes na classe original. Os métodos devem referenciar aos métodos equivalentes da classe original.
2. Substitua todas as ocorrências da classe doadora com referências aos campos e métodos da classe destinatária.
3. Agora teste o programa e tenha certeza que nenhum erro foi adicionado. Se os testes mostrarem que tudo está funcionando OK, começe usando a técnica [Mover Métodos](https://github.com/henryhamon/sourcemaking/blob/master/3_refactoring/2_refactoring_techniques/2_moving_features_between_objects/1_move_method.md) e [Mover Campos](https://github.com/henryhamon/sourcemaking/blob/master/3_refactoring/2_refactoring_techniques/2_moving_features_between_objects/2_move_field.md) para transplantar completamente todas as funcionalidades da classe original para a classe destinatária. Continue fazendo isto até que a classe original esteja completamente vazia.
4. Apague a classe original.