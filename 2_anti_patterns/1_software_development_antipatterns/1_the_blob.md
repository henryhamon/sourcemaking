# A Bolha
* **Nome do Anti-Padrão:** A Bolha
* **Também conhecido como:** _Winnebago and The God Class_
* **Escala mais frequente:** Aplicação
* **Nome da solução refatorada:** Refatoramento de responsabilidades
* **Tipo da solução refatorada:** _Software_
* **Causas Raíz:** Preguiça e pressa
* **Forças Desequilibradas:** Gerênciamento de Funcionalidade, Performance, Complexidade
* **Evidência Anedótica:** "Esta é a classe que é realmente o coração de nossa arquitetura."

## Segundo Plano
Você se lembra do filme original em preto e branco _The Blob_ (A bolha)? Talvez você somente tenha visto o _remake_ atual. Em ambos os casos, a linha da história é quase a mesma: Um gotejante, alieníjena que parece uma gelatina que veio do espaço de alguma forma para a terra.
Sempre que a gelatina comia coisas (geralmente desavisados), ela crescia. Enquanto isso, terráqueos incrédulos entraram em pânico e ignoraram o cientista maluco que sabia o que estava acontecento. Muito mais pessoas foram comidas antes delas se darem conta. a Bolha crescia tanto que ameaçava destruir todo o planeta.
O filme é uma boa analogia para o Anti-Padrão Bolha, o qual é conhecido por consumir arquiteturas inteiras de orientação a objeto.
![A Bolha](https://sourcemaking.com/files/v2/content/antipatterns/blob-2x.png) 

## Formulário Geral
A Bolha é encontrada em projetos onde existe uma classe que monopoliza o processamento, e outras classes que primariamente encapsulam dados. Este Anti-Padrão é caracterizado por um diagrama de classes composto de uma simples classe controladora complexa cercada por simples classes de dados. O problema chave aqui é que a maioria das responsabilidades são alocadas para uma simples classe.

No geral, a Bolha é um projeto procedural, embora possa ser representado usando a notação de objeto e implementado em linguagens orientadas a objetos. Um projeto procedural separa o processamento dos dados, enquanto que em um projeto orientado a objetos os modelos de dados e o processamento são fundidos, juntamente com partições.

A Bolha contém a maioria do processamento, e os outros objetos contém os dados. Arquiteturas com a Bolha tem separado o processo dos dados; em outras palavras,


The Blob contains the majority of the process, and the other objects contain the data. Architectures with the Blob have separated process from data; in other words, they are procedural-style rather than object-oriented architectures.

![blob 2-2x](https://sourcemaking.com/files/v2/content/antipatterns/Blob%20-%202-2x.png)

A Bolha pode ser resultado de alocação de requisitos inapropriada. Por exemplo, a Bolha pode ser um módulo de um _software_ que recebe responsabilidades que sobrepõe a maioria das outras partes do sistema para controle do sistema ou o gerenciamento do sistema. 
A Bolha é também frequentemente um resultado de um desenvolvimento iterativo onde o código de prova de conceito evolui ao longo do tempo em um protótipo, e eventualmente, um sistema de produção. Isto é geralmente agravado pelo uso principalmente de linguagens de programação _GUI-centric_, como Visual Basic, que permite uma simples forma de evoluir a sua funcionalidade, e portanto, durante o desenvolvimento incremental ou prototipagem. 

A alocação de responsabilidades não é reparticionada durante a evolução do sistema, então aquele módulo acaba ficando predominante. A Bolha é geralmente acompanhada de código desnecessário, fazendo ficar difícil de diferenciar entre uma funcionalidade útil da classe Bolha e código legado que não é mais usado(veja o Anti-Padrão _Lava Flow_ ou fluxo de lava).

## Sintomas e Consequências
* Uma simples classe com um grande número de atributos, operações, ou ambos. Uma classe com 60 ou mais atributos e operações geralmente indica a presença da Bolha.
* Uma coleção disparada de atributos não relacionados e operações encapsuladas em uma única classe. Uma falta geral de coesão dos atributos e operações é típica da Bolha.
* Uma simples classe controladora com simples associadas, classes de dados.
* Uma ausência de projeção orientada a objetos. Um loop principal do programa dentro da classe Bolha associado a objetos de dados relativamente passivos. Uma simples classe controladora geralmente encapsula a funcionalidade de aplicativos internos, bem como um programa principal procedural.
* Um projeto legado que não foi devidamente refatorado em um projeto orientado a objetos.
* A Bolha compromete as vantagens inerentes de um projeto orientado a objetos. Por exemplo, a Bolha limita a habilidade de modificar o sistema sem afetar a funcionalidade de outros objetos encapsulados. Modificações na Bolha afetam o extenso software dentro do encapsulamento da Bolha. Modificações para outros objetos no sistema também irão provavelmente impactar o software na Bolha.
* A classe da Bolha é tipicamente muito complexa para reusar e testar. Isto pode não ser eficiente, ou introduzir uma complexidade excessiva ao reuso da Bolha para subconjuntos de sua funcionalidade.
* A classe da Bolha pode ser pesada de se carregar na memória, usar recursos excessivos, mesmo para operações simples.

## Causas Típicas
* Falta de uma arquitetura orientada a objetos. Os projetistas podem não ter um entendimento adequado dos principios da orientação a objetos. Alternativamente, a equipe pode não possuir habilidades de abstração apropriadas.
* Falta de (qualquer) arquitetura. A ausência de definição de componentes do sistema, suas integrações, e o uso específico das linguagens de programação selecionadas. Isto permite que os programas evoluam de forma _ad hoc_, porque as linguagens de programação são usadas para outros fins, e não para os que foram destinadas. 
* Falta de aplicação da arquitetura. As vezes este Anti-Padrão cresce acidentalmente, mesmo depois de uma arquitetura razoável ter sido planejada. Isto pode ser o resultado de uma revisão de arquitetura inadequada. Isto é especialmente prevalente quando as equipes de desenvolvimento são novas na orientação a objetos.
* Intervenção muito limitada. Em projetos interativos, desenvolvedores tendem a adicionar pequenas peças de funcionalidade para classes que já estão funcionando, ao invés de adicioná-las a novas classes, or revisar a hierarquia da classe para uma alocação mais efetiva de responsabilidades.
* Desasrte especificado. As vezes a Bolha resulta da forma com que os requisitos são especificados. Se os requerimentos ditam uma solução procedural, então os compromissos arquiteturais podem ser feitos durante a análise de requisitos que são difíceis de mudar. Definindo a arquitetura do sistema como parte da análise de requisitos é geralmente inapropriado, e frequentemente leva para o Anti-Padrão Bolha, ou pior  
  
## Exceções Conhecidas
A Bolha - Anti-Padrão é aceitável quando envolvendo sistemas legados. Onde não é necessário o particionamento de _software_, somente uma camada final de código para fazer o sistema legado ser mais acessível.

## Solução Refatorada
Como a maioria dos Anti-Padrões desta seção, a solução envolve uma forma de refatoramento. A chave é mover o comportamento para longe da Bolha. Pode ser apropriado reatribuir o comportamento a alguns dos objetos de dados encapsulados de uma maneira que torna esses objetos mais capazes e a  Bolha menos complexa. O método para as responsabilidades de refatoração é descrito a seguir:
1. Identifique o categorize os atributos e operações relacionados de acordo com os contratos. Estes contratos precisam ser coesos de forma que eles todos direcionem para um foco comum, comportamento, ou função dentro do sistema no geral. Por exemplo, um diagrama de biblioteca do sistema é representado com uma potencial classe Bolha chamada _LIBRARY_.

No exemplo mostrado na figura 1, a classe _LIBRARY_ encapsula a soma de todas as funcionalidades do sistema. Assim sendo, o primeiro passo é identifica conjuntos de operações e atributos coesos que representam contratos. Neste caso, nós podemos coletar operações relacionadas ao gerenciamento de catalogo, como _Sort-Catalog_ and _Search-Catalog_.
Nós podemos também idenficiar todas as operações e atributos relacionados a itens individuais, como _Print-Item_, _Delete-Item_, e assim por diante.
![Figura 1](https://sourcemaking.com/files/v2/content/antipatterns/Blob2%20-%203-2x.png)
Figura 1 


![Figura 2](https://sourcemaking.com/files/v2/content/antipatterns/Blob2%20-%204-2x.png)
Figura 2 

2. O segundo passo é procurar por "lares naturais" para estas coleções de funcionalidades baseadas em contratos e migrá-las para lá. Neste exemplo, nós coletamos operações relacionadas aos catalogos e migramos elas da classe _LIBRARY_ e movemos elas para a classe _CATALOG_.

Nós fazemos o mesmo com operações e atributos relacionados aos itens, movendo eles para a classe _ITEM_. Ambos simplificam a classe _LIBRARY_ e fazem as classes _ITEM_ e _CATALOG_ mais simples do que tabelas de dados encapsulados. O resultado é um melhor modelo de orientação a objeto.
![Figura 3](https://sourcemaking.com/files/v2/content/antipatterns/Blob2%20-%205-2x.png)
Figura 3

3. O terceiro passo é remover todos as "muito-acoplados", ou redundantes, "indiretas". No exemplo, a classe _ITEM_ é inicialmente acoplada a classe _LIBRARY_, onde cada item realmente pertence a _CATALOG_, que ao mesmo tempo pertence a _LIBRARY_.
4. Em seguida, onde for apropriado, nós migramos os associados para as classes derivadas para uma classe base comum. No exemplo, uma fez que uma acoplada foi removida entre as classes _LIBRARY_ e _ITEM_, nós precisamos mirgrar _ITEM_s para _CATALOG_s, como mostrado na figura 4.
![Figura 4](https://sourcemaking.com/files/v2/content/antipatterns/Blob2%20-%206-2x.png)
Figura 4

5. Finalmente, nós removemos todas as associações temporárias, substituindo-as, conforme apropriado, por especificadores de tipo para atributos e argumentos de operação;

Em nosso exemplo, um _Check-Out-Item_ ou um _Search-For-Item_ seriam um processo temporário, e poderiam ser movidos em um classe temporária separada com atributos locais que estabeleceriam a localização específica ou critério de pesquisa para uma instância específica de um _check-out_ ou pesquisa.


## Variações
As vezes, com um sistema composte de classe da Bolha e os seus objetos de dados de suporte, muito trabalho foi investido para habilitar a refatoração da arquitetura da classe. Uma abordagem alternativa pode estar disponível que proporcione uma solução de "80%".
Ao invés de uma refatoração da "cabeça aos pés" da hierarquia da classe inteira, é possível reduzir a classe da Bolha de uma classe controladora para uma classe coordenadora. A classe Bolha original gerencia a funcionalidade do sistema; As classes de dados são extendidas com parte do seu próprio processamento.
As classes de dados operam em direção da classe modificada coordenadora. Este processo pode permitir a retenção da hierarquia da classe original, exceto para as migrações de funcionalidades de processamento da classe Bolha para alguma das classes de dados encapsuladas.
Riel identifica duas grandes formas do Anti-Padrão Bolha. Ele as chama estas duas formas de Classes de Deus: Forma Comportamental e Formulário de Dados.
A forma comportamental é um objeto que contém um processo centralizado que interaje com a maioria das outras partes do sistema. O Formulário de Dados é um objeto que contém dados compartilhados usados pela maioria de outros objetos no sistema. Riel introduz um número de heurísticas da orientação a objeto para detectar problemas e refatoração de projetos das Classes de Deus.

## Aplicabilidade para outros Pontos de Vista e Medidas
Ambos pontos de vista, arquitetônico e administrativo, desempenham papéis fundamentais na prevenção do Anti-Padrão Bolha. A prevenção da Bolha pode exigir policiamento contínuo da arquitetura para garantir uma distribuição adequada das responsabilidades. 
É através de um ponte de vista arquitetônico que uma Bolha emergente é reconhecida. Com uma análise e processo de projeção orientado a objetos maduro, e um gerente de alerta que entende o projeto, os desenvolvedores podem impedir o aparecimento de uma Bolha.
O fator mais importante é que, na maioria dos casos, é muito menos desgastante criar um projeto apropriado do que retrabalhar o projeto depois da implementação. Um investimento inicial em uma boa arquitetura e a educação do time pode garantir que um projeto não seja afetado pela Bolha e a maioria dos outros Anti-Padrões.
Pergunte a qualer vendedor de seguros, e ele ou lea pode-lhe dizer que a maioria de seguros é comprado depois que foi necessário por pessoas que são mais pobres, mas mais espertas.

## Exemplo
Um modulo GUI que se destina a interface com um módulo de processamento assume gradualmente a funcionalidade de processamento em segundo plano. Um exemplo disto é uma tela _PowerBuilder_ para entrada/recuperação de dados. A tela pode:
1. Mostrar dados.
2. Editar dados.
3. Fazer a validação simples de tipo. O desenvolvedor então adiciona a funcionalidade ao que foi planejado para ser o mecanismo de decisão:
    * Validação complexa.
    * Algoritmos que usam os dados validados para acessar as próximas ações.
4. O desenvolvedor então recebe novos requisitos para:
    * Extender a GUI para três formulários.
    * Fazê-lo _script-driven_ (incluindo o desenvolvimento de um mecanismo de script).
    * Adicionar novos algoritmos para o mecanismo de decisão.
        Extend the GUI to three forms.
        Make it script-driven (including the development of a script engine).
        Add new algorithms to the decision engine.

O desenvolvedor extendo o módulo atual para incorporar todas estas funcionalidades. Então ao invés de desenvolver vários módulos, um simples módulo é desenvolvido. Se a aplicação desejada é arquiteturada e projetada, é mais fácil de manter e extender.

![...](https://sourcemaking.com/files/v2/content/antipatterns/Blob3%20-%201-2x.png)
![---](https://sourcemaking.com/files/v2/content/antipatterns/Blob3%20-%202-2x.png)