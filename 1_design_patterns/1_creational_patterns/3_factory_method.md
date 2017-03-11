# Factory Method
## Intenção
* Definir uma interface para criação de um objeto, mas permitir que subclasses decidam qual classe instanciar. _Factory Method_ permite que uma classe transfira a instanciação para subclasses.
* Definir um construtor "virtual".
* O operador ```new``` é considerado nocivo.

## Problema
Um _framework_ precisa padronizar o modelo arquitetural para uma variedade de aplicações, mas permitir que aplicações individuais definam o seu próprio domínio de objetos e providenciar para a sua própria instanciação.

## Discussão
_Factory Method_ é para criar objetos como um Método Modelo é para implementar um algoritmo. Uma superclasse especifica todos os comportamentos padrões e genéricos (usando "_placeholders_" virtuais puros para etapas de criação), e então delegam os detalhes da criação para subclasses que são fornecidas pelo cliente.

_Factory Method_ faz o projeto mais customizável e somente um pouco mais complicado. Outros padrões de projeto precisam de novas classes, enquanto que o _Factory Method_ somente precisa de uma nova operação.

As pessoas geralmente usam o _Factory Method_ como a forma padrão para criar objetos; mas ele não é necessário se: a classe que é instanciada nunca muda, ou a instanciação ocupa uma operação que as subclasses pode facilmente sobrescrever (como uma operação de inicialização).

_Factory Method_ é parecido com o _Abstract Factory_ mas sem a enfase em famílias.

_Factory Methods_ são rotineiramente especificados por um _framework_ arquitetural, e então implementados pelo usuário do _framework_.

Factory Methods are routinely specified by an architectural framework, and then implemented by the user of the framework.

Structure
A implementação do _Factory Method_ discutido no _Gang of Four_(abaixo) em grande parte sobrepõe-se com o _Abstract Factory_. Por esta razão, a apresentação neste capítulo foca na abordagem que tornou-se popular desde então.  

![Scheme of Factory Method](https://sourcemaking.com/files/v2/content/patterns/Factory_Method.svg)

Uma crescente definição popular do _factory method_ é: um método estático de uma classe que retorna um objeto daquele tipo de classe. Mas diferente de um construtor, o objeto atual que ele retorna pode ser uma instancia de uma subclasse. Diferente de um construtor, um objeto existente pode ser reusado, ao invés de criar um novo objeto. Diferente de um construtor, _factory methods_ podem ter nomes diferentes e mais descritivos(por exemplo: ```Color.make_RGB_color(float red, float green, float blue)``` e ```Color.make_HSB_color(float hue,float saturation,float brightness)```).

![Scheme of Factory Method](https://sourcemaking.com/files/v2/content/patterns/Factory_Method_1.svg)

O cliente é totalmente desacoplado dos detalhes de implementação das classes derivadas. Criação Polimórfica agora é possível.

![Scheme of Factory Method](https://sourcemaking.com/files/v2/content/patterns/Factory_Method__.svg)


## Exemplo
O _Factory Method_ define uma interface para criar objetos, mas permite que as subclasses decidam quais classes instanciar. Prensas de moldagem por injeção demonstram este padrão. Fabricantes de brinquedos de plástico processam plástico moldando pó, e injetando o plástico em moldes das formas desejadas. A classe do brinquedo (car, action, figure, etc.) é determinada pelo molde.

![Example of Factory Method](https://sourcemaking.com/files/v2/content/patterns/Factory_Method_example1.svg)


## Check list
1. Se você tem uma hierarquia de herança que exercita polimorfismo, considere adicionar uma capacidade de criação polimórfica definindo um _factory method_ estático(```static```) na classe base.
2. Projete os argumentos para o _factory method_. Que qualidades ou características são necessárias ou suficientes para identificar a classe derivada correte para instanciar?
3. Considere planejar um "_object pool_" interno que irá permitir que os objetos possam ser reusados ao invés de criá-los a partir do zero.
4. Considere fazer todos os construtores ```private``` ou ```protected```.

## Regras de Ouro
* Classes de _Abstract Factory_ são geralmente implementadas com _Factory Methods_, mas elas podem ser implementadas usando Protótipo.
* _Factory Methods_ são geralmente chamados dentro de Métodos Modelo.
* _Factory Method_: criação através da herança. Protótipo: criação através da delegação.
* Geralmente, projetos começam Geralmente, projetos começam usando Factory Method (menos complicado, mais customizável, subclasses proliferam) e evoluem para Abstract Factory, Protótipo ou Construtor (mais flexivel, mais complexo) na medida que o projetista descobre onde mais flexibilidade é necessária.
* Protótipo não precisa do subclassing, mas ele precisa de uma operação de Inicialização. Factory Method precisa de subclassing, mas não precisa de Inicialização. 
* A vantagem de um _Factory Method_ é que ele pode retornar a mesma instancia múltiplas vezes, ou pode retornar uma subclasse ao invés de um objeto com o tipo exato.
* Alguns defensores do _Factory Method_ recomendam que, como uma questão de linguagem de projeto(ou não, por uma questão de estilo) absolutamente todos os construtores precisam ser privados ou protegidos(```private``` ou ```protected```). Não é assunto da importância de ninguém se uma classe fabrica um novo objeto ou recicla um objeto antigo.
*  O operador ```new``` é considerado nocivo. Existe uma diferença entre requisitar um objeto e criar um. O operador ```new``` sempre cria um objeto, e falha em encapsular a criação do objeto. O _Factory Method_ garante o encapsulamento, e permite que o objeto seja requisitado sem o acoplamento inextricável do ato de criação.
