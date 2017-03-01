# Obsolescência Contínua

## Problema do Anti-Padrão
A tecnologia está mudando muito rapidamente então os desenvolvedores tem dificuldade em se "manter em dia" com as versões atuais de _software_ e encontrar combinações de lançamentos de produtos que trabalhem junto.

Levando em conta que toda linha de produto comercial envolve lançamentos de novos produtos, a situação se tornou cada vez mais difícil para desenvolvedores lidarem. Encontrar lançamentos de produtos compatíveis que possam interoperar com sucesso é cada vez mais difícil.

![Obsoleto](https://sourcemaking.com/files/sm/images/obsolete.jpg)

Java é um exemplo conhecido deste fenômeno, com novas versões saindo a cada poucos meses. Por exemplo, pelo tempo que um livro de Java 1.X vai para a impressão, um novo _Java Development Kit_ torna a informação obsoleta. Java não está sozinho; muitas outras tecnologias também participam da Obsolecência Contínua.
A maioria dos exemplos que comprovam estes flagrantes são os que tem o nome do ano em suas marcas, como por exemplo o _Product98_. Desta forma, estes produtos exibem a progressão de sua obsolescência. Outro exemplo desta progressão são as tecnologias dinamicas da _Microsoft_:
* DDE
* OLE 1.0
* OLE 2.0
* COM
* ActiveX
* DCOM
* COM?

Do ponto de vista do marketing de tecnologia, existem dois fatores chave: _mindshare_ e _marketshare_. A inovação rápida necesita de atenção dedicada dos cosumidores para ficar atualizada com as últimas características, anúncios e terminologias de um produto.
Para aqueles seguindo a tecnologia, a rápida inovação contribui para o _mindshare_; em outras palavras, sempre existem novas notícias sobre uma tecnologia X. Uma vez que um _marketshare_ dominante é obtido, o rendimento primário dos fornecedores é através da obsolescência e substituição de produtos anteriores. Quanto mais rápido as tecnologias se tornam obsoletas (ou são percebidas como obsoletas), maior a renda. 

## Solução Refatorada
Um fator estabilizante importante no mercado da tecnologia é os padrões dos sistemas abertos. Um padrão de consórcio é um produto de um consenso da indústria que requer tempo e investimento.
Iniciativas conjuntas de marketing criam conscientização e aceitação do usuário a medida que as tecnologias avançam para o _mainstream_. Existe uma inércia inerente neste processo que beneficia os consumidores, uma vez que um produto de um fornecedor está conforme um padrão, é improvável que o fabricante altere as características conformes do produto.
As vantagens da rápida obsolescência da tecnologia são transitivas. Arquitetos e desenvolvedores dependem de interfaces que sejam estáveis ou que eles possam controlar. Os padrões de sistemas abertos dão uma medida de estabilidade a um mercado de tecnologia de outra forma caótico.

## Variações
O _Wolf Ticket_ Mini-Anti-Padrão descreve várias abordagens que os consumidores podem usar para influenciar a direção de um produto em direção a um um produto melhorado de qualidade. 