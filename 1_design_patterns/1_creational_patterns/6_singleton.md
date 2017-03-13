# Singleton

## Intenção
* Garantir que uma classe tenha apenas uma instancia, e prover um ponto global de acesso para ela.
* Encapsuladas "inicialização _just-in-time_" ou "inicialização no primeiro uso".

## Problema
Aplicação precisa de uma, e somente uma, instancia de um objeto. Adicionalmente, inicialização "pregiçosa"(_lazy_) e acesso global são necessários.

## Discussão
Fazer a classe de uma simples instância de objeto responsável por criação, inicialização, acesso, e aplicação. Declare a instancia como um membro de dados staticos privados(```private```). Providencie uma função pública estática que encapsule todo o código de inicialização, e dê acesso para a instancia.

O cliente chama a função acessora (usando o nome da classe e operador de resolução de escopo) sempre que uma referência a uma instancia única é necessária.

_Singleton_ somente deve ser considerado se todos os três dos sequintes critérios forem satisfeitos:
* A propriedade da instancia única não pode ser razoavelmente atribuída.
* Inicialização "preguiçosa" é desejável.
* O acesso global não é fornecido de outra forma.

Se a propriedade de uma simples instancia, quando e onde a inicialização ocorre, e o acesso global não são problemas, _Singleton_ não é suficientemente interessante.

O padrão _Singleton_ pode ser extendido para suportar acesso para um número específico de instancias específico da aplicação.

A abordagem "acessor de função de membro estático" não irá suportar _subclassing_ da classe _Singleton_. Se é desejado _subclassing_, consulte a discussão no livro.

Deleção de uma instancia/classe _Singleton_ é um problema de projeto não-trivial. Veja "_To Kill A Singleton_" de John Vlissides para uma discussão.


## Estrutura

![Scheme of Singleton](https://sourcemaking.com/files/v2/content/patterns/singleton1.svg)

Faça a classe de simples instancia responsável pelo acesso e "inicialização no primeiro uso". A única instancia é um atributo estático privado. A função acessora é um método estático público.

![Scheme of Singleton](https://sourcemaking.com/files/v2/content/patterns/Singleton.svg)

## Exemplo
O padrão _Singleton_ garante que uma classe somente tenha uma instancia e fornaça um ponto de acesso global para aquela instância. Isto é chamado depois que o _Singleton_ é definido, o que é definido para user um conjunto contendo um elemento. O escritório do Presidente dos Estados Unidos é um _Singleton_. A Constituição dos Estados Unidos especifica os meios pelos quais um presidente é eleito, limita os termos do escritório, e define a ordem de sucessão. Como um resultado, pode haver no máximo um presidente ativo ao mesmo tempo. Independentemente da identidade pessoal do presidente ativo, o título, "O Presidente dos Estados Unidos" é um ponto de acesso global que identifica a pessoa no escritório.

![Example of Singleton](https://sourcemaking.com/files/v2/content/patterns/Singleton_example1.svg)


## Check list
1. Defina um atributo estático privado na classe de "instancia simples".
2. Defina uma função acessora estática pública na classe. 
3. Faça "inicialização preguiçosa" (criação no primeiro uso) na função acessora.
4. Defina todos os construtores para serem ```protected``` ou ```private```.
5. Clientes somenete podem usar a função acessora para manipular o _Singleton_.


## Regras de Outo
* _Abstract Factory_, Construtor e Protótipo podem usar _Singleton_ na sua implementação.
* Objetos da Fachada são geralmente _Singletons_ porque somente um objeto de Fachada é necessário.
* Objetos de Estado são geralmente _Singletons_.
* A vantagem de _Singleton_ sobre variáveis globais é que você tem certeza absoluta do número de instancias quando você usa _Singleton_, e, você pode mudar a sua mente e gerenciar qualquer número de instancias.
* O padrão de projeto _Singleton_ é um dos padrões mais usados inapropriadamente. _Singletons_ são feitos para serem usados quando uma classe precisa ter exatamente uma instancia, nem mais, nem menos. Projetistas frequentemente usam _Singletons_ como uma tentativa fracassada de substituir variáveis globais. Uma _Singleton_ é, para intenções e propósitos, uma variável global. A _Singleton_ não elimina a global; ela meramente a renomeia.
* Quando o _Singleton_ não é necessário? Resposta curta: na maioria do tempo. Reposta longa: quando é mais simples passar um recurso de um objeto como uma referencia para os objetos que precisam dela, ao invés de deixar que objetos acessem o recurso globalmente. O problema real com _Singletons_ é que eles dão-lhe uma desculpa tão boa para não pensar cuidadosamente sobre a visibilidade adequada de um objeto. Encontrar o equilíbrio de exposição e proteção para um objeto é crítico para manter a flexibilidade.
* Nosso grupo teve um hábito ruim de usar dados globais, então eu fiz um grupo de estudo em _Singleton_. A proxima coisa que eu sabia _Singletons_ apareceram todo lugara e nenhum dos problemas relacionados a dados globais foram embora. A resposta para a questão dos dados globais não é, "Faça isto um _Singleton_." a resposta é, "Porque diabos você está usando dados globais?" alterando o nome não muda o problema. De fato, isto pode fazê-lo ainda pior porque isto dá a oportunidade de dizer, "Bem eu não estou fazendo aquilo, eu estou fazendo isto" - mesmo que isto e aquilo seja a mesma coisa.