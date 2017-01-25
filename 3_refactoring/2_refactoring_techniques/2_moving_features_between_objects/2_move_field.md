# Mover Campos
## Problema
Um campo é usado em outra classe além da sua.

![Antes](https://sourcemaking.com/images/refactoring/Move%20Field%20-%20Before.png)

## Solução
Criar um novo campo na nova classe e redirecionar todos os usuários do campo antigo para o novo.

![Depois](https://sourcemaking.com/images/refactoring/Move%20Field%20-%20After.png)

## Porque Refatorar
Geralmente os campos são movidos como uma parte da técnica de [Extração de Classe](https://sourcemaking.com/refactoring/extract-class).Decidir em qual classe deixar o campo pode ser difícil. Aqui está a nossa regra de ouro: **coloque o campo no mesmo local que o método que o usa** (ou então onde a maioria dos métodos estão)
Esta regra irá ajudar em outros casos quando um campo está localizado no local errado.

## Como Refatorar
1. Se o campo for público, a refatoração será muito mais fácil se você faz o campo _private_ e tem métodos de acesso público (para isto, você pode [Encapsular o campo](https://sourcemaking.com/refactoring/encapsulate-field)).
2. Crie o mesmo campo com os mesmos métodos de acesso na classe destinatária.
3. Decida como você irá referenciar a classe destinatária. Você pode já ter um campo ou método que retorne o objeto apropriado, se não, você irá precisar escrever um novo método ou campo para guardar o objeto da classe destinatária.
4. Substitua todas as referências do campo antigo com as apropriadas chamadas aos métodos na classe destinatária. Se o campo não é _private_, cuidado com as suas superclasses e subclasses.
5. Remova o campo na classe original. 