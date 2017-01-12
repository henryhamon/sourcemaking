# Strategy
## Intenção
* Definir uma família de algoritmos, encapsulando cada um, e deixando-os substituíveis. _Strategy_ deixa os algoritmos bem independentes para quem for usá-lo.
* Detectar a abstração em uma _interface_, deixar detalhes de implementação para classes derivadas.

## Problema
Uma das principais estratégias de um design orientado a objeto é o princípio [aberto-fechado(open-closed)](http://www.devmedia.com.br/open-close-principle/18970).

A figura demonstra como isso normalmente é feito - encapsula os detalhes da interface em uma classe base, e deixa os detalhes para as classes derivadas. Clientes então podem se acoplar a uma interface, e não sofrer ao fazer uma mudança: sem impacto quando o número de subclasses muda, e sem impacto quando uma implementação de uma classe derivada muda.

![alt text](https://sourcemaking.com/files/v2/content/patterns/Strategy1.svg)

Um ditado da comunidade de software conhecido há muito tempo é, "maximize a coesão e minimize o acoplamento". A abordagem orientada a objeto mostrada na figura, se refere a minimização de acoplamento. Desde que o cliente está acoplado a abstração(interface) e não a uma implementação em particular da abstração, o cliente está fazendo um "acoplamento abstrato".

A caracterização mais popular de um princípio de "acoplamento abstrato" é o "programe para uma interface, não uma implementação".

Clientes preferem um "nível a mais de indireção" que a _interface_ oferece. A _interface_ provém a abstração do que o cliente precisa, e a implementação da interface na verdade está escondida.

## Estrutura
A interface representa tanto uma classe base abstrata, quanto a assinatura dos métodos que o cliente precisa. No primeiro caso, a hierarquia de herança representa um polimorfismo dinâmico. No outro caso, a _interface_ representa  o modelo de código para o cliente e a hierarquia de herança representa um polimorfismo estático.

![alt text]("https://sourcemaking.com/files/v2/content/patterns/Strategy_.svg")

## Exemplo
O _Strategy_ define um conjunto de algoritmos que podem ser usados indistintamente. Maneiras de se transportar para um aeroporto é um exemplo de _Strategy_. Dá para ir de várias maneiras, como, ir dirigindo, pegar um táxi, um ônibus, usar o transporte do aeroporto, limusine, etc. Em alguns aeroportos, metrôs e helicópteros também são uma opção. Todos esses tipos de transporte irão levar o viajante para o aeroporto, e eles podem ser usados indistintamente. O viajante precisa escolher a estratégia baseado no custo, conveniência e tempo.

![alt text]("https://sourcemaking.com/files/v2/content/patterns/Strategy_example1.svg")

## Check List
1. Identifique um algoritmo que o cliente gostaria de acessar de maneira flexível.
2. Especifique a assinatura para um algoritmo em uma interface.
3. Implemente os algoritmos nas classes base.
4. Clientes se acoplam a interface.

## Regras de Ouro
* _Strategy_ é como o _Template Method_ com exceção da sua granularidade.
* _State_ é como o _Strategy_ com exceção de sua intenção.
* _Strategy_ deixa você mudar a implementação de um objeto. _Decorator_ permite você mudar de pele.
* _State_, _Strategy_, _Bridge_(e em alguma escala o _Adapter_) tem estruturas de solução similares. Todos eles são do tipo _'Handle/Body' idiom_. Eles se diferenciam na intenção, isto é, resolvem problemas diferentes.
* _Strategy_ possui 2 implementações diferentes, a primeira é parecida com o _State_. A difereça é onde acontece a ligação (_Strategy_ é um padrão _bind-once_, enquanto o _State_ é mais dinâmico).
* Objetos _Strategy_ frequentemente fazem bons _Flyweights_.
