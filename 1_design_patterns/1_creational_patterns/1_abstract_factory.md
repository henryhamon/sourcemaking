# Abstract Factory
## Intenção
* Fornecer uma interface para criação de objetos relacionados ou dependentes sem especificar suas classes concretas.
* Uma hierarquia que encapsula: muitas possíveis "plataformas", e a construção do conjunto de "produtos".
* O operador _new_ é considerado prejudicial.

## Problema
Se uma aplicação precisa ser portável, é necessário encapsular as dependecias de plataforma. Estas plataformas precisam incluir: um sistema de janelas, sistema operacionais, banco de dados, etc. Muitas vezes, esse encapsulamento não é projetado com antecedência, e muitas adaptações e _case statements_ com opções para todos as plataformas suportadas, começam se multiplicar como coelhos no código.

## Discussão
Fornecer um nível de indireção que abstraia a criação das famílias de objetos dependentes ou relacionados, sem especificar diretamente suas classes concretas. O objeto "factory" tem a responsabilidade de fornecer serviços(métodos) para toda uma plataforma ou família de objetos. Clientes nunca criam objetos da plataforma diretamente, sempre utilizam a factory fazer isso para eles.
Este mecanismo faz com que a troca de famílias de objetos seja fácil, porque a classe específica do objeto "factory" apareça apenas uma vez em toda a aplicação, onde é instanciada. A aplicação pode alterar toda a família de produtos simplesmente por instanciar uma classe _abstract factory_ concreta diferente.
Pelo motivo do serviço fornecido ser tão impactante, esta classe geralmente é implementada como um _singleton_.

## Estrutura
A _abstract factory_ define um método _factory_ por produto. Cada método _factory_ encapsula o operador _new_ e os produtos de classes concretas, de uma plataforma específica. Cada "plataforma" é modelada como uma classe derivada de _factory_.

![alt text](https://sourcemaking.com/files/v2/content/patterns/Abstract_Factory.svg)


## Exemplo
O propósito do _Abstract Factory_ é fornecer uma interface para criação de famílias de objetos relacionados, sem especificar as classes concretas. Este padrão é achado nos equipamentos de estampagem de chapa metálica, usado nas fábricas automobilísticas japonesas. O equipamento é um _Abstract Factory_, o qual cria autopeças. O mesmo maquinário é também usado para criar portas direitas e esquerdas, pára-lamas direito e esquerdo, capôs, etc. para diferentes tipos de carros. Através do uso de rolos para trocar os moldes de estampagem, as classes concretas produzidas pelo maquinário, podem ser alteradas em cerca de 3 minutos.

![alt text](https://sourcemaking.com/files/v2/content/patterns/Abstract_Factory_example1.svg)


## Check List
1. Defina se a independencia de plataforma e a criação de serviços são a origem do problema.
2. Mapeie uma matriz de "plataforma" versus "produto".
3. Defina uma interface _factory_ que consista em um método _factory_ por produto.
4. Defina uma classe _factory_ derivada para cada plataforma, que encapsula todas as referências para o operador _new_.
5. O cliente deve tirar todas as referências _new_ e passar a utilizar os métodos _factory_ para criar os objetos produtos.

## Regras de Ouro
* Algumas vezes mais de um padrão pode resolver o problema: tem casos que tanto o _Prototype_ quanto o _Abstract Factory_ podem ser benéficos. Outras vezes eles podem ser complementares: _Abstract Factory_ pode armazenar um conjunto de _Prototypes_ o qual clona e retorna objetos produto, _Builder_ pode usar um dos outros padrões para implementar quais componentes devem ser construídos. _Abstract Factory_, _Buider_ e _Prototype_ podem utilizar o _Singleton_ na sua implementação.
* _Abstract Factory_, _Builder_ e _Prototype_, definem um objeto _Factory_, responsável por conhecer e criar as classes de objetos produto, e fazer disso um parâmetro do sistema. _Abstract Factory_ possui o objeto _factory_ produzindo objetos de muitas classes. _Builder_ possui o objeto _factory_ construindo produtos complexos, incrementalmente, usando um protocolo complexo correspondente. _Prototype_ tem um objeto _factory_ construindo um outro objeto a partir da cópia deste.
* Classes _Abstract Factory_ geralmente são construídas utilizando _Factory Methods_, mas também podem ser feitas utilizando _Prototype_.
* _Abstract Factory_ pode ser usada como uma alternativa para o _Facade_, para camuflar a especificação da plataforma.
* O _Builder_ é focado na construção de objetos complexos passo-a-passo. _Abstract Factory_ da ênfase na criação de famílias de objetos. _Builder_ retorna um produto como passo final, já o _Abstract Factory_, assim que o método é invocado, o objeto é retornado.
* Frequentemente, se começa utilizando o _Factory_ por ser mais simples e mais customizável, e evolui para _Abstract Factory_, _Prototype_ ou _Builder_ que são mais flexíveis e também mais complexos, de acordo com a complexidade do projeto e necessidade de mais flexibilidade.
