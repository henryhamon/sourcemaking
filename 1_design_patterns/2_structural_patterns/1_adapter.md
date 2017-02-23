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

***TODO - Falta terminar a tradução!