# Construtor
## Intenção
* Separar a construção de um objeto completo da sua representação então o mesmo processo de construção pode criar diferentes representações.
* Analisar uma representação complexa, criar um de muitos alvos.


## Problema
Uma aplicação precisa criar os elementos de uma agregação complexa. A especificação para a agregação existe somente em um armazenamento secundário e uma de muitas representações precisam ser construídas no armazenamento primário.

## Discussão
Separar o algoritmo para interpretação (isto é, ler e analisar) um mecanismo de persistência armazenado (por exemplo, arquivos RTF) do algoritmo para construir e representar um de muitos produtos alvo (por exemplo, ASCII, TeX, widget de texto). O foco/distinção está na criação de agragados complexos. 

O "diretor" invoca os serviços do "construtor" como ele interpreta o formato externo. O "construtor" cria parte do objeto complexo cada vez que ele é chamado e mantém todos os estados intermediários. Quando o produto é finalizado, o cliente obtém o resultado do "construtor".

Oferece um controle mais refinado sobre o processo de construção. Ao contrário de padrões criacionais que constroem produtos de uma vez só, o padrão Construtor constrói o produto passo a passo sobre o controle do "diretor".

## Estrutura
O leitor encapsula a análise de entrada comum. A hierarquia do Construtor faz possível a criação polimórfica de muitas representações peculiares de alvos.
![Builder](https://sourcemaking.com/files/v2/content/patterns/Builder.svg)

## Exemplo
O padrão Construtor separa a construção de um objeto complexo da sua representação então o mesmo processo de contrução pode criar diferentes representações. Este padrão é usado por restaurantes _fast food_ para construir lanches de crianças. O lanche das crianças tipicamente consiste de um item principal, um item secundário, uma bebida, e um brinquedo (por exemplo, um hamburguer, fritas, Coca, e um dinossauro de brinquedo). Note que pode haver variação do conteúdo do lanche das crianças, mas o processo de construção é o mesmo. 
Se um cliente pede um hamburguer, x-burguer, ou x-frango, o processo é o mesmo. O empregado no balcão dirige a "tripulação" para montar um item principal, item secundário e brinquedo. Estes itens são então colocados no saquinho. A bebida é colocada em um copo e fica fora do saco. Este mesmo processo é usado em restaurantes concorrentes.
![Example of Builder](https://sourcemaking.com/files/v2/content/patterns/Builder_example1.svg)


## Check list
1. Decidir se é uma entrada comum e quantas representações possível (ou saídas) é o problema em questão.
2. Encapsular a análise de entradas comuns em uma classe Leitora.
3. Desenvolva um protocolo padrão para criar todas as representação de saídas possíveis. Capture as etapas deste protocolo em uma interface Construtora.
4. Defina uma classe Construtora derivada para cada representação do "alvo".
5. O cliente cria um objeto Leitor e um objeto Construtor, e registra o último com o primeiro.
6. O cliente solicita ao Leitor para "construir".
7. O cliente solicita ao Construtor para retornar o resultado.
 

## Regras de Ouro
* As vezes os padrões criacionais são complementares: Construtor pode usar um dos outros padrões para implementar quais componentes serão construídos. _Abstract Factory_, Construtor, e Protótipo podem usar _Singleton_ na sua implementação.
* Construtor foca em construir um objeto complexo passo a passo. _Abstract Factory_ enfatiza uma família de objetos de produtos (tanto simples quanto complexos). Construtor retorna o produto como uma etapa final, mas na medida em que a _Abstract Factory_ está em causa, o produto é devolvido imediatamente.
* Construtor geralmente constrói um Composto.
* Geralmente, projetos começam
Geralmente, projetos começam usando _Factory Method_ (menos complicado, mais customizável, subclasses proliferam) e evoluem para _Abstract Factory_, Protótipo ou Construtor (mais flexivel, mais complexo) na medida que o projetista descobre onde mais flexibilidade é necessária.