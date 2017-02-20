# Ocultar Delegação
## Problema
O cliente obtém o objeto B de um campo ou método do objeto A. Então o cliente chama um método do objeto B.

![Antes](https://sourcemaking.com/images/refactoring/Hide%20Delegate%20-%20Before.png)

## Solução
Criar um novo método na classe A que delegue a chamada para o objeto B. Agora o cliente não sabe, ou depende da, classe B.

![Depois](https://sourcemaking.com/images/refactoring/Hide%20Delegate%20-%20After.png)

## Porque Refatorar
Para começar, vamos olhar a terminologia:
* Delegação - o objeto final que contém a funcionalidade necessária pelo cliente.
* Servidor - o objeto ao que o cliente tem acesso direto.

Uma cadeia de chamadas aparece quando um cliente solicita um objeto de outro objeto, então o segundo objeto solicita outro, e assim por diante. Estas sequências de chamadas envolvem o cliente em uma navegação ao longo da estrutura da classe. Qualquer alteração nestas interrelações irá precisar de alterações no lado do cliente.

## Benefícios
* Esconde a delegação do cliente. Quanto menos o código do cliente precisar saber sobre os detalhes dos relacionamentos entre objetos, mais fácil será fazer alterações no programa.

## Inconvenientes
* Se você precisar criar um número excessivo de métodos com delegação, a classe servidora arrisca ter muitos _ir - entre_ desnecessários, levando para um excesso de [Intermediários](https://sourcemaking.com/refactoring/smells/middle-man).

## Como Refatorar
1. Para cada método da classe delegada chamado pelo cliente, crie um método na classe servidora que delegue a chamada para a classe delegada.
2. Mude o código do cliente para que sejam chamados os métodos da classe servidora.
3. Se as suas alterações livrarem o cliente de precisar da classe delegada, você pode remover o método de acesso para a classe delegada para a classe servidora (O método que foi originalmente usado para acessar a classe delegada).