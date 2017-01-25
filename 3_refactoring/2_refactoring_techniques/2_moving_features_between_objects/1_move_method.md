# Mover Métodos
## Problema
Um método é usado em outra classe que não é a sua.

![alt text](https://sourcemaking.com/images/refactoring/Move%20Method%20-%20Before.png)

## Solução
Criar um novo método na classe que use o outro método, então mover o código do método antigo para cá. Transformar o código do método original em uma referência ao novo método na outra classe ou então remova ele inteiramente.

![alt text](https://sourcemaking.com/images/refactoring/Move%20Method%20-%20After.png)

## Porque Refatorar
* Você deve mover um método para uma classe que contenha a maioria dos dados usados pelo método. Isto faz as classes mais coerentes internamente.
* Você deve mover um método para reduzir ou eliminar a dependência das classes, chamando o método na classe em que ele está localizado. Isto pode ser útil se a classe a ser chamada já é dependente da classe para qual você está planejando mover este método. Isto reduz a dependência entre classes.

## Como Refatorar
* Verifique todas as funcionalidades usadas pelo método antigo na sua classe. Pode ser uma boa ideia movê-las também. Como uma regra, se uma funcionalidade é usada somente pelo método em consideração, você deve certamente mover esta funcionalidade. Se alguma funcionalidade é usada por outros métodos também, você deve mover estes métodos também. As vezes é muito mais fácil mover um número grande de métodos do que definir relacionamentos entre eles nas diferentes classes.
* Tenha certeza que o método não está declarado em _superclasses_ ou _subclasses_. Se este for o caso, você terá que se abster de movê-lo, ou implementar algum tipo de polimorfismo na classe destinatária para garantir funcionalidades variadas de um método dividido em classes doadoras.
* Declare o novo método na classe destinatária. Você pode querer dar um novo nome para o método que é mais apropriado para a nova classe.
* Decida como você irá referenciar a classe destinatária. Você pode ter uma variável ou método que retorne o objeto apropriado, mas se não, você precisa escrever um novo método ou variável para guardar o objeto na classe destinatária.
* Agora você tem uma forma de referenciar o objeto destinatário e um novo método na sua classe. Com tudo isto, você pode transformar o método antigo em uma referência ao novo método.
* Observe: você pode remover o método antigo inteiramente? Se sim, coloque uma referência ao novo método em todos os lugares que usam o antigo.