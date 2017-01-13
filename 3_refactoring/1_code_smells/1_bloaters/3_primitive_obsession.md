# Obsessão Primitiva
## Sinais e Sintomas
* Uso de tipo de dado primitivo em vez de pequenos objetos para tarefas simples(como moedas, strings especiais para números de telefones, etc.)
* Uso de constantes para codificar informações(como a constante `_USER_ADMIN_ROLE = 1_` para referenciar usuários com privilégios de administrador.
* Uso de constantes como nome de campos para usar em um array de dados.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/primitive-obsession-1.png)

## Causas do Problema
Como a maioria dos outros _smells_, obsessão primitiva surge em momentos de fraqueza. O programador fala, "só mais um campo pra armazenar dados!". Criar um campo primitivo é bem mais fácil que criar uma classe nova, certo? Então isso é feito. Então outro campo precisa ser adicionado da mesma maneira. A classe se torna grande e pesada.

Tipos primitivos são frequentemente usados para "simular" tipos. Então em vez de você ter um tipo separado, você tem um conjunto de números ou strings que formam os dados permitidos para alguma entidade. Nomes fáceis de entender são dados para números e strings via constantes, de maneira que eles ficam espalhados por todo lado.

Outro exemplo de um mal uso de tipo primitivo é simulação de campo(_field simulation_). A classe contém um grande array de diferentes dados e strings constantes(que são especificados na classe) são usados como índice de array pra buscar esses dados.

## Tratamento
* Se você tem uma grande variedade de campos, é possível lógicamente agrupar alguns deles em suas próprias classes. Ainda melhor, mover o comportamento associados à esses dados para classe também. Para isso, tente _Replace Data Value with Object_.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/primitive-obsession-2.png)

* Se os valores dos campos primitivos são usados como parâmetros de métodos, vá com _Introduce Parameter Object_ ou _Preserve Whole Object_.
* Quando dados complicados são codificados em variáveis, use _Replace Type Code with Class_, _Replace Type Code with Subclasses_ ou _Replace Type Code with State/Strategy_.
* Se existe arrays entre as variáveis, use _Replace Array with Object_.

## Consequêcia
* O código se torna mais flexível, graças ao uso de objetos em vez de tipos primitivos.
* Melhor entendimento e organização de código. Operações em cima dos dados são feitos no mesmo lugar, em vez de ser espalhado. Sem dúvidas sobre o significado dessas constantes estranhas e o porquê delas estar em um array.
* Mais fácil de achar código duplicado.

![alt text](https://sourcemaking.com/images/refactoring-illustrations/2x/primitive-obsession-3.png)
