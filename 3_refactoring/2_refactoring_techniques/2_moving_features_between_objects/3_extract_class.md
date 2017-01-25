# Extração de Classe 
## Problema
Quando uma classe faz o trabalho de duas, resultados constransgedores.

![Antes](https://sourcemaking.com/images/refactoring/Extract%20Class%20-%20Before.png)

## Solução
Criar uma nova classe e colocar os campos e métodos responsáveis pela funcionalidade relevante nela.

![Depois](https://sourcemaking.com/images/refactoring/Extract%20Class%20-%20After.png)

## Porque Refatorar
Classes sempre começam limpas e fáceis de entender. Elas fazem seu próprio trabalho e lembram o seu negócio como ele é, sem tocar no trabalho de outras classes. Mas quando um programa expande, um método é adicionado, então um campo... e eventualmente, algumas classes estão com mais responsabilidades que nunca imaginaram. 

## Benefícios
* Este método de refatoração irá ajudar a manter a aderência ao Princípio de Responsabilidade Única (_Single Responsibility Principle_). O código de suas classes será mais óbvio e entendível.
* Classes de responsabilidade única são mais confiáveis e tolerantes a mudanças. Por exemplo, digamos que você tem uma classe que é responsável por dez coisas. Quando você muda esta classe para fazer melhor uma coisa, acaba correndo o risco de quebrar as outras nove.

## Inconvenientes
* Se você exagerar com esta tecnica de refatoração, você terá que recorrer ao _[Inline Class](https://sourcemaking.com/refactoring/inline-class)_

## Como Refatorar
Antes de começar, decida como exatamente você quer dividir a responsabilidade das classes.
1. Crie uma nova classe contendo uma funcionalidade relevante.
2. Crie um relacionamento entre a classe antiga e a nova. De maneira ótima, este relacionamento é unidirecional; Isto permite reusar a segunda classe sem nenhum problema. No entando, se você achar necessário definir um relacionamento de duas mãos, ele pode ser definido.
3. Use [Mover Campos](https://github.com/henryhamon/sourcemaking/blob/master/3_refactoring/2_refactoring_techniques/2_moving_features_between_objects/2_move_field.md) e [Mover Métodos](https://github.com/henryhamon/sourcemaking/blob/master/3_refactoring/2_refactoring_techniques/2_moving_features_between_objects/1_move_method.md) para cada campo e método que você decidiu mover para a nova classe. Para métodos, começe com os privados para reduzir o risco de ter um monte de erros. Tente realocar somente um pedaço por vez e teste os resultados após cada movimento, para evitar uma pilha de erros para corrigir no final.
4. Quando você terminar, dê mais uma olhada nas classes resultantes. Uma classe antiga com as responsabilidades alteradas pode ser renomeada para aumentar a clareza. Verifique novamente se você pode se livrar de relacionamentos de duas mãos entre classes, se houver algum.
5. Pense também na acessibilidade exterior da nova classe. Você pode esconder a classe do cliente inteiramente fazendo-a privada, gerenciando isto via campos da classe antiga. Alternativamente, você pode fazê-la pública permitindo que o cliente altere os valores diretamente. As suas decisões dependem de quão seguro é o comportamento da classe antiga quando mudanças diretas inesperadas são feitas com os valores da nova classe.