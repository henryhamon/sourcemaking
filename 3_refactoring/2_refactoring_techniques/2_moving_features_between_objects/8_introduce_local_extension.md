# Introdução de Extensão Local
## Problema
Uma classe de utilidades não contém algums métodos que você precisa. Mas você não pode adicionar estes métodos na classe.

![Antes](https://sourcemaking.com/images/refactoring/Introduce%20Local%20Extension%20-%20Before.png)

## Solução
Crie uma nova classe contendo os métodos e torne-a filha ou um encapsulamento da classe utilitária.

![Depois](https://sourcemaking.com/images/refactoring/Introduce%20Local%20Extension%20-%20After.png)

## Porque Refatorar
A classe que você está usando não tem os métodos que você precisa. O que é pior, você não pode adicionar estes métodos (porque as classes estão em uma bilbioteca de terceitros, por exemplo).
Existem duas saídas:
* Crie uma **subclasse** da classe relevante, contendo os métodos e herdando todo o resto da classe pai. Esta maneira é mais fácil mas as vezes é bloqueada pela classe(devido a ela ser "final").
* Crie uma classe encapsulada que contenha todos os novos métodos e qualquer outra coisa irá delegar para o objeto relacionado da classe utilitária. Este método é mais trabalhoso quando você não precisa somente codificar para manter o relacionamento entre o encapsulamento e o objeto utiliátio, mas também um grande número de métodos de delegação simples para emular a interface pública da classe utilitária.

## Benefícios
* Movendo os métodos adicionais para uma classe extensiva separada (encapsulada ou subclasse), você evita inflar classes clientes com código que não se encaixa. Os componentes do programa são mais coerentes e mais re-usáveis.

## Como Refatorar
1. Crie uma nova classe:
* Opção A: Faça ela ser uma filha da classe utilitária.
* Opção B: Se você optou por fazer um encapsulamento, crie um campo na classe guardando um objeto da classe utilitária para qual a delegação será feita. Quando usando esta opção você vai precisar também criar métodos que repitam os métodos públicos da classe utilitária e contém simples delegação aos métodos do objeto utilitário.
2. Crie um construtor que utilize os parâmetros do construtor da classe utilitária.
3. Também crie um construtor "conversor" alternativo que recebe somente o objeto da classe original nos seus parâmetros. Isto irá ajudar a substituir a extensão para objetos da classe original.
4. Crie novos de extensão na classe. Mova métodos estrangeiros de outras classes para esta classe ou ainda, apague os métodos estrangeiros se a funcionalidade deles já está presente na extensão.
5. Substitua o uso do classe utilitária com a nova classe de extensão nos locais onde a funcionalidade dela é requerida.