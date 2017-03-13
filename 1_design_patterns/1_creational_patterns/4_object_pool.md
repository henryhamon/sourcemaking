# Pool de Objetos
## Intenção
O _pooling_ de objetos pode oferecer um aumento de performance significante; na sua maioria é efetivo em situações onde o custo de inicialização de uma classe é alto, a taxa de instanciação de uma classe é alto, e o número de instanciações em uso por um tempo é baixo.

## Problema
_Pools_ de Objetos (também conhecidos como _pools_ de recursos) são usados para gerenciar o _caching_ de objetos. Um cliente com acesso a um _pool_ de objetos pode evitar criar novos Objetos simplesmente solicitando ao _pool_ por um que já esteja instanciado. Geralmente o _pool_ irá ser um _pool_ crescente, ou seja o próprio _pool_ criará novos objetos se o _pool_ estiver vazio, ou nós podemos ter um _pool_, que restrinja o número de objetos criados.

Isto é desejável para manter todos os objetos reutilizáveis que não estão atualmente em uso pelo mesmo _pool_ de objetos então eles podem ser gerenciados por uma política coerente. Para alcançar isto, a classe de _Pool_ Reutilizável é projetada para ser um _singleton_.

## Discussão
O _Pool_ de Objetos permite outros objetos "_check out_" do seu _pool_, quando estes objetos não são mais necessários pelo seus processos, eles são retornados para o _pool_ para serem reutilizados.

Contudo, nós não queremos que um processo precise esperar por um objeto particular para ser liberado, então o _Pool_ de Objetos também instância o novos objetos na medida que eles são necessários, mas também precisa implementar uma facilidade para limpar objetos não usados periodicamente.

## Estrutura
A ideia geral para o padrão do _Pool_ de Conexão é que se instancias de uma classe podem ser reutilizadas, você evita criar instancias da classe reutilizando elas.

The general idea for the Connection Pool pattern is that if instances of a class can be reused, you avoid creating instances of the class by reusing them.

![Object Pool scheme](https://sourcemaking.com/files/v2/content/patterns/Object_pool1.svg)

* ```Reutilizável``` - Instancias de classes neste papel colaboram com outros objetos por uma quantia limitada de tempo, então eles não são mais necessários para essa colaboração.
* ```Cliente``` - Instancias de classes neste papel usam objetos Reutilizáveis.
* ```Pool Reutilizável``` - Instancias de classes neste papel gerenciam objetos Reutilizáveis para usá-los pelo objetos Cliente.
   
Usualmente, é desejável manter todos os objetos Reutilizáveis que não estão atualmente no mesmo _pool_ de objetos então eles podem ser gerenciados por uma política coerente. Para conseguir isto, a classe do _ReusablePool_ é projetada para ser uma classe _singleton_. O(s) seu(s) construtor(es) são _private_, o que força outras classes a chamar o método _getInstance_ para obter uma instância da classe _ReusablePool_.

Um objeto Cliente chama o método _acquireReusable_ do objeto do _Pool_ Reutilizável quando ele precisa de um objeto Reutilizável. Um objeto _ReusablePool_ mantém uma coleção de objetos Reutilizáveis. Ele usa a coleção de objetos Reutilizáveis para conter um _pool_ de objetos Reutilizáveis_ que não estão atualmente em uso. 

Se existe algum objeto Reutilizável no _pool_ quando o método _acquireReusable_ é chamado, ele remove um objeto Reutilizável do _pool_ e o retorna. Se o _pool_ está vazio, então o método _acquireReusable_ cria um objeto Reusável se ele puder. Se o método _acquireReusable_ não puder criar um novo objeto Reutilizável, então ele esperá até que um objeto Reutilizável é retornado para a coleção.

Objetos cliente passam um objeto Reutilizável para um método _releaseReusable_ do objeto _ReusablePool_ quando eles terminaram o processamento com o objeto. O método _releaseReusable_ retorna um objeto reutilizável para o _pool_ de objetos reutilizáveis que não estão em uso. 

Em muitas aplicações do padrão do Pool de Objetos, existem razões para limitar o número total de objetor Reutilizáveis que podem existir. Nestes casos o objeto _ReusablePool_ que cria objetos reutilizáveis é responsável por não criar mais do que um  número máximo especificado de objetos reutilizáveis. Se objetos de _Pool_ Reutilizável são responsável por limitar o número de objetos que eles irão criar, então a classe do _Pool_ Reutilizável terá um método para especificar o número máximo de objetos que serão criados. O método é indicado no diagrama acima como _setMaxPoolSize_.

## Exemplo
O padrão do _Pool_ de Objetos é similar a um depósito de um escritório. Quando um empregado é contratado, o gerente do escritório precisa preparar um espaço de trabalho para ele. Ela calculá se há ou não um equipamento de reposição no depósito do escritório. Se existir, ela o usa. Se não, ela cria uma requisição para comprar um novo equipamento da _Amazon_. No caso de um empregado ser demitido, o seu equipamento é movido para o depósito, onde ele pode ser pego quando um novo local de trabalho for necessário.

![Object Pool example](https://sourcemaking.com/files/v2/content/patterns/Object_pool_example1.svg)


## Check list
* Criar a classe do ```_Pool_ de objetos``` com um array privado de ```Objetos``` dentro dela.
* Criar os métodos ```acquire``` e ```release``` na classe do _Pool_ de Objetos.
* Tenha certeza que o seu _Pool_ de Objetos é _Singleton_.


## Regras de Ouro
* O padrão _Factory Method_ pode ser usado para encapsular a criação lógica para objetos. No entando, ele não gerencia eles depois da sua criação, o padrão do _pool_ de objetos mantém um registro dos objetos que ele cria.
* _Pools_ de Objetos são geralmente implementados como _Singletons_.
