# Adaptador
## Intenção
* Converter a interface de uma classe em uma outra interface que o cliente espera. O adaptador permite que classes trabalhem juntas, que anteriormente, não poderiam devido a incompatibilidade de interfaces.
* Encapsula uma classe existente com uma nova interface.
* Inpedância corresponde a um componente antigo para um novo sistema.

## Problema
Um componente "da prateleira" funcionalidades atraentes que você gostaria de re-usar, mas a sua "visão de mundo" não é compatível com a filosofia e arquitetura do sistema atualmente sendo desenvolvido.

## Discussão
A reutilização sempre foi dolorosa e elusiva. Uma razão tem sido a tribulação de projetar algo novo, enquanto reusando algo antigo. Sempre há uma coisa que não se dá muito bem entre o velho e o novo. Isto pode ser em dimensões físicas ou não. Pode ser _timing_ ou sincronização. Podem ser suposições infelizes ou padrões concorrentes. É como o problema de inserir o novo _plug_ elétrico de 3 pinos em uma tomada antiga de 2 pinos, algum tipo de adaptador é necessário.

![Exemplos de Adaptador no Mundo Físico](https://sourcemaking.com/files/v2/content/patterns/Adapter_realexample.svg)

Adaptador é sobre criar uma abstração intermediária que traduz, ou mapeia, os componentes antigos para o novo sistema. Os clientes chamam os métodos no objeto do adaptador que redireciona eles em chamadas para o componente antigo. Esta estratégia pode ser implementada tanto com herança, como agregação.
O adaptador funciona como um encapsulamento ou modificador de uma classe existente. Ele providencia uma visão diferente ou traduzida de uma classe.

## Estrutura
Abaixo, o método _display_ de um componente Retângulo legado espera receber os parâmetros "x,y,w,h". Mas o cliente quer passar "superior esquerdo x e y" e "inferior direito x e y". Esta incongruência pode ser reconciliada adicionando um nível adicional de indireção - o objeto Adaptador.

![Exemplo Retângulo](https://sourcemaking.com/files/v2/content/patterns/Adapter_1.svg)

O adaptador pode ser também pensado como um "encapsulamento".
![Exemplo Wrapper](https://sourcemaking.com/files/v2/content/patterns/Adapter.svg)


## Exemplo
O padrão do Adaptador permite classes incompatíveis trabalharem juntas convertendo a interface de uma classe em uma interface esperada pelos clientes. Chaves de soquete são um exemplo de adaptador. Um soquete se junta a uma chave catraca, desde que o tamanho da unidade seja o mesmo. Os tamanhos da unidade padrão dos EUA são 1/2" e 1/4". Obviamente, uma unidade de 1/2" não se encaixa em uma chave 1/4" a menos que seja usado um adaptador.

![Exemplo Chaves e Adaptadores](https://sourcemaking.com/files/v2/content/patterns/Adapter_example1.svg)

## Check List
1. Identificar os jogadores: o(s) componente(s) que deseja ser acomodado (Cliente) e o componente que precisa do adaptador.
2. Identificar a interface que o cliente necessita.
3. Projetar uma classe de encapsulamento que possa conectar o adaptado ao cliente.
4. A classe adaptadora/encapsuladora "tem uma" instância da classe adaptada.
5. A classe adaptadora/encapsuladora "mapeia" a interface do cliente para a interface do adaptado. 
6. O cliente usa (é acoplado) a nova interface.

## Regras de Ouro
* O adaptador faz as coisas funcionar depois que elas são projetadas; Pontes fazem elas funcionar antes disto.
* Pontes são primeiramente projetadas para permitir que a abastração e a implementação variem independentemente. O adaptador é relacionado para fazer classes não relacionadas trabalhar juntas.
* O adaptador fornece uma interface diferente para o seu assunto. Proxy providencia a mesma interface. _Decorator_ fornece uma interface melhorada.
* Adaptador destina-se para alterar a interface de um objeto existente. _Decorator_ melhora outro objeto sem alterar a sua interface. _Decorator_ é, portanto, mais transparente para uma aplicação do que um adaptador é. Como uma consequência, _Decorator_ suporta composição recursiva, a qual não é possível somente com adaptadores puros.
* Fachada define uma nova interface, enquanto o adaptador reutiliza uma interface antiga. Lembre-se que o adaptador faz com que duas interfaces existentes funcionem em conjunto, em vez de definir uma inteiramente nova.
