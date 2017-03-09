# Padrões de Projeto
Na engenharia de _software_, um padrão de projeto é uma solução geral que se repete comumente para um problema em um projeto de _software_. Um padrão de projeto não é um projeto terminado que pode ser transformado diretamente em código. É uma descrição ou modelo para mostrar como resolver um problema que pode ser usado em várias situações diferentes.

## Usos de Padrões de Projeto
Os padrões de projeto pode acelerar o processo de desenvolvimento provendo testados, paradigmas de desenvolvimento comprovados. Um projeto de _software_ efetivo precisa considerar problemas que podem não se tornar visíveis até mais tarde na implementação. Reutilização de padrões de projeto ajuda a prevenir problemas súbitos que podem causar problemas maiores e melhora a legibilidade do código para desenvolvedores e arquitetos familiares com os padrões.

Frequentemente, as pessoas somente ententem como aplicar certas técnicas de projeto de _software_ para certos problemas. Estas técnicas são difíceis de aplicar para uma área de problemas mais ampla. Os padrões de projeto dão soluções gerais, documentadas em um formato que não exige especificações ligadas a um problema específico.

Além do mais, os padrões permitem que os desenvolvedores usando bem conhecidos, nomes bem entendidos para interações com _software_. Os padrões de projeto comuns podem ser aperfeiçoados com o decorrer do tempo, fazendo eles mais robustos do que projetos _Ad-hoc_.

## Padrões de Projetos Criacionais
Estes padrões de projetos são todos sobre a instanciação de classes. Este padrão pode ser mais tarde dividido entre padrões de _class-creation_ e padrões _object-creational_. Enquanto os padrões _class-creation_ usam herança efetivamente no processo de instanciação, os padrões _object-creation_ usam delegação efetivamente para fazer o trabalho.
* [Abstract Factory](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/1_creational_patterns/1_abstract_factory.md): Cria uma instância de muitas famílias de classes.
* [Construtor](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/1_creational_patterns/2_builder.md): Separa a construção do objeto da sua representação.
* [Factory Method](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/1_creational_patterns/3_factory_method.md): Cria uma instância de muitas classes derivadas.
* [Pool de Objetos](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/1_creational_patterns/4_object_pool.md): Evita aquisição desgastante e soltura de recursos reclicando objetos que não estão mais em uso.
* [Protótipo](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/1_creational_patterns/5_prototype.md): A instância completamente inicializada para ser copiada ou clonada.
* [Singleton](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/1_creational_patterns/6_singleton.md): Uma classe da qual somente uma única instância pode existir.

## Padrões Estruturais de Projetos
Estes padrões de projetos são todos sobre a composição de objetos e classes. Os padrões de criação de classes Estruturais usam herança para compor interfaces. Padrões de objetos estruturais definem maneiras de compor objetos para obter novas funcionalidades.
* [Adaptador](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/1_adapter.md): Combina interfaces de diferentes classes.
* [Ponte](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/2_bridge.md): Separa uma interface de objeto da sua implementação.
* [Composite](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/3_composite.md): Uma estrutura de árvore de objetos simples e compostos.
* [Decorador](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/4_decorator.md): Adiciona responsabilidades para objetos dinâmicamente.
* [Fachada](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/5_facade.md): A simples classe que representa um subsistema inteiro.
* [Flyweight](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/6_flyweight.md): Uma instância refinada usada para compartilhamento eficiente.
* [Dados de Classe Privada](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/7_private_class_data.md): Restringe acessos de acessador/mutador.
* [Proxy](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/2_structural_patterns/8_proxy.md): Um objeto representando outro objeto.


## Padrões Comportamentais de Projetos
Estes padrões de projeto são todos sobre a comunicação dos objetos da classes. Os padrões comportamentais de projeto se ocupam mais especificamente com a comunicação entre objetos.
* [Corrente de Responsabilidade](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/01_chain_of_responsability.md): Uma maneira de passar uma requisição entre uma cadeia de objetos.
* [Comando](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/02_command.md): Encapsula uma requisição de comando como um objeto.
* [Interpretador](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/03_interpreter.md): Uma forma de incluir elementos da linguagem no programa.
* [Iterador](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/04_iterator.md): Sequencialmente acessa os elementos de uma coleção.
* [Mediador](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/05_mediator.md): Define comunicação simplificada entre classes.
* [Memento](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/06_memento.md): Captura e restaura um estado interno de um objeto.
* [Objeto Nulo](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/07_null_object.md): Designado para agir como o valor padrão de um objeto.
* [Observador](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/08_observer.md): Uma forma de notificar alterações para um número de classes.
* [Estado](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/09_state.md): Altera o comportamento de um objeto quando o seu estado muda.
* [Estratégia](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/10_strategy.md): Encapsula um algoritmo dentro de uma classe.
* [Método Modelo](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/11_template_method.md): Define os passos exatos de um algoritmo para uma subclasse.
* [Visitante](https://github.com/henryhamon/sourcemaking/blob/master/1_design_patterns/3_behavioral_patterns/12_visitor.md): Define uma nova operação para uma classe sem fazer nenhuma mudança.


## Criticismo
O conceito de padrões de projeto foi criticado por alguns no campo da ciência de computação.

### Mirando no alvo errado
A necessidade por padrões resulta de usar linguagens ou técnicas de computadores com habilidade de abstração insuficientes. Em um processo ideal, um conceito não deve ser copiado, mas meramente referenciado. Mas se algo é referenciado ao invés de copiado, então não há um "padrão" para nomear e catalogar. Paul Graham escreveu na redação _Revenge of the Nerds_(Vingança dos Nerds).

Peter Norvig dá um argumento similar. Ele demonstra que 16 de 23 padrões no livro de Padrões de Projeto (que foi primeiramente focado em C++) foram simplificados ou eliminados (via suporte direto da linguagem) em List ou Dylan.

### Faltam Fundamentos Formais
O estudo dos padrões de projeto foi excessivamente _ad hoc_, e alguns argumentaram que o conceito dolorosamente precisa ser colocado em uma linguagem mais formal. Em OOPSLA 1999, a _Gang of Four_ foi (com a cooperação completa deles) submetida para um julgamento, para o qual eles "investiram" com inúmeros crimes contra a ciência de computação. Eles foram "condenados" por 2/3 dos "jurados" que atenderam o julgamento.

### Levam para soluções ineficientes
A ideia do padrão de projeto é uma tentativa de padronizar o que já aceitou as melhores práticas. No princípio isto pode parecer benéfico, mas na prática isto geralmente resulta em duplicação de código desnecessária. Há quase sempre uma solução mais eficiente para usar uma implementação "bem-construída" ao invés do que o padrão de projeto "apenas o suficiente".

### Não difere significativamente de outras abstrações
Alguns autores alegam que os padrões de projeto não diferem significativamente de outras formas de abstração, e que o uso de novas terminologias (emprestadas da comunidade de arquitetura) para descrever fenômenos existentes no campo da programação é desnecessário.
O paradigma do _Model-View-Controller_ é apresentado como um exemplo de "padrão" que preda o conceito de "padrões de projeto" por muitos anos. Alguns argumentam ainda que a principal contribuição da comunidade de Padrão de Projetos (e o livro _Gang of Four_) foi o uso do padrão de linguagem de Alexandre como uma forma de documentação; uma prática muitas vezes ignorada na literatura.


