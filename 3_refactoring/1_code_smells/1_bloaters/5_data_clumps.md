# Agrupamento de Dados
## Sinais e Sintomas
Algumas vezes diferentes partes do código possuem grupos idênticos de variáveis (como os parâmetros para conectar com o banco de dados). Esses grupos devem ser transformados em classes.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/data-clumps-1.png)

## Causas do Problema
Frequentemente esses grupos de dados acontecem por ser mal estruturado ou "programação copia e cola(copypasta programming)".

Se você quer ter certeza que é um agrupamento de dados, apenas apague um dos dados e veja se os outros valores ainda fazem sentido. Se esse não é o caso, este é um bom sinal de que o grupo de variáveis deve ser combinado em um objeto.

## Tratamento
* Se os campos repetidos formam os campos de uma classe, utilize _Extract Class_ pra mover os campos para sua própria classe.
* Se o mesmo grupo de dados é passado como parâmetros de método, use _Introduce Parameter Object_ para transformar os dados em uma classe.
* Se alguns dados são passados para um método, pense em passar todo o objeto, em vez dos campos individuais. _Preserve Whole Object_ irá ajudar nessa tarefa.
* Veja o código usado por esses campos. Pode ser uma boa idéia mover esse código para uma classe de dados.

## Consequência
* Melhora o entendimento e organização do código. Operações sobre os dados em particular estão agora reunidos em um único local, em vez de espalhado pelo código.
* Reduz o tamanho do código.

![alt text](instead of haphazardly throughout the code)

## Quando Ignorar
* Passar o objeto todo como parâmetro, em vez de passar apenas seus valores(tipos primitivos), pode causar dependência entre as duas classes.
