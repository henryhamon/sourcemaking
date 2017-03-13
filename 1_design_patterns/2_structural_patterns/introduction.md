# Padrões Estruturais
Na engenharia de _software_, são os padrões de projeto estruturais que facilitam o projeto identificando uma forma simples de realizar relacionamentos entre entidades. 
* [Adaptador](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/1_adapter.md): Combina interfaces de diferentes classes.
* [Ponte](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/2_bridge.md): Separa uma interface de um objeto da sua implementação.
* [Composto](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/3_composite.md): Uma estrutura de árvore de objetos simples e compostos.
* [Decorador]("https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/4_decorator.md): Adiciona responsábilidades para objetos dinâmicamente.
* [Fachada](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/5_facade.md): Uma simples classe que representa o subsistema inteiro.
* [Flyweight](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/6_flyweight.md): Uma instância refinada usada para compartilhamento eficiente.
* [Dados de Classe Privada](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/7_private_class_data.md): Restringe acesso do acessor/mutador.
* [Proxy](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/8_proxy.md): Um objeto representando outro objeto.

## Regras de Ouro
* Adaptador faz as coisas funcionarem depois de elas serem projetadas. A Ponte faz este trabalho antes disto.
* A Ponte é projetada para permitir que a abstralção e a implementação variem independentemente. Adaptador é adaptado para fazer classes não relacionadas trabalharem juntas.
* O Adaptador fornece uma interface diferente para o seu assunto. Proxy fornece a mesma interface. Decorador fornece uma interface enriquecida.
* O Adaptador muda uma interface de objeto, Decorador enriquece as responsabilidades de um objeto. Decorador é portanto mais transparente para o cliente. Como uma consequência, Decorador suporta composição recursiva, o que não é possível com Adaptadores puros.
* Composto e Decorador tem diagramas de estrutura parecidos, refletindo o fato que ambos se apoiam em composição recursiva para organizar um amplo número de objetos
* Composto pode ser atravessado com Iterador. Visitante pode aplicar uma operação sobre um Composto. Composto pode usar Cadeia de Responsábilidade para permitir que componentes acessem propriedades globais através dos seus pais. Pode também usar o Decorador para sobrescrever estas propriedades em partes de sua composição. Ele pode usar Observador para emprestar a estrutura de um objeto para outro e Estado para permitir que um componente mude o seu comportamento na medida em que muda o seu estado.
* Composto pode deixar você compor um Mediador de peças menores através de composição recursiva.
* Decorador permite que você troque a pele de um objeto. Estratégia permite que você troque os culhões.
* Decorador é feito para permitir que você adicione responsabilidades a objetos sem o _subclassing_. Composto(s) foco não é em embelezamento, mas sim na representação. Estas intenções são distintas, mas complementares. Consequentemente, Composto e Decorador são frequentemente usados juntos. 
* Decorador e Proxy tem propostas diferentes mas estruturas similares. Ambos descrevem como fornecer um nível de indireção para outro objeto, e as implementações mantém uma referência para o objeto para qual eles mandam solicitações.
* Fachade define uma nova interface, enquanto que o Adaptador reutiliza uma interface antiga. Lembre que o adaptador faz duas interfazer existentes trabalharem juntas ao contrário do que definir uma nova inteiramente.
* Objetos da Fachada são geralmente _Singleton_ porque somente um objeto _Fachada_ é necessário.
* Mediador é similar ao Fachada no fato que eles abstraem a funcionalidade de classes existentes. Mediador abstrae/centraliza comunicação arbitrária entre objetos coligados, Fachada define uma interface mais simples para um subsistema, e não adiciona uma nova funcionalidade, e isto não é conhecido pelas classes do subsistema.
* _Abstract Factory_ pode ser usado como uma alternativa para a _Fachada_ para esconder classes específicas de plataforma.
* Enquanto que _Flyweight_ mostra como fazer muitos pequenos objetos, Fachada mostra como fazer um único objeto representar um subsistema inteiro.
* _Flyweight_ é geralmente combinado com o Composto para implementar nós de folha compartilhados.
* _Flyweight_ explica quando e como objetos de Estado podem ser compartilhados.