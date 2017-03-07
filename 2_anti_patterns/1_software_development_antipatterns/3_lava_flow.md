# Fluxo de Lava
* **Nome do Anti-Padrão:** Fluxo de Lava
* **Também conhecido como:** Código Morto
* **Escala mais frequente:** Aplicação
* **Nome da solução refatorada:** Gerenciamento de Configuração Arquitetônica
* **Tipo da solução refatorada:** Processo
* **Causas Raíz:** Avarice, avidez e preguiça
* **Forças Desequilibradas:** Gerênciamento de Funcionalidade, Performance, Complexidade
* **Evidência Anedótica:** "Oh aquilo! Bem Ray e Emil (eles não estão mais com a empresa) escreveram aquela rotina quando Jim(que deixou no mês passado) estava tentando uma solução para o código processamento de Irene (ela está em outro departamento agora, também). Eu não acho que ela é usada mais agora, mas eu não tenho certeza. Irene não documentou ela muito claramente, então nos achamos que podemos somente deixar tudo como está por enquanto. Afinal, "não se mexe em time que está ganhando", não é?!

## Segundo Plano
Em uma expedição de mineração de dados, nós começando procurar por algum discernimento no desenvolvimento de uma interface padrão para um tipo particular de sistema. O sistema que estávamos minerando era muito similar a aquele que esperávamos, eventualmente, apoiar o padrão que estávamos trabalhando. Isto foi também um sistema originado na pesquisa e altamente complexo. A medida em que "escavamos" nele, nós entrevistamos muitos dos desenvolvedores relativo a certos componentes do massante número de páginas do código mostrado para nós.

De novo e de novo, nós obtinhamos a mesma resposta: "Eu não sei para que aquela classe é; ela foi escrita antes de eu entrar aqui". Nós gradualmente percebemos que entre 30 e 50 por cento do código que compreendia este sistema tão complexo não foi compreendido ou documentado por qualquer um atualmente trabalhando nele.

Além disso, a medida que analisamos isto, nós aprendemos que o código questionável realmente não tinha nenhum propósito no sistema atual; ao invés, ele estava lá por tentativas ou abordagens anteriores por desenvolvedores a muito tempo. A equipe atual, enquanto muito brilhante, era "medrosa" para modificar ou deletar código que eles não escreveram ou que eles não sabiam o verdadeiro propósito, por medo de quebrar algo e não saber onde ou como consertá-lo.

Neste ponto, nós começando chamando estas bolhas de código "lava", referenciando a natureza fluida em que se originaram em comparação com a dureza basáltica e dificuldade em removê-la uma vez que se solidificou. De repente, ele percebeu em nós que tínhamos identificado um potencial Anti-Padrão.

Quase um ano depois, a depois de muito mais expedições de mineração de dados e esforços de _design_ de interface, nós encontramos o mesmo padrão frequentemente que estávamos rotineiramente chamando de Fluxo de Lava ao longo do departamento.

![Lava Flow](https://sourcemaking.com/files/sm/images/antipatterns/img_29.jpg) 

## Formulário Geral
O Anti-Padrão Fluxo de Lava é comumente encontrado em sistemas que se originaram como uma pesquisa mas terminaram em produção. Isto é caracterizado pelos fluxos de versões de desenvolvimento anteriores espalhadas sobre a "paisagem" de código, que agora se endureceram em uma massa de código basáltico, que não se move, geralmente inútil, que ninguém pode se lembrar muito, se de fato é alguma coisa.

Este é o resultado de desenvolvimento de tempos anteriores (talvez Jurrásico) quando, enquanto em um modo de pesquisa, os desenvolvedores tentaram muitas formas de realizar as coisas, tipicamente em uma corrida para entregar algum tipo de demonstração, lançando as práticas de projeto para os ventos e sacrificando a documentação.

``
// Esta classe foi escrita por algúem mais cedo (Alex?) para gerenciar o indexamento
// ou alguma coisa(talvez). É provavelmente importante. Não apague. Eu não acho que 
// seja usada em qualquer lugar - pelo menos não no novo módulo MacroINdexer que pode
// atualmente substituir qualquer coisa que para que este foi usado
class IndexFrame extends Frame {
  // IndexFrame constructor
  // ---------------------------
  public IndexFrame(String index_parameter_1)
  {
    // OBS: Precisa-se adicionar coisas aqui...
    super (str);
  }
  // ---------------------------
``

O resultado são muitos fragmentos de código, variáveis de classes desviadas, e procedimentos que não são claramente relacionados ao sistema no geral. De fato, estes fluxos são geralmente tão complicados em aparência e "como espaguetes"(enrolados) que eles parecem importantes, mas ninguém pode realmente explicar o que eles fazem ou porque eles existem.

As vezes, um velho, desenvolvedor herdeiro de cabelos grisalhos pode lembrar de certos detalhes, mas tipicamente, todo mundo decidiou "deixar as coisas como estão", uma vez em que o código em questão "realmente não causa nenhum dano, e pode ser realmnete crítico, e nós simplesmente não temos tempo para mexer com ele".

Embora possa ser divertido dissecar estes fluxos e estudar sua antropologia, geralmente não existem tempo suficiente na agenda para estes "meandros". Ao invés disso, os desenvolvedores geralmente tomam a rota conveniente e trabalham cuidadosamente em torno deles.

Este padrão é, contudo, incrívelmente comum em lojas de projetos "inovativos" onde a "prova de conceito" ou o código do protótipo rapidamente vão para a produção. Este é um projeto pobre, por muitas razões chave:
* Fluxos de lava são desgastantes para analisar, verificar e testar. Todo este esforço é gasto inteiramente em vão e é um desperdício absoluto. Na prática, a verificação e o teste são raramente possíveis.
* Os fluxos de lava podem ser pesados de se carregar na memória, gastando recursos importantes e impactando a performance.
* Como muitos Anti-Padrões, você perde muitas das vantagens inerentes de um projeto orientado a objetos. Neste caso, você perde a habilidade de fazer alavancagem de modularização e reusar sem futuramente proliferar os glóbulos do Fluxo de Lava.

## Sintomas e Consequências
* FVariáveis sem justificativa frequentemente e fragmentos de código no sistema.
* Complexidade não documentada, funções que parecem importantes, classes, ou segmentos que não se relacionam claramente com a arquitetura do sistema.
* Arquitetura do sistema muito perdida.
* Blocos inteiros de código comentados sem explicação ou documentação.
* Muitas áreas de código "no fluxo" ou "para ser substituido".
* Código não usado(morto), somente deixado.
* Interfaces não usadas, inexplicadas, ou obsoletas localizada em arquivos de cabeçalho.
* Se um código com Fluxo de Lava não é removido, ele pode continuar a proliferar assim que o código é reusado em outras áreas.
* Se o processo que leva para um Fluxo de Lava não é verificado, ele pode crescer exponencialmente com desenvolvedores sucessores, muito apressados ou intimidados a analisar o fluxo original, continuam a produzir novos, fluxos secundários na medida que eles tentam trabalhar ao redor dos originais, isto compõe o problema.
* Na medida em que o fluxo se compõe e se complica, ele se torna rapidamente impossível de documentar o código ou entender a sua arquitetura o suficiente para fazer melhorias.

## Causa Típicas
* Código R&D colocado na produção sem pensar em gerenciamento de configuração.
* Distribuição sem controle de código não finalizado. Implementação de muitas abordagens de teste em direção a implementar alguma funcionalidade.
* Um único desenvolvedor (lobo solitário) escreveu o código.
* Falta de gerenciamento de configuração ou conformidade com políticas de gerenciamento de processos.
* Falta de arquitetura, ou um desenvolvimento dirigido sem arquitetura. Este é especialmente prevalente com times de desenvolvimento transitórios.
* Processo de desenvolvimento repetitivo. Geralmente, os objetivos do projeto de _software_ não são claros ou mudam repetitivamente. Para lidar com estas mudanças, o projeto precisa de retrabalho, retrocesso, e desenvolver protótipos. Em resposta aos prazos de demonstração, existe uma tendência de fazer alterações apressadas no código no ar para lidar com problemas imediatos. O código nunca é limpo, deixando considerações sobre arquitetura e a documentação adiados indefinidamente.
* Marcas arquiteturais. As vezes, compromissos arquitetônicos que são feitos durante a análise de requisitos são encontrados para não funcionar após alguma quantidade de desenvolvimento. A arquitetura do sistema pode ser reconfigurada, mas estes erros _inline_ são raramente removidos. Pode até não ser possível descomentar código desnecessário, especialmente nos ambientes de desenvolvimento modernos onde centenas de arquivos individuais compreendem o código de um sistema. "Quem vai olhar todos estes arquivos? Basta ligá-los!"
 
## Exceções Conhecidas
Pequena escala, os protótipos descartáveis em um ambiente R&D são ideais para implementar o Anti-Padrão Fluxo de Lava. É essencial entregar rapidamente, e o resultado não é preciso ser sustentável.

## Solução Refatorada
Existe somente um golpe certeiro para previnir o Anti-Padrão Fluxo de Lava: garantir que a arquitetura preceda o desenvolvimento de código para a produção. Esta arquitetura precisa ser voltada para um processo gerenciamento de configuração que garanta a conformidade arquitetural e acomode "Rastejamento de missão"(mudança de requisitos).

Se a consideração arquitetônica é encurtada, finalmente, o código que é desenvolvido não é parte da arquitetura alvo, e isto é portanto redundante ou morto. Além do tempo, o código morto se torna problemático para análise, testes, e revisão. 

Em casos onde o Fluxo de Lava já existe, a cura pode ser dolorosa. Um importante princípio é evitar mudanças de arquitetura durante o desenvolvimento. Em particular, isto se aplica para a arquitetura computacional, as interfaces do _software_ que definem a solução de integração de sistemas. O gerenciamento precisa postergar até que uma arquitetura clara tenha sido definida e disseminada para os desenvolvedores.

Definir a arquitetura pode precisar de uma ou mais descobertas de atividades do sistema. A descoberta do sistema é necessário para localizar os componentes que são realmente usados e necessários para o sistema. A descoberta do sistema também identificam aquelas linhas de código que podem ser seguramente excluídas. Esta atividade é tediosa; ela requer habilidades investigativas de um experiente detetive de _software_.

Na medida em que o código suspeito é eliminado, _bugs_ são introduzidos. Quando isto acontece, é necessário resistir a vontade de corrigir imediatamente os problemas sem compreender totalmente a causa do erro. Estude as dependências. Isto irá ajudar você a definir melhor a arquitetura desejada. 

Para evitar o Fluxo de Lava, é importante definir interfaces de _software_ a nível de sistema que sejam estáveis, bem definidas, e claramente documentadas. Investimento em interfaces de _software_ de qualidade podem produzir grandes dividendos a longo prazo comparado com o custo de "martelar" os glóbulos endurecidos do código contendo o Fluxo de Lava.

Ferramentas como o Sistema de Controle de Código Fonte(_Source-Code Control System (SCCS)_) ajudam no gerenciamento da configuração. SCCS é "enpacotado" com a maioria dos ambientes Unix e providenciam a capacidade básica de gravar histórico de atualizações nos arquivos controlados pela configuração.


## Exemplo
Nós recentemente participamos em uma expedição de mineração de dados onde nós tentamos indentificar interfaces evolucionárias que resultaram de interfaces de arquitetura preliminares que nós originamos e estavam no processo de atualização.

O sistema que nós mineramos foi escolhido porque os desenvolvedores utilizaram a nossa arquitetura inicial em um único caminho que fascinou-nos: Essencialmente, eles construiram um serviço "quase-evento" de nosso _framework_ interaplicação genérico.

A medida em que nós estudamos o sistema deles, nós encontramos um grande números de segmentos de código que nos confundiu. Estes segmentes não pareciam contribuir para a arquitetura no geral que nós esperávamos encontrar. Eles eram as vezes incoesos e somente as vezes muito esparçamente documentaram.

Quando nós questionamos os desenvolvedores atuais sobre alguns destes segmentos, a resposta foi, "Oh o que? Nós não estamos usando mais aquela abordagem. Reggie estava tendando algo, mas nós arrumamos com uma maneira melhor. Eu imagino que alguns dos outros códigos de Reggie pode depender daquela coisa, então nós não apagamos nada". A medida em que procuramos mais profundamente, nós aprendemos que Reggie não está mais na instituição, e não está lá por um longo tempo, então os segmentos de código de lá tinham alguns meses de vida.

Depois de dois dias de examinação de código, nós imaginamos que a maioria do código que compunha o sistema foi na sua maioria similar ao código que nós já examinamos: completamente um Fluxo de Lava.

Nós colhemnos muito pouco que nos ajudou a articular como a arquitetura deles foi construída; portanto, era quase impossível a  


We gleaned very little that helped us articulate how their architecture actually was constructed; therefore, it was nearly impossible to mine. At this point, we essentially gave up trying to mine the code and instead focused on the current developer's explanations of what was "really" going on, hoping to somehow codify their work into interface extensions that we could incorporate into our upcoming revisions to our generic interapplication framework.

One solution was to isolate the single, key person who best understood the system they had developed, and then to jointly write IDL with that person. On the surface, the purpose of the IDL we were jointly writing was to support a crisis demonstration that was weeks away.

By utilizing the Fire Drill Mini-AntiPattern, we were able to get the systems developers to validate our IDL by using it to rapidly build a CORBA wrapper for their product for the demonstration. Many people lost a lot of sleep, but the demonstration went well. There was, of course, one side effect to this solution: We ended up with the interface, in IDL, which we had set out to discover in the first place.
Related Solutions

In today's competitive world, it is often desirable to minimize the time delay between R&D and production. In many industries, this is critical to a company's survival. Where this is the case, inoculation against Lava Flow can sometimes be found in a customized configuration-management (CM) process that puts certain limiting controls in place at the prototyping stage, similar to "hooks" into a real, production-class develop ment without the full restraining impact on the experimental nature of R&D.

Where possible, automation can play a big role here, but the key lies in the customization of a quasi-CM process that can be readily scaled into a full-blown CM control system once the product moves into a production environment. The issue is one of balance between the costs of CM in hampering the creative process and the cost of rapidly gaining CM control of the development once that creative process has birthed something useful and marketable.

This approach can be facilitated by periodic mapping of a prototyping system into an updated system architecture, including limited, but standardized inline documentation of the code.


Applicability To Other Viewpoints And Scales

The architectural viewpoint plays a key role in preventing Lava Flows initially. Managers can also play a role in early identification of Lava Flows or the circumstances that can lead to Lava Flows. These managers must also have the authority to put the brakes on when Lava Flow is first identified, postponing further development until a clear architecture can be defined and disseminated.

As with most AntiPatterns, prevention is always cheaper than correction, so up-front investment in good architecture and team education can typically ensure a project against this and most other AntiPatterns. While this initial cost does not show immediate returns, it is certainly a good investment.