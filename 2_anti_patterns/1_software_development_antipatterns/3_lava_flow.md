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

Nós colhemnos muito pouco que nos ajudou a articular como a arquitetura deles foi construída; portanto, era quase impossível para mim. Neste ponto, nós essencialmente desistimos de tentar minerar o código e ao invés de focar nas explicações dos desenvolvedores atuais do que está "realmente" acontecento, acreditando que de alguma forma codificar o trabalho deles em extensões de interface que pudessemos incorporar em nossas próximas revisões para nosso _framework_ interaplicações.

Uma solução era isolar a única, pessoa chave que melhor entendia o sistema que eles desenvolveram, e então, em seguida escrever em conjunto um IDL com aquela pessoa. Naquela superfície, a proposta do IDL que nós escrevemos em conjunto para apoiar uma demonstração de crise que durou semanas.

Utilizando o Mini-Anti-Padrão Simulação de Incêndio, nós fomos capaz de obter que os desenvolvedores do sistema validassem nosso IDL usando ele para rapidamente construir um _CORBA wrapper_ para o produto deles para a demonstração. Muitas pessoas perderam muito sono, mas a demonstração foi bem. Existia, com certeza, um efeito colateral para esta solução: Nós terminamos com a interface, em IDL, que tínhamos decidido descobrir em primeiro lugar. 


## Soluções Refatoradas
Em nosso mundo competitivo de hoje, é geralmente desejável minimizar o atraso entre R&D e produção. Em muitas indústrias, isto é crítico para a sobrevivência da compania. Quando é este o caso, a "vacina" contra o Fluxo de Lava pode as vezes ser encontrado um processo de gerenciamento de configuração customizado(CM) que coloca controles de limitação certeiros no lugar de um estágio de prototipação, similar a "ganchos" no real, desenvolvimento da classe de produção sem o impacto restritivo total sobre o caráter experimental do R&D. 

Quando possível, a automação pode desempenhar um grande papel aqui, mas a chave reside na customização de um processo _quasi-CM_ que pode ser facilmente dimensionado para um sistema de controle CM completo quando o produto se move para um ambiente de produção. O problema é os custos do balanço entre o CM dificultando o processo criativo e o custo de rápidamente ganhar controle do CM do desenvolvimento uma vez que o processo criativo fez nascer algo útil e comercializavel. 

Esta abordagem pode ser facilitada por um mapeamento periódico de um sistema de prototipagem em uma arquitetura de sistema atualizada, incluindo limitada, mas padronizada documentação _inline_ no código.


## Aplicabilidade para outros Pontos de Vista e Medidas
O ponto de vista arquitetural desempenha um papel importante prevenindo Fluxos de Lava inicialmente. Gerentes pode também desempenhar um papel na identificação precoce de Fluxos de Lava ou as circunstâncias que podem levar a um Fluxo de Lava. Estes gerentes podem também ter a autoridade para colocar os freios quando o Fluxo de Lava é primariamente identificado, adiando desenvolvimentos futuros até que uma arquitetura clara pode ser definida e disseminada.

Como a maioria dos Anti-Padrões, prevenção é sempre mais barata do que correção, então investimentos em boa arquitetura e educação da equipe pode tipicamente garantir um projeto contra a maioria de outros Anti-Padrões. Enquanto este custo inicial não mostra retornos imediatos, ele é certamente um bom investimento.
