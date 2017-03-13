# Protótipo
## Intenção
* Especificar os tipos de objetos para criar usando uma instancia prototipal, e criar novos objetos copiando este protótipo.
* "_Co-opt_" uma instancia de uma classe para usar como um criador de todas as instancias futuras.
* O operador ```new``` é considerado prejudicial.

## Problema
Aplicação "incomoda" a classe do objeto a ser criado em cada expressão ```new```.

## Discussão
Declare uma classe base abstrata que especifique um método "clone" puro virtual, e, mantenha um dicionário de todos as classes "clonáveis" concretas derivadas. Qualquer classe que necessite de uma capacidade de "construtor polimórfico": deriva da classe base abstrata, registra a sua instancia de protótipo, e implementa a operação ```clone()```.

O cliente então, ao invés de escrever código que invoca o operador ```new``` em um nome de classe, chama a operação "clone" na classe base abstrata, passando uma string ou dados enumerados que deriva a classe derivada concreta particular desejada.


## Estrutura
A fábrica sabe como encontrar o Protótipo correto, e cada produto sabe como gerar novas instancias dele mesmo.
The Factory knows how to find the correct Prototype, and each Product knows how to spawn new instances of itself.

![Scheme of Prototype](https://sourcemaking.com/files/v2/content/patterns/Prototype.svg)


## Exemplo
O padrão Protótipo especifica os tipos de objetos para criar usando uma instancia prototipal. Protótipos de novos produtos são geralmente construídos antes da produção completa, mas neste exemplo, o protótipo é passivo e não participa da cópia dele mesmo. A divisão mitótica de uma célula - resultando em duas células idênticas -  é um exemplo de um protótipo que executa um papel ativo em copiar ela mesmo e assim, demonstra o padrão Protótipo. Quando uma célula se divide, resulta em duas célular de um genotipo identico. Em outras palavras, a célula clona ela mesma.

![Example of Prototype](https://sourcemaking.com/files/v2/content/patterns/Prototype_example1.svg)


## Check list
1. Adicionar um método ```clone()``` para a hierarquia existente de "produto".
2. Projetar um "registro" que mantém o _cache_ de objetos de protótipo. O registro pode ser encapsulado em uma nova classe ```Factory```, ou na classe base da hierarquia do "produto".
3. Projetar um _factory method_ que: pode (ou não) aceitar argumentos, encontra o objeto de protótipo correto, chama o ```clone()``` naquele objeto, e retorna o resultado.
4. O cliente substitui todas as referências ao operador ```new``` com chamadas ao _factory method_.


## Regras de Ouro
* As vezes padrões criacionais são competidores: existem casos onde tanto Protótipo ou _Abstract Factory_ podem ser devidamente utilizados. Em outras vezes eles são complementares: _Abstract Factory_ pode guardar um conjunto de Protótipos da qual clonar e retornar objetos. _Abstract Factory_, Construtor, e Protótipo podem usar _Singleton_ na suas implementações.
* As classes _Abstract Factory_ são geralmente implementadas com _Factory Methods_, mas elas podem ser implementadas usando Protótipo.
* _Factory Method_ criação através da herança. Protótipo: criação através da delegação.
* Geralmente, projetos começam Geralmente, projetos começam usando Factory Method (menos complicado, mais customizável, subclasses proliferam) e evoluem para Abstract Factory, Protótipo ou Construtor (mais flexivel, mais complexo) na medida que o projetista descobre onde mais flexibilidade é necessária.
* Protótipo não precisa do subclassing, mas ele precisa de uma operação de Inicialização. Factory Method precisa de subclassing, mas não precisa de Inicialização. 
* Projetos que podem ter um uso "pesado" dos padrões Composto e Decorador geralmente podem se beneficiar do Protótipo também.
* Protótipo "_co-opts_" uma instancia de uma classe para usar como um criador de todas as instancias futuras.
* Protótipos são úteis quando a inicialização de objetos é desgastante, e você antica algumas poucas variações nos parâmetros de inicialização. Neste contexto, Protótipo pode evitar a desgastante "criação a partir do zero", e suporta clonagem "barata" de um protótipo pré-inicializado.
* Protótipo é o único entre os outros padrões criacionais que não precisa de uma classe - somente um objeto. Linguagens orientadas a objetos como _Self_ e _Omega_ que acabam com classes que confiam completamente em protótipos para criar novos objetos.
